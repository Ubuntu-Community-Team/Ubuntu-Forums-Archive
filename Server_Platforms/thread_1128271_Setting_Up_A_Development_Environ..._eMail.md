---
title: "Setting Up A Development Environ... eMail"
date: 2009-04-17
forum: Server Platforms
---

### Post by Ebon Lupus on 2009-04-17
I've been trying to set up a server on my personal machine, running Ubuntu 8.10, to work with PHP and mySQL design. I'm using Apache 2 and PHPmyadmin... it's all working fine. So far.

What I am interested doing is using something like "sendmail" or "exim" to test web forms, etc., which will be used to send me notifications and/or comments. Pretty basic stuff. Unfortunately, I cannot find any reliable tutorials for making this happen, and after several attempts have taken a step back.

The question is... can someone please direct me to a useful tutorial that is more than one-liners, so I can know what's happening, but not so verbose I need a degree in computer science to translate it into English. All I want to do at this point is type a comment into a web form using a PHP script running on my computer and then receiving it in my gmail.com eMail inbox.

I would greatly appreciate, maybe even worship, anyone capable of helping me out with this.

---

### Post by Ebon Lupus on 2009-04-17
Never mind... I figured it out. I installed ssmtp and it works fine. The information I found regarding it's use was mostly wrong for my machine, but anyway... If this emulated SendMail stuff for posting email from a PHP script on your own server seems to be confusing anyone else, here is what I found out.

Install ssmtp with:```
sudo apt-get install ssmtp
```
Once installed some extremely limited documentation can be found in the README files here: /usr/share/doc/ssmtp/ The configuration file can be found here: /etc/ssmtp/ssmtp.conf and there is a configuration utility that can be executed as: ```
sudo dpkg-reconfigure ssmtp
```
Newbies might find the simple fields of the configuration file confusing, here is what I discovered:[QUOTE="/etc/ssmtp/ssmtp.conf"]#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster [COLOR="Blue"]I left this alone.[/COLOR]

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail.example.com [COLOR="Blue"]This should be your ISP's mailhub. My ISP is Charter, so the mailhub is mail.charter.net.[/COLOR]

# Where will the mail seem to come from?
#rewriteDomain=example.com [COLOR="Blue"]This is the domain you want the message to _appear_ to be from.[/COLOR]

# The full hostname
hostname=your_machines_name [COLOR="Blue"]This is the name you assigned to your machine when you installed Ubuntu.[/COLOR]

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=NO [COLOR="Blue"]This defaults as "NO" but I like setting my own "from" address in my PHP scripts, so I set it to "YES."[/COLOR][/QUOTE]

---

