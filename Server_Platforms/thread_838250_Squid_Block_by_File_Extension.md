---
title: "Squid Block by File Extension"
date: 2008-06-23
forum: Server Platforms
---

### Post by tuhintt on 2008-06-23
I have configure my squid to block some file by extension to prevent downloading. example,

acl BlockExt url_regex -i \.mp3$ \.asx$ \.wma$ \.wmv$ \.avi$ \.mpeg$ 
http_access deny BlockExt all

And its working fine. most of mp3,mpg download is blocked but recently i have discovered user can download mp3 from some specific web site. like [www.mp3.com](www.mp3.com). ([http://www.mp3.com/free-music/11-A/all-free-music](http://www.mp3.com/free-music/11-A/all-free-music))

I have check and found this sites user different kind of link to download like,
[http://dw.com.com/redir?siteid=31&edid=3&ptid=&ontid=11735&ctype=RF;Song;ATN;PTNR&cval=3;21460710;2;&desturl=http%3A%2F%2Fdownload.mp3.com%2Findex.php%3Fsect%3Dforce_download%26type%3D3%26track_id%3D21460710%26time%3D1214201264%26auth%3Db286519c195e3dc51e7c0fee7fdda182](http://dw.com.com/redir?siteid=31&edid=3&ptid=&ontid=11735&ctype=RF;Song;ATN;PTNR&cval=3;21460710;2;&desturl=http%3A%2F%2Fdownload.mp3.com%2Findex.php%3Fsect%3Dforce_download%26type%3D3%26track_id%3D21460710%26time%3D1214201264%26auth%3Db286519c195e3dc51e7c0fee7fdda182)

if i check my squid access log, i have only found this log,
[http://dw.com.com/redir?](http://dw.com.com/redir?)
[http://download.mp3.com/index.php?](http://download.mp3.com/index.php?) 

i am afraid maybe there is more site user can download mp3 or mpg files without any restriction.

Did i mis configure my squid? Pls help.

Thanks to All.

---

### Post by Cadmus on 2008-06-23
I'm not sure how mature it is as a method, but squid can restrict content by MIME type.

[Blocking MIME types (from Squid wiki)]("http://wiki.squid-cache.org/KnowledgeBase/BlockingMimeTypes")

---

### Post by windependence on 2008-06-23
> **tuhintt said:**
> I have configure my squid to block some file by extension to prevent downloading. example,

acl BlockExt url_regex -i \.mp3$ \.asx$ \.wma$ \.wmv$ \.avi$ \.mpeg$ 
http_access deny BlockExt all

And its working fine. most of mp3,mpg download is blocked but recently i have discovered user can download mp3 from some specific web site. like [www.mp3.com](www.mp3.com). ([http://www.mp3.com/free-music/11-A/all-free-music](http://www.mp3.com/free-music/11-A/all-free-music))

I have check and found this sites user different kind of link to download like,
[http://dw.com.com/redir?siteid=31&edid=3&ptid=&ontid=11735&ctype=RF;Song;ATN;PTNR&cval=3;21460710;2;&desturl=http%3A%2F%2Fdownload.mp3.com%2Findex.php%3Fsect%3Dforce_download%26type%3D3%26track_id%3D21460710%26time%3D1214201264%26auth%3Db286519c195e3dc51e7c0fee7fdda182](http://dw.com.com/redir?siteid=31&edid=3&ptid=&ontid=11735&ctype=RF;Song;ATN;PTNR&cval=3;21460710;2;&desturl=http%3A%2F%2Fdownload.mp3.com%2Findex.php%3Fsect%3Dforce_download%26type%3D3%26track_id%3D21460710%26time%3D1214201264%26auth%3Db286519c195e3dc51e7c0fee7fdda182)

if i check my squid access log, i have only found this log,
[http://dw.com.com/redir?](http://dw.com.com/redir?)
[http://download.mp3.com/index.php?](http://download.mp3.com/index.php?) 

i am afraid maybe there is more site user can download mp3 or mpg files without any restriction.

Did i mis configure my squid? Pls help.

Thanks to All.

This is done using a URL rewrite, a mask, or a redirect to protect the real location of the download files. You will find quite a few sites like this. You would need something that could detect the file type before it starts streaming. Unfortunately, that isn't easy. The only other suggestion is blocking known sites like Websense does. Personally I abhor that stuff but I understand your reasons.

-Tim

---

### Post by madunix on 2012-04-23
I have also done the above ... but still they could bypass proxy if they want download .zip  , they write into the URL .zip?mmmm then the file can be download .... how can be this stopped.

---

