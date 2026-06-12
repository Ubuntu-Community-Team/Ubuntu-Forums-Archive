---
title: "Internet connection sharing + iptables and mailserver"
date: 2009-12-30
forum: Server Platforms
---

### Post by asbjotve on 2009-12-30
I am running a server with:

DHCP3
LAMP
Openssh-server
Mailserver
and also running internet connection sharing from it.

My problem is that i follow the guide for setting up mailserver that I found here: [http://howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10](http://howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10)

Since I have internet connection sharing (called ICS by now), I also have to run iptables to get it.

I can send ac recceive mail as long as iptables are turned off, and that's the problem. I can´t turn it off because it´s needed by ICS. 

Any tip what i could do with that, to get it working to send and recceive mail with iptables turned on?


Last: Solved, added ACCEPT-rule before Masquerading-rule (I am using webmin)

---

### Post by iponeverything on 2009-12-30
> **asbjotve said:**
> I am running a server with:

DHCP3
LAMP
Openssh-server
Mailserver
and also running internet connection sharing from it.

My problem is that i follow the guide for setting up mailserver that I found here: [http://howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10](http://howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10)

Since I have internet connection sharing (called ICS by now), I also have to run iptables to get it.

I can send ac recceive mail as long as iptables are turned off, and that's the problem. I can´t turn it off because it´s needed by ICS. 

Any tip what i could do with that, to get it working to send and recceive mail with iptables turned on?

Just pass and don't masq the port 25 traffic.

---

### Post by asbjotve on 2009-12-30
Hmm, will I get ICS if I dont masquerade?

And this is the guide I followed for ICS [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

