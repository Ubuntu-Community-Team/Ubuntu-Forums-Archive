---
title: "Ftp server"
date: 2014-05-27
forum: Server Platforms
---

### Post by Ultimax on 2014-05-27
Hi everyone I just installed Ubuntu 14.04 LTS and i want to create my own FTP Server which i can access from anywhere i go. I did install vsftpd but i dont know how to cofigure it and to configure it I know that you have to go to etc and than something to find the vsftpd.conf file. But when i click on it and edit i cant save it because its read only and it says you have to have the administrator rights but i don't know how to do that. Please don't tell me I shouldnt be doing this, i want to learn how to make my own server and run it efficiently. I have spent many hours researching but nothing helps. Its not detailed enough for me to run the server properly. I dont want to use Filezilla because i would have to install it on the server computer and the client computer. If FTP is hard i also want to create a web server and have my own domain and host it from my desktop computer. If someone can please give me a detailed instructions on how to do it I would really appreciate it. Thankss.

---

### Post by slickymaster on 2014-05-27
Hi Ultimax, welcome to the forums.

I'm moving your thread to the **Server Platforms** sub-forum, a more adequate place for it.

---

### Post by jonobr on 2014-05-27
Hello

I would recommend if your going to get deep into server installations and working with programs, you pick yourself a good text editor like [ Vi]("http://en.wikipedia.org/wiki/Vi") or [vim]("http://en.wikipedia.org/wiki/Vim_%28text_editor%29")
Reason being is that everything in ubuntu or *nix system is a file, and manipulating those files is key to getting good at ubuntu.

For your specific config file your trying to monitor, you dont have permissions to edit it.
When your used to vi you can open a terminal window and su vi vsftd.conf and modify accordingly.

---

### Post by Ultimax on 2014-05-28
Thanks and I will get that program, but I still need complete detailed instructions on how to install the FTP OR WEB Server knowing that I'm only a beginner and want to learn how to start my own server.

---

### Post by pqwoerituytrueiwoq on 2014-05-28
install [openssh-server](apt:openssh-server) then you can login using fireftp in firefox (or winscp on windows), just change the protocol dropdown to sftp
as for a domain look at a ddns service (i found duckdns to be good for me)
just give your normal user access to where you have your public html/php content

---

### Post by Ultimax on 2014-05-29
Thanks so I wont have to go through port forwarding steps and this will be available anywhere I go?

---

### Post by pqwoerituytrueiwoq on 2014-05-30
ANY service requires port forwarding unless you don't use a router
it is a basic feature, just log into your router and forward port #21 to your server

---

### Post by brent1975 on 2014-05-30
Hello Ultimax!! sounds like you are in need of some information. I have guides for everything you are trying to accomplish. 

How to install a web server This includes Apache, MySql, and PHP:  [Click Here]("http://forums.kc-linux.com/index.php/topic/40-installing-apache-php5-mysql-and-phpmyadmin/")

How to organize your sites with sub-domains: [Click Here]("http://forums.kc-linux.com/index.php/topic/37-creating-subdomains-in-apache/")

How to setup an FTP Server: [Click Here]("http://forums.kc-linux.com/index.php/topic/30-setting-up-a-ftp-server-with-vsftpd/")

Once you get tired of FTP (which you will) I would suggest installing Samba + openvpn to access your resources from anywhere

How to install Samba: [Click Here]("http://forums.kc-linux.com/index.php/topic/28-samba-file-server/")

How to install OpenVpn: [Click Here]("https://www.digitalocean.com/community/articles/how-to-install-openvpn-access-server-on-ubuntu-12-04") (retrieved from google search)

How to install a firewall: [Click Here]("http://forums.kc-linux.com/index.php/topic/18-iptables/") (Follow carefully)

all these tutorials/guides are done from command line (in the terminal) There are many different text editors out there. I personally use nano which comes default on the server. I try and not install things if I don't have to. It's quit simple to use and gets the job done. I am sure google will have info on nano.

Hope this helps getting you in the right direction.

---

### Post by Ultimax on 2014-05-30
Thank you sooo much guys! I really appreciate it! I will mark this thread as solved as soon as I try it out. If I have any problems I will notify you guys. Thanks!

---

