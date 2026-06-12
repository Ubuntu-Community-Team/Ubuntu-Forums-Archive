---
title: "Squid proxy very slow for web in default config"
date: 2010-01-09
forum: Server Platforms
---

### Post by MountainX on 2010-01-09
I just set up squid for the first time. I have zero experience with proxy servers. I used this guide:
[http://news.softpedia.com/news/Seting-Up-a-HTTP-Proxy-Server-with-Authentication-and-Filtering-52467.shtml](http://news.softpedia.com/news/Seting-Up-a-HTTP-Proxy-Server-with-Authentication-and-Filtering-52467.shtml)

(I also looked at a few other guides such as this one: [http://ubuntuforums.org/showthread.php?t=320733](http://ubuntuforums.org/showthread.php?t=320733). However, I wanted to most barebones config to start with and the link I used was the simplest.)

So now that I have it set up, I'm testing it with FoxyProxy. It is not working well. I went to speedtest.net. The download and ping tests were just as fast as without the proxy, but the upload test fails completely. Furthermore, many web pages load very slowly or not at all. So performance is very mixed, but mostly poor.

What should I look at first to begin to understand my problem? Thanks.

---

### Post by Barriehie on 2010-01-10
> **MountainX said:**
> I just set up squid for the first time. I have zero experience with proxy servers. I used this guide:
[http://news.softpedia.com/news/Seting-Up-a-HTTP-Proxy-Server-with-Authentication-and-Filtering-52467.shtml](http://news.softpedia.com/news/Seting-Up-a-HTTP-Proxy-Server-with-Authentication-and-Filtering-52467.shtml)

(I also looked at a few other guides such as this one: [http://ubuntuforums.org/showthread.php?t=320733](http://ubuntuforums.org/showthread.php?t=320733). However, I wanted to most barebones config to start with and the link I used was the simplest.)

So now that I have it set up, I'm testing it with FoxyProxy. It is not working well. I went to speedtest.net. The download and ping tests were just as fast as without the proxy, but the upload test fails completely. Furthermore, many web pages load very slowly or not at all. So performance is very mixed, but mostly poor.

What should I look at first to begin to understand my problem? Thanks.

What do the logs say?

---

### Post by MountainX on 2010-01-10
> **Barriehie said:**
> What do the logs say?

One problem I see is TCP_DENIED/407. I'd like to test it with no auth required at all. How would I go about that?

This is one version of the config file I have tried: [http://talk.maemo.org/showpost.php?p=462461&postcount=48](http://talk.maemo.org/showpost.php?p=462461&postcount=48)

Here's the tail of the log:
```

1263145044.919   1398 11.22.333.44 TCP_MISS/200 4894 GET http://speedtest.net/ myuser DIRECT/69.17.117.207 text/html
1263145045.070    151 11.22.333.44 TCP_MISS/200 1230 GET http://cdn.speedtest.net/base.css? myuser DIRECT/72.21.81.133 text/css
1263145045.145     74 11.22.333.44 TCP_HIT/200 1844 GET http://cdn.speedtest.net/global/theme/ui.core.css myuser NONE/- text/css
1263145045.207     38 11.22.333.44 TCP_HIT/200 4429 GET http://cdn.speedtest.net/global/theme/ui.datepicker.css myuser NONE/- text/css
1263145045.306     98 11.22.333.44 TCP_HIT/200 17291 GET http://cdn.speedtest.net/global/theme/ui.theme.css myuser NONE/- text/css
1263145045.462    155 11.22.333.44 TCP_MISS/200 31184 GET http://cdn.speedtest.net/st.css? myuser DIRECT/72.21.81.133 text/css
1263145045.525     18 11.22.333.44 TCP_HIT/200 635 GET http://ads.ookla.com/adx.js myuser NONE/- application/javascript
1263145045.640    114 11.22.333.44 TCP_HIT/200 57765 GET http://cdn.speedtest.net/global/jquery-1.3.2.min.js myuser NONE/- application/x-javascript
1263145045.781    141 11.22.333.44 TCP_HIT/200 8605 GET http://cdn.speedtest.net/global/jquery.easing.1.3.js myuser NONE/- application/javascript
1263145045.891    109 11.22.333.44 TCP_HIT/200 53694 GET http://cdn.speedtest.net/global/jquery-ui-personalized-1.6rc6.min.js myuser NONE/- application/x-javascript
1263145080.781    226 11.22.333.44 TCP_MISS/200 894 GET http://speedtest.net/favicon.ico myuser DIRECT/69.17.117.207 image/x-icon
1263145082.179      6 11.22.333.44 TCP_MISS/503 1730 POST http://safebrowsing.clients.google.com/safebrowsing/downloads? myuser DIRECT/74.125.65.100 text/html
1263145082.971      0 11.22.333.44 TCP_MEM_HIT/200 900 GET http://speedtest.net/favicon.ico myuser NONE/- image/x-icon
1263145084.477    920 11.22.333.44 TCP_MISS/200 4894 GET http://speedtest.net/ myuser DIRECT/69.17.117.207 text/html
1263145112.751   1170 11.22.333.44 TCP_MISS/200 4894 GET http://speedtest.net/ myuser DIRECT/69.17.117.207 text/html
1263145112.780      2 11.22.333.44 TCP_MISS/200 1629 GET http://cdn.speedtest.net/reset-fonts.css? myuser DIRECT/72.21.81.133 text/css
1263145112.931    150 11.22.333.44 TCP_HIT/200 2113 GET http://cdn.speedtest.net/images/bg-main.gif myuser NONE/- image/gif
1263145113.075    144 11.22.333.44 TCP_HIT/200 47279 GET http://cdn.speedtest.net/images/bg-top.gif myuser NONE/- image/gif
1263145113.348    217 11.22.333.44 TCP_HIT/200 3775 GET http://cdn.speedtest.net/images/s-icons.gif myuser NONE/- image/gif
1263145113.439     15 11.22.333.44 TCP_MISS/200 666 GET http://cdn.speedtest.net/images/bg-secondarymenu.gif myuser DIRECT/72.21.81.133 image/gif
1263145113.508    433 11.22.333.44 TCP_MISS/200 1416 GET http://ads.ookla.com/adjs.php? myuser DIRECT/69.17.117.207 application/x-javascript
1263145113.508     68 11.22.333.44 TCP_HIT/200 9458 GET http://cdn.speedtest.net/images/s-ptlink.png myuser NONE/- image/png
1263145113.645     62 11.22.333.44 TCP_MISS/200 10259 GET http://cdn.speedtest.net/global/swfobject.js? myuser DIRECT/72.21.81.133 application/x-javascript
1263145113.792    272 11.22.333.44 TCP_MISS/200 25357 GET http://ads.ookla.com/adimage.php? myuser DIRECT/69.17.117.207 image/jpeg
1263145113.908    116 11.22.333.44 TCP_MISS/200 7417 GET http://cdn.speedtest.net/global/st.js? myuser DIRECT/72.21.81.133 application/javascript
1263145114.001     93 11.22.333.44 TCP_HIT/200 7377 GET http://www.google-analytics.com/urchin.js myuser NONE/- text/javascript
1263145114.127    126 11.22.333.44 TCP_MISS/200 1155 GET http://ads.ookla.com/adlog.php? myuser DIRECT/69.17.117.207 image/gif
1263145114.261     87 11.22.333.44 TCP_MISS/200 1418 GET http://ads.ookla.com/adjs.php? myuser DIRECT/69.17.117.207 application/x-javascript
1263145114.270    246 11.22.333.44 TCP_HIT/200 59357 GET http://cdn.speedtest.net/images/s-ptpromo.png myuser NONE/- image/png
1263145114.563    292 11.22.333.44 TCP_HIT/200 37403 GET http://cdn.speedtest.net/images/s-promos.jpg myuser NONE/- image/jpeg
1263145114.887    291 11.22.333.44 TCP_MISS/200 31065 GET http://ads.ookla.com/adimage.php? myuser DIRECT/69.17.117.207 image/gif
1263145115.141    236 11.22.333.44 TCP_MISS/200 1445 GET http://ads.ookla.com/adlog.php? myuser DIRECT/69.17.117.207 image/gif
1263145115.200     25 11.22.333.44 TCP_HIT/200 15772 GET http://cdn.speedtest.net/images/bg-bottom.gif myuser NONE/- image/gif
1263145115.593      9 11.22.333.44 TCP_HIT/200 2878 GET http://cdn.speedtest.net/images/logo-ookla.gif myuser NONE/- image/gif
1263145115.649     35 11.22.333.44 TCP_MISS/200 518 GET http://www.google-analytics.com/__utm.gif? myuser DIRECT/74.125.45.102 image/gif
1263145116.744   2166 11.22.333.44 TCP_MISS/200 414805 GET http://cdn.speedtest.net/flash/speedtest-fcc.swf? myuser DIRECT/72.21.81.133 application/x-shockwave-flash
1263145117.195    437 11.22.333.44 TCP_MISS/200 623 GET http://speedtest.net/crossdomain.xml myuser DIRECT/69.17.117.207 application/xml
1263145117.657    462 11.22.333.44 TCP_MISS/200 28189 GET http://speedtest.net/speedtest-config.php? myuser DIRECT/69.17.117.207 text/xml
1263145126.196    604 11.22.333.44 TCP_HIT/200 616 GET http://speedtest.nefcom.net/crossdomain.xml myuser NONE/- text/xml
1263145126.339    142 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145126.488    149 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145126.656     63 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145126.815    158 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145126.987    171 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145127.146    159 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145127.314    118 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145127.491    177 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145127.658     63 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145127.820    161 11.22.333.44 TCP_MISS/200 424 GET http://speedtest.nefcom.net/speedtest/latency.txt? myuser DIRECT/69.57.112.4 text/plain
1263145128.925    986 11.22.333.44 TCP_MISS/200 245821 GET http://speedtest.nefcom.net/speedtest/random350x350.jpg? myuser DIRECT/69.57.112.4 image/jpeg
1263145129.268   1449 11.22.333.44 TCP_MISS/200 245821 GET http://speedtest.nefcom.net/speedtest/random350x350.jpg? myuser DIRECT/69.57.112.4 image/jpeg
1263145139.471   9876 11.22.333.44 TCP_MISS/200 1986719 GET http://speedtest.nefcom.net/speedtest/random1000x1000.jpg? myuser DIRECT/69.57.112.4 image/jpeg
1263145140.215  10439 11.22.333.44 TCP_MISS/200 1986719 GET http://speedtest.nefcom.net/speedtest/random1000x1000.jpg? myuser DIRECT/69.57.112.4 image/jpeg
1263145140.621    384 11.22.333.44 TCP_MISS/200 350 POST http://speedtest.nefcom.net/speedtest/upload.php? myuser DIRECT/69.57.112.4 text/html
1263145140.659    191 11.22.333.44 TCP_MISS/200 350 POST http://speedtest.nefcom.net/speedtest/upload.php? myuser DIRECT/69.57.112.4 text/html
1263145140.971    144 11.22.333.44 TCP_MISS/200 350 POST http://speedtest.nefcom.net/speedtest/upload.php? myuser DIRECT/69.57.112.4 text/html
1263145155.484    407 11.22.333.44 TCP_MISS/200 4489 GET http://www.pingtest.net/ myuser DIRECT/69.17.117.207 text/html
1263145155.599     77 11.22.333.44 TCP_MISS/200 1629 GET http://cdn.pingtest.net/reset-fonts.css? myuser DIRECT/72.21.81.133 text/css
1263145155.644     29 11.22.333.44 TCP_MISS/200 1230 GET http://cdn.pingtest.net/base.css? myuser DIRECT/72.21.81.133 text/css
1263145155.755    110 11.22.333.44 TCP_HIT/200 27896 GET http://cdn.pingtest.net/global/jqueryui/css/custom-theme/jquery-ui-1.7.2.custom.css myuser NONE/- text/css
1263145155.904    114 11.22.333.44 TCP_MISS/200 32119 GET http://cdn.pingtest.net/pt.css? myuser DIRECT/72.21.81.133 text/css
1263145156.453    550 11.22.333.44 TCP_HIT/200 57762 GET http://cdn.pingtest.net/global/jquery-1.3.2.min.js myuser NONE/- application/javascript
1263145156.813    197 11.22.333.44 TCP_HIT/200 8608 GET http://cdn.pingtest.net/global/jquery.easing.1.3.js myuser NONE/- application/javascript
1263145157.068    255 11.22.333.44 TCP_HIT/200 53577 GET http://cdn.pingtest.net/global/jqueryui/js/jquery-ui-1.7.2.custom.min.js myuser NONE/- application/javascript
1263145157.580    167 11.22.333.44 TCP_MISS/200 2000 GET http://www.pingtest.net/global/functions.js? myuser DIRECT/69.17.117.207 application/javascript
1263145157.920    303 11.22.333.44 TCP_MISS/200 10259 GET http://cdn.pingtest.net/global/swfobject.js? myuser DIRECT/72.21.81.133 application/x-javascript
1263145158.100    180 11.22.333.44 TCP_MISS/200 14365 GET http://cdn.pingtest.net/global/deployJava.js? myuser DIRECT/72.21.81.133 application/x-javascript
1263145158.312    212 11.22.333.44 TCP_MISS/200 6129 GET http://cdn.pingtest.net/global/pt.js? myuser DIRECT/72.21.81.133 application/javascript
1263145158.409     96 11.22.333.44 TCP_MISS/200 15439 GET http://pagead2.googlesyndication.com/pagead/expansion_embed.js myuser DIRECT/74.125.65.167 text/javascript
1263145158.582     61 11.22.333.44 TCP_MISS/200 1324 GET http://cdn.pingtest.net/images/bg-main.gif myuser DIRECT/72.21.81.133 image/gif
1263145159.302    685 11.22.333.44 TCP_MISS/200 159482 GET http://cdn.pingtest.net/images/bg-top.png myuser DIRECT/72.21.81.133 image/png
1263145160.303    685 11.22.333.44 TCP_MISS/200 4913 GET http://googleads.g.doubleclick.net/pagead/ads? myuser DIRECT/74.125.65.154 text/html
1263145160.393     90 11.22.333.44 TCP_MISS/200 1561 GET http://pagead2.googlesyndication.com/pagead/abglogo/abg-en-100c-000000.png myuser DIRECT/74.125.65.167 image/png
1263145160.444     50 11.22.333.44 TCP_MISS/200 2269 GET http://pagead2.googlesyndication.com/pagead/sma8.js myuser DIRECT/74.125.65.167 text/javascript
1263145160.490     45 11.22.333.44 TCP_MISS/200 2344 GET http://cdn.pingtest.net/images/logo-pingtest.gif myuser DIRECT/72.21.81.133 image/gif
1263145160.787    167 11.22.333.44 TCP_MISS/200 3597 GET http://cdn.pingtest.net/images/s-icons.gif myuser DIRECT/72.21.81.133 image/gif
1263145160.881     93 11.22.333.44 TCP_MISS/200 666 GET http://cdn.pingtest.net/images/bg-secondarymenu.gif myuser DIRECT/72.21.81.133 image/gif
1263145160.949     68 11.22.333.44 TCP_MISS/200 5964 GET http://cdn.pingtest.net/images/s-stlink.gif myuser DIRECT/72.21.81.133 image/gif
1263145161.040     92 11.22.333.44 TCP_MISS/200 1650 GET http://cdn.pingtest.net/images/bg-pt.gif myuser DIRECT/72.21.81.133 image/gif
1263145161.089     48 11.22.333.44 TCP_MISS/200 1214 GET http://pagead2.googlesyndication.com/pagead/sma_blank.png myuser DIRECT/74.125.65.167 image/png
1263145174.604     85 11.22.333.44 TCP_HIT/200 934 GET http://www.pingtest.net/favicon.ico myuser NONE/- image/x-icon
1263145176.212    580 11.22.333.44 TCP_MISS/200 4489 GET http://www.pingtest.net/ myuser DIRECT/69.17.117.207 text/html
1263145176.761    549 11.22.333.44 TCP_MISS/200 4883 GET http://googleads.g.doubleclick.net/pagead/ads? myuser DIRECT/74.125.65.154 text/html
1263145179.217    583 11.22.333.44 TCP_MISS/200 4489 GET http://www.pingtest.net/ myuser DIRECT/69.17.117.207 text/html
1263145179.310      9 11.22.333.44 TCP_MISS/200 3022 GET http://cdn.pingtest.net/global/browserdetect.js? myuser DIRECT/72.21.81.133 application/x-javascript
1263145179.592    281 11.22.333.44 TCP_MISS/200 4895 GET http://googleads.g.doubleclick.net/pagead/ads? myuser DIRECT/74.125.65.154 text/html
1263145179.593    162 11.22.333.44 TCP_MISS/200 31685 GET http://cdn.pingtest.net/images/s-promos.jpg myuser DIRECT/72.21.81.133 image/jpeg
1263145182.006     11 11.22.333.44 TCP_DENIED/407 1821 GET http://cdn.pingtest.net/LQApplet.jar - NONE/- text/html
1263145209.341      5 11.22.333.44 TCP_DENIED/407 1821 GET http://cdn.pingtest.net/LQApplet.jar myuser NONE/- text/html

```

---

### Post by MountainX on 2010-01-10
checking something else before I post a follow up...

---

### Post by MountainX on 2010-01-10
confused. taking a break...

---

### Post by Barriehie on 2010-01-10
See if your squid.conf has this line:
```

acl CONNECT method CONNECT

```

---

### Post by MountainX on 2010-01-10
> **Barriehie said:**
> See if your squid.conf has this line:
```

acl CONNECT method CONNECT

```
yes, I have that line

---

### Post by Barriehie on 2010-01-10
Okay, how about attaching your squid.conf?

---

### Post by MountainX on 2010-01-10
> **Barriehie said:**
> Okay, how about attaching your squid.conf?

Here it is:
[http://talk.maemo.org/showpost.php?p=462461&postcount=48](http://talk.maemo.org/showpost.php?p=462461&postcount=48)

---

