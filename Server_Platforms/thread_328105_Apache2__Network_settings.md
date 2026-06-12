---
title: "Apache2 / Network settings"
date: 2006-12-30
forum: Server Platforms
---

### Post by Bunro on 2006-12-30
Help needed with Apache2/ network settings.
 

 I had some problems with my network connection, this is solved now but I had to change my network settings in:
  /etc/hosts Listing:
 127.0.0.1 localhost
 

 # The following lines are desirable for IPv6 capable hosts
 ::1 ip6-localhost ip6-loopback
 fe00::0 ip6-localnet
 ff00::0 ip6-mcastprefix
 ff02::1 ip6-allnodes
 ff02::2 ip6-allrouters
 ff02::3 ip6-allhosts
  127.0.1.1 notebook.THUIS
 

 In my installation I made use of LocalhostSubdomain
 [https://help.ubuntu.com/community/LocalhostSubdomain](https://help.ubuntu.com/community/LocalhostSubdomain)
 

 The situation was before my network problems:
 [http://notebook/](http://notebook/)
 Where my local site is for development.
 [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
 Here was PHPMyAdmin was situated
 

 I think the problem is with in the /etc/hosts but I am not sure. At this stage I can not get to: [http://localhost]("http://localhost/") and [http://notebook]("http://notebook/") Apache2 seems to running.
 Hopefully there is someone that can help me getting things working again. This would be great!!!
 

 Best regards, Robert

---

### Post by Bunro on 2007-01-01
I solved the problem. Hopefully it can help some one else.
 

 I had to adapt the following file like this:
 sudo gedit /etc/network/interfaces
 auto lo
 iface lo inet loopback
 

 auto eth0
 iface eth0 inet dhcp
 

 auto eth1
 iface eth1 inet dhcp
 

 auto eth2
 iface eth2 inet dhcp
 

 auto ath0
 iface ath0 inet dhcp
 

 auto wlan0
 iface wlan0 inet dhcp
 

 On a post I read that I had to command out the first two line, but this was finally the problem by setting this back my local web server is working again. Also because of this sudo was not working correctly any more.
 

 Best regards, Robert

---

