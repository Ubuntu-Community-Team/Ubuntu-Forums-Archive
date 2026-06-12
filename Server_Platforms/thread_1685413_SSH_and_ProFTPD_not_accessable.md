---
title: "SSH and ProFTPD not accessable"
date: 2011-02-10
forum: Server Platforms
---

### Post by subhagato on 2011-02-10
I have set up a OpenSSH and a ProFTPd server along with Apache Web server on Ubuntu within a LAN. When the PC is within the same gateway as of my laptop (ie. 10.105.8.x) i am able to access SSH and FTP. But when it is moved to 10.104.1.x Apache HTTP is still accessible but SSH and FTP servers are not accessible any more. Please help.

---

### Post by cariboo on 2011-02-10
Why did you move your server ip address to a totally different netblock? Do you have iptables rules setup?

---

### Post by subhagato on 2011-02-11
No I have not set iptables. I dont know about it. Can you please help me configuring the SSH and FTP server accessible from 10.105.8.x

---

### Post by iiz on 2011-02-11
If you want to have 10.105.x.x lan setup, this is more for an airport wifi or a school or a large corporation, you can set your netmask to 255.255.0.0 on all machines. Setting the subnet to /16 will allow you to access it. When you do this though, assuming you have a lot of clients connected to the lan, you will have a greater chance for network collisions.

Have a look at [http://www.ralphb.net/IPSubnet/index.html](http://www.ralphb.net/IPSubnet/index.html) to get an idea of how subnetting and ip address work, I honestly don't know much on the subject.

Good luck

---

