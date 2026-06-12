---
title: "problems w/ proxychains"
date: 2010-05-27
forum: Security
---

### Post by gost on 2010-05-27
OK, I have Tor/Privoxy installed correctly and running. I then installed proxychains from the package manager. When I try to execute proxychains nmap x.x.x.x, I get error messages stating that proxychains cannot connect to x.x.x.x:XXXX. At the end before I get a cursor, it says 'need more proxies' So I looked for free proxies, added a couple to the /etc/proxychains.conf and it made no difference. Any thoughts on what I am doing wrong/ignorant of?

-g

---

### Post by AcidMoon on 2010-05-29
I'm not an expert but proxychains works for me when I have tor and privoxy installed. The guide I use to install tor is here: [https://help.ubuntu.com/community/To...w&redirect=TOR]("https://help.ubuntu.com/community/Tor?action=show&redirect=TOR")
An example command I use is: proxychains nmap -sT -PN -n -sV -p21,25,80 IPADDRESS
Check this blog which helped me: [http://www.commondork.com/2009/06/26/tunneling-nmap-through-tor/](http://www.commondork.com/2009/06/26/tunneling-nmap-through-tor/)
Hope this helps :)

---

### Post by johnkills on 2010-05-29
I am not sure but I think the configuration file of proxychains right at the end it says something like

socks 127.0.0.1 9050  

That "9050" is the port Tor is running but for me it was a different port and when I changed that proxychains started working fine.  So you have to find what is the right port. If it it still wont work, tell me and I will check my config file. :)

Also make sure that "socks 127.0.xxxx" is not commented with #, sometimes it is.

---

### Post by AcidMoon on 2010-05-29
+1
At the end of the gksu gedit /etc/proxychains.conf I have "socks4     127.0.0.1 9050" 
Also as per the guide I referenced about tor, It instructs you to put "forward-socks4a / localhost:9050 ." at the end of the gksu gedit /etc/privoxy/config.

---

