---
title: "How to become a ubuntu/linux expert"
date: 2010-02-03
forum: Server Platforms
---

### Post by userkiller on 2010-02-03
Hi guys am kinda old to this community but i was alway from ubuntu for couple of months. I didn't really get to learn anything but that's why am here to lean, since knowledge is power. i would like you guys to give me a head start explain what is ubuntu cloud i read the description and still didn't understand it.

What's the best website to learn linux? 

Thank you, am looking forward on becoming a linux server administrator soon :)

---

### Post by kevin11951 on 2010-02-03
The easiest way I think is to install Ubuntu Server Edition, and leave it w/o a gui of any kind (inc. no webmin), and try to do everything you need to by CLI, and googling what you dont know.  

ie.  Setup Drupal and SugarCRM by cli only, and when you are done you should know at least a little about Linux CLI and the rest of the lamp stack.  Also for the sake of knowledge, setup each site on a different ip address (virtualhosts, and /etc/network/interfaces)...

---

### Post by lykwydchykyn on 2010-02-03
> **userkiller said:**
> Hi guys am kinda old to this community but i was alway from ubuntu for couple of months. I didn't really get to learn anything but that's why am here to lean, since knowledge is power. i would like you guys to give me a head start explain what is ubuntu cloud i read the description and still didn't understand it.

I can't claim to understand it fully myself, since it seems to be "clouded" in a good bit of marketing speak, but as I understand it (and someone correct me if I'm off here) Ubuntu enterprise cloud is basically a virtualization infrastructure that allows you to quickly create virtual instances of Ubuntu for running network services.

I'm basing my understanding on the fact that it's described in the literature as providing "Amazon EC2-like features", and Amazon EC2 is basically a service where you can rent virtual machines hosted on Amazon's servers.

> 
What's the best website to learn linux? 

Which aspects of Linux?  And which Linux?  There are a few good command line sites out there, but mostly you want to just get experience.

If you REALLY want to become a Linux guru, here's my advice:
 - Get rid of other OSes on your systems.  Run only Linux on everything.  If you don't know how to do something on Linux, force yourself to figure it out.  If you can't play your favorite games... good.  You have learning to do.

 - Hang out on a forum like this and read newbie questions.  If you don't know the answer to a question, see if you can figure it out by experimenting with your own system or researching on the web.

 - Get an old machine and make it a server.  Even if you don't need a server.  Look for services to run on it, even if you barely have any use for them.  I'd say you at least want to know your way around samba, bind, and apache.  And use config files rather than GUIs; not only are they universal, but they give you a better understanding of what's actually going on.

 - Buy some O'Reilly books on Linux, especially from the "hacks" series.  You can usually find them used for under ten dollars apiece on Amazon, Ebay, or Half.com.  

> 
Thank you, am looking forward on becoming a linux server administrator soon :)

May your dreams come to fruition in the best of ways.

---

### Post by quietas on 2010-02-03
LIke they said usage really is the way. I haven't seen a goo [www.learnlinuxsupereasy.com](www.learnlinuxsupereasy.com) or something. The Linux for Dummies book is a good start and has some decent info plus reference material. I'd browse your local bookstore and see what is readable to you. Orielly books are nearly always great, but not always the best to start with.

I'd recommend two things. Find a purpose for your computer. Host a website, put up a blog, make a mail server, maybe a local lan file server, basically find a reason to have the machine. This will give you a reason to poke around and actually do it. In my sig I have a link to my thread on home servers, there is a bunch of info about what other people are using Ubuntu for.

And the second thing I would recommend: Try it as a desktop as well. You will get both a different perspective on what it can do (nearly everything) and how Linux interacts with the rest of the world.

---

