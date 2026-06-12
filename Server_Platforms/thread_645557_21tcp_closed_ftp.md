---
title: "21/tcp closed ftp"
date: 2007-12-20
forum: Server Platforms
---

### Post by wilerk on 2007-12-20
Hi All,

I'm a web developer and really want to use FileZilla to connect to my server, but when I do and it comes to the LIST part I get the error: 425 Can't open data connection. So I looked online and it says ports might be blocking my connection. So I used NMAP to scan my open ports on 127.0.0.1 and I get 21/tcp closed ftp. 

I don't have any firewall software running so how do I get this to open? Or is this some other problem that has nothing to do with the port?

The network is wired using DHCP in the hosts I have the following:

127.0.0.1 localhost
127.0.0.1 LT-TFM
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00:0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Don't know if that's useful, oh and I'm running 7.10, oh and I'm a newbie.

Regards,

Xander

---

### Post by wilerk on 2007-12-20
Anybody?

---

### Post by lmahoney on 2007-12-20
Are you running an FTP server on port 21 or do you have a super server like inetd running to pass off the request to an FTP server? Maybe a little more info can help.

---

### Post by wilerk on 2007-12-21
Hi lmahoney,

Nope I'm just trying to connect from my machine to an FTP server.

And no matter what server I try I get the same error message. I use my ubuntu as a workstation, I'm running Windows XP virtually in VirtualBox and even in there I have the same problem. 

EDIT: I feel a little embarrassed now, I changed the transfer mode to active and I get in.

Sorry to have wasted readers time!

Thanks,

Xander

---

