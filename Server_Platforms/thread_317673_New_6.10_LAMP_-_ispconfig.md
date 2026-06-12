---
title: "New 6.10 LAMP - ispconfig"
date: 2006-12-12
forum: Server Platforms
---

### Post by Indiana Red on 2006-12-12
After following an excellent walk-through for the 6.10 LAMP server (no GUI)I am trying to get ispconfig running as well.  I am a linux command line ultra noob.  I have D/Ld the tar file on my XP box and my Ubuntu server is on the same LAN.
Just not sure how to get it over there and install it. :-k 
I think I am missing something here....
Anyone?

---

### Post by Zelut on 2006-12-12
actually, if your LAMP server has a network connection you can try this command to download it to your server directly & then follow the rest of the instructions to unzip & install:

wget [http://superb-west.dl.sourceforge.net/sourceforge/ispconfig/ISPConfig-2.2.8.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/ispconfig/ISPConfig-2.2.8.tar.gz)

I hope that helps.

---

### Post by Indiana Red on 2006-12-12
ah.  I found similar advice elsewhere.
Thanks


Got it to unpack and install.   Man that is a long setup process.  (slow computer)
Odd that I followed the "perfect setup ubuntu 6.10 server" including the Apache 2 w/ PHP but during the ispconfig it verifies Apache 1.3.xx was configured.
Odd.

---

### Post by gnaunited on 2006-12-12
I think it installs both, cause ISPconfig uses 1.3 and not 2. I could be wrong though.

---

### Post by Indiana Red on 2006-12-13
Well, I'll find out more once I can logint ISPCONFIG
My problem now is that from within my LAN/subnet, I can connect to [https://ipaddress:81](https://ipaddress:81)  but page canot be found on [https://domainname:81](https://domainname:81)
when using the IP, the browser connects, as the blue title bar shows the site I am "at" but the page is entirely blank.  Trying to view the source code, is even greyed out.  Nothign there.
Any suggestions.
A DNS problem sounds like?

---

### Post by zero-9376 on 2007-06-27
this sounds more like a firewall problem to me, perhaps you/your hosting service/your isp have port 81 closed off. if its you or the hoster you can enable port forwarding to allow access.

---

