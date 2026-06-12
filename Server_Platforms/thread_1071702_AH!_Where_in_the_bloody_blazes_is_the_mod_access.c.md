---
title: "AH! Where in the bloody blazes is the mod_access.c file for apache?"
date: 2009-02-16
forum: Server Platforms
---

### Post by Caesonia on 2009-02-16
OK, the title says it all. I am trying to install some RBL fucntionality to my apache server, but I can't find the mod_access.c file that needs to be patched. Everybody keeps referring to src, but everywhere I go related to possible source, I can't find it. I certainly find the .so modules, but not the .c source. 

Please please please....where is it? I have used grep, locate, and it's not there. 

TIA:):)

---

### Post by inphektion on 2009-02-16
aptitude install apache-src

that will get you the src files.

---

### Post by Caesonia on 2009-02-17
> **inphektion said:**
> aptitude install apache-src

that will get you the src files.

UM...nope. It says the package doesn't exist. It can't be found either for my Ubuntu installation or for my CentOS 5.0 installation. This is starting to fit into another of those Linux specially kept secrets, where we give out tiny bits of information, so newer people can guess for a while, and then dump the OS and go away so we don't have to deal with anymore sorts of problems. 

I know I need to modify the mod_access.c file, and I want a backup before I start installing things.

But thanks.

---

### Post by az on 2009-02-17
> **Caesonia said:**
> UM...nope. It says the package doesn't exist. It can't be found either for my Ubuntu installation or for my CentOS 5.0 installation. This is starting to fit into another of those Linux specially kept secrets, where we give out tiny bits of information, so newer people can guess for a while, and then dump the OS and go away so we don't have to deal with anymore sorts of problems. 

I know I need to modify the mod_access.c file, and I want a backup before I start installing things.

But thanks.

[http://packages.ubuntu.com/search?searchon=contents&keywords=mod_access.c+&mode=filename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=mod_access.c+&mode=filename&suite=hardy&arch=any)

There doesn't seem to be a source file named like that.  Perhaps the thing you want to build is outdated?   That would explain why you need to muck around with source code.

Specifically, what do you need to do?  What source are you trying to compile and where did you get it.  Knowing that may help someone solve your problem.

---

### Post by Caesonia on 2009-02-17
> **az said:**
> [http://packages.ubuntu.com/search?searchon=contents&keywords=mod_access.c+&mode=filename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=mod_access.c+&mode=filename&suite=hardy&arch=any)

There doesn't seem to be a source file named like that.  Perhaps the thing you want to build is outdated?   That would explain why you need to muck around with source code.

Specifically, what do you need to do?  What source are you trying to compile and where did you get it.  Knowing that may help someone solve your problem.


Hi. I am trying to install spamhaus's RBL to protect my apache 2.x installation. According to their instructions, I have to modify the mod_access.c file. I have found all the mod_access.so files, which supposedly share the same directory as the .c files. But I only see .so files there.

For example /etc/httpd/modules/mod_access.so

They give you a series of commands to run, and then you go and modify your http.conf file, which I have done a number of times. 

The date on these instructions were a bit older, and perhaps what I need is installed by default now. I don't know. But so far installing the blacklist from SpamHaus has REALLY cut down on the junk coming into the mail server, and I would love to use that list to cut down on brute force attempts. 

TIA.:)

---

### Post by jimv on 2009-02-17
THis looks a lot easier that what you're trying to do:

[http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch](http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch)

Also, Fail2Ban will ban IP address after a certain number of failed logins.

[http://www.fail2ban.org/wiki/index.php/Apache](http://www.fail2ban.org/wiki/index.php/Apache)

---

### Post by Zeosa on 2009-02-17
You indicate that you're on apache2. this file (mod_access.c)is no longer in the source tree for 2.x, but is on 1.3.

The instruction that you're following appear to be for 1.3. For apache 2, there is a module available which should load right in, there's a decent howto here: [http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch](http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch)

---

### Post by az on 2009-02-18
It's going to be packaged in Jaunty:
[http://packages.ubuntu.com/jaunty/libapache2-mod-spamhaus](http://packages.ubuntu.com/jaunty/libapache2-mod-spamhaus)

---

### Post by Caesonia on 2009-02-18
> **jimv said:**
> THis looks a lot easier that what you're trying to do:

[http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch](http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch)

Also, Fail2Ban will ban IP address after a certain number of failed logins.

[http://www.fail2ban.org/wiki/index.php/Apache](http://www.fail2ban.org/wiki/index.php/Apache)

Woot! Much more friendly. I'll try the ubuntu installation tonight with a cuppa. Looks like RHEL isn't going to play so nicely. TA bunches.

---

### Post by Caesonia on 2009-02-18
> **Zeosa said:**
> You indicate that you're on apache2. this file (mod_access.c)is no longer in the source tree for 2.x, but is on 1.3.

The instruction that you're following appear to be for 1.3. For apache 2, there is a module available which should load right in, there's a decent howto here: [http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch](http://www.howtoforge.com/how-to-block-spammers-with-apache2-mod_spamhaus-debian-etch)

Funny thing that. The instructions were right specific on it being for 2.xx. " If you are using Apache1.3 do NOT use this patch."

Thing is, I am just so bloody new at it. I build my first little home Linux thingy a year ago, then suddenly several web servers and internal servers were tossed at me with a mail server in the mix. Ubuntu has really been the most friendly, and has the best community here! I build all the new machines with it. 

So toss me an erroneous doc like this one I've got, and I assume the problem is me.  

TA bunches.

---

