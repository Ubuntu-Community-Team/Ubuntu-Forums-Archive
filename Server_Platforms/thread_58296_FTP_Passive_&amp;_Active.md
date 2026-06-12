---
title: "FTP Passive &amp; Active"
date: 2005-08-19
forum: Server Platforms
---

### Post by lee_connell on 2005-08-19
Hey all,

I'm completely stumped here even after googling around for answers.  I have a client running war ftp on a windows 2000 box.  Some clients outside of the server network can connect and list directories and transfer files and some others cannot. 

It seems xp machines cannot list directories.  from linux or windows 2003 it works fine.  NOTE:  i am not using passive yet active and all these client machines are behind firewalls not allowing any incoming port traffic.  

How is this even working on the linux and win2k3 machines?  Is it connecting back through the original connection made by the client?  I'm confused on how this is working because in active mode the client needs certain ports open to allow this to happen which is not the case.

Also why does some clients being xp not allow this to happen even with firewall (internal) is off.

I hope i am somewhat clear on this.  I just want to understand the reason of WHY it is working on some and how.

I do know how to fix this by using passive on the ftp server and setting a port range but im more interested in how its working for some the way it's setup now

thanks!

---

### Post by gruepig on 2005-08-20
My guess is that Linux is silently falling back to passive mode when active mode fails.  Either that or even though your clients are behind firewalls, they have an exception for active mode ftp.  (In general, passive mode is what you want, so if that works, you're all set.  For an explanation of active and passive mode ftp, see [http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html).)

---

### Post by lee_connell on 2005-08-22
none of the clients are allowing traffic in.  My company is behind a pix and one out of 3 computers running xp pro w/ sp2 can log in and retrieve files and dir listings.  It's completely awkward and makes troubleshooting much harder and frusterating.  Any idea on that?

Anyways i'm going to just configure the ftp server to use passive port range and open it up on the firewall.

thanks, and if you have a reason why it was working i would be greatly thankful.

---

### Post by LordHunter317 on 2005-08-23
That one box was most definitely behind a firewall.

If the clients are behidn a firewall or NAT, then you want to use passive FTP.  ACtive FTP doesn't work with NAT or a firewall without special support in the firewall, or a FTP-proxy.

If the server is behind a firewall or NAT, then you want to use active FTP.  Passive FTP doesn't work with NAT or a firewall without special support in the firewall, or a FTP-proxy.

Needless to say, putting a FTP Server behind NAT is a bad idea.  Realistically, that would require you to use a FTP proxy.

---