### Post by kimda on 2010-02-03
Install loads of different distributions on a spare machine or install them in a virtualmachine (vmware/virtualbox etc..) so that you can muck around. There are several good websites to learn how to set up certain things. This is a great one: [http://www.howtoforge.org](http://www.howtoforge.org)  If you are into Debian/Ubuntu like me: 
[http://www.debian-administration.org](http://www.debian-administration.org) 
Learn about the commandline. If you know how to maintain a ubuntu box from the commandline you will also know to do the same with redhat or suse. Learn how to setup different daemons (like apache, bind, postfix (or other mailservers), ftp server, samba etc...).

---

### Post by quietas on 2010-02-03
I forgot one tip also. Really it covers everything computers infact.

Play with it till it breaks. Learn to fix it. That's the beat way to understand what you are doing. =)

---

### Post by Johnsie on 2010-02-03
The best way to learn is by installing an alpaha version of ubuntu and riding the wave of all th errors that wil comin up

---

### Post by lisati on 2010-02-03
Sometimes it's good to learn by doing. In the week or so that I've had my main desktop accepting emails via smtp, I've gained a greater appreciation of the challenges faced by email service providers while I've been tinkering with the settings to reject unwanted emails.

---

### Post by userkiller on 2010-02-03
> **lykwydchykyn said:**
> I can't claim to understand it fully myself, since it seems to be "clouded" in a good bit of marketing speak, but as I understand it (and someone correct me if I'm off here) Ubuntu enterprise cloud is basically a virtualization infrastructure that allows you to quickly create virtual instances of Ubuntu for running network services.

I'm basing my understanding on the fact that it's described in the literature as providing "Amazon EC2-like features", and Amazon EC2 is basically a service where you can rent virtual machines hosted on Amazon's servers.


Which aspects of Linux?  And which Linux?  There are a few good command line sites out there, but mostly you want to just get experience.

If you REALLY want to become a Linux guru, here's my advice:
 - Get rid of other OSes on your systems.  Run only Linux on everything.  If you don't know how to do something on Linux, force yourself to figure it out.  If you can't play your favorite games... good.  You have learning to do.

 - Hang out on a forum like this and read newbie questions.  If you don't know the answer to a question, see if you can figure it out by experimenting with your own system or researching on the web.

 - Get an old machine and make it a server.  Even if you don't need a server.  Look for services to run on it, even if you barely have any use for them.  I'd say you at least want to know your way around samba, bind, and apache.  And use config files rather than GUIs; not only are they universal, but they give you a better understanding of what's actually going on.

 - Buy some O'Reilly books on Linux, especially from the "hacks" series.  You can usually find them used for under ten dollars apiece on Amazon, Ebay, or Half.com.  



May your dreams come to fruition in the best of ways.


You and every body else are wonderful person thatnks for the quick tips guys.;)

Yea when i began with linux i was just running server it self with no gui, i managed to host my site and set up samba server, i kinda forgot but i still remember couple of stuff.

Thanks guys, am really looking forward of becoming a linux guru :)

---

### Post by FuturePilot on 2010-02-03
> **lykwydchykyn said:**
> I can't claim to understand it fully myself, since it seems to be "clouded" in a good bit of marketing speak, but as I understand it (and someone correct me if I'm off here) Ubuntu enterprise cloud is basically a virtualization infrastructure that allows you to quickly create virtual instances of Ubuntu for running network services.

I'm basing my understanding on the fact that it's described in the literature as providing "Amazon EC2-like features", and Amazon EC2 is basically a service where you can rent virtual machines hosted on Amazon's servers.


Which aspects of Linux?  And which Linux?  There are a few good command line sites out there, but mostly you want to just get experience.

If you REALLY want to become a Linux guru, here's my advice:
 - Get rid of other OSes on your systems.  Run only Linux on everything.  If you don't know how to do something on Linux, force yourself to figure it out.  If you can't play your favorite games... good.  You have learning to do.

 - Hang out on a forum like this and read newbie questions.  If you don't know the answer to a question, see if you can figure it out by experimenting with your own system or researching on the web.

 - Get an old machine and make it a server.  Even if you don't need a server.  Look for services to run on it, even if you barely have any use for them.  I'd say you at least want to know your way around samba, bind, and apache.  And use config files rather than GUIs; not only are they universal, but they give you a better understanding of what's actually going on.

 - Buy some O'Reilly books on Linux, especially from the "hacks" series.  You can usually find them used for under ten dollars apiece on Amazon, Ebay, or Half.com.  



May your dreams come to fruition in the best of ways.

