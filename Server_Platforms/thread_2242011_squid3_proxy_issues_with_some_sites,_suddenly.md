---
title: "squid3 proxy issues with some sites, suddenly?"
date: 2014-08-30
forum: Server Platforms
---

### Post by Higgins909 on 2014-08-30
I moved to a new house and got a different isp, not one thing changed with my server or desktop.

Websites like youtube google and facebook, and a few smaller websites have issues loading.
 I don't know why, but when I take proxy settings off those select websites work fine :/

old isp SuddenLink new isp AT&T

I tried rebuilding my cache, and that was a waste :/

squid3.... its on the LAN and only for people on the local network. ran fine for a few years without problem.

if you need some info I will do my best to get it.

Thanks,
Higgins909

---

### Post by SeijiSensei on 2014-08-30
I presume you are not proxying HTTPS traffic through Squid.  Sites like Google and Facebook usually default to HTTPS these days.  If you monitor squid's access.log, what do you see when you make requests at these sites?

---

### Post by Higgins909 on 2014-08-30
the top ones are google, and some other ones are squid website, lots of tcp_miss/200? i never understood how to read the 2 bigger numbers at the start of log

```
1409416280.338 115555 192.168.0.77 TCP_MISS/200 4884 CONNECT bn1msgr1010701.gateway.messenger.live.com:443 - DIRECT/134.170.18.40 -
1409416350.857 176223 192.168.0.77 TCP_MISS/200 2236 CONNECT safebrowsing.google.com:443 - DIRECT/2607:f8b0:4000:807::1000 -
1409416350.860 176009 192.168.0.77 TCP_MISS/200 21763 CONNECT safebrowsing-cache.google.com:443 - DIRECT/2607:f8b0:4000:805::1003 -
1409416438.995     64 192.168.0.77 TCP_MISS/200 730 GET http://www.google.com/url? - DIRECT/2607:f8b0:4000:807::1012 text/html
1409416439.394    216 192.168.0.77 TCP_MISS/200 9082 GET http://www.squid-cache.org/ - DIRECT/209.169.10.131 text/html
1409416439.518     57 192.168.0.77 TCP_MISS/200 4022 GET http://www.squid-cache.org/default.css - DIRECT/209.169.10.131 text/css
1409416439.738    180 192.168.0.77 TCP_MISS/200 29243 GET http://www.squid-cache.org/Images/img4.jpg - DIRECT/209.169.10.131 image/jpeg
1409416439.775    115 192.168.0.77 TCP_MISS/200 624 GET http://www.squid-cache.org/Images/img2.gif - DIRECT/209.169.10.131 image/gif
1409416439.790    110 192.168.0.77 TCP_MISS/200 607 GET http://www.squid-cache.org/Images/img5.gif - DIRECT/209.169.10.131 image/gif
1409416439.793    113 192.168.0.77 TCP_MISS/200 962 GET http://www.squid-cache.org/Images/img1.gif - DIRECT/209.169.10.131 image/gif
1409416439.794    114 192.168.0.77 TCP_MISS/200 954 GET http://www.squid-cache.org/Images/img3.gif - DIRECT/209.169.10.131 image/gif
1409416439.800    121 192.168.0.77 TCP_MISS/200 940 GET http://www.squid-cache.org/Images/img8.gif - DIRECT/209.169.10.131 image/gif
1409416439.800    121 192.168.0.77 TCP_MISS/200 605 GET http://www.squid-cache.org/Images/img7.gif - DIRECT/209.169.10.131 image/gif
1409416440.138     77 192.168.0.77 TCP_MISS/200 1846 GET http://www.squid-cache.org/favicon.ico - DIRECT/209.169.10.131 image/x-icon
1409416447.646    266 192.168.0.77 TCP_MISS/200 8822 GET http://www.squid-cache.org/Intro/ - DIRECT/209.169.10.131 text/html
1409416456.235    108 192.168.0.77 TCP_MISS/200 1151 GET http://www.squid-cache.org/cfgman.css - DIRECT/209.169.10.131 text/css
1409416457.505   1621 192.168.0.77 TCP_MISS/200 241959 GET http://www.squid-cache.org/Doc/config/ - DIRECT/209.169.10.131 text/html
1409416461.925    212 192.168.0.77 TCP_MISS/200 13277 GET http://www.squid-cache.org/Doc/config/access_log/ - DIRECT/209.169.10.131 text/html
```

All I ever really changed was refresh_pattern and some ram and cache location/size in webmin
```
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i \.(gif|png|jpg|jpeg|ico)$ 10080 90% 43200 override-expire ignore-no-cache ignore-no-store ignore-private
refresh_pattern -i \.(iso|avi|wav|mp3|mp4|mpeg|swf|flv|x-flv)$ 43200 90% 432000 override-expire ignore-no-cache ignore-no-store ignore-private
refresh_pattern -i \.(deb|rpm|exe|zip|tar|tgz|ram|rar|bin|ppt|doc|tiff)$ 10080 90% 43200 override-expire ignore-no-cache ignore-no-store ignore-private
refresh_pattern -i \.index.(html|htm)$ 0 40% 10080
refresh_pattern -i \.(html|htm|css|js)$ 1440 40% 40320
refresh_pattern . 0 40% 40320
```

google can hang when you already searched something and try searching somthing else, it just sits there white screen with searchbar...
youtube mostly wont load videos or thumbs some of the time, but when a video does load it load like 2-9 seconds then stops then like half minute later loads more then 2-9 then repeats.
tho it never done this before? during the move it was about 2 weeks b4 I could setup my stuff again.
if im not proxying https then shouldn't it go without being cached or something?

---

### Post by SeijiSensei on 2014-08-31
The Google connections are using IPv6.  I don't know whether that matters.

---

### Post by Higgins909 on 2014-10-26
Sorry for the very late reply, but I ended up finding a ipv6 option in my router, turned that off and it works fine.  I wonder what if I had used my ipv6 address, but I really don't understand ipv6.

Solved.

---

