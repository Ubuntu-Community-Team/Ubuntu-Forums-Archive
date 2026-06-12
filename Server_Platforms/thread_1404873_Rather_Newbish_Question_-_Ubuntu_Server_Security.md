---
title: "Rather Newbish Question - Ubuntu Server Security"
date: 2010-02-11
forum: Server Platforms
---

### Post by grouchotron on 2010-02-11
e

---

### Post by Jive Turkey on 2010-02-12
Your question is pretty broad.  What you need to look at are the services that are running on the server, and then you should research how to secure those services individually.  By service, I really mean every network aware application on the computer.  The general consensus that I have seen among people more knowledgeable than me is that you should start with a strong password, and keep the system patched and up to date, then maybe tighten up the firewall.  There are numerous guides available for making apache more secure.  After monkeying around with the individual services to get them into the safest usable setting, you can go and learn how to harden things even further with apparmor or selinux.

As far as risks, its difficult to predict what an attacker might do if they got root access to your server.  Don't make decisions based on fear, make them based on how much you enjoy tinkering with stuff.  I've had servers in my home exposed to the internet for the last 2 years and never detected a hack.

---

### Post by yogesh.girikumar on 2010-02-12
Hi,[INDENT]      > but he wanted to know how secure it was, whether or not it is possible for someone to access or damage the pc or other computers on the network. How secure is the default installation? I'm just hosting an html page.   [/INDENT]Apache is a reasonably secure web server. A simple webpage without any scripts is very less likely to be compromised. Someone else using your installation to affect other client users will have to have access to your web server. So it is necessary for the server to be very secure in a serious business/mission critical installation. Though the server setup is secure, it is absolutely essential to ensure that the server is really secure and to take measures to increase the security and handle threats. 

> Any suggestion on how to make the server more secure?
Security is based on ( among other things )..


       1. Permissions on files / directories and other similar configurations of Apache.
2. Ports that the server is listening to.
3. CGI scripts and the security associated with them
4. Modules loaded in apache.
5. Script level security for PHP, Perl, Python etc..
6. Log analysis


       Some security tips in these links:


       [http://httpd.apache.org/docs/2.0/misc/security_tips.html](http://httpd.apache.org/docs/2.0/misc/security_tips.html)
[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)[INDENT]      > How realistic is the risk to a server hosting a website that likely, very few people will see? Are the install defaults secure enough that I can comfortably tell him not to worry about it?   [/INDENT]Since the default installation of Apache in Ubuntu is pretty simple and minimalistic, it's reasonably secure. But you might still want to carefully secure it further depending upon the nature of the website and the sensitivity of the data contained in it.
       
Hope this is helpful !

---

### Post by Porter200el on 2010-02-12
> **yogesh.girikumar said:**
> Hi,Apache is a reasonably secure web server. A simple webpage without any scripts is very less likely to be compromised. Someone else using your installation to affect other client users will have to have access to your web server. So it is necessary for the server to be very secure in a serious business/mission critical installation. Though the server setup is secure, it is absolutely essential to ensure that the server is really secure and to take measures to increase the security and handle threats. 

Security is based on ( among other things )..


       1. Permissions on files / directories and other similar configurations of Apache.
2. Ports that the server is listening to.
3. CGI scripts and the security associated with them
4. Modules loaded in apache.
5. Script level security for PHP, Perl, Python etc..
6. Log analysis


       Some security tips in these links:


       [http://httpd.apache.org/docs/2.0/misc/security_tips.html](http://httpd.apache.org/docs/2.0/misc/security_tips.html)
[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)Since the default installation of Apache in Ubuntu is pretty simple and minimalistic, it's reasonably secure. But you might still want to carefully secure it further depending upon the nature of the website and the sensitivity of the data contained in it.
       
Hope this is helpful !

That is a great reply, you have to love the ubuntu community, very well done yogesh!!

---

