---
title: "Think I've found my server distro..."
date: 2008-08-21
forum: Testimonials &amp; Experiences
---

### Post by Dark Shade on 2008-08-21
Hello all, new guy here.

I'm relatively new to Linux (though have worked in the Terminal.app in Mac OS X often) and I've been using virtual machines to test out different distros.  The main reason why I am doing this now is because I managed to get a 1U rackmount server for a reasonable price, and I want to setup a dedicated web/game server on it.  After checking out other threads on experiences, I threw a couple up and checked out to see which one was for me.

First up was Gentoo, many have sung its praises, and by following the directions *to the letter* from its handbook, I managed to install it and recompile the kernel (wow, did that take a while).  I needed to test other systems so I put it on the backburner.

Next I tried Slackware.  I did try it back in 10.x days but at that time, Linux wasn't for me.  I was somewhat familiar with the install and setup, but realized soon after that I needed more experience in Linux in general to master it.

Then Debian was my next venture, very easy to get up and running, but still I was having difficulty doing pretty standard things, figuring I was just too much of a noob to even bother fixing.

Finally I setup Ubuntu server 8.04.  It actually installed everything I needed in a nice package, auto-resolving dependencies, and is my only 'fully functional' Linux virtual system.  Apache2, mysqlserver, php5, phpmyadmin, webmin, all working perfectly so far.

Now the only thing I need is for the hardware for the server to arrive and there will most definitely be an Unbuntu server out in the 'wild' under my control.

Several guides on the internet as well as this forum has helped considerably in my attempts to get a server up and going.  Well, just wanted to share my (limited) experience with Linux so far and hope to learn a lot really soon.

---

### Post by wolfen69 on 2008-08-22
hey dark, nice to meet ya

---

### Post by rmayer32 on 2008-08-22
I too love the server version. I have two of them running out of my house..lol

---

### Post by ukripper on 2008-08-22
i have upgraded my servers from gutsy to hardy without any problems. my backup + fileserver has currently uptime of 63 days.

spec -
athlon XP 1500+ 1300Mhz
748MB RAM on idle 25 MB used after all services running.
10GB HDD
400GB EXTERNAL NTFS drive attached for network backup via rsync ssh

SSH for remote administration (personally i don't like webmin)
No GUI on server. Perfect setup

Welcome to the community.

---

### Post by Dark Shade on 2008-08-25
I figured I'd ask here instead of opening a new thread.

What are some MUST-HAVE items I should have for my web/game server?  I have a small list here that don't come with a standard install and just to update existing installations:

apache2
mysql-server
php5
libapache2-mod-php5
phpmyadmin
ia32-libs
schedutils

Not on apt-get

webmin
zlib


Anything else I should add?

---

### Post by ukripper on 2008-08-25
> **Dark Shade said:**
> I figured I'd ask here instead of opening a new thread.

What are some MUST-HAVE items I should have for my web/game server?  I have a small list here that don't come with a standard install and just to update existing installations:

apache2
mysql-server
php5
libapache2-mod-php5
phpmyadmin
ia32-libs
schedutils

Not on apt-get

webmin
zlib


Anything else I should add?

where is ssh???

---

### Post by Dark Shade on 2008-08-25
> **ukripper said:**
> where is ssh???

Ah, see, exactly what I needed reminded of.  Anything else?  :)

---

### Post by Crafty Kisses on 2008-08-25
Good to hear and welcome to the Ubuntu community.

---

### Post by ukripper on 2008-08-26
> **Dark Shade said:**
> Ah, see, exactly what I needed reminded of.  Anything else?  :)

ok let us get some more specific here. What exactly is the purpose of the server you want to build and what are your server specs?

---

### Post by Dragonbite on 2008-08-26
I want to try and set up an Ubuntu server, but I am fairly new to server administration (and still getting into trouble with networking ;) ) so I'm a little apprehensive on going CLI.

I've found [[COLOR="Blue"]HowToForge[/COLOR]]("http://www.howtoforge.org"), which has helped but are there any CLI tools or web-based tools I could install for managing the server?

I'm looking for a fairly basic file/print/web server at this point (got another machine running my DHCP) and then want to build upon the web server aspect (include mod_mono for ASP.NET, Drupal (w/PHP), etc.).

Currently I'm using openSUSE because I can SSH into it and run Yast in the CLI but would love to set up an Ubuntu Server.

