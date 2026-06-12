---
title: "apache errors"
date: 2009-08-08
forum: Server Platforms
---

### Post by blindmen on 2009-08-08
Hi all,

I've noticed that my apache spawn too many processes and it should really do nothing at the moment.

there is maybe 50-ty of them in ps -aux 

www-data 13028  0.0  0.5  33368  5268 ?        S    Aug07   0:07 /usr/sbin/apache2 -k start

in error.log I have lot of refusal messages like :

[Sun Aug 09 00:59:58 2009] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 222.73.15.202:80 (*) failed
[Sun Aug 09 00:59:55 2009] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 72.20.27.9:80 (*) failed
and so on ...

in the access.log every second few new requests are comming. I have a public static IP, but there is nothing running on my server at the moment.

e.g

58.221.28.242 - - [09/Aug/2009:00:57:32 +0200] "GET [http://www.jzmusf.cn/default.aspx](http://www.jzmusf.cn/default.aspx) HTTP/1.1" 404 299 "http://www.baidu.com" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1)"
60.10.222.25 - - [09/Aug/2009:01:00:40 +0200] "GET [http://mp3.baidu.com/m?f=ms&tn=baidump3&ct=134217728&lf=&rn=&word=%CF%E3%CB%AE%D3%D0%B6%BE+%BA%FA%D1%EE%C1%D6&lm=-1](http://mp3.baidu.com/m?f=ms&tn=baidump3&ct=134217728&lf=&rn=&word=%CF%E3%CB%AE%D3%D0%B6%BE+%BA%FA%D1%EE%C1%D6&lm=-1) HTTP/1.0" 200 9788 "http://mp3.baidu.com/m?f=ms&tn=baidump3&ct=134217728&lf=&rn=&word=%CF%E3%CB%AE%D3%D0%B6%BE+%BA%FA%D1%EE%C1%D6&lm=-1" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 2000; DigExt; TUCOWS Network)"
189-18-120-50.dsl.telesp.net.br - - [09/Aug/2009:01:00:46 +0200] "GET [http://217.146.187.16/config/isp_verify_user?l=golf_man5124&p=Cleo](http://217.146.187.16/config/isp_verify_user?l=golf_man5124&p=Cleo) HTTP/1.0" 200 26 "http://217.146.187.16" "-"
c-98-228-93-157.hsd1.il.comcast.net - - [09/Aug/2009:01:00:46 +0200] "GET [http://119.160.244.89/config/isp_verify_user?l=RUSTY986+&p=Misty](http://119.160.244.89/config/isp_verify_user?l=RUSTY986+&p=Misty) HTTP/1.0" 999 4707 "-" "-"
58.221.28.242 - - [09/Aug/2009:00:57:33 +0200] "GET [http://www.jzmusf.cn/default.aspx](http://www.jzmusf.cn/default.aspx) HTTP/1.1" 404 299 "http://www.baidu.com" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1)"
66-199-241-162.reverse.ezzi.net - - [09/Aug/2009:01:00:46 +0200] "GET [http://gobuysoftware.com/Internet-Download-Manager.html](http://gobuysoftware.com/Internet-Download-Manager.html) HTTP/1.0" 200 40550 "http://gobuysoftware.com/download-managers.html" "Mozilla/5.0 (Windows; U; Windows NT 5.1; ru; rv:1.9.0.7) Gecko/2009021910 Firefox/3.0.7\r"
61.147.123.22 - - [09/Aug/2009:01:00:43 +0200] "GET [http://ad.yieldmanager.com/imp?Z=300x250&s=585092&_salt=1801558638&B=12&m=2&u=http%3A%2F%2Fwww.roundarea.com%2F&r=1](http://ad.yieldmanager.com/imp?Z=300x250&s=585092&_salt=1801558638&B=12&m=2&u=http%3A%2F%2Fwww.roundarea.com%2F&r=1) HTTP/1.0" 200 686 "http://ad.yieldmanager.com/st?ad_type=iframe&ad_size=300x250&section=585092" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.4322; Alexa Toolbar)"
61.147.123.22 - - [09/Aug/2009:01:00:43 +0200] "GET [http://ad.103092804.com/st?ad_type=ad&ad_size=728x90&section=627489](http://ad.103092804.com/st?ad_type=ad&ad_size=728x90&section=627489) HTTP/1.0" 302 - "http://www.potentialability.com" "Mozilla/4.0 (compatible; MSIE 6.0; Win32)"
123.234.76.37 - - [09/Aug/2009:01:00:30 +0200] "GET [http://newyorkinvestmentgroup.com/?a=home](http://newyorkinvestmentgroup.com/?a=home) HTTP/1.1" 502 412 "http://newyorkinvestmentgroup.com/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1)"
41.207.20.66 - - [09/Aug/2009:01:00:39 +0200] "POST [http://mail.zoznam.sk/Session/99829-stOmYfDv9QGKM26KtRPI-jizepbo/compose.wssp](http://mail.zoznam.sk/Session/99829-stOmYfDv9QGKM26KtRPI-jizepbo/compose.wssp) HTTP/1.1" 200 522 "http://mail.zoznam.sk/Session/99829-stOmYfDv9QGKM26KtRPI-jizepbo/compose.wssp?OrigMessage=1477&OrigMailbox=INBOX&Operation=ReplyAll&" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
c-98-228-93-157.hsd1.il.comcast.net - - [09/Aug/2009:01:00:48 +0200] "GET [http://119.160.244.88/config/isp_verify_user?l=Rodja+&p=Misty](http://119.160.244.88/config/isp_verify_user?l=Rodja+&p=Misty) HTTP/1.0" 999 4707 "-" "-"
61.147.123.22 - - [09/Aug/2009:01:00:44 +0200] "GET [http://ad.yieldmanager.com/imp?Z=728x90&anprice=&s=627489&_salt=2777298681&B=12&m=2&u=http%3A%2F%2Fwww.potentialability.com%2F&r=1](http://ad.yieldmanager.com/imp?Z=728x90&anprice=&s=627489&_salt=2777298681&B=12&m=2&u=http%3A%2F%2Fwww.potentialability.com%2F&r=1) HTTP/1.0" 200 703 "http://www.potentialability.com" "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)"
61.147.99.131 - - [09/Aug/2009:01:00:46 +0200] "GET [http://ad.yieldmanager.com/imp?Z=300x250&s=657622&_salt=1480087594&B=12&m=2&u=http%3A%2F%2Fwww.debugscript.com%2F&r=1](http://ad.yieldmanager.com/imp?Z=300x250&s=657622&_salt=1480087594&B=12&m=2&u=http%3A%2F%2Fwww.debugscript.com%2F&r=1) HTTP/1.0" 200 701 "http://ad.xtendmedia.com/st?ad_type=iframe&ad_size=300x250&section=657622" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; .NET CLR 1.0.3705; Alexa Toolbar)"
61.147.99.131 - - [09/Aug/2009:01:00:46 +0200] "GET [http://ad.xtendmedia.com/imp?Z=300x250&s=657622&_salt=389703533&B=12&m=2&u=http%3A%2F%2Fwww.debugscript.com%2F&r=1](http://ad.xtendmedia.com/imp?Z=300x250&s=657622&_salt=389703533&B=12&m=2&u=http%3A%2F%2Fwww.debugscript.com%2F&r=1) HTTP/1.0" 302 - "http://ad.xtendmedia.com/st?ad_type=iframe&ad_size=300x250&section=657622" "Mozilla/4.0 (compatible; MSIE 5.5; Windows 98; Alexa Toolbar)"
61.147.123.22 - - [09/Aug/2009:01:00:46 +0200] "GET [http://ad.yieldmanager.com/st?anprice=&ad_type=ad&ad_size=728x90&section=650840](http://ad.yieldmanager.com/st?anprice=&ad_type=ad&ad_size=728x90&section=650840) HTTP/1.0" 200 4167 "http://www.topsbrand.com" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; Alexa Toolbar)"


