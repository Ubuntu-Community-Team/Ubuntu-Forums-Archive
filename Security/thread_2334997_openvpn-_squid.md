---
title: "openvpn- squid"
date: 2016-08-24
forum: Security
---

### Post by marwanq on 2016-08-24
hello!

guys this is my set up my openvpn client traffic goes to  openvpn server and after that i want to the traffic to be forwarded to squid proxy so that it can be filtered.
now i am trying to block pakhweels.com but it is not working.
my web_deny file has [www.pakheels.com]("http://www.pakheels.com") written in it.
i am able to forward my openvpn client traffice to squid server since it is visible in access.log but when i apply acl to block a website i have no success.Kindly help!.

openvpn client  has 10.8.0.10
openvpn server has 10.8.0.1
tun0 is the interface


squid conf
```

acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet1 src 192.168.0.0/16    # RFC1918 possible internal network

acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT
acl allow_network src 10.8.0.0/24 
acl web_deny dstdomain "/etc/squid3/web_deny"





http_access allow all

http_access deny !Safe_ports

http_access deny CONNECT !SSL_ports

http_access allow localhost manager
http_access deny manager



http_access allow localnet
http_access allow localnet1


http_access deny web_deny
http_access allow allow_network

http_access deny all











http_port 3128 transparent



coredump_dir /var/spool/squid3



refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320


visible_hostname softfw

```




openvpn server conf
```

;local a.b.c.d

port 1194

;proto tcp
proto udp

;dev tap
dev tun

;dev-node MyTap

ca ca.crt
cert server.crt
key server.key  # This file should be kept secret

dh dh2048.pem

server 10.8.0.0 255.255.255.0

ifconfig-pool-persist ipp.txt

;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100

;server-bridge

;push "route 192.168.10.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"


;client-config-dir ccd
;route 192.168.40.128 255.255.255.248

;client-config-dir ccd
;route 10.9.0.0 255.255.255.252

;learn-address ./script

push "redirect-gateway def1"

push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"

;client-to-client

;duplicate-cn

keepalive 10 120

;tls-auth ta.key 0 # This file is secret

;cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES

comp-lzo

;max-clients 100

;user nobody
;group nogroup

persist-key
persist-tun

status openvpn-status.log

;log         openvpn.log
;log-append  openvpn.log

verb 3

;mute 20


```


