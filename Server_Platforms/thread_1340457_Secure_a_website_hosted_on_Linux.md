---
title: "Secure a website hosted on Linux ???"
date: 2009-11-28
forum: Server Platforms
---

### Post by Archipur on 2009-11-28
Hi,
 
I am a beginner in Linux and I would like to use Linux for hosting my website but I have no idea how to secure it.
 
Have you an idea how to secure a ubuntu web server?
Is there any Firewall/Antivirus software that works on Ubuntu?
What is the best method to make a Ubuntu web server as secure as possible?
 
Please help,
thanks

---

### Post by Cuco3 on 2009-11-28
Haven't tried it before, but I imagine you're gonna want to run a JeOS virtual appliance (it's a virtualized computer that runs the absolutely necessary files/protocols for say, a web server, for example).

After that, you'll want to properly configure your firewall, and remove any unnecessary services and programs that are running. You'll probably also want to configure AppArmor.

Google and reading the instructions will be your friends here. Also, expect to get your hands dirty and learn new technologies.

Please bookmark this thread and report back on any progress you've made and post any useful links you may have found along the way.

Good luck.

---

### Post by whoop on 2009-11-28
Lots of useful information:
[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

### Post by BkkBonanza on 2009-11-29
There's a sticky up above on security and server admin. 
Start with that.

First, get your ssh admin access secure by,
1. changing port (prevents most port scans from finding you)
2. disabling root login (stops brute force on known root user id)
3. preferably using key authentication (defies brute force attacks)

Next, remove or disable any services not really used. 
Read up on "server hardening" (google).

If you do that and only have a web server running on port 80 (& 443) then you probably don't need a firewall (especially if already behind a router).

Then concentrate on ensuring your web code and applications are secure. That may mean checking you have most recent updates and/or auditing your own code to improve resistance to vulnerabilities. Most web server vulnerabilities nowadays are related to unsafe programming practices.

---

### Post by Archipur on 2009-11-29
[COLOR=black][FONT=Verdana]Thanks for all the replies.

I have heard that most of the web servers can be hacked very easily. How can I make my web server really secure and strong and how can I prevent that professional hacker&#8217;s compromise it in very sophisticated ways it or steal sensitive information?[/FONT][/COLOR]

---

### Post by BkkBonanza on 2009-11-29
Read. and Learn. 
Web servers aren't a problem but many web applications have vulnerabilities.
There is no quick way to be 100% safe.
You need to do the homework.

---

### Post by Archipur on 2009-11-29
> **whoop said:**
> Lots of useful information:
[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)
 
I'm a beginner with Linux and I'm a bit confused:
 
[COLOR=black][FONT=Verdana]The link provided is for the Debian OS. Isn’t this another distribution of Linux?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]What is the difference between a Debian and an Ubuntu web server? Is it the same?[/FONT][/COLOR]

---

### Post by BkkBonanza on 2009-11-29
Ubuntu is based on Debian so much of it is the same or similar.
There are two main variants in Linux - Debian and Red Hat. 
Most of what you read about one distribution can be applied to others but sometimes the specific commands may be different. A lot of the difference in the two main variants is in the boot/init system and the package managers - install commands. The security and server hardening should be pretty much the same for most Linuxs.

---

### Post by Archipur on 2009-11-30
Thanks. I will follow the instruction described on [[COLOR=#444444]http://www.debian.org/doc/manuals/se...-debian-howto/[/COLOR]]("http://www.debian.org/doc/manuals/securing-debian-howto/") and check if my web applications have vulnerabilities.
 
 
Where can I read about the latest threats/vulnerabilities that have been detected? Is there a website that gives the latest security information for Linux web servers?
 
So I can check if my server is vulnerable to a new hack technique and secure the server as soon as a vulnerabilities is detected by other persons.

---

### Post by BkkBonanza on 2009-11-30
Web server software can be broken into several components. In general, you would use a program like Apache to serve a site, and a backend database like mysql for data, and perhaps PHP for the application code - as a common example. Software like Apache and mysql and php is regularly updated for any known security vulnerabilities so you should keep these packages updated to prevent against known threats. 

Your bigger problem is with the web application that you would either create or run premade, written in PHP, Perl, or other languages. While some of these are well looked after and updated regularly a lot of this code often is not. And code you may write yourself, unless you audit it for security vulnerabilities is very much unknown. 

Probably the biggest threat in web applications is hackers finding programming errors that would allow them to gain information and access, allow them to use social engineering techniques to gain user details or other information. This area requires skill and experience to obtain any real level of security and often even well established applications are found to have holes. In this area there is just no simple one-fix solution. How you manage it depends on what applications you run and the details of your site, what data you maintain and the consequences when hacked.

For example, you would take different levels of pre-caution and auditing between a blog site with no real user details or commerce transactions compared to a site maintaining a user base with frequent credit card transactions and requiring SSL connections. Part of understanding security is determining how much is required and what consequences would occur if breached.

Given that you're just starting out I think this is something you will have to expect to grow into. Really, google is probably your best tool in increasing your knowledge here - combined with some thoughtful search terms.

---

### Post by Vegan on 2009-11-30
My site is secure, however spammers still manage to get into my forum occasionally. The spammers want to be seen, malware does not.

I have a piece on my forum for setting up Apache and how to make it work.

Look on the LAMP section.

---

### Post by windependence on 2009-11-30
As a suggestion, I would advise running a separate firewall in front of your web server(s). Many people don't realize, a simple DDOS attack can bring down your server if the only line of defense is on the actual server. In fact, I don't run ANY firewalls on my servers. I run a pfsense box in front of my server so that if there IS a large flood attack, the cpu on your server is not so overwhelmed it wiggs out just from the load. Running a DMZ is even better to separate your webservers from your local LAN and the web itself. Refraining from running a GUI is also a good security practice. You'll see that Ubuntu did not put a GUI in the server version precisely because it is a security risk.

-Tim

---

### Post by R.Bucky on 2009-11-30
*2 Windependence - I inherited a soerkis box with pfsense at work. Any traffic has to get through a primary router then pfsense. I have since turned off firewalls on Ubuntu Server. 

Also, 1 thing not mentioned for security is fail2ban. I started using it around 6 months ago to block unwanted ssh attempts couple with a non-standard port on ssh. I have not had one attempt on ssh since the port change, but occasionally it has to stop a mail server attempt here and there. Give it a shot.

---

