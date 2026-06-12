---
title: "ssh connects, but dumps me out without error message"
date: 2006-01-14
forum: Server Platforms
---

### Post by mad_phoenix on 2006-01-14
The title pretty much says it all.  I have a Ubuntu box on my LAN (server install) that I'm trying to configure as a web server.  I went through the ubuntu install and installed openssh-server.  Checked whether it was functional from Putty on a windows machine, it works.  Now at my home, when I try to connect from my ubuntu laptop, it gives me this...

```
btimm@MadPhoenix:~$ ssh -l btimm 192.168.1.102
btimm@192.168.1.102's password:
Linux MadPhoenix 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sat Jan 14 16:04:07 2006
btimm@MadPhoenix:~$

```

Notice anything strange?  Like the fact that it connects, gives the welcome message, and then returns me to my normal command prompt without an error message?  Does anybody know what's going on here, or have an idea of how I could fix it?  Thanks in advance!

--mad_phoenix

p.s. I also tried putting the hostname into my /etc/hosts file and connecting that way.  Still didn't work.

---

### Post by Zelut on 2006-01-14
from your output above it looks like you're connecting to yourself (unless both machines have the same name).. 

I use ssh regularly to connect between my machines.  Each have a different name and that is the only way I can tell them apart..

---

### Post by mad_phoenix on 2006-01-14
Wow you were absolutely right.  Guess i should've looked at my dhcp clients table a little closer....

Thanks for pointing me in the right direction!

---

### Post by Zelut on 2006-01-14
Hey no problem :)

---

