---
title: "Ubuntu Server Setup"
date: 2006-10-21
forum: Server Platforms
---

### Post by bdwetzel on 2006-10-21
Hi,
I have been trying to setup a web server on my amd64 machine.  At first I tried just using the LAMP server setup and I could access the the apache server by typing in the local IP address.  I have looked at several threads here and in other forums (including:[Howto Forge: Perfect Setup]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") and [Server Forum Thread: 281050]("http://www.ubuntuforums.org/showthread.php?t=281050")).  
Anyway I am struggling because I am brand new to linux and even newer to setting up servers:???: , but i really want to learn this.  I looked at the server forum for help but the problem is I am running this behind a switch not a router.  How do i get the assigned ip address on my server machine (not LAN ip address), and then how do i use it to configure my /etc/network/interfaces (eth0) to allow me to access that from the internet.   I went ahead and reinstalled the server without LAMP and then installed ssh.  I can connect to ssh remotely from this desktop (dapper ubuntu x86).  That is as far as I have gotten...i appreciate your help.

---

### Post by gustolove on 2006-10-21
if you can get to your computer through ssh from another location (not on the local network) but you are unable to get to the website that u want to host it may be because your ISP may block port 80. 

you will most likely need to change the port that the server (i assume apache) is listening on. 

/etc/apache2/ports.conf <--- edit that and change the port to something else... 8080 is a comon port to host on if 80 is blocked.

after you edit the port that the server listens on you will need to restart the apache server: ```
sudo /usr/sbin/apache2ctl restart
```

and then when u want to get to the server just go to the addresss

[http://yourip:port](http://yourip:port)

an example of this would be [http://66.102.7.104:80](http://66.102.7.104:80)

but with the numbers changed

--------------


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

^^that is a good tutorial

---

### Post by bdwetzel on 2006-10-21
Sorry, I should have made myself clear.  I can connect to ssh on a local network using the local ip (user@192.168.x.x) I have not made a connection over the internet...but i will check out that link...thanks for your help though.

---

