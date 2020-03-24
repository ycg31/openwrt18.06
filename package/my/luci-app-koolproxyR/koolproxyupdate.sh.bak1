wget 'https://houzi-.coding.net/p/my_dream/d/my_dream/git/raw/master/kp.dat' -O files/usr/share/koolproxy/data/rules/kp.dat
wget 'https://shaoxia1991.coding.net/p/yhosts/d/yhosts/git/raw/master/hosts' -O files/usr/share/koolproxy/data/rules/yhosts.txt
wget 'https://shaoxia1991.coding.net/p/yhosts/d/yhosts/git/raw/master/data/tvbox.txt' -O files/usr/share/koolproxy/data/rules/tvbox.txt
wget 'https://secure.fanboy.co.nz/r/fanboy-annoyance.txt' -O files/usr/share/koolproxy/data/rules/fanboy.txt
wget 'https://easylist-downloads.adblockplus.org/easylistchina.txt' -O files/usr/share/koolproxy/data/rules/easylistchina.txt
wget 'https://shaoxia1991.coding.net/p/koolproxyR_rule_list/d/koolproxyR_rule_list/git/raw/master/kpr_our_rule.txt' -O files/usr/share/koolproxy/data/rules/kpr_our_rule.txt
wget 'https://raw.githubusercontent.com/user1121114685/koolproxyR/master/koolproxyR/koolproxyR/data/rules/user.txt' -O files/usr/share/koolproxy/data/user.txt
cp files/usr/share/koolproxy/data/user.txt files/usr/share/koolproxy/data/rules/user.txt
wget 'https://raw.githubusercontent.com/user1121114685/koolproxyR/master/koolproxyR/koolproxyR/data/koolproxyR_ipset.conf' -O files/usr/share/koolproxy/koolproxy_ipset.conf

wget https://easylist-downloads.adblockplus.org/easylistchina+easylist.txt -O- | grep ^\|\|[^\*]*\^$ | sed -e 's:||:address\=\/:' -e 's:\^:/0\.0\.0\.0:' > files/usr/share/koolproxy/dnsmasq.adblock
sed -i '/youku/d' files/usr/share/koolproxy/dnsmasq.adblock
sed -i '/[1-9]\{1,3\}\.[1-9]\{1,3\}\.[1-9]\{1,3\}\.[1-9]\{1,3\}/d' files/usr/share/koolproxy/dnsmasq.adblock

#处理fanboy.txt
# 删除导致KP崩溃的规则
sed -i '/^\$/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/\*\$/d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 给三大视频网站放行 由kp.dat负责
sed -i '/youku.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/iqiyi.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/qq.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/g.alicdn.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/tudou.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/gtimg.cn/d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 给知乎放行
sed -i '/zhihu.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt	
# 将规则转化成kp能识别的https
cat files/usr/share/koolproxy/data/rules/fanboy.txt | grep "^||" | sed 's#^||#||https://#g' >> files/usr/share/koolproxy/data/rules/fanboy_https.txt

# 移出https不支持规则domain=
sed -i 's/\(,domain=\).*//g' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i 's/\(\$domain=\).*//g' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i 's/\(domain=\).*//g' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i '/\^$/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i '/\^\*\.gif/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i '/\^\*\.jpg/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt

cat files/usr/share/koolproxy/data/rules/fanboy.txt | grep "^||" | sed 's#^||#||http://#g' >> files/usr/share/koolproxy/data/rules/fanboy_https.txt
cat files/usr/share/koolproxy/data/rules/fanboy.txt | grep -i '^[0-9a-z]'| grep -v '^http'| sed 's#^#https://#g' >> files/usr/share/koolproxy/data/rules/fanboy_https.txt
cat files/usr/share/koolproxy/data/rules/fanboy.txt | grep -i '^[0-9a-z]'| grep -v '^http'| sed 's#^#http://#g' >> files/usr/share/koolproxy/data/rules/fanboy_https.txt
cat files/usr/share/koolproxy/data/rules/fanboy.txt | grep -i '^[0-9a-z]'| grep -i '^http' >> files/usr/share/koolproxy/data/rules/fanboy_https.txt

# 给github放行
sed -i '/github/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
# 给api.twitter.com的https放行
sed -i '/twitter.com/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
# 给facebook.com的https放行
sed -i '/facebook.com/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i '/fbcdn.net/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
# 给 instagram.com 放行
sed -i '/instagram.com/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
# 给 twitch.tv 放行
sed -i '/twitch.tv/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
# 删除可能导致卡顿的HTTPS规则
sed -i '/\.\*\//d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
# 给国内三大电商平台放行
sed -i '/jd.com/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i '/taobao.com/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt
sed -i '/tmall.com/d' files/usr/share/koolproxy/data/rules/fanboy_https.txt

