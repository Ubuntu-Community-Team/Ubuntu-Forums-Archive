---
title: "Web server help"
date: 2011-02-28
forum: Server Platforms
---

### Post by paulc8481 on 2011-02-28
I am trying to build a web server but i am running into a couple of small problems.  I have installed ubuntu 10.4 server and have also installed "Lamp' server applications successfully. I also have successfully got my "It Works" test page to come up on the screen on my other computer.  The only instructions I have are for Ubuntu 8.4 server so this may be part of the problems.
  My hurdle is,  that when it tells me to go into the:
     sudo nano /etc/apache2/apache2.conf file,  to change "ServerTokens to prod", this is nowhere to be found.  Also the same for change "ServerSignature to Off" and "Expose_php to Off" in the php.ini file is not there.  
 
   Please remember, I am new to this stuff so be gentle.  Although I am running into these minor problems I am enjoying learning unix command line and do look forward to hosting my own webpages on my own system.
 
Thanks paul.

---

### Post by volkswagner on 2011-02-28
I can confirm those differences exist between 8.04 and 10.04.  You're correct.  I'm sorry that I can't comment on validity of such, but at least give you a bump to someone more capable to offer advice.

One bit of advice I can give... always create a backup of any configuration file prior to editing it.

like

```
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak 
```

Or use any added extension of your preference.

---

### Post by paulc8481 on 2011-03-02
Thank you for responding to my message.  I think I am going to try another direction.  I am now using Desktop 10.04 and have installed LAMP with all upgrades.  but still seem to be having the same problem.  A couple of minor questions that you may be able to answer.  If I am port forwarding ports 80 and 22 through my router, do i need a firewall on my system?  and will that token and ServerSignature issue now be a problem?
 
Thanks Paul

---

### Post by wongo888 on 2011-03-03
I recall reading somewhere that your edits should go into *httpd.conf* and not *apache.conf* for the reason that upgrades may wipe out *apache.conf* but they won't touch the other. You might want to check on that to confirm it is the case.

**expose_php** stops php from reporting its version number during requests. You can disable it (or add it if it is missing) in your php.ini file:

[http://phpsec.org/projects/phpsecinfo/tests/expose_php.html](http://phpsec.org/projects/phpsecinfo/tests/expose_php.html)

In Ubuntu 10.04LTS the php.ini file can be found at

```
$ sudo vim /etc/php5/apache2/php.ini
```

**ServerTokens** and **ServerSignature** similarly stops Apache from reporting its version. Change it here (line 27 and 39):

```
$ sudo vim /etc/apache2/conf.d/security
```

Some info [http://articles.slicehost.com/2010/5/19/apache-configuration-on-ubuntu-part-2](http://articles.slicehost.com/2010/5/19/apache-configuration-on-ubuntu-part-2)

Remember to restart apache

```
$ sudo apache2ctl -k restart
```

When these changes are implemented, your HTTP headers look like this:

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Encoding: gzip
Content-Length: 9492
Date: Thu, 03 Mar 2011 05:01:31 GMT
Vary: Accept-Encoding
Server: Apache
Keep-Alive: timeout=5
Connection: Keep-Alive
Proxy-Connection: Keep-Alive

```

Otherwise it looks something like this:

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Encoding: gzip
Content-Length: 9769
Server: Apache/2.2.14 (Ubuntu)
X-Powered-By: PHP/5.3.2-1ubuntu4.7
Date: Thu, 03 Mar 2011 05:07:41 GMT
Vary: Accept-Encoding
Keep-Alive: timeout=5
Connection: Keep-Alive
Proxy-Connection: Keep-Alive


```

The idea is to keep the bad guys guessing what you are running.

---

### Post by paulc8481 on 2011-03-03
Thanks Wongo for your response.  I will give it a try as soon as I get home tonight.  Could you also give me a bit of info on Firewalling my server?  I am having a bit of trouble loading Shorewall or I think I may have it installed but cant get to the file to activate ports 80 and 22 only.  If I am going to use my router's firewall with port forwarding do I need to worry about Whorewall?
 
Thanks....Paul

---

### Post by bsntech on 2011-03-03
Hi Paul -

On your router, you will need to setup the port forwarding of ports 80 and 22 to the internal IP of the server to get them to connect.

If you are behind a router, this really is enough - because the router acts as your firewall - and is only allowing ports 80 and 22 through.

However, you can certainly setup a firewall called "IPTABLES" - which is built into Ubuntu by default.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/")

---

### Post by wongo888 on 2011-03-03
Bsntech is correct.

System security is often a tradeoff between how valuable the system is and how much time and effort you are willing to put into securing it. If this is not a mission critical system (and how many of those are run behind consumer-grade Linksys routers) then you can get away with keeping your system up to date and patched.

I have seen more data loss and service disruption caused by inadequate backup/restore policy, by using weak passwords and by insecure application programming than I have to seen caused by daemon hacks due to open ports.

---

### Post by wojox on 2011-03-03
I would port forward 80 (http) and 443 (https) on your router. Do you really need a reason to enable 22 (ssh) externally? You can still connect to 22 inside your lan. If you do open the port on the router look into configuring the settings properly.

Have it listen on a different port, turn off root login, set up Public/Private Key Authentication...

---

### Post by paulc8481 on 2011-03-04
Boy, All you guys are the best!  Thanks for all the info, being a beginner at this stuff I need it.  No my system is not mission critical.  I have taken some web design courses, PhP, and Java, but the only thing left I think is to be able to build my own Web server to host some of my own pages and prodjects for other courses I may take.  One other question,  How do I get a Domain name for my system?  I'll get back with all of you regarding the status of my server.  Hopefully I'll be up and running this weekend, but if I run into any more trouble I hope you all can put up with me for a bit longer.
 
Thanks for all your help
 
Paul

---

