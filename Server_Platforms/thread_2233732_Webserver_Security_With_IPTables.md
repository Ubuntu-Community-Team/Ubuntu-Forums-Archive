---
title: "Webserver Security With IPTables"
date: 2014-07-10
forum: Server Platforms
---

### Post by thufirhawat2 on 2014-07-10
Hello! I have a personal web server that I host with DDNS to share things with friends and family because I believe facebook to be the devil.

My server is a 14.04 using apache2, and I use fail2ban for security. The default rule for SSH works great, and I made a custom rule for http/https that will ban any IP that generates too many 404 errors. That way, if anyone is trying to guess directories that I prefer to be private, they will get banned after a couple of guesses, and this works great as well, I just have to keep pretty meticulous about making sure I have all my HTML code correct when I publish a new page or make changes, but I am pretty good about that anyway.

My concern is that at 3:00 AM every night, my logwatch is e-mailing me that I am getting this error in my apache access log:

```
114.232.151.16 - - [08/Jul/2014:03:00:10 -0400] "GET [http://hotel.qunar.com/render/hoteldiv.jsp](http://hotel.qunar.com/render/hoteldiv.jsp)?
&__jscallback=XQScript_4 HTTP/1.1" 404 457 "[http://hotel.qunar.com/](http://hotel.qunar.com/)" "Mozilla/5.0 (Windows NT 6.1; WOW64) 
AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.1916.114 Safari/537.36"

```

I am not quite savvy enough to discern what it is they are trying to do, but since it happens at the exact same time every night, I surmise that it is some kind of automated scanner that is trying to log information about my ports/services or something. Whatever it is, I do not like it, and I would prefer to not see it in my daily log reports any more, so I tried to create a custom IPFilter with Fail2ban to block this crap. I am sure I did something wrong however, because in fail2ban's logs, the rule is not even being triggered. I thought about the default apache-noscripts rule in fail2ban, but that references apache's error logs, not the access logs, and nothing is recorded in the error logs when this happens.

Here is the fail2ban filter I created named seedyhosts:

```

# Fail2Ban configuration file
#
[Definition]
failregex = <HOST> - - \[.*\] "(GET|POST).*HTTP.* hotel.qunar.com
ignoreregex =

```

And in the jail.conf I added this:

```
[
enabled = true
port = http,https
filter = seedyhosts
logpath = /var/log/apache2/access.log
bantime = -1
findtime = 90000
maxretry = 1
/CODE]

I wanted it to permanently ban the host (which is what a -1 in the bantime does to my understanding) if it retried more than once in 25 hours. 

Would I be better off instead trying to use that 457 error code it generates instead, something like this in the filter?

[CODE]
# Fail2Ban configuration file
#
[Definition]
failregex = <HOST> - - \[.*\] "(GET|POST).*HTTP.* 457
ignoreregex =

```

I am just no sure what else might generate that error and ban some IPs unexpectedly. Any help would be much appreciated, thanks.

---

### Post by SeijiSensei on 2014-07-10
Is the source always 114.232.151.16?  If so, I'd just ban the host.  Add a line to /etc/rc.local like this:
```
/sbin/iptables -I INPUT -s 114.232.151.16 -j REJECT
```
Using the "-I" switch puts this rule at the top of the ruleset so it won't interfere with anything else you have already.

I write scripts to generate iptables rulesets from lists of IP addresses.  Most of my scripts include an "evil" option:
```

EVIL=$(cat /usr/local/etc/evil)
for h in $EVIL
do
    iptables -A INPUT -s $h -j REJECT
done

```
Then I throw annoying hosts into /usr/local/etc/evil, one IP per line, and rerun the ruleset generator.

---

### Post by thufirhawat2 on 2014-07-10
Thank you! I was wondering if there was a simple way to just ban IP addresses. I looked in /etc/rc,local and it says the script is executed at the end of each multiuser runlevel, I am not sure I know what that means, how frequently would that be? Do you have any in depth documentation about how to make some of these scripts that I could reference? This is very intriguing.

Unfortunately for this scenario, the IP appears to be dynamic. It is actually different every night, which makes me think this is particularly malicious. 

If anyone has any other suggestions, I would be grateful, thank you.

---