# 删除不必要信息重新打包 15 表示从第15行开始 $表示结束
sed -i '15,$d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 合二归一
cat files/usr/share/koolproxy/data/rules/fanboy_https.txt >> files/usr/share/koolproxy/data/rules/fanboy.txt
# 删除可能导致kpr卡死的神奇规则
sed -i '/https:\/\/\*/d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 给 netflix.com 放行
sed -i '/netflix.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 给 tvbs.com 放行
sed -i '/tvbs.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/googletagmanager.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 给 microsoft.com 放行
sed -i '/microsoft.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 给apple的https放行
sed -i '/apple.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
sed -i '/mzstatic.com/d' files/usr/share/koolproxy/data/rules/fanboy.txt
# 终极 https 卡顿优化 grep -n 显示行号  awk -F 分割数据  sed -i "${del_rule}d" 需要""" 和{}引用变量
# 当 koolproxyR_del_rule 是1的时候就一直循环，除非 del_rule 变量为空了。	
	koolproxyR_del_rule=1
	while [ $koolproxyR_del_rule = 1 ];do
		del_rule=`cat files/usr/share/koolproxy/data/rules/fanboy.txt | grep -n 'https://' | grep '\*' | grep -v '/\*'| grep -v '\^\*' | grep -v '\*\=' | grep -v '\$s\@' | grep -v '\$r\@'| awk -F":" '{print $1}' | sed -n '1p'`
		if [[ "$del_rule" != "" ]]; then
			sed -i "${del_rule}d" files/usr/share/koolproxy/data/rules/fanboy.txt
		else
			koolproxyR_del_rule=0
		fi
  done

#处理easylistchina.txt
sed -i '/^\$/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/\*\$/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给btbtt.替换过滤规则。
sed -i 's#btbtt.\*#\*btbtt.\*#g' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给手机百度图片放行
sed -i '/baidu.com\/it\/u/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# # 给手机百度放行
# sed -i '/mbd.baidu.comd' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给知乎放行
sed -i '/zhihu.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给apple的https放行
sed -i '/apple.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/mzstatic.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt

# 将规则转化成kp能识别的https
cat files/usr/share/koolproxy/data/rules/easylistchina.txt | grep "^||" | sed 's#^||#||https://#g' >> files/usr/share/koolproxy/data/rules/easylistchina_https.txt
# 移出https不支持规则domain=
sed -i 's/\(,domain=\).*//g' files/usr/share/koolproxy/data/rules/easylistchina_https.txt
sed -i 's/\(\$domain=\).*//g' files/usr/share/koolproxy/data/rules/easylistchina_https.txt
sed -i 's/\(domain=\).*//g' files/usr/share/koolproxy/data/rules/easylistchina_https.txt
sed -i '/\^$/d' files/usr/share/koolproxy/data/rules/easylistchina_https.txt
sed -i '/\^\*\.gif/d' files/usr/share/koolproxy/data/rules/easylistchina_https.txt
sed -i '/\^\*\.jpg/d' files/usr/share/koolproxy/data/rules/easylistchina_https.txt

cat files/usr/share/koolproxy/data/rules/easylistchina.txt | grep "^||" | sed 's#^||#||http://#g' >> files/usr/share/koolproxy/data/rules/easylistchina_https.txt
cat files/usr/share/koolproxy/data/rules/easylistchina.txt | grep -i '^[0-9a-z]'| grep -v '^http'| sed 's#^#https://#g' >> files/usr/share/koolproxy/data/rules/easylistchina_https.txt
cat files/usr/share/koolproxy/data/rules/easylistchina.txt | grep -i '^[0-9a-z]'| grep -v '^http'| sed 's#^#http://#g' >> files/usr/share/koolproxy/data/rules/easylistchina_https.txt
cat files/usr/share/koolproxy/data/rules/easylistchina.txt | grep -i '^[0-9a-z]'| grep -i '^http' >> files/usr/share/koolproxy/data/rules/easylistchina_https.txt
# 给facebook.com的https放行
sed -i '/facebook.com/d' files/usr/share/koolproxy/data/rules/easylistchina_https.txt
sed -i '/fbcdn.net/d' files/usr/share/koolproxy/data/rules/easylistchina_https.txt
# 删除可能导致卡顿的HTTPS规则
sed -i '/\.\*\//d' files/usr/share/koolproxy/data/rules/easylistchina_https.txt