this is a part of access log 
```

1472059179.770   2367 10.8.0.10 TCP_MISS/200 9531 GET http://cache4.pakwheels.com/ad_pictures/1253/Slide_toyota-aqua-s-15-2014-12533323.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059179.914   2503 10.8.0.10 TCP_MISS/200 16493 GET http://cache1.pakwheels.com/ad_pictures/1230/Slide_toyota-prado-2012-12301020.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059179.940   2527 10.8.0.10 TCP_MISS/200 6812 GET http://cache3.pakwheels.com/ad_pictures/1208/Slide_nissan-dayz-highway-star-2013-12085892.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059180.220   2809 10.8.0.10 TCP_MISS/200 13158 GET http://cache4.pakwheels.com/ad_pictures/1268/Slide_toyota-prado-tx-4-2012-12680738.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059180.322   2906 10.8.0.10 TCP_MISS/200 11421 GET http://cache3.pakwheels.com/ad_pictures/1152/Slide_honda-grace-2-2014-11528339.jpeg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059180.326   2915 10.8.0.10 TCP_MISS/200 27998 GET http://cache3.pakwheels.com/ad_pictures/1225/Slide_honda-any-model-139-2015-12257604.jpeg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059180.622   3205 10.8.0.10 TCP_MISS/200 12441 GET http://cache1.pakwheels.com/ad_pictures/1245/Slide_toyota-corolla-1-6-gli-automatic-2011-12454041.57367 - HIER_DIRECT/148.251.245.44 binary/octet-stream
1472059180.964   1335 10.8.0.10 TCP_MISS/200 9145 GET http://cache3.pakwheels.com/ad_pictures/1254/Slide_daihatsu-move-custom-g-2016-12547503.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059181.216   1440 10.8.0.10 TCP_MISS/200 8018 GET http://cache4.pakwheels.com/ad_pictures/1190/Slide_toyota-aqua-l-16-2013-11904158.jpeg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059181.436   1201 10.8.0.10 TCP_MISS/200 20259 GET http://cache2.pakwheels.com/ad_pictures/1233/Slide_toyota-prado-tx-4-2011-12336372.jpeg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059181.456    826 10.8.0.10 TCP_MISS/200 9769 GET http://cache2.pakwheels.com/ad_pictures/1253/Slide_mercedes-benz-250d-2010-12535535.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059181.558   4153 10.8.0.10 TCP_MISS/200 8831 GET http://cache2.pakwheels.com/ad_pictures/1221/Slide_honda-fit-hybrid-base-grade-1-3-2012-12212828.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059181.823    854 10.8.0.10 TCP_MISS/200 11330 GET http://cache3.pakwheels.com/ad_pictures/1239/Slide_honda-airwave-m-s-package-2007-12395592.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059181.966   1614 10.8.0.10 TCP_MISS/200 15984 GET http://cache2.pakwheels.com/ad_pictures/1267/Slide_daihatsu-move-2013-12674441.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059182.506   1065 10.8.0.10 TCP_MISS/200 22880 GET http://cache2.pakwheels.com/ad_pictures/1097/Slide_mercedes-benz-cls-cls-500-2005-10979643.JPG - HIER_DIRECT/148.251.245.44 image/jpeg
1472059182.632    656 10.8.0.10 TCP_MISS/200 9952 GET http://cache3.pakwheels.com/ad_pictures/1261/Slide_daihatsu-mira-x-limited-3-2013-12612805.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059183.377  17945 10.8.0.10 TCP_MISS/200 1245 GET http://track.adform.net/adfscript/? - HIER_DIRECT/37.157.2.25 text/javascript
1472059183.774    364 10.8.0.10 TCP_MISS/200 11574 GET http://s2.adform.net/stoat/582/s2.adform.net/bootstrap.js - HIER_DIRECT/23.50.172.234 text/javascript
1472059184.174    369 10.8.0.10 TCP_MISS/200 2435 GET http://track.adform.net/adfserve/? - HIER_DIRECT/37.157.2.25 text/javascript
1472059184.232   1590 10.8.0.10 TCP_MISS/200 24142 GET http://cache4.pakwheels.com/ad_pictures/1096/Slide_porsche-911-911-carrera-2005-10966363.JPG - HIER_DIRECT/148.251.245.44 image/jpeg
1472059186.392  20961 10.8.0.10 TCP_MISS/200 1213 GET http://track.adform.net/adfscript/? - HIER_DIRECT/37.157.2.25 text/javascript
1472059186.616   6694 10.8.0.10 TCP_MISS/200 6383 GET http://cache2.pakwheels.com/ad_pictures/1217/Slide_toyota-prius-l-1-8-2011-12175466.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059186.942   5106 10.8.0.10 TCP_MISS/200 34094 GET http://cache1.pakwheels.com/ad_pictures/1230/Slide_bmw-3-series-320i-2003-12309555.JPG - HIER_DIRECT/148.251.245.44 image/jpeg
1472059186.949   7002 10.8.0.10 TCP_MISS/200 8040 GET http://cache1.pakwheels.com/ad_pictures/1237/Slide_suzuki-wagon-r-stingray-x-14-2012-12373812.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059186.973    350 10.8.0.10 TCP_MISS/200 37440 GET http://s2.adform.net/stoat/582/s2.adform.net/load/v/0.0.94/e/jQSBgg/i/8IP4AAAAIAA/r:AdConstructor:contents/HTML:types/Standard - HIER_DIRECT/23.50.172.234 text/javascript
1472059186.994   6659 10.8.0.10 TCP_MISS/200 7924 GET http://cache1.pakwheels.com/ad_pictures/1266/Slide_toyota-aqua-g-37-2013-12663340.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059187.256    194 10.8.0.10 TCP_MISS/200 25209 GET http://s2.adform.net/Banners/Elements/Files/45923/1246695/1246695.js? - HIER_DIRECT/23.50.172.234 application/x-javascript
1472059187.425  10012 10.8.0.10 TCP_MISS/200 7571 GET http://cache4.pakwheels.com/ad_pictures/1254/Slide_mercedes-benz-e-class-e-200-2014-12542542.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059187.611   6043 10.8.0.10 TCP_MISS/200 12450 GET http://cache3.pakwheels.com/ad_pictures/1219/Slide_toyota-land-cruiser-zx-2012-12191083.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059187.827   6365 10.8.0.10 TCP_MISS/200 21370 GET http://cache4.pakwheels.com/ad_pictures/1066/Slide_mercedes-benz-slk-slk200-kompressor-2006-10666278.JPG - HIER_DIRECT/148.251.245.44 image/jpeg
1472059187.913    913 10.8.0.10 TCP_MISS/200 20773 GET http://cache2.pakwheels.com/ad_pictures/1270/Slide_toyota-corolla-gli-2-2013-12702917.jpeg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059187.936    988 10.8.0.10 TCP_MISS/200 11277 GET http://cache1.pakwheels.com/ad_pictures/1228/Slide_honda-civic-vti-1-8-i-vtec-2013-12284020.jpg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059187.953    974 10.8.0.10 TCP_MISS/200 12221 GET http://cache3.pakwheels.com/ad_pictures/1021/Slide_toyota-vitz-1-0-f-2012-10215871.jpeg - HIER_DIRECT/148.251.245.44 image/jpeg
1472059189.043   2621 10.8.0.10 TCP_MISS/200 2389 GET http://track.adform.net/adfserve/? - HIER_DIRECT/37.157.2.25 text/javascript



```

---

### Post by SeijiSensei on 2016-08-24
You say you entered [www.pakwheels.com](www.pakwheels.com) in web_deny. URLs like cache1.pakwheels.com are being accepted since they don't match [www.pakwheels.com](www.pakwheels.com).  Try using just ".pakwheels.com" in the web_deny list.

---

### Post by marwanq on 2016-08-27
> **SeijiSensei said:**
> You say you entered [www.pakwheels.com]("http://www.pakwheels.com") in web_deny. URLs like cache1.pakwheels.com are being accepted since they don't match [www.pakwheels.com]("http://www.pakwheels.com").  Try using just ".pakwheels.com" in the web_deny list.


i have done that but it is  not working. it seems there is some  problem   with the iptables. i have used these commands..

iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE   (forwards openvpn client traffic from tun0 to eth0 so that internet can be used
iptables -t nat -A PREROUTING -p tcp --dport 80 -i tun0 -j DNAT --to 192.168.1.4:3128
iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE

---