### Post by thufirhawat2 on 2014-07-11
So I loaded a USB drive and got on a public wifi and went to the URL ([FONT="Calibri"][[COLOR=#0000ff]http://hotel.qunar.com/render/hoteldiv.jsp[/COLOR]]("http://hotel.qunar.com/render/hoteldiv.jsp")[/FONT]) that keeps pegging my server, and it prompted me to download a .js script file. Here is what the script contains:

```
{"hotCityConfig":{"domestic":["&#28909;&#38376;&#22478;&#24066;","ABCDE","FGHJ","KLMNP","QRSTW","XYZ"],"intercity":["&#28909;&#38376;&#22478;&#24066;","&#19996;&#21335;&#20122;","&#28023;&#23707;","&#20122;&#27954;","&#27431;&#27954;","&#32654;&#27954;","&#22823;&#27915;&#27954;"],"data":{"domestic":{"&#28909;&#38376;&#22478;&#24066;":{"title":"&#28909;&#38376;&#22478;&#24066;","cityList":[{"char":" ","list":[{"cityurl":"beijing_city","name":"&#21271;&#20140;"},{"cityurl":"shanghai_city","name":"&#19978;&#28023;"},{"cityurl":"guangzhou","name":"&#24191;&#24030;"},{"cityurl":"shenzhen","name":"&#28145;&#22323;"},{"cityurl":"qingdao","name":"&#38738;&#23707;"},{"cityurl":"dalian","name":"&#22823;&#36830;"},{"cityurl":"hangzhou","name":"&#26477;&#24030;"},{"cityurl":"nanjing","name":"&#21335;&#20140;"},{"cityurl":"chengdu","name":"&#25104;&#37117;"},{"cityurl":"wuhan","name":"&#27494;&#27721;"},{"cityurl":"chongqing_city","name":"&#37325;&#24198;"},{"cityurl":"sanya","name":"&#19977;&#20122;"},{"cityurl":"xiamen","name":"&#21414;&#38376;"},{"cityurl":"hongkong_city","name":"&#39321;&#28207;"},{"cityurl":"macao_city","name":"&#28595;&#38376;"}]}],"charSort":true},"ABCDE":{"title":"ABCDE","cityList":[{"char":"A","list":[{"cityurl":"aba","name":"&#38463;&#22365;"},{"cityurl":"anshan","name":"&#38797;&#23665;"},{"cityurl":"anqing","name":"&#23433;&#24198;"},{"cityurl":"anshun","name":"&#23433;&#39034;"},{"cityurl":"anyang","name":"&#23433;&#38451;"},{"cityurl":"ankang","name":"&#23433;&#24247;"},{"cityurl":"akesu","name":"&#38463;&#20811;&#33487;"},{"cityurl":"aletai","name":"&#38463;&#21202;&#27888;"}]},{"char":"B","list":[{"cityurl":"beijing_city","name":"&#21271;&#20140;"},{"cityurl":"beihai","name":"&#21271;&#28023;"},{"cityurl":"baoding","name":"&#20445;&#23450;"},{"cityurl":"baoshan","name":"&#20445;&#23665;"},{"cityurl":"baoji","name":"&#23453;&#40481;"},{"cityurl":"baishan","name":"&#30333;&#23665;"},{"cityurl":"baotou","name":"&#21253;&#22836;"},{"cityurl":"baoting","name":"&#20445;&#20141;"},{"cityurl":"bangbu","name":"&#34444;&#22496;"},{"cityurl":"binzhou","name":"&#28392;&#24030;"}]},{"char":"C","list":[{"cityurl":"chengdu","name":"&#25104;&#37117;"},{"cityurl":"chongqing_city","name":"&#37325;&#24198;"},{"cityurl":"changsha","name":"&#38271;&#27801;"},{"cityurl":"changzhou","name":"&#24120;&#24030;"},{"cityurl":"changchun","name":"&#38271;&#26149;"},{"cityurl":"changde","name":"&#24120;&#24503;"},{"cityurl":"chizhou","name":"&#27744;&#24030;"},{"cityurl":"chenzhou","name":"&#37108;&#24030;"},{"cityurl":"chaozhou","name":"&#28526;&#24030;"},{"cityurl":"cangzhou","name":"&#27815;&#24030;"}]},{"char":"D","list":[{"cityurl":"dalian","name":"&#22823;&#36830;"},{"cityurl":"dali","name":"&#22823;&#29702;"},{"cityurl":"dandong","name":"&#20025;&#19996;"},{"cityurl":"dongguan","name":"&#19996;&#33694;"},{"cityurl":"datong","name":"&#22823;&#21516;"},{"cityurl":"diqing","name":"&#36842;&#24198;"},{"cityurl":"dezhou","name":"&#24503;&#24030;"},{"cityurl":"dongying","name":"&#19996;&#33829;"},{"cityurl":"deyang","name":"&#24503;&#38451;"},{"cityurl":"daqing","name":"&#22823;&#24198;"}]},{"char":"E","list":[{"cityurl":"eerduosi","name":"&#37122;&#23572;&#22810;&#26031;"},{"cityurl":"enshi","name":"&#24681;&#26045;&#33258;&#27835;&#24030;"},{"cityurl":"ezhou","name":"&#37122;&#24030;"}]}],"charSort":true},"FGHJ":{"title":"FGHJ","cityList":[{"char":"F","list":[{"cityurl":"fuzhou_fujian","name":"&#31119;&#24030;"},{"cityurl":"foshan","name":"&#20315;&#23665;"},{"cityurl":"fangchenggang","name":"&#38450;&#22478;&#28207;"},{"cityurl":"fushun","name":"&#25242;&#39034;"},{"cityurl":"fuyang_anhui","name":"&#38428;&#38451;"},{"cityurl":"fuxin","name":"&#38428;&#26032;"},{"cityurl":"fuzhou_jiangxi","name":"&#25242;&#24030;"}]},{"char":"G","list":[{"cityurl":"guangzhou","name":"&#24191;&#24030;"},{"cityurl":"guilin","name":"&#26690;&#26519;"},{"cityurl":"guiyang","name":"&#36149;&#38451;"},{"cityurl":"ganzi","name":"&#29976;&#23388;"},{"cityurl":"ganzhou","name":"&#36195;&#24030;"},{"cityurl":"guangyuan","name":"&#24191;&#20803;"},{"cityurl":"guigang","name":"&#36149;&#28207;"},{"cityurl":"guangan","name":"&#24191;&#23433;"},{"cityurl":"gannan","name":"&#29976;&#21335;"},{"cityurl":"guyuan","name":"&#22266;&#21407;"}]},{"char":"H","list":[{"cityurl":"hangzhou","name":"&#26477;&#24030;"},{"cityurl":"huangshan","name":"&#40644;&#23665;"},{"cityurl":"huizhou_guangdong","name":"&#24800;&#24030;"},{"cityurl":"haerbin","name":"&#21704;&#23572;&#28392;"},{"cityurl":"hefei","name":"&#21512;&#32933;"},{"cityurl":"haikou","name":"&#28023;&#21475;"},{"cityurl":"huzhou","name":"&#28246;&#24030;"},{"cityurl":"huhehaote","name":"&#21628;&#21644;&#28009;&#29305;"},{"cityurl":"hengyang","name":"&#34913;&#38451;"},{"cityurl":"huludao","name":"&#33899;&#33446;&#23707;"}]},{"char":"J","list":[{"cityurl":"jiaxing","name":"&#22025;&#20852;"},{"cityurl":"jinan","name":"&#27982;&#21335;"},{"cityurl":"jinzhong","name":"&#26187;&#20013;"},{"cityurl":"jinhua","name":"&#37329;&#21326;"},{"cityurl":"jiujiang","name":"&#20061;&#27743;"},{"cityurl":"jiangmen","name":"&#27743;&#38376;"},{"cityurl":"jiaozuo","name":"&#28966;&#20316;"},{"cityurl":"jining","name":"&#27982;&#23425;"},{"cityurl":"jiuquan","name":"&#37202;&#27849;"},{"cityurl":"jinzhou","name":"&#38182;&#24030;"},{"cityurl":"jingdezhen","name":"&#26223;&#24503;&#38215;"},{"cityurl":"jilin_city","name":"&#21513;&#26519;"},{"cityurl":"jian","name":"&#21513;&#23433;"}]}],"charSort":true},"KLMNP":{"title":"KLMNP","cityList":[{"char":"K","list":[{"cityurl":"kunming","name":"&#26118;&#26126;"},{"cityurl":"kaifeng","name":"&#24320;&#23553;"},{"cityurl":"kashi","name":"&#21888;&#20160;"},{"cityurl":"kelamayi","name":"&#20811;&#25289;&#29595;&#20381;"}]},{"char":"L","list":[{"cityurl":"lijiang","name":"&#20029;&#27743;"},{"cityurl":"luoyang","name":"&#27931;&#38451;"},{"cityurl":"leshan","name":"&#20048;&#23665;"},{"cityurl":"lasa","name":"&#25289;&#33832;"},{"cityurl":"lanzhou","name":"&#20848;&#24030;"},{"cityurl":"liangshan","name":"&#20937;&#23665;"},{"cityurl":"langfang","name":"&#24266;&#22346;"},{"cityurl":"lianyungang","name":"&#36830;&#20113;&#28207;"},{"cityurl":"liuzhou","name":"&#26611;&#24030;"},{"cityurl":"linyi","name":"&#20020;&#27778;"}]},{"char":"M","list":[{"cityurl":"mianyang","name":"&#32501;&#38451;"},{"cityurl":"maoming","name":"&#33538;&#21517;"},{"cityurl":"meizhou","name":"&#26757;&#24030;"},{"cityurl":"meishan","name":"&#30473;&#23665;"},{"cityurl":"mudanjiang","name":"&#29281;&#20025;&#27743;"},{"cityurl":"maanshan","name":"&#39532;&#38797;&#23665;"}]},{"char":"N","list":[{"cityurl":"nanjing","name":"&#21335;&#20140;"},{"cityurl":"ningbo","name":"&#23425;&#27874;"},{"cityurl":"nanning","name":"&#21335;&#23425;"},{"cityurl":"nanchang","name":"&#21335;&#26124;"},{"cityurl":"nanping","name":"&#21335;&#24179;"},{"cityurl":"nanchong","name":"&#21335;&#20805;"},{"cityurl":"nantong","name":"&#21335;&#36890;"},{"cityurl":"ningde","name":"&#23425;&#24503;"},{"cityurl":"nanyang","name":"&#21335;&#38451;"},{"cityurl":"neijiang","name":"&#20869;&#27743;"}]},{"char":"P","list":[{"cityurl":"putian","name":"&#33670;&#30000;"},{"cityurl":"pingxiang","name":"&#33805;&#20065;"},{"cityurl":"panjin","name":"&#30424;&#38182;"},{"cityurl":"panzhihua","name":"&#25856;&#26525;&#33457;"},{"cityurl":"pingliang","name":"&#24179;&#20937;"},{"cityurl":"pingdingshan","name":"&#24179;&#39030;&#23665;"},{"cityurl":"puyang","name":"&#28654;&#38451;"},{"cityurl":"puer","name":"&#26222;&#27953;"}]}],"charSort":true},"QRSTW":{"title":"QRSTW","cityList":[{"char":"Q","list":[{"cityurl":"qingdao","name":"&#38738;&#23707;"},{"cityurl":"qinhuangdao","name":"&#31206;&#30343;&#23707;"},{"cityurl":"qiandongnan","name":"&#40660;&#19996;&#21335;"},{"cityurl":"quanzhou","name":"&#27849;&#24030;"},{"cityurl":"qingyuan","name":"&#28165;&#36828;"},{"cityurl":"qionghai","name":"&#29756;&#28023;"},{"cityurl":"qiannan","name":"&#40660;&#21335;"},{"cityurl":"qiqihaer","name":"&#40784;&#40784;&#21704;&#23572;"},{"cityurl":"quzhou","name":"&#34914;&#24030;"},{"cityurl":"qinzhou","name":"&#38054;&#24030;"}]},{"char":"R","list":[{"cityurl":"rizhao","name":"&#26085;&#29031;"},{"cityurl":"rikaze","name":"&#26085;&#21888;&#21017;"}]},{"char":"S","list":[{"cityurl":"shanghai_city","name":"&#19978;&#28023;"},{"cityurl":"sanya","name":"&#19977;&#20122;"},{"cityurl":"shenzhen","name":"&#28145;&#22323;"},{"cityurl":"suzhou_jiangsu","name":"&#33487;&#24030;"},{"cityurl":"shenyang","name":"&#27784;&#38451;"},{"cityurl":"shijiazhuang","name":"&#30707;&#23478;&#24196;"},{"cityurl":"shaoxing","name":"&#32461;&#20852;"},{"cityurl":"shaoguan","name":"&#38902;&#20851;"},{"cityurl":"shangrao","name":"&#19978;&#39286;"},{"cityurl":"shantou","name":"&#27733;&#22836;"},{"cityurl":"shiyan","name":"&#21313;&#22576;"}]},{"char":"T","list":[{"cityurl":"tianjin_city","name":"&#22825;&#27941;"},{"cityurl":"taiyuan","name":"&#22826;&#21407;"},{"cityurl":"taian","name":"&#27888;&#23433;"},{"cityurl":"tangshan","name":"&#21776;&#23665;"},{"cityurl":"taizhou_zhejiang","name":"&#21488;&#24030;"},{"cityurl":"taizhou_jiangsu","name":"&#27888;&#24030;"},{"cityurl":"tianshui","name":"&#22825;&#27700;"},{"cityurl":"tongren","name":"&#38108;&#20161;"}]},{"char":"W","list":[{"cityurl":"wuhan","name":"&#27494;&#27721;"},{"cityurl":"wuxi","name":"&#26080;&#38177;"},{"cityurl":"wulumuqi","name":"&#20044;&#40065;&#26408;&#40784;"},{"cityurl":"wenzhou","name":"&#28201;&#24030;"},{"cityurl":"weihai","name":"&#23041;&#28023;"},{"cityurl":"wuhu","name":"&#33436;&#28246;"},{"cityurl":"weifang","name":"&#28493;&#22346;"},{"cityurl":"weinan","name":"&#28205;&#21335;"},{"cityurl":"wanning","name":"&#19975;&#23425;"},{"cityurl":"wenchang","name":"&#25991;&#26124;"},{"cityurl":"wuzhou","name":"&#26791;&#24030;"}]}],"charSort":true},"XYZ":{"title":"XYZ","cityList":[{"char":"X","list":[{"cityurl":"xiamen","name":"&#21414;&#38376;"},{"cityurl":"xian","name":"&#35199;&#23433;"},{"cityurl":"xiangxi","name":"&#28248;&#35199;"},{"cityurl":"xuzhou","name":"&#24464;&#24030;"},{"cityurl":"xining","name":"&#35199;&#23425;"},{"cityurl":"xishuangbanna","name":"&#35199;&#21452;&#29256;&#32435;"},{"cityurl":"xianyang","name":"&#21688;&#38451;"},{"cityurl":"xinzhou","name":"&#24571;&#24030;"},{"cityurl":"xinxiang","name":"&#26032;&#20065;"},{"cityurl":"xuancheng","name":"&#23459;&#22478;"},{"cityurl":"xianning","name":"&#21688;&#23425;"},{"cityurl":"xiangfan","name":"&#35140;&#27146;"}]},{"char":"Y","list":[{"cityurl":"yangzhou","name":"&#25196;&#24030;"},{"cityurl":"yantai","name":"&#28895;&#21488;"},{"cityurl":"yichang","name":"&#23452;&#26124;"},{"cityurl":"yangjiang","name":"&#38451;&#27743;"},{"cityurl":"yinchuan","name":"&#38134;&#24029;"},{"cityurl":"yaan","name":"&#38597;&#23433;"},{"cityurl":"yibin","name":"&#23452;&#23486;"},{"cityurl":"yanbian","name":"&#24310;&#36793;"},{"cityurl":"yingkou","name":"&#33829;&#21475;"},{"cityurl":"yueyang","name":"&#23731;&#38451;"},{"cityurl":"yuxi","name":"&#29577;&#28330;"},{"cityurl":"yancheng","name":"&#30416;&#22478;"},{"cityurl":"yanan","name":"&#24310;&#23433;"},{"cityurl":"yichun_jiangxi","name":"&#23452;&#26149;"},{"cityurl":"yuncheng","name":"&#36816;&#22478;"}]},{"char":"Z","list":[{"cityurl":"zhuhai","name":"&#29664;&#28023;"},{"cityurl":"zhengzhou","name":"&#37073;&#24030;"},{"cityurl":"zhoushan","name":"&#33311;&#23665;"},{"cityurl":"zhangjiajie","name":"&#24352;&#23478;&#30028;"},{"cityurl":"zhaoqing","name":"&#32903;&#24198;"},{"cityurl":"zhenjiang","name":"&#38215;&#27743;"},{"cityurl":"zhangzhou","name":"&#28467;&#24030;"},{"cityurl":"zhongshan","name":"&#20013;&#23665;"},{"cityurl":"zhanjiang","name":"&#28251;&#27743;"},{"cityurl":"zaozhuang","name":"&#26531;&#24196;"},{"cityurl":"zhuzhou","name":"&#26666;&#27954;"},{"cityurl":"zibo","name":"&#28100;&#21338;"},{"cityurl":"zunyi","name":"&#36981;&#20041;"},{"cityurl":"zigong","name":"&#33258;&#36129;"},{"cityurl":"zhangjiakou","name":"&#24352;&#23478;&#21475;"}]}],"charSort":true}},"intercity":{"&#28909;&#38376;&#22478;&#24066;":{"title":"&#28909;&#38376;&#22478;&#24066;","cityList":[{"char":" ","list":[{"cityurl":"singapore_city","name":"&#26032;&#21152;&#22369;"},{"cityurl":"bangkok","name":"&#26364;&#35895;"},{"cityurl":"seoul","name":"&#39318;&#23572;"},{"cityurl":"taipei","name":"&#21488;&#21271;&#24066;"},{"cityurl":"bali","name":"&#24052;&#21400;&#23707;"},{"cityurl":"maldives","name":"&#39532;&#23572;&#20195;&#22827;"},{"cityurl":"kuala_lumpur","name":"&#21513;&#38534;&#22369;"},{"cityurl":"tokyo","name":"&#19996;&#20140;"},{"cityurl":"chiang_mai","name":"&#28165;&#36808;"},{"cityurl":"koh_phuket_tha","name":"&#26222;&#21513;"},{"cityurl":"jeju","name":"&#27982;&#24030;&#23707;"},{"cityurl":"sabah","name":"&#27801;&#24052;"},{"cityurl":"ko_samui_district","name":"&#33487;&#26757;&#23707;"},{"cityurl":"dubai","name":"&#36842;&#25308;"},{"cityurl":"boracay_philippines","name":"&#38271;&#28393;&#23707;"},{"cityurl":"pattaya","name":"&#33453;&#25552;&#38597;"},{"cityurl":"london_england","name":"&#20262;&#25958;"},{"cityurl":"paris_city","name":"&#24052;&#40654;"},{"cityurl":"hongkong_city","name":"&#39321;&#28207;"},{"cityurl":"macao_city","name":"&#28595;&#38376;"}]}],"cls":"inter","charSort":false},"&#19996;&#21335;&#20122;":{"title":"&#19996;&#21335;&#20122;","cityList":[{"char":" ","list":[{"cityurl":"singapore_city","name":"&#26032;&#21152;&#22369;"},{"cityurl":"bangkok","name":"&#26364;&#35895;"},{"cityurl":"koh_phuket_tha","name":"&#26222;&#21513;"},{"cityurl":"bali","name":"&#24052;&#21400;&#23707;"},{"cityurl":"chiang_mai","name":"&#28165;&#36808;"},{"cityurl":"ko_samui_district","name":"&#33487;&#26757;&#23707;"},{"cityurl":"kuala_lumpur","name":"&#21513;&#38534;&#22369;"},{"cityurl":"boracay_philippines","name":"&#38271;&#28393;&#23707;"},{"cityurl":"da_nang_vn","name":"&#23704;&#28207;"},{"cityurl":"ho_chi_minh_city","name":"&#32993;&#24535;&#26126;&#24066;"},{"cityurl":"langkawi","name":"&#20848;&#21345;&#23041;"},{"cityurl":"manila","name":"&#39532;&#23612;&#25289;"},{"cityurl":"siem_reap_cambodia","name":"&#26297;&#31890;&#24066;"},{"cityurl":"phnom_penh_new","name":"&#37329;&#36793;"},{"cityurl":"jakarta","name":"&#38597;&#21152;&#36798;"},{"cityurl":"hanoi_vn","name":"&#27827;&#20869;"},{"cityurl":"bintan_ria","name":"&#27665;&#20025;&#23707;"},{"cityurl":"cebu_city","name":"&#23487;&#21153;"},{"cityurl":"yangon_yan","name":"&#20208;&#20809;"},{"cityurl":"vientiane_capital","name":"&#19975;&#35937;&#24066;"},{"cityurl":"redang_island_ter","name":"&#28909;&#28010;&#23707;"},{"cityurl":"louangphabang","name":"&#29701;&#21187;&#25289;&#37030;"},{"cityurl":"krong_preah_sihanouk","name":"&#35199;&#21704;&#21162;&#20811;&#24066;"},{"cityurl":"hue_vn_vie","name":"&#39034;&#21270;"},{"cityurl":"tp_hoi_an","name":"&#20250;&#23433;"},{"cityurl":"mui_ne_pha","name":"&#32654;&#22856;"},{"cityurl":"ha_long","name":"&#19979;&#40857;&#28286;"},{"cityurl":"nha_trang_kha","name":"&#33469;&#24196;"}]}],"cls":"inter","charSort":false},"&#28023;&#23707;":{"title":"&#28023;&#23707;","cityList":[{"char":" ","list":[{"cityurl":"koh_phuket_tha","name":"&#26222;&#21513;"},{"cityurl":"bali","name":"&#24052;&#21400;&#23707;"},{"cityurl":"maldives","name":"&#39532;&#23572;&#20195;&#22827;"},{"cityurl":"jeju","name":"&#27982;&#24030;&#23707;"},{"cityurl":"ko_samui_district","name":"&#33487;&#26757;&#23707;"},{"cityurl":"boracay_philippines","name":"&#38271;&#28393;&#23707;"},{"cityurl":"sabah","name":"&#27801;&#24052;"},{"cityurl":"saipan_mnp","name":"&#22622;&#29677;&#23707;"},{"cityurl":"langkawi","name":"&#20848;&#21345;&#23041;"},{"cityurl":"hawaii_county","name":"&#22799;&#23041;&#22839;"},{"cityurl":"okinawa_oki","name":"&#20914;&#32499;"},{"cityurl":"seychelles_sey","name":"&#22622;&#33292;&#23572;"},{"cityurl":"fiji_fij","name":"&#26000;&#27982;"},{"cityurl":"gold_coast_qld","name":"&#40644;&#37329;&#28023;&#23736;"},{"cityurl":"bintan_ria","name":"&#27665;&#20025;&#23707;"},{"cityurl":"cebu_city","name":"&#23487;&#21153;"},{"cityurl":"guam","name":"&#20851;&#23707;"},{"cityurl":"palau_ot","name":"&#24085;&#21171;"},{"cityurl":"cairns_qld","name":"&#20975;&#24681;&#26031;"},{"cityurl":"redang_island_ter","name":"&#28909;&#28010;&#23707;"},{"cityurl":"pangkor_island_per","name":"&#37030;&#21679;&#23707;"}]}],"cls":"inter","charSort":false},"&#20122;&#27954;":{"title":"&#20122;&#27954;","cityList":[{"char":" ","list":[{"cityurl":"bangkok","name":"&#26364;&#35895;"},{"cityurl":"chiang_mai","name":"&#28165;&#36808;"},{"cityurl":"jeju","name":"&#27982;&#24030;&#23707;"},{"cityurl":"osaka","name":"&#22823;&#38442;"},{"cityurl":"da_nang_vn","name":"&#23704;&#28207;"},{"cityurl":"ho_chi_minh_city","name":"&#32993;&#24535;&#26126;&#24066;"},{"cityurl":"langkawi","name":"&#20848;&#21345;&#23041;"},{"cityurl":"siem_reap_cambodia","name":"&#26297;&#31890;&#24066;"},{"cityurl":"kyoto_kyo","name":"&#20140;&#37117;"},{"cityurl":"phnom_penh_new","name":"&#37329;&#36793;"},{"cityurl":"busan_kr","name":"&#37340;&#23665;"},{"cityurl":"jakarta","name":"&#38597;&#21152;&#36798;"},{"cityurl":"hanoi_vn","name":"&#27827;&#20869;"},{"cityurl":"mumbai_suburban","name":"&#23391;&#20080;"},{"cityurl":"istanbul_ist","name":"&#20234;&#26031;&#22374;&#24067;&#23572;"},{"cityurl":"colombo_wp","name":"&#31185;&#20262;&#22369;"},{"cityurl":"hakone_ash","name":"&#31665;&#26681;&#30010;"},{"cityurl":"yangon_yan","name":"&#20208;&#20809;"},{"cityurl":"nagoya_aic","name":"&#21517;&#21476;&#23627;"},{"cityurl":"incheon_kr","name":"&#20161;&#24029;"},{"cityurl":"malacca_mel","name":"&#39532;&#20845;&#30002;"},{"cityurl":"vientiane_capital","name":"&#19975;&#35937;&#24066;"},{"cityurl":"nara_nar","name":"&#22856;&#33391;"},{"cityurl":"pyongyang_pyongyang","name":"&#24179;&#22756;"},{"cityurl":"otaru_hok","name":"&#23567;&#27197;&#24066;"},{"cityurl":"jerusalem_il","name":"&#32822;&#36335;&#25746;&#20919;"},{"cityurl":"hai_phong_vn","name":"&#28023;&#38450;&#24066;"}]}],"cls":"inter","charSort":false},"&#27431;&#27954;":{"title":"&#27431;&#27954;","cityList":[{"char":" ","list":[{"cityurl":"paris_city","name":"&#24052;&#40654;"},{"cityurl":"berlin_ber","name":"&#26575;&#26519;"},{"cityurl":"moscow_g","name":"&#33707;&#26031;&#31185;"},{"cityurl":"frankfurt_da","name":"&#27861;&#20848;&#20811;&#31119;"},{"cityurl":"munich_m","name":"&#24917;&#23612;&#40657;"},{"cityurl":"madrid_com","name":"&#39532;&#24503;&#37324;&#33258;&#27835;&#21306;"},{"cityurl":"vienna_vie","name":"&#32500;&#20063;&#32435;"},{"cityurl":"geneva_gen","name":"&#26085;&#20869;&#29926;"},{"cityurl":"prague_hla","name":"&#24067;&#25289;&#26684;"},{"cityurl":"lisbon_pt","name":"&#37324;&#26031;&#26412;"},{"cityurl":"zurich_zur","name":"&#33487;&#40654;&#19990;"},{"cityurl":"florence","name":"&#20315;&#32599;&#20262;&#33832;"},{"cityurl":"brussels","name":"&#24067;&#40065;&#22622;&#23572;"},{"cityurl":"st_petersburg_g","name":"&#22307;&#24444;&#24471;&#22561;"},{"cityurl":"cannes_alp","name":"&#25115;&#32435;"},{"cityurl":"marseille_bou","name":"&#39532;&#36187;"},{"cityurl":"kobenhavn","name":"&#21733;&#26412;&#21704;&#26681;"},{"cityurl":"stuttgart_s","name":"&#26031;&#22270;&#21152;&#29305;"},{"cityurl":"helsinki_hel","name":"&#36203;&#23572;&#36763;&#22522;"},{"cityurl":"budapest","name":"&#24067;&#36798;&#20329;&#26031;"},{"cityurl":"nuremberg_mid","name":"&#32445;&#20262;&#22561;"},{"cityurl":"government_of_rotterdam","name":"&#40575;&#29305;&#20025;"},{"cityurl":"cambridge_cam","name":"&#21073;&#26725;"},{"cityurl":"liverpool_mer","name":"&#21033;&#29289;&#28006;"},{"cityurl":"athens_ath","name":"&#38597;&#20856;"}]}],"cls":"inter","charSort":false},"&#32654;&#27954;":{"title":"&#32654;&#27954;","cityList":[{"char":" ","list":[{"cityurl":"los_angeles_ca","name":"&#27931;&#26441;&#30710;"},{"cityurl":"new_york_new","name":"&#32445;&#32422;"},{"cityurl":"san_francisco_county","name":"&#26087;&#37329;&#23665;"},{"cityurl":"vancouver_gre","name":"&#28201;&#21733;&#21326;"},{"cityurl":"hawaii_county","name":"&#22799;&#23041;&#22839;"},{"cityurl":"dallas_tx","name":"&#36798;&#25289;&#26031;"},{"cityurl":"san_diego_county","name":"&#22307;&#36845;&#25096;"},{"cityurl":"cancun_qroo","name":"&#22350;&#26118;"},{"cityurl":"philadelphia_pa_us","name":"&#36153;&#22478;&#21439;"},{"cityurl":"denver_co","name":"&#20025;&#20315;"},{"cityurl":"ottawa_ott","name":"&#28197;&#22826;&#21326;"},{"cityurl":"baltimore_md","name":"&#24052;&#23572;&#30340;&#25705;&#21439;"},{"cityurl":"portland_vic_au","name":"&#27874;&#29305;&#20848;"},{"cityurl":"port_au_prince_oue","name":"&#22826;&#23376;&#28207;"},{"cityurl":"orlando_ora","name":"&#22885;&#20848;&#22810;"},{"cityurl":"kansas_city_was","name":"&#22570;&#33832;&#26031;&#22478;"},{"cityurl":"rocky_mountain_house_div","name":"&#33853;&#22522;&#23665;"},{"cityurl":"miami_mia","name":"&#36808;&#38463;&#23494;"},{"cityurl":"trinidad_flo","name":"&#29305;&#31435;&#23612;&#36798;"},{"cityurl":"seattle_kin","name":"&#35199;&#38597;&#22270;"},{"cityurl":"new_orleans_orl","name":"&#26032;&#22885;&#23572;&#33391;"},{"cityurl":"houston_har","name":"&#20241;&#26031;&#39039;"},{"cityurl":"atlanta_ful","name":"&#20122;&#29305;&#20848;&#22823;"},{"cityurl":"chicago_coo","name":"&#33437;&#21152;&#21733;"}]}],"cls":"inter","charSort":false},"&#22823;&#27915;&#27954;":{"title":"&#22823;&#27915;&#27954;","cityList":[{"char":" ","list":[{"cityurl":"fiji_fij","name":"&#26000;&#27982;"},{"cityurl":"gold_coast_qld","name":"&#40644;&#37329;&#28023;&#23736;"},{"cityurl":"guam","name":"&#20851;&#23707;"},{"cityurl":"palau_ot","name":"&#24085;&#21171;"},{"cityurl":"cairns_qld","name":"&#20975;&#24681;&#26031;"},{"cityurl":"perth_wa","name":"&#29632;&#26031;"},{"cityurl":"christchurch_chr","name":"&#22522;&#30563;&#22478;"},{"cityurl":"adelaide_sa","name":"&#38463;&#24503;&#33713;&#24503;"},{"cityurl":"pora_pora","name":"&#21338;&#25289;&#21338;&#25289;&#23707;"},{"cityurl":"wellington_wel","name":"&#24800;&#28789;&#39039;"},{"cityurl":"rotorua_rot","name":"&#32599;&#25176;&#40065;&#29926;"},{"cityurl":"quimperle_fin","name":"&#22350;&#20329;&#33713;"},{"cityurl":"coromandel","name":"&#31185;&#32599;&#26364;&#24503;"},{"cityurl":"broome_wa","name":"&#24067;&#40065;&#22982;"},{"cityurl":"malbork_gmi","name":"&#39532;&#23572;&#22561;"}]}],"cls":"inter","charSort":false}}},"_CAPTIAL":"&#21271;&#20140;","_INTERCITY":"&#39321;&#28207;"}}
```

Does anyone know what they would be trying to accomplish with this? Are they scanning to see if my server can be used as a proxy maybe? Is there nothing I can do about it really? Would anyone have a best guess on what kind of threat this represents? Thanks again.

---

### Post by SeijiSensei on 2014-07-11
I'd guess it's a proxy attempt.

Notice that the log entry you posted reports this request received a 404 ("not found") status code.  Your server isn't revealing anything.

---

### Post by thufirhawat2 on 2014-07-22
So I have piddled with this problem for a little while, and I found a post in another forum where someone suggested putting hostnames in a file I did not know existed at /etc/hosts.deny. This supposedly prevents hostnames from accessing your server.

So here is my hosts.deny file:

```
  GNU nano 2.2.6            File: /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "rpcbind" for the
# daemon name. See rpcbind(8) and rpc.mountd(8) for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.
#
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
ALL: hotel.qunar.com
```

However, I am still getting pegged by this host nightly. After I added them to hosts.deny, I tried pinging the site and since I received replies, I kind of figured it would not work. My logs clearly show the hostname giving me 404 and 457 errors every night with the script they are trying to run, so my server is getting DNS resolution on the IP address, it just is not denying it. Is there something I am missing? I tried searching for multiple examples of how to configure this, and everything pretty much just said to put ALL: hostnameyoudont.like and you would be good to go. I have already went through and configured mod_security after reading SeijiSensei's wonderful linode security section in his signature, and I am not terribly worried that this constitutes a serious security threat, it is just the principle of the thing. And I am a little obsessive about my logs being clean with no errors or weirdness. Any suggestions are, as always, appreciated.

---

### Post by Habitual on 2014-07-22
```
iptables -I INPUT -p tcp --dport 80 -m string --algo bm --string "qunar" --to 1000 -j DROP
```

---

### Post by thufirhawat2 on 2014-07-22
> **Habitual said:**
> ```
iptables -I INPUT -p tcp --dport 80 -m string --algo bm --string "qunar" --to 1000 -j DROP
```

Fascinating, thank you! I am a little embarrassed I did not figure this out from the man pages of iptables which I have read through quite a bit in trying to find a solution. I did not realize that modules for iptables such as the -m option have their own separate man page to read through, and I think I see what you did there. To make things simpler in the future and to take a page from SeijiSensei's book where he mentioned above he keeps an "evil" list, is there a way I could modify this to match any entries listed in a file instead of the rule specifically looking for only that dns entry? So create a list of hostnames (starting with qunar) in a directory like /usr/local/etc/hostsidontlike and then modify my iptables command to say:

```
iptables -I INPUT -p tcp --dport 80 -m string --algo bm --string "/usr/local/etc/hostsidontlike" --to 1000 -j DROP
```

Although I do not know if that syntax would still be correct for what I am trying to do, or if it would have to be further modified, maybe it does not need quotes around a file name or something? Thank you so much, in any event, this has helped me learn a lot about iptables' capabilities.

---

### Post by Habitual on 2014-07-22
> **thufirhawat2 said:**
> Fascinating, thank you! I am a little embarrassed I did not figure this out from the man pages of iptables which I have read through quite a bit in trying to find a solution. I did not realize that modules for iptables such as the -m option have their own separate man page to read through, and I think I see what you did there. To make things simpler in the future and to take a page from SeijiSensei's book where he mentioned above he keeps an "evil" list, is there a way I could modify this to match any entries listed in a file instead of the rule specifically looking for only that dns entry? So create a list of hostnames (starting with qunar) in a directory like /usr/local/etc/hostsidontlike and then modify my iptables command to say:

```
iptables -I INPUT -p tcp --dport 80 -m string --algo bm --string "/usr/local/etc/hostsidontlike" --to 1000 -j DROP
```

Although I do not know if that syntax would still be correct for what I am trying to do, or if it would have to be further modified, maybe it does not need quotes around a file name or something? Thank you so much, in any event, this has helped me learn a lot about iptables' capabilities.

hotel.qunar.com is most likely just another victim that is distributing files its' admins don't know about.
I wouldn't use that with "/usr/local/etc/hostsidontlike", I'd revisit fail2ban for that.
I wrote a "how to get started" over [here...]("https://www.linuxquestions.org/questions/blog/habitual-558710/getting-started-with-fail2ban-36031/")

Basically, I'd try this in seedyhosts.conf
```


docroot = /var/www/html
badadmin = qunar 
# Option:  failregex
# Notes.:  
# Values:  TEXT
#

failregex = ^<HOST> .*"GET \/(?:%(badadmin)s).*?"
            ^<HOST> .*"POST \/(?:%(badadmin)s).*?"

ignoreregex =
```

Test it with 
```
fail2ban-regex /var/log/apache2/access.log /etc/fail2ban/filter.d/seedyhosts.conf
```

Let us know.

---

### Post by SeijiSensei on 2014-07-22
>  To make things simpler in the future and to take a page from SeijiSensei's book where he mentioned above he keeps an "evil" list, is there a way I could modify this to match any entries listed in a file instead of the rule specifically looking for only that dns entry

I generate my iptables rulesets with a custom bash script.  To handle "evil" hosts I use code like this:

```

EVIL=$(cat /etc/firewall/evil)

for h in $EVIL
do
    iptables -A INPUT -s $h -j REJECT
done

```

That generates a rule for every entry in /etc/firewall/evil.

You can do the same thing for pretty much any type of rule.  You could put domain names into a file then generate rules like the one you presented above for each domain.

---

### Post by TheFu on 2014-07-22
I would solve this using iptables too, like our friends Habitual and SeijiSensei say, but ... if you want yet another option, I suspect that mod_security would have options to use referrers as block options.  I don't use apache, but I know that nginx can do this stuff easily. We use it for all sorts of anti-social attempts against our websites.
* limiting which IPs/subnets can access specific parts of websites
* blocking certain abusive webcrawlers (especially baidu which doesn't honor robots.txt, so we block them completely)
* blocking certain abusive feed readers
* blocking certain requests - anything with "php" is blocked as is anything with "admin"
* if an IP creates too many requests, we slow that IP down and limit the connection count.
That's off the top of my head. We are doing other things too, I'm certain.

Learning iptables can become a full-time job. There are some really great books on it, but most people just need a few examples to get what they need done.  Every "firewall" on Linux is really just a front-end to iptables, so don't worry if you feel better using ufw or gufw or one of the other front-ends.

With just a little bash scripting, like shown above, automation of most things in Linux is possible.

---

### Post by thufirhawat2 on 2014-07-23
Thank you all so much for your help with this. I decided to go with a script that uses the command:

```
SEEDYHOSTS=$(cat /etc/firewall/seedyhosts)
for h in $SEEDYHOSTS
do
   iptables -D INPUT -m string --algo bm --string "$h" --to 1000 -j DROP;  iptables -I INPUT -m string --algo bm --string "$h$
done

```

and keep a naughty list in the directory specified. In testing, I found that if I did not delete the previous lines in iptables that had been added by the script, I ended up with a bunch of duplicates, which may or may not matter, but did not seem wise. There may be a more elegant way to deal with this, but the script is working and keeping those jerks from messing up my beautiful logs ;P.  So now, I can just add annoying hosts to my file and rerun my script to update all the rules, essentially combining SeijiSensei's and Habitual's brilliant suggestions. Thank you so much for the information! I have very recently been learning about bash scripting in particular by automating my backups, so that solution appealed to me greatly.

I have also installed and have been trying to learn more about the intricacies of modsecurity for apache, so thanks to TheFu as well for giving me some more interesting ideas to look into. As it stands, I have loaded it, symlinked the core rule set into the active directory, left it in debug for awhile, read what was going down in the logs, and then turned it on. Everything seems to work fine with it, and I was excited that it blocked me and gave me a forbidden message when I tried to upload files with scripts in them to my owncloud login, that was pretty cool. 

I am a windows IT administrator by trade, and so I am used to really only being able to buy canned software, configure it by the manual, and hope for the best. The flexibility and simplicity of Linux continues to astound me every day. I like being able to make my own rules, not rely on some junk written or designed by people who have no personal liability for anything that might go wrong if it does not work. That is why even though I am a windows administrator, I have banned Microsoft products from my home, Linux only, I absolutely love it.

---

### Post by Doug S on 2014-07-23
I have been following this thread, but have nothing to add over what has already been said. However, only this morning realized that I get the same thing on my site, but only since June 14th and only 8 times, so far.```
access.log:58.60.220.241 - - [23/Jul/2014:01:09:04 -0700] "GET http://hotel.qunar.com/render/hoteldiv.jsp?&__jscallback=XQScript_4 HTTP/1.1" 404 452 "http://hotel.qunar.com/" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.1916.114 Safari/537.36"
```all of the 8 times are from China.

Edit: I will just add: Be careful when using the string module in iptables, as it can use much more CPU time, depending on how busy your site is.

---