---

### Post by Dark Shade on 2008-08-26
> **ukripper said:**
> ok let us get some more specific here. What exactly is the purpose of the server you want to build and what are your server specs?

Certainly.

Tyan Tiger i7320 - S5350
Dual Xeon 3.6GHz 800MHz FSB
4GB ECC/Registered DDR2100
360GB SATA HDD
Colocated with 100Mbit connection

The purpose of the server is to host around 5 websites using php4+5/mysql/apache, administered mainly via Webmin and/or phpmyadmin.  On these websites will contain several mysql databases of small size for a handful of forums, small-time statistical analysis and a Medaiwiki with a few hundred thousand pageviews a month, with apache hosting three or so domain names.

It also will be hosting a few games such as Team Fortress 2, Quake III and Battlefield 2.  

I'm more skilled to know how much power is needed for the games (I know what settings are useful and useless, players per server limits, etc), and not so experienced when it comes to how much power/dedication is needed for the websites and their respective interactions with the system.

The apache2, mysql-server, php5, libapache-mod-php5,, ssh phpmyadmin and webmin are pretty self explanatory.  The ia32-libs I read are necessary for compiling and running 32-bit applications in a 64-bit OS.  Schedutils are included to set processor affinities to heavy processes such as TF2 and BF2.  Zlib is for compatibility concerns I encountered previously.

Anything else I can be clear about?  :popcorn:

