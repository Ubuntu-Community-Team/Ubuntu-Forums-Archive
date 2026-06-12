---
title: "Samba security"
date: 2010-09-07
forum: Security
---

### Post by SquALeD on 2010-09-07
Hi there, 

Been running 9.04 desktop successfully for quite a while now with Samba, Transmission, Zoneminder and VSFTP but have recently reinstalled with 10.04 server as I've been playing around with terminal/ssh via a virtual machine on my iMac.

Its up and running with hardly any snags at all. Really impressed and so glad i went to a server distro. :p

Now, I know about securing my ssh via paired keys but do I have to do anything with the Samba install to secure it seeing as its within my lan? or am I missing something..All I've done in the smb.conf is to share my 3 NTFS  media HDDs with my music/movies etc on. I've not set up any per user share options at all. Works flawlessly with a Mac/Windows environment and also with my 2 DLNA media streamers. Too easily in fact... paranoia...

Is it safe to allow Samba to be configured like this?

---

### Post by bodhi.zazen on 2010-09-07
So long as you are behind a router you are fine.

I assume you are a home user and you do not have any users on your LAN who would abuse your shares.

If your shares are private, I would use kerberos .

---

### Post by SquALeD on 2010-09-07
Hi bodhi.zazen thank you for the reply.

Yes, Samba is operating on my private lan behind a router/firewall with minimal ports open, even the (non default) SSH port and FTP port are closed until i need them from outside my lan.

Thanks for the info..!


[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")_**[[COLOR=#980101][B]**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")[/B]_

---

### Post by bodhi.zazen on 2010-09-07
> **SquALeD said:**
> Hi bodhi.zazen thank you for the reply.

Yes, Samba is operating on my private lan behind a router/firewall with minimal ports open, even the (non default) SSH port and FTP port are closed until i need them from outside my lan.

Thanks for the info..!




IMO you are fine with that setup.

---