This x1000
Experience experience experience.

---

### Post by eWheeler on 2011-09-06
I suppose it depends if you are looking for a set of common commands.  I recommend starting with the command line, learning pipes and a bit of shell scripting.  

If you want a challenge, trace the boot of your system from calling /sbin/init all the way to your login screen.  If you understand everything those scripts are doing then you are on your way to becoming an expert!  Of course an expert keeps learning new stuff too---especially since new software and changes perpetuate Linux!

A site like this may be helpful too:  [URL="http://www.papermonkey.net/"]UNIX
Tutorial: Absolute Beginner to Linux "Expert" in 10 Lessons[/URL]

Cheers,

-Eric

---

### Post by Dangertux on 2011-09-06
If it helps I recently interviewed for a system admin job that I likely won't take (pay isn't as good as what I already make)

However the types of things they were looking for were this.

-- bash scripting knowledge
-- modification of files using tools like sed, awk
-- usage of vi/vim
-- iptables syntax
-- perl , python or php knowledge (this probably was dependent on the employer not so much the position)
-- understanding services (how to stop start restart etc)
-- cron jobs and creating remove editing them
-- compiling custom kernels
-- dns knowledge (bind)
-- usage of webmin
-- cpanel/WHM
-- basic cli knowledge (du, head, tail, dd, cp, mv, ls, chattr, chmod, chown, lsattr, rm)


Not really sure these things qualify you as an expert, but they qualify you for employment, which can lead to you being an expert. Side note, the job offering was just over $60k /yr with decent benefits. So if you're looking for a starting point to becoming a "server admin" professionally, I hope that helps.

If you're just wanting to do it for a hobby, do as others said and just dive in and learn learn learn.

---

### Post by spynappels on 2011-09-06
> **Dangertux said:**
> If it helps I recently interviewed for a system admin job that I likely won't take (pay isn't as good as what I already make)

However the types of things they were looking for were this.

-- bash scripting knowledge
-- modification of files using tools like sed, awk
-- usage of vi/vim
-- iptables syntax
-- perl , python or php knowledge (this probably was dependent on the employer not so much the position)
-- understanding services (how to stop start restart etc)
-- cron jobs and creating remove editing them
-- compiling custom kernels
-- dns knowledge (bind)
-- usage of webmin
-- cpanel/WHM
-- basic cli knowledge (du, head, tail, dd, cp, mv, ls, chattr, chmod, chown, lsattr, rm)


Not really sure these things qualify you as an expert, but they qualify you for employment, which can lead to you being an expert. Side note, the job offering was just over $60k /yr with decent benefits. So if you're looking for a starting point to becoming a "server admin" professionally, I hope that helps.

If you're just wanting to do it for a hobby, do as others said and just dive in and learn learn learn.

+1 to this, these are the skills we require for starter (Unix) sys-admins.

---

### Post by whatthefunk on 2011-09-06
Everything listed so far is great.  I dont think anybody else has mentioned this so far, so I will: try to customize everything and find out as many ways to do it as possible.  Start out with figuring out how to do basic desktop customizations in the GUI.  Then figure out how to do the same things in the command line.  Then progress to more advanced customizations.  Change your boot screen, improve your boot time, make your own icon theme, customize your startup applications, change the look of your menu etc.  Youll get a good feel for how things work and in the end, your system will be exactly how you want it.

---

### Post by haqking on 2011-09-06
Linux can be daunting due to unfamiliar terrritory but to become a confident user and then onto an expert which only comes only with experience and read, read, read and try, try try then there are at least some basics needed.

First of all i suggest getting to get grips with the security model early on, as there is alot of misunderstanding about Viruses in Linux and malware in general etc so i refer you first to the importance of using sudo here at:

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

here for security in general

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and these stickies (in my signature)

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

here for virus information

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

and this will give you a good grounding in the security of your system and such like.

After that it is a case of play, setup virtual machines so you can play without trashing your machine, see:

[www.virtualbox.org](www.virtualbox.org)

