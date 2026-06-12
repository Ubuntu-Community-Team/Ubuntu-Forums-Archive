---
title: "sort of two servers"
date: 2009-08-09
forum: Server Platforms
---

### Post by johnh10000 on 2009-08-09
Hi gang,

I have just come back off holiday, and repaired my broken mail server, which was easy, just didn't have time b4 hols.  I moved it to another box on my network, which is rapidly becoming my server box. JUanty.

My main box, (terminal) also running jaunty, is my annon ftp server, which works fine.  As my website is now be served from tux2, I need user ftp on that box to uplaod photos and the like, for the webiste.

Now to explain, I have one IP numeber, and dynadns so tux.isa-geek.org and tux2... basicly resolve to the same place.  So I ask my router to port forward, mail stuff to 192.168.1.4 (tux2) and annon ftp to 192.168.1.3 (tux)

So I have setup port 90-91 to be tux2's ftp.
I have changed services ftp bit to 90 and 91
and chaged proftpd's port number to 90.

but can't connect any ideas?

Resolving address of tux2.isa-geek.org
Status:	Connecting to 82.6.x.x:91...
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server

---
also I used NX while I was away, to logon, to update the website, this uses ssh. fine.  But to connect to tux, how would I change the ssh port of tux?

---

