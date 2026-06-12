---
title: "Ultimate PHP Developer desktop setup (brainstorm)"
date: 2008-04-11
forum: The Cafe
---

### Post by SymenTimmermans on 2008-04-11
Hi guys, 

I am a full-time php developer working with several php frameworks. I have a live production server for my clients, and when i'm developing i'm mostly working on subdomains of my company domain.

I'm interested in setting up a desktop development system running a LAMP stack on steroids.

**The functions this desktop should perform are: **
- Run a webserver (apache)
- Run a database server (mysql)
- Run scripting languages (php - maybe php4 AND php5)
- Run some kind of dns server (makes it easier to have multiple projects on the same server)
- have some kind of server control panel for easily adding new domains, subdomains, databases, etc.
- Run a few nice IDE's (phpeclipse, aptana, jedit)
- Graphical software for web design
- various browsers for testing purpopses
- be able to run various php frameworks
- run some kind of version control software
- some kind of mechanism for easily deploying projects to a live server.
- your suggestion?

Software packages i'm looking at for these functions:

**Webserver**

Apache, pretty much factory standard 

**Database server**

Mysql, again following standard

**Scripting**

PHP 4 and PHP 5 and the ability to be able to choose which version runs on which domain

**DNS server**

I'm not even sure if a dns server is needed for what i want to do, i'm looking for people who can elaborate on this

**Server control panel**

Something like WHM, HELM or CPanel ( fellow developers should know what i'm talking about)
Basically I want domain management software. I'm not sure what's on the market...

**IDE's**

I'm very fond of eclipse-based editors like Aptana and phpEclipse. I'm also a fan of Zend Studio, but being a proprietary app, i think i shouldn't discuss zend right now. 
jEdit also looks promising.

**Graphical software**

Several programs are available, probably better leaving it up to the developer himself, because most graphical software is a matter of taste. I, for instance, can never understand why people recommend Gimp as an alternative to Photoshop. If you understand the power of Photoshop, Gimp is a toy. </rant>

**Browsers**

Firefox, Epiphany, Konqueror
non-native: IE4Linux, Safari through PlayOnLinux
Also a Windows VM is recommended.

**PHP Frameworks**

Like graphical software, a matter of taste and habit. I use CakePHP, QCodo, have used Prado and CodeIgniter, and am right now looking at symfony. 
The reason i'm mentioning multiple frameworks, is because I want to be able to install multiple frameworks and they shouldn't interfere with eachother.

**Version control software**

CVS or SVN, whavever suits you, but it should work and integrate nicely with apache and the IDE's.

**Live server deployment**

I'm not sure if these kind of programs exist. Of course it would be relatively easy to implement this functionality in bash scripts. 

**Your suggestion**

What do you think should be included in this ultimate setup, ultimately?

---

### Post by SymenTimmermans on 2008-04-11
The end result of this brainstorm should be to have a comprehensive guide to setting up such a system I am describing... Unless I'm the only one interested of course.

---

### Post by tcpip4lyfe on 2008-04-11
I don't know a whole lot about the development side but I'm a network admin and as for DNS you can install bind with webmin and then create a top level domain and then a couple sub domains to do what you want to accomplish.  For example you can create domain.com and then create virtual hosts in /etc/apache2/sites-enabled so you can have client1.domain.com and client2.domain.com.  Then if you don't want clients to be able to see what other other stuff you are working on you can make some users and mess with .htaccess to create individual usernames and passwords. As for the rest of the system I would install a gusty server addition (upgrade to hardy when it's out of beta) and then at the end of the install choose "lamp server" at the end.  If you need a gui just install the gnome desktop when you are done with the server. If you're just doing demo you won't even need a new computer, any computer built within the last years would be just fine.

---

