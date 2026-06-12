---
title: "Trouble installing Realtek RTL8188EE Driver on Kali Linux"
date: 2015-11-25
forum: Ubuntu/Debian BASED
---

### Post by Tristan_Young on 2015-11-25
After about 2 sleepless nights, i can't possibly find out why my wifi card isn't working on my laptop. AT first, it would connect to my network, however my network manager was not able to find an ip with DHCP or by setting up a static IP address, not allowing me to have internet access. I figured i just needed to update my driver but keep getting an error 2 message whenever i try to run "make" under super user. 

Dl'ed the driver version:* rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013*

Here is an a screenshot of the error message i get: [ATTACH=CONFIG]265775[/ATTACH]

My wifi card fails to find an IP on other versions as well.

Here is the output from uname -a if that helps find a solution: [I]Linux kali 3.18.0-kali1-amd64 #1 SMP Debian 3.18.3-1~kali4
[/I]
Much would be appreciated if you guys can help me fix this issue as this has been the biggest pain the past couple days. 
Thanks in advance!

---

### Post by coffeecat on 2015-11-26
Kali, not Ubuntu.

*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Rob Sayer on 2015-11-26
According to this:

[http://docs.kali.org/introduction/what-is-kali-linux](http://docs.kali.org/introduction/what-is-kali-linux)

Kali isn't based on Ubuntu, it's Debian based.  While ubuntu is debian based, they are not the same.  And I wouldn't bother posting on the debian forums.  They don't do beginner hand holding.  Debian is made for more advanced users.  You could do a search on their forums for your adapter, but try:

[http://forums.kali.org/](http://forums.kali.org/)

Installing binary drivers from the manufacturer's site isn't such a good idea in linux.  They only work for the current kernel release generally.  And the troubler with binary drivers is that they're impossible to support in linux.

---

