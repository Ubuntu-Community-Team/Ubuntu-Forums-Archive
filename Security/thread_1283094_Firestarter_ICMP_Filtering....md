---
title: "Firestarter ICMP Filtering..."
date: 2009-10-05
forum: Security
---

### Post by dreamvirus on 2009-10-05
Hello!
I am new to firestarter & I really like Ubuntu...
So please tell me what filtering shouldi check & what are the consequences....i am torrent user so what are the pros & cons of each filtering option
Thank you.

[IMG]http://i36.tinypic.com/um29y.png[/IMG]

---

### Post by OrangeCrate on 2009-10-05
See here for guidance:

[http://firestarter.sourceforge.net/manual/wizard.php](http://firestarter.sourceforge.net/manual/wizard.php)

---

### Post by lovinglinux on 2009-10-05
Also check the security section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

It doesn't talk about ICMP but it has some information about firewalls and bittorrent.

BTW, I recommend removing Firestarter and installing gufw.

---

### Post by divyesh456 on 2009-10-08
The advanced options are mainly for the experienced user. 
  *Preferred packet rejection method*. Firestarter can either reject or drop connections that are not allowed by the security policy. When the firewall rejects a connection, it sends an error packet to the source telling it the connection was denied. Dropping a connecting on the other hand does nothing. In this case the source of the denied connection is non the wiser, in some cases it is even impossible to tell whether there is a machine at the firewall's IP at all. Since rejecting connections allows the remote party to map the network services as well as waste your bandwidth, we recommend you keep the default behavior of dropping connections silently. 
  *Block broadcast traffic*. This option blocks all network traffic with a destination or source address that marks it as either a global or local broadcast. 

_________________________________________________
[hair dressing games](http://www.y3.com/search-results/18354/hair-dressing-games)  [SMART LIPOSUCTION](http://www.laserlipoguide.com/)

---

