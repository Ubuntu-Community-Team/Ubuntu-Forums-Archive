---
title: "new at servers -- can't find the right how-to"
date: 2005-12-21
forum: Server Platforms
---

### Post by greenwom on 2005-12-21
So I want to start a small homebased website 

I installed apache2, php, mysql (I have searched and read a bit) but I'm losted.

I know I need to register a domain, setup a static IP (or a redirect software) and then setup the server.  I've never messed with this backend stuff and I'm lost.  Most of the How-to's I've found assume that I know a few things.  

I don't :) 

I need a start to finish how to (and some additional reading material)

so if someone can point me to the how-to or documentation I need I'd be a happy troll......:mrgreen: :mrgreen: 

I've tried the wiki, the apache website, and the ulmighty google but no luck.
(or I'm looking in the wrong place.

---

### Post by greenwom on 2005-12-22
To clarify I want to set up http for a website for content and have the ability to have a FTP server.

---

### Post by harisund on 2005-12-22
Try reading this if you want.. it is a pretty neat and comprehensive guide . 
[http://aboutdebian.com/](http://aboutdebian.com/)
Go to the servers section.. but you can pretty much read all of them since it is quite an interesting read

---

### Post by mindwerks on 2005-12-22
Yeah, I'm in the same boat greenwom. 

I new to the linux world and am trying to do the same thing. The problem I'm having is that the How-To instructions do not ever seem to match the file system on my computer. 

An example would be installing Mysql from source. After you get it made and installed you have to do some post setup prep like setting it up to start at boot and such. The only problem is that where they tell you to go to do these steps doesn't exist and doesn't seem to be anywhere I could find. 

So I'm like... hmmm.... well crap. LOL

---

### Post by greenwom on 2005-12-22
Well I just read through 
[http://www.aboutdebian.com/internet.htm](http://www.aboutdebian.com/internet.htm)

This looks to be a great guide.  I'll make the promise that if I get this up I'll do my best to post a how-to for noobs.

This is what I've got so far.  (for a home server to host a 'fun' site)
buy a domain (I'm going to use bigdaddy.com)
apt-get apache2
gedit /etc/apache/httpd.conf and put the info needed in the above guide.
install a Dynamic DNS package (don't know which one yet) (I've read you have to set this up on the DNS end also)
Set up the router to work with the Dynamic-DNS (updates your changing IP)

that's the basics (I think ** I know there's more), I'm reading into the different packages that provide the functions I need (DNS and the like).  So any suggestions -- I'm all ears.

---

### Post by ewtesterman@cox.net on 2005-12-23
If you have the additional hardware (I found a P 1 and through some ram and a hard drive in it) you can download and install SME Server and be done with the nasty work in about 1 hour. I like Ubuntu and use it for desktops, but SME makes a great Web Server, Gateway, Email Server, VPN, FTP, ect..... I am also a newbie yet I had the server fully installed fully configured and up in less than two hours. I have read in the Wiki that Ubunut is tring to do a simular type of quick install, but until then. Another great feature of the SME is that you administer from a graphical web page. 

P.S. You may want to see if your ISP is blocking port 80 (most of them do). If this is the case you will have to configure Apache to listen on a different port I use 8080, if this is true then you will have to add :8080 to the end of your ip address when trying to access your server from the net so your raw address would be something like 68.97.216.228:8080 I hope this helps.

---

### Post by LoclynGrey on 2005-12-23
I've set up a few web servers in linux. I used to do it the easy way using [xampp]("http://www.apachefriends.org/en/xampp-linux.html"). 
Then the other day I was reading on this forum about setting up MythTV and found the following commands, which were very helpful. (and in fact made it even easier)

In terminal:

sudo apt-get install apache2

sudo apt-get install mysql-server

sudo apt-get install phpmyadmin

>
(or have a read for more detail, [http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html))

Next steps:
1. if your webserver is on a pc inside your network, you will have to open up a port on your router to direct to that pcs ip address. (Dlink call this a virtual server setting)
2. you will need a static IP, or suitable service to update the redirection for your ever changing dynamic ip.
3. Domain name is finally needed. (like [www.[whatever]](www.[whatever]).[com,org etc etc)

---

### Post by exkalibur on 2005-12-23
Actually, the apache2.conf is the configuration file. Not the http.conf.......Was true in older versions but changed for version 2.

Regards

---

### Post by kpd on 2005-12-23
greenwom--
i've set up an apache2/php/mysql server using ubuntu recently, and i'm happy to help if you have specific questions. (though i won't be much help with ISP/domain name questions)

i used this:
[http://ubuntuforums.org/archive/index.php/t-17875.html](http://ubuntuforums.org/archive/index.php/t-17875.html)

this might also be helpful, though i haven't used it:
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)
(detailed, more custom configuration)

---

### Post by greenwom on 2005-12-24
Thanks all for the posts so far.... 
just so you know, I've got a P3, 160Mb of ram with breezy just for this server.

KDP, I'll look into these threads.

I purchased a domain from godaddy.com and created the dyndns.org account but I don't know what's next on that end.  If I understand it right I have to point the URL from godaddy.com to the dynamic dns site to adjust for the non-static IP address.

At this point I (think i) have to open a port on the router and then point/ tie the server to the router and then that should talk to the URL.  I think I have the concept down but we'll see.......

---

### Post by exkalibur on 2005-12-24
Try this link.Lot of good info....

[http://www.dslwebserver.com/main/fr_index.html?/main/main.html]("http://www.dslwebserver.com/main/fr_index.html?/main/main.html")

Regards

---