(Also, a semi-technical question.  I had to RMA my server because of a bad motherboard, but I am itching to get this installation up and running.  If I install Ubuntu on a hard drive using a different system, can I just transplant that hard drive into the new server when it comes and not run into conflictions?  I know Windows 2000 hates being moved away but Ubuntu is a whole different animal.  Would it auto-resolve new hardware when it's installed in a new system?)

---

### Post by ukripper on 2008-08-27
> **Dark Shade said:**
> Certainly.

Tyan Tiger i7320 - S5350
Dual Xeon 3.6GHz 800MHz FSB
4GB ECC/Registered DDR2100
360GB SATA HDD
Colocated with 100Mbit connection

The purpose of the server is to host around 5 websites using php4+5/mysql/apache, administered mainly via Webmin and/or phpmyadmin.  On these websites will contain several mysql databases of small size for a handful of forums, small-time statistical analysis and a Medaiwiki with a few hundred thousand pageviews a month, with apache hosting three or so domain names.

It also will be hosting a few games such as Team Fortress 2, Quake III and Battlefield 2.  

I'm more skilled to know how much power is needed for the games (I know what settings are useful and useless, players per server limits, etc), and not so experienced when it comes to how much power/dedication is needed for the websites and their respective interactions with the system.

The apache2, mysql-server, php5, libapache-mod-php5,, ssh phpmyadmin and webmin are pretty self explanatory.  The ia32-libs I read are necessary for compiling and running 32-bit applications in a 64-bit OS.  Schedutils are included to set processor affinities to heavy processes such as TF2 and BF2.  Zlib is for compatibility concerns I encountered previously.

Anything else I can be clear about?  :popcorn:

(Also, a semi-technical question.  I had to RMA my server because of a bad motherboard, but I am itching to get this installation up and running.  If I install Ubuntu on a hard drive using a different system, can I just transplant that hard drive into the new server when it comes and not run into conflictions?  I know Windows 2000 hates being moved away but Ubuntu is a whole different animal.  Would it auto-resolve new hardware when it's installed in a new system?)

Your server is more than powerful to host 5 websites with decent bandwidth, so i believe you won't be having any perfomance issues if you solely run the websites. My only lack of understanding comes from your Gaming server as my expertise is based upon the stats of performance, latency and  robustness of the system - unless i know how your system performs under heavyload and on average over time it is quite hard for me to judge how would your server perform under heavy load of usage!

What i would suggest you to first go through some stress and spike testing on gaming server and then as a webserver and finally as a both. Take out the loadaverage over time and you will get the graph over time as a result which would help you analyse the performance, latency and the robustness of the system.

And for your second query, i think there shouldn't be a problem just slotting the drive into the new server. My only concern is if it RAID based then you have to be little careful incase redundant volume tries to recreate itself when loaded into the new machine may overwrite your previous data.

Overall, I think you should be alright but the test speaks for itself! I don't believe in words I believe in the result.

---

### Post by Dark Shade on 2008-08-27
> **ukripper said:**
> Your server is more than powerful to host 5 websites with decent bandwidth, so i believe you won't be having any perfomance issues if you solely run the websites. My only lack of understanding comes from your Gaming server as my expertise is based upon the stats of performance, latency and  robustness of the system - unless i know how your system performs under heavyload and on average over time it is quite hard for me to judge how would your server perform under heavy load of usage!

What i would suggest you to first go through some stress and spike testing on gaming server and then as a webserver and finally as a both. Take out the loadaverage over time and you will get the graph over time as a result which would help you analyse the performance, latency and the robustness of the system.

And for your second query, i think there shouldn't be a problem just slotting the drive into the new server. My only concern is if it RAID based then you have to be little careful incase redundant volume tries to recreate itself when loaded into the new machine may overwrite your previous data.

Overall, I think you should be alright but the test speaks for itself! I don't believe in words I believe in the result.

I assumed as much about the websites, the only trick to them is configuration.

The plan is to have the two heavy games (BF2 and TF2) set to affinity to different processors, and then spread the remaining utilization between webserving and the 'light' games (Quake II, III).  The only one I can really *test* *right now* is Quake III, as I load the game I want, I can add 16 bots to see what the CPU% toll is, and approximate from that.  With no other game servers running and nothing going on through apache, it runs between 4%-13% consistently.  Looking good so far, since I will only be allowing 12 clients on there at a time anyway in the real world test.

The server won't run with a RAID configuration as I only have one hard drive to put in it, and I don't foresee needing more space for quite a while.  I'm running it on a 2.5GHz AMD Athlon x2 at the moment to best estimate how the actual server will react, although the architecture and overall speeds are different, it's the closest machine to approximate at the moment, pending the arrival of the (hopefully operational) actual server.

---

### Post by ukripper on 2008-08-28
> **Dark Shade said:**
> I assumed as much about the websites, the only trick to them is configuration.

The plan is to have the two heavy games (BF2 and TF2) set to affinity to different processors, and then spread the remaining utilization between webserving and the 'light' games (Quake II, III).  The only one I can really *test* *right now* is Quake III, as I load the game I want, I can add 16 bots to see what the CPU% toll is, and approximate from that.  With no other game servers running and nothing going on through apache, it runs between 4%-13% consistently.  Looking good so far, since I will only be allowing 12 clients on there at a time anyway in the real world test.

The server won't run with a RAID configuration as I only have one hard drive to put in it, and I don't foresee needing more space for quite a while.  I'm running it on a 2.5GHz AMD Athlon x2 at the moment to best estimate how the actual server will react, although the architecture and overall speeds are different, it's the closest machine to approximate at the moment, pending the arrival of the (hopefully operational) actual server.

Based on those tests it looks promising in real world scenario. As you have described you are limiting clients to 12 should be fine to run websites and game server as duo.I believe you still have a backing up plan already in place.

---

### Post by Dark Shade on 2008-08-28
> **ukripper said:**
> Based on those tests it looks promising in real world scenario. As you have described you are limiting clients to 12 should be fine to run websites and game server as duo.I believe you still have a backing up plan already in place.


The important data will have daily redundant backups via a collection of services (tar, curl, ftp) through a shell script utilizing cron.

Programs such as the game servers won't be backed up as their size prohibits daily or even weekly backups, but everything regarding the web sites and other important data will be.

---

### Post by ukripper on 2008-08-29
> **Dark Shade said:**
> The important data will have daily redundant backups via a collection of services (tar, curl, ftp) through a shell script utilizing cron.

Programs such as the game servers won't be backed up as their size prohibits daily or even weekly backups, but everything regarding the web sites and other important data will be.

Great. If you decide to sync at anytime you may perhaps use rsync via ssh as a shell/bash script. Then you can cron the script to run at schedule time.

rsync works both ways and one way sync and can be used as backup too.

For dumping backups to remote host I believe tar is more than enough.

---

### Post by Dark Shade on 2008-08-29
> **ukripper said:**
> Great. If you decide to sync at anytime you may perhaps use rsync via ssh as a shell/bash script. Then you can cron the script to run at schedule time.

rsync works both ways and one way sync and can be used as backup too.

For dumping backups to remote host I believe tar is more than enough.

Yeah I am still considering rsync, though I know nothing about how it's setup and all that, guess it'll be another learning experience.

---

