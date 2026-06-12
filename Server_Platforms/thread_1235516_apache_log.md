---
title: "apache log"
date: 2009-08-09
forum: Server Platforms
---

### Post by blindmen on 2009-08-09
[B]Anyone can explain plz ?

my server name is doctore.sk

I expected to see in my apache logs sth like this

e.g

117.82.83.230 - - [09/Aug/2009:12:54:56 +0200] "GET [http://www.doctore.sk](http://www.doctore.sk) HTTP/1.0" 404 213 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"

BUT

this is what I've found. Loads of weird stuff for me.
[/B]  
117.82.83.230 - - [09/Aug/2009:12:54:56 +0200] "GET [http://www.accessteams.com/proxyheader.php](http://www.accessteams.com/proxyheader.php) HTTP/1.0" 404 213 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
78.108.178.170 - - [09/Aug/2009:12:54:57 +0200] "POST [http://flatearth.sakura.ne.jp/mgf/mt-tb.cgi/1968](http://flatearth.sakura.ne.jp/mgf/mt-tb.cgi/1968) HTTP/1.1" 404 216 "http://flatearth.sakura.ne.jp/" "Mozilla/5.0 (Windows; U; Windows NT 5.1; ru; rv:1.8.0.4) Gecko/20060508 Firefox/1.5.0.4"
58.221.28.242 - - [09/Aug/2009:12:54:57 +0200] "GET [http://www.jzmusf.cn/default.aspx](http://www.jzmusf.cn/default.aspx) HTTP/1.1" 404 184 "http://www.baidu.com" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1)"
220.175.122.99 - - [09/Aug/2009:12:54:57 +0200] "GET [http://www.sbwww.cn/tubiao/ssc/kjfx.asp?qishu=28](http://www.sbwww.cn/tubiao/ssc/kjfx.asp?qishu=28) HTTP/1.1" 404 189 "\xcf\xf2http://js.sbwww.cn\xbf\xaa\xbb\xf0" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1)"
78.108.178.170 - - [09/Aug/2009:12:54:57 +0200] "POST [http://blog.expandexcellence.com/2007/02/14/happy-valentines-day-with-nancy-laine-numerologist/trackback.aspx](http://blog.expandexcellence.com/2007/02/14/happy-valentines-day-with-nancy-laine-numerologist/trackback.aspx) HTTP/1.1" 404 274 "http://blog.expandexcellence.com/" "Mozilla/5.0 (Windows; U; Windows NT 5.1; ru; rv:1.8.0.4) Gecko/20060508 Firefox/1.5.0.4"


[B]Any idea why and how can I restrict or ban those offending clients ?

Thanks[/B]

---

