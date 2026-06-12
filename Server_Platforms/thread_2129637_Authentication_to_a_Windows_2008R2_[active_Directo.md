---
title: "Authentication to a Windows 2008R2 [active Directory] stopped working"
date: 2013-03-26
forum: Server Platforms
---

### Post by ifmusic on 2013-03-26
Hi!, I've been reading around these forums but I'm still unable to solve my problem.
I have a ubuntu server box I put together some years ago. 
A couple of weeks ago, a co-worker told me me he could not login with his domain credentials.
I know he used to be able to do so, I had samba/winbind/kerberos working.

All the tests I perform come back just fine:
-The computer account is created ok
-id <aduser> returns perfectly
-sudo net ads testjoin, "Join is Ok"
everithing seems to be just fine, but!

if I go to a tty or ssh and enter my AD account at the login prompt.. Access Denied!
(Samba version 3.0.28a, my configured DC is running 2008R2)

Any clues? Thanks!
Rodrigo

---

