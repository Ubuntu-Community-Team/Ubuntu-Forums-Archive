---
title: "just installed apache,mysql on localhost, am i in danger?"
date: 2011-08-03
forum: Security
---

### Post by loolooyyyy on 2011-08-03
i installed apache and mysql and phpmyadmin to test my website
i dont want to use softwares like xampp, directly using apache is way more easy
and since wordpress asks for ftp to upgrade plugins, i installed vsftpd, they all use one-lettered simple password, am i in danger from hackers? since i'm connected to internet
can they do anything to my computer?
do any of these things i installed(such as vsftpd) open a particular port and put the OS in danger?
tanx

---

### Post by cariboo on 2011-08-03
About passwords:

[IMG]http://i.imgur.com/1UAyll.jpg[/IMG]

---

### Post by MechaMechanism on 2011-08-03
> **cariboo907 said:**
> About passwords:

[IMG]http://i.imgur.com/1UAyll.jpg[/IMG]
LOL!!!:lolflag:

---

### Post by loolooyyyy on 2011-08-03
tanx for the reply
but do i need the passwords here? for apache/sql/phpmyadmin?
are they accessible from another computer while i'm connected to the internet?

---

### Post by cariboo on 2011-08-03
Good strong passwords are always a good idea. I may have misunderstood, but you said your vsftpd password was a single character. Ftp is inherently insecure, so the better the password, the safer your are. Don't succumb to laziness if you are worried about your data.

If all you are doing, is testing your web site, and not actually going live, I'd suggest you don't allow access  from the internet, and only allow access from your internal network.

---

### Post by loolooyyyy on 2011-08-04
> **cariboo907 said:**
> 

If all you are doing, is testing your web site, and not actually going live, I'd suggest you don't allow access  from the internet, and only allow access from your internal network.

my account does have a good password, but apache since it's just serving me i dont think it needs one?
and again it's the apache i'm worried about, how do i make it unaccessible from internet?
actually what things are accessible in ubuntu?

---

### Post by loolooyyyy on 2011-08-04
> **salemeni said:**
> Hi
You can use Nmap to scan you station (or server ) to scan ports.
#nmap -sS @IP
You can download this software from nmap.org 
Thanks

what ports should be closed and how do i close them?
my laptop is not meant to be a server, just me surfing net (and playing around with apache/joomla/wordpress to see how they work)

---

### Post by loolooyyyy on 2011-08-04
> **cariboo907 said:**
> Good strong passwords are always a good idea. I may have misunderstood, but you said your vsftpd password was a single character. Ftp is inherently insecure, so the better the password, the safer your are. Don't succumb to laziness if you are worried about your data.


sorry for too many questions: i installed vsftpd, now i'm planning to remove it, i dont think i need ftp on my machine to access itself (at all), should i totally disable ftp? how do i do it? and does that make any problems? for instance if an application does use it internally, i dont know, maybe firefox? nautilus?
tanx again

---

### Post by cariboo on 2011-08-04
Is your computer directly connected to the internet, or are you connecting through a router? If you connect through a router, you have nothing to worry about if you haven't forwarded any ports to the router.

Nmap is a good tool for checking what ports are open, but salemeni's advice is just plain wrong. Nmap is available in the repositories, you should stick with installing packages from the repositories as much as possible. To get proper results from nmap, it should be run from another computer on your home network, otherwise it will show ports that are open and accessible, but only by the system nmap was run on.

---

### Post by loolooyyyy on 2011-08-05
> **cariboo907 said:**
> Is your computer directly connected to the internet, or are you connecting through a router? If you connect through a router, you have nothing to worry about if you haven't forwarded any ports to the router.

Nmap is a good tool for checking what ports are open, but salemeni's advice is just plain wrong. Nmap is available in the repositories, you should stick with installing packages from the repositories as much as possible. To get proper results from nmap, it should be run from another computer on your home network, otherwise it will show ports that are open and accessible, but only by the system nmap was run on.

i have a router, and no port forwarding, so i guess i'm fine!
tanx for your time

---

