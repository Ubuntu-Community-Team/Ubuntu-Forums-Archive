---
title: "cgi &amp; lighttpd 500 internal server error"
date: 2009-12-18
forum: Server Platforms
---

### Post by sartic on 2009-12-18
2009-12-18 09:12:28: (log.c.97) server started 
2009-12-18 09:13:17: (mod_cgi.c.584) cgi died, pid: 1892 
2009-12-18 09:13:20: (mod_cgi.c.584) cgi died, pid: 1893 
2009-12-18 09:13:28: (mod_cgi.c.584) cgi died, pid: 1894 
2009-12-18 09:13:30: (mod_cgi.c.584) cgi died, pid: 1895 

ligttpd works great, i enabled mod cgi but whenever i try to pipe cgi width my program i have "500 internal server error"
Question how do I enable some more deeper loging of lighttpd?
cgi died not helping me

---

### Post by sanitycheck on 2010-01-03
I don't think it's you, I think it's lighttpd in 9.10 (assumes you use 9.10).  I'm still having problems with CGI.  This is true for systems upgraded to 9.10 from an earlier version, and fresh installs.

One fix turned out to be the *opposite* of a fix for an earlier lighttpd bug or bugs (#292347 and #179484).  The fix for those bugs is to comment out a line in 10-cgi.conf, but I *added* that line and could finally get CGI to work on both localhost and from a remote client.

I added the "server.modules" line here:

```
server.modules  += ( "mod_cgi" )

alias.url       += ( "/cgi-bin/" => "/usr/lib/cgi-bin/" )

$HTTP["remoteip"] =~ "127.0.0.1" {
	alias.url = ( "/cgi-bin/" => "/usr/lib/cgi-bin/" )
	$HTTP["url"] =~ "^/cgi-bin/" {
		cgi.assign = ( "" => "" )
	}
}

$HTTP["url"] =~ "^/cgi-bin/" {
	cgi.assign = ( "" => "" )
}
```

One of two CGI programs running on one Core2 server still does not work, and it did before I upgraded it to 9.10.  This was a server I upgraded from 8.04 LTS all the way to 9.10 over a couple of days.  I believe, however, CGI stopped working earlier in the upgrade process, at 8.10 or 9.04.  I dismissed the failure initially as a minor problem thinking I could easily fix it later.  A fresh 9.10 install on the same box has the same problem with the same program.

Somehow I got the problem CGI program to work on a Core i5 9.10 workstation, but still can't get it to work on the Core2.  They're both 64-bit installs, though the Core i5 is Kubuntu Desktop and the Core2 is Server.  I've spent hours trying to figure out what is different, but can't find anything.

The CGI program I eventually got to work was the [[COLOR="Blue"]Motion related project[/COLOR]]("http://www.lavrsen.dk/foswiki/bin/view/Motion/MjpegProxyGrab") called mj-prox.  The program mj-grab is the one that I still can't get to work.

---

### Post by sartic on 2010-01-03
Yeap 64bit karmic desktop on amd x2. Thx 4 msg I will try it.

---