and this sub-forum [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

that way you can play with partitions and CLI etc without risking anything.

Also see the command line:

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[http://linuxcommand.org/](http://linuxcommand.org/)

Then it comes down to what you want do and achieve, try the following for a starter:

[http://www.makeuseof.com/tag/10-applications-install-ubuntu-lucid-lynx/](http://www.makeuseof.com/tag/10-applications-install-ubuntu-lucid-lynx/)
[http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/](http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/)
[http://blog.sudobits.com/2011/03/07/top-10-ubuntu-games/](http://blog.sudobits.com/2011/03/07/top-10-ubuntu-games/)

There is so much, it is a case of where do you start.

These are mainly Desktop related, but you also need a grounding in servers and services so here is a good read:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

This is of course all pertaining to Ubuntu, to become a Linux Guru or Expert you need to have a grounding in all these concepts across Distros so i refer you back to the virtualisation section to play with distros as much as you like.

Set up servers, crack security, network Vm together, do backups, file sharing etc etc

Have fun

Regards

haqking

---

### Post by Habitual on 2011-09-06
This is my opinion only on this subject:

If you want to *use* Linux, install any commonly popular distro.

If you want to ***learn*** Linux, install Slackware.

---

### Post by haqking on 2011-09-06
> **Habitual said:**
> This is my opinion only on this subject:

If you want to *use* Linux, install any commonly popular distro.

If you want to ***learn*** Linux, install Slackware.


how does installing Slackware give the OP any access to anything different for learning Linux ?

if he could do something in Slackware which he couldnt do in another Distro then he would be learning Slackware and not Linux in general

---

### Post by lykwydchykyn on 2011-09-06
> **haqking said:**
> how does installing Slackware give the OP any access to anything different for learning Linux ?

if he could do something in Slackware which he couldnt do in another Distro then he would be learning Slackware and not Linux in general

I think the point is that Ubuntu is designed to make using Linux as easy and abstracted as possible.  If your goal is to dig into the guts and learn it, that's counter to your goal.

That's not saying you can't dig into the guts of Ubuntu, but many distros (like Slackware) give you no other option but to dig in and get your hands dirty.  

In that sense, they are ideal for the person wishing to learn more about Linux internals.

---

### Post by haqking on 2011-09-06
> **lykwydchykyn said:**
> I think the point is that Ubuntu is designed to make using Linux as easy and abstracted as possible.  If your goal is to dig into the guts and learn it, that's counter to your goal.

That's not saying you can't dig into the guts of Ubuntu, but many distros (like Slackware) give you no other option but to dig in and get your hands dirty.  

In that sense, they are ideal for the person wishing to learn more about Linux internals.


Dont get me wrong, i am familiar with Slackware.

I just meant for the OP it would seem that it means Slackware is more Linux than anything else is, all the same guts and services are there to play with in any distro pretty much, i know Ubuntu abstarcts the complex.

---

### Post by Habitual on 2011-09-06
> **lykwydchykyn said:**
> I think the point is that Ubuntu is designed to make using Linux as easy and abstracted as possible.  If your goal is to dig into the guts and learn it, that's counter to your goal.

That's not saying you can't dig into the guts of Ubuntu, but many distros (like Slackware) give you no other option but to dig in and get your hands dirty.  

In that sense, they are ideal for the person wishing to learn more about Linux internals.

+1
Too many people these days do not know the system, just the GUI equivalents of c-li commands. This has the same effect on the end-user as the Microsoft-Era Desktop Environments. Lots of people know the DE, but very few know what's going on "under the hood".

You can learn linux using any distro if you are so inclined.

The desire to know what's "under the hood" is distro-agnostic.
The Desktop Experience is not conducive to learning linux. It is conducive to using linux IMHO.

Once one is proficient with Linux at the c-li, then the distro does not matter.

Again, this is my opinion of "How to become an expert"

---

### Post by haqking on 2011-09-06
> **haqking said:**
> how does installing Slackware give the OP any access to anything different for learning Linux ?

if he could do something in Slackware which he couldnt do in another Distro then he would be learning Slackware and not Linux in general

> **Habitual said:**
> +1
Too many people these days do not know the system, just the GUI equivalents of c-li commands. This has the same effect on the end-user as the Microsoft-Era Desktop Environments. Lots of people know the DE, but very few know what's going on "under the hood".

You can learn linux using any distro if you are so inclined.

The desire to know what's "under the hood" is distro-agnostic.
The Desktop Experience is not conducive to learning linux. It is conducive to using linux IMHO.

Once one is proficient with Linux at the c-li, then the distro does not matter.

Again, this is my opinion of "How to become an expert"


OK for clarity so you know i am not disagreeing with you, i agree with your latest post.

I read your original slackware comment wrong probably, i replied for the OP benefit really incase he was led to believe that slackware was more Linux than any other distro, i read your statement like Slackware was more of a real linux if you like than another distro ;-)

peace

---

### Post by Habitual on 2011-09-06
> **haqking said:**
> OK for clarity so you know i am not disagreeing with you, i agree with your latest post.

I read your original slackware comment wrong probably, i replied for the OP benefit really incase he was led to believe that slackware was more Linux than any other distro, i read your statement like Slackware was more of a real linux if you like than another distro ;-)

peace

No harm, no foul.
I'm pretty opinionated after 17 years in IT, so I tend to not articulate my points sometimes.

Peace.

---

### Post by Dangertux on 2011-09-06
> **Habitual said:**
> +1
Too many people these days do not know the system, just the GUI equivalents of c-li commands. This has the same effect on the end-user as the Microsoft-Era Desktop Environments. Lots of people know the DE, but very few know what's going on "under the hood".

You can learn linux using any distro if you are so inclined.

The desire to know what's "under the hood" is distro-agnostic.
The Desktop Experience is not conducive to learning linux. It is conducive to using linux IMHO.

Once one is proficient with Linux at the c-li, then the distro does not matter.

Again, this is my opinion of "How to become an expert"

While I agree 90% with what you're saying here I disagree on one point.

To truly master something you must master all elements. This includes the desktop environment as well as the CLI. I think far too many administrator's are overzealous to call themselves gurus because they can stream edit like a pro.

A skill is a skill regardless of if it is considered relevant in your field. So to some (usually sysadmins) mastery of the graphical user interface is a trivial matter. While to another (graphic designer) it might be crucial to success. It's all in point of view.

In my personal opinion if you truly obtain mastery, your task is done and you would not continue with it.

---

### Post by haqking on 2011-09-06
> **Habitual said:**
> No harm, no foul.
I'm pretty opinionated after 17 years in IT, so I tend to not articulate my points sometimes.

Peace.

no worries. I am very opinionated after 25+ ;-)

I hardly ever articulate what i mean, and confuse myself with what i say all the time...LOL

---

### Post by haqking on 2011-09-06
> **Dangertux said:**
> While I agree 90% with what you're saying here I disagree on one point.

To truly master something you must master all elements. This includes the desktop environment as well as the CLI. I think far too many administrator's are overzealous to call themselves gurus because they can stream edit like a pro.

A skill is a skill regardless of if it is considered relevant in your field. So to some (usually sysadmins) mastery of the graphical user interface is a trivial matter. While to another (graphic designer) it might be crucial to success. It's all in point of view.

In my personal opinion if you truly obtain mastery, your task is done and you would not continue with it.


true mastery only comes when you learn that change is the only constant and so you can never really truly master anything ;-)

---

### Post by Dangertux on 2011-09-06
> **haqking said:**
> true mastery only comes when you learn that change is the only constant and so you can never really truly master anything ;-)

Exactly my point.

Also the original question is extremely loaded.

You can be amazing at a certain part of ubuntu/linux and not so strong at another.  To truly become a master of an entire operating system and all of its possibility would be a difficult task to undertake.

---

### Post by Habitual on 2011-09-06
> **haqking said:**
> true mastery only comes when you learn that change is the only constant and so you can never really truly master anything ;-)

+2

Very zen.
Personally, I strive for proficiency.

---

### Post by haqking on 2011-09-06
> **Habitual said:**
> +2

Very zen.
Personally, I strive for proficiency.

ha i was raking my sand pit and typing on my google nexus...LOL

I strive for achieving what i need to do without too many headaches ;-)

---

