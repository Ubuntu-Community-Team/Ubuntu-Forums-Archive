---
title: "Advice For a LAMP Server &quot;First Timer&quot;"
date: 2008-06-20
forum: Server Platforms
---

### Post by INsaneJuly on 2008-06-20
Hello all,

I am going to be setting up a LAMP server soon, using Ubuntu Server Edition.  :???:  I was curious to see if anyone had any advice for a "first timer" at setting up and maintaining the server.  Thanks in advance!  :biggrin:

---

### Post by Kolipoki on 2008-06-20
Still a noob here, but I guess much of what you need to know will depend on the plans and purposes for that server. A common setup can be found in the [[COLOR="RoyalBlue"]**Ubuntu Server Guide**[/COLOR]]("https://help.ubuntu.com/8.04/serverguide/C/index.html"). Another superb how-to is from [www.howtoforge.com](www.howtoforge.com) [[COLOR="RoyalBlue"]**here**[/COLOR]]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts").

Oh I forgot, the how-to in howtoforge.com includes option for installing IPConfig, which could be a bit of an overkill if you don't need all of what it offers. I actually failed my first attempt on installing it. So, you might want to try [[COLOR="RoyalBlue"]**Webmin**[/COLOR]]("http://www.webmin.com/") for the administration and maintenance.

---

### Post by INsaneJuly on 2008-06-23
Thanks!  Those links were extremely helpful.   8-)

---

### Post by windependence on 2008-06-23
What are you wanting to run on the server? Message board? CMS? Simple web site?


-Tim

---

### Post by INsaneJuly on 2008-07-02
> **windependence said:**
> What are you wanting to run on the server? Message board? CMS? Simple web site?


-Tim

I was thinking of (and I'm not sure what I could do locally, since this is my first instance of assembling a server), maybe a local chat, database hosting,  and file-hosting.

---

### Post by ixus_123 on 2008-07-02
fail2ban is a worthwhile install.

it basically stops repeated attempts (by bots mostly) to log into your server via SSH. The config file is annotated well and there is plenty of info on the site on how to set it up.

How much RAM do you have - do you need speed?

you might not need a swap file - it's upto you.  Swapping on a server causes slowdown, if often better (if you have someone to power-cycle it) to let it kernel panic with out of memory errors, than thrash about on the swap file.

If you have swap, there is no need to go larger than 2GB no matter what you RAM size imho.

phpmyadmin gives you a nice front end to MySQL - which might make backing up easier for you.

opensourcecms.com has tons of content management systems that you can demo online - awesomeness!

smartmontools is a good install.  You can set it up to monitor your hard disks and email you for predictive failures - loads of howtos on this on the www

I had a 1Ghz Via C3 mini-itx server running for the last few years but the power supply is getting a bit noisy now so I am migrating the LAMP over to a new asus barebones with core2 celeron and 4GB RAM.  I plan to run virtual machines on it to consolidate my mess.

hardware wise, I'd go for quiet stuff if possible.

The box I have has a huge cpu heatsink with low speed fan and the power supply with 120mm fan - no case fans. Not much cooling is needed for me as the system is vastly overspecced and is never really under much load. I want it to be quiet and not suck in a ton of dust which the low powered via seemed to do over the years.

Disable everthing you don't need in the BIOS - sound, parallel ports, floppy etc and disable "wait for F1 if error" or any similar messages and set power state to power on after power loss

good luck with your build :)

---

### Post by INsaneJuly on 2009-03-05
> **ixus_123 said:**
> fail2ban is a worthwhile install.

it basically stops repeated attempts (by bots mostly) to log into your server via SSH. The config file is annotated well and there is plenty of info on the site on how to set it up.

How much RAM do you have - do you need speed?

you might not need a swap file - it's upto you.  Swapping on a server causes slowdown, if often better (if you have someone to power-cycle it) to let it kernel panic with out of memory errors, than thrash about on the swap file.

If you have swap, there is no need to go larger than 2GB no matter what you RAM size imho.

phpmyadmin gives you a nice front end to MySQL - which might make backing up easier for you.

opensourcecms.com has tons of content management systems that you can demo online - awesomeness!

smartmontools is a good install.  You can set it up to monitor your hard disks and email you for predictive failures - loads of howtos on this on the www

I had a 1Ghz Via C3 mini-itx server running for the last few years but the power supply is getting a bit noisy now so I am migrating the LAMP over to a new asus barebones with core2 celeron and 4GB RAM.  I plan to run virtual machines on it to consolidate my mess.

hardware wise, I'd go for quiet stuff if possible.

The box I have has a huge cpu heatsink with low speed fan and the power supply with 120mm fan - no case fans. Not much cooling is needed for me as the system is vastly overspecced and is never really under much load. I want it to be quiet and not suck in a ton of dust which the low powered via seemed to do over the years.

Disable everthing you don't need in the BIOS - sound, parallel ports, floppy etc and disable "wait for F1 if error" or any similar messages and set power state to power on after power loss

good luck with your build :)


Wow!  Thank you so much for your info!  It has helped me greatly!  :-D

---