any ideas ???

Thanks

---

### Post by Vegan on 2009-08-08
This looks a lot like a DDoS type of a situation. My own server can manage with 1 million hit a second, so I scream "bite me".

I set up my system to be able to cope with extreme loads intentionally. I have an advanced Ethernet adapter to help with the loading.

Some tard attacked my site a month ago, he could not bring my server down. :lol: I had some 285,000 hits in an hour according to Google. Usually its somewhat less than that.

My advice, get a high-end adapter and network hardware and this should help a bit.

---

### Post by blindmen on 2009-08-09
Well , yes that's the part I agree with.

Questions are 

1. WHY ? my server is really not interesting ... for now it was serving only It work's page

2. It significantly slowed the response from apache server. (everything else worked promptly). What can I do about it

3. [Sun Aug 09 00:59:58 2009] [error] (110)Connection timed out: proxy: HTTP: **attempt to connect to 222.73.15.202:80** (*) failed
why this error is in my error.log ? I do not attempt to connect that host. It looks like it's some kind of action of my apache on the requests mentioned above.

Thanks

---

### Post by tuam on 2009-09-16
It may be a little late, but you might be running your apache as proxy for others. You really shouldn't allow apache to do this :?

FF,

Daniel

---

### Post by t3r0 on 2009-09-16
seems like that you are allowing proxy requests to everyone. This is really bad idea. Please see [http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html) for information about configuring and securing your apache proxy

---

