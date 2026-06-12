---
title: "ftp can not accessed by other win machine"
date: 2010-03-08
forum: Server Platforms
---

### Post by apachemaven on 2010-03-08
Hi:
I have installed ubuntu9.10-desktop-i386,then I install the vsftpd to transfer files with my another computer which own a win xp os.

And the ip of the win computer is "192.168.2.10",this address is fixed.
the ip of the Ubuntu compuer is "192.168.11.1",the address is dynamic,since I use the wireless network.


When I startup the ftp server in my ubuntu, I can not access it from my win computer,but I can access it in my ubuntu .

However when I startup the tomcat in my win machine, I can access it in my ubuntu using"http://192.168.2.10:8080/files"

So , what is the problem?

---

### Post by kiranmurari on 2010-03-08
Hi,

 As incoming connections to the ubuntu desktop is not successful, this looks like a firewall issue. 
Can you check if firewall is enabled on ubuntu desktop?
```
$ sudo ufw status
```If the status is active, you can disable the firewall with the following command.
```
$ sudo ufw disable
```Hope this helps.

---

### Post by apachemaven on 2010-04-19
Thanks, I will have a try.

---