# 删除不必要信息重新打包 15 表示从第15行开始 $表示结束
sed -i '6,$d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 合二归一
cat files/usr/share/koolproxy/data/rules/easylistchina_https.txt >> files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给三大视频网站放行 由kp.dat负责
sed -i '/youku.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/iqiyi.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/g.alicdn.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/tudou.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/gtimg.cn/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给https://qq.com的html规则放行
sed -i '/qq.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 删除可能导致kpr卡死的神奇规则
sed -i '/https:\/\/\*/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给国内三大电商平台放行
sed -i '/jd.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/taobao.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/tmall.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给 netflix.com 放行
sed -i '/netflix.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给 tvbs.com 放行
sed -i '/tvbs.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
sed -i '/googletagmanager.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 给 microsoft.com 放行
sed -i '/microsoft.com/d' files/usr/share/koolproxy/data/rules/easylistchina.txt
# 终极 https 卡顿优化 grep -n 显示行号  awk -F 分割数据  sed -i "${del_rule}d" 需要""" 和{}引用变量
# 当 koolproxyR_del_rule 是1的时候就一直循环，除非 del_rule 变量为空了。	
	koolproxyR_del_rule=1
	while [ $koolproxyR_del_rule = 1 ];do
		del_rule=`cat files/usr/share/koolproxy/data/rules/easylistchina.txt | grep -n 'https://' | grep '\*' | grep -v '/\*'| grep -v '\^\*' | grep -v '\*\=' | grep -v '\$s\@' | grep -v '\$r\@'| awk -F":" '{print $1}' | sed -n '1p'`
		if [[ "$del_rule" != "" ]]; then
			sed -i "${del_rule}d" files/usr/share/koolproxy/data/rules/easylistchina.txt
		else
			koolproxyR_del_rule=0
		fi
  done
cat files/usr/share/koolproxy/data/rules/kpr_our_rule.txt >> files/usr/share/koolproxy/data/rules/easylistchina.txt

#处理yhosts.txt
# 删除不必要信息重新打包 0-11行 表示从第15行开始 $表示结束
# sed -i '1,11d' files/usr/share/koolproxy/data/rules/yhosts.txt

# 开始Kpr规则化处理
cat files/usr/share/koolproxy/data/rules/yhosts.txt > files/usr/share/koolproxy/data/rules/yhosts_https.txt
sed -i 's/^127.0.0.1\ /||https:\/\//g' files/usr/share/koolproxy/data/rules/yhosts_https.txt
cat files/usr/share/koolproxy/data/rules/yhosts.txt >> files/usr/share/koolproxy/data/rules/yhosts_https.txt
sed -i 's/^127.0.0.1\ /||http:\/\//g' files/usr/share/koolproxy/data/rules/yhosts_https.txt
# 处理tvbox.txt本身规则。
sed -i 's/^127.0.0.1\ /||/g' files/usr/share/koolproxy/data/rules/tvbox.txt
# 合二归一
cat  files/usr/share/koolproxy/data/rules/yhosts_https.txt > files/usr/share/koolproxy/data/rules/yhosts.txt
cat files/usr/share/koolproxy/data/rules/tvbox.txt>> files/usr/share/koolproxy/data/rules/yhosts.txt
rm -rf files/usr/share/koolproxy/data/rules/tvbox.txt


# 此处对yhosts进行单独处理
sed -i 's/^@/!/g' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i 's/^#/!/g' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/localhost/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/broadcasthost/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/broadcasthost/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/cn.bing.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给三大视频网站放行 由kp.dat负责
sed -i '/youku.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/iqiyi.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/g.alicdn.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/tudou.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/gtimg.cn/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给知乎放行
sed -i '/zhihu.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给https://qq.com的html规则放行
sed -i '/qq.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给github的https放行
sed -i '/github/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给apple的https放行
sed -i '/apple.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/mzstatic.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给api.twitter.com的https放行
sed -i '/twitter.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给facebook.com的https放行
sed -i '/facebook.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/fbcdn.net/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给 instagram.com 放行
sed -i '/instagram.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 删除可能导致kpr卡死的神奇规则
sed -i '/https:\/\/\*/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给国内三大电商平台放行
sed -i '/jd.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/taobao.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/tmall.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给 netflix.com 放行
sed -i '/netflix.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给 tvbs.com 放行
sed -i '/tvbs.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
sed -i '/googletagmanager.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 给 microsoft.com 放行
sed -i '/microsoft.com/d' files/usr/share/koolproxy/data/rules/yhosts.txt
# 终极 https 卡顿优化 grep -n 显示行号  awk -F 分割数据  sed -i "${del_rule}d" 需要""" 和{}引用变量
# 当 koolproxyR_del_rule 是1的时候就一直循环，除非 del_rule 变量为空了。
	koolproxyR_del_rule=1
	while [ $koolproxyR_del_rule = 1 ];do
		del_rule=`cat files/usr/share/koolproxy/data/rules/yhosts.txt | grep -n 'https://' | grep '\*' | grep -v '/\*'| grep -v '\^\*' | grep -v '\*\=' | grep -v '\$s\@' | grep -v '\$r\@'| awk -F":" '{print $1}' | sed -n '1p'`
		if [[ "$del_rule" != "" ]]; then
			sed -i "${del_rule}d" files/usr/share/koolproxy/data/rules/yhosts.txt
		else
			koolproxyR_del_rule=0
		fi
  done
# 删除临时文件
rm files/usr/share/koolproxy/data/rules/*_https.txt
rm files/usr/share/koolproxy/data/rules/kpr_our_rule.txt		
