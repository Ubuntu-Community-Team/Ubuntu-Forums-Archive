---
title: "How to create websites, FTP-accounts and MySQL databases?"
date: 2012-06-01
forum: Server Platforms
---

### Post by kramer65 on 2012-06-01
Hello,

I am messing around with Ubuntu server installed in a virtualbox instance so that I can practice with setting things up. I first followed [this guide]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3") which leaves me with a Server installation including the [ISPConfig control panel]("http://www.ispconfig.org/").

When I go to 192.168.1.67 in my browser (in the guest-OS) I get to see Apache's "*It works!*". I can edit this file in /var/www, so everything seems to work fine. I now wanted to connect to the server using FTP. So I went into the ISPConfig panel, created a site (test.com) and attached an FTP-account. I then opened Filezilla and filled in the username, password, and the ip-address (192.168.1.67). Everything seems to go fine, until it checks the password:
> Commando:	USER kramer65
Antwoord:	331 User kramer65 OK. Password required
Commando:	PASS *********
Antwoord:	530 Login authentication failed

I then removed the FTP-account and tried again, and it gives the same response including "*User kramer65 OK.*". 

At this point I am kind of confused and have some questions I wonder about:
[LIST=1]
[*][COLOR="Silver"]Where would the files of this created website (test.com) be located? I can't find anything under /var/www[/COLOR][EDIT2] I just found the folder /var/www/test.com/ . When I go to 192.168.1.67/test.com however, I get a 403 Forbidden message. How can I access the files of my newly created site?
[*]How can I create an FTP-account and connect to it using Filezilla?
[*][COLOR="Silver"]How can I create MySQL databases and users (like I used to do in Cpanel/DirectAdmin)?[/COLOR] [EDIT] Nevermind. Found this under Websites >> Database.. #-o
[/LIST]

As you can see I am quite a noob on the server, but I would love to learn more! Anybody who can help me out?

---

### Post by clay7 on 2012-06-01
I'm fairly inexperienced with this stuff too, but I had a problem with FTP as well that was solved. Instead of using FTP, which is not secure, use SFTP. You can get a free program for this at  [http://winscp.net](http://winscp.net). I've always been able to connect using this immediately after my server was set up by the hosting provider. I think the reason that you can use SFTP on a fresh server without any server configuration (as opposed to FTP) is because it communicates on the same port as SSH (22).

I realize that you're using this over a home network and that the security risk is low, but this should fix it for you.

Also, to check that you have the correct IP address to your local machine, SSH into it and type "ifconfig" (without quotes). It will tell you the machine's IP, gateway, etc. I use putty for SSH, which is also free.

Hope that helps!

---

