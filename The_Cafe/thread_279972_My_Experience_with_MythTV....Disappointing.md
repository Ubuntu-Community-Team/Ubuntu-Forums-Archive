---
title: "My Experience with MythTV....Disappointing"
date: 2006-10-18
forum: The Cafe
---

### Post by basketcase on 2006-10-18
No this is not an I hate linux rant, I actually have it on one of my desktops, and on my notebook.  I very much like Linux, and am awaiting the day when I can convert 100%. 

Anways, my little trek with MythTV started a number of months back, and at that time unsuccessful, moreso because of hardware issues I was facing, than the software.  

Move to this past weekend...Hardware is working well, and I'm off.  I had downloaded ZenWalk linux and wanted to see what it was all about.  Hardware detection was great, everything functioned as I could hope it would, so I said, what the hey, lets see if we can get MythTV installed.  Found that ZenWalk was based on Slackware, and though new to me (slackware), I figured again why not.  I have to say, there seems to be a lack of a how-to for something more recent (hardware/software available).  The how-tos seemed out-dated.  I know, I'm bitching and should do it myself.  Anyways, I'm too dependable upon apt-get, and was lost with packagemanagement with Netpkg.  Strike 1.

I had the latest version of KnoppMyth downloaded and burned to a CD, when trying to install I initially encountered an error -- uncertain what, tons of characters (not letters or anything of the sorts) on the screen that made no sense.  I figured it was a bad burn.  

Burned new disk for KnoppMyth and it installed.  Everything was running smoothly, no complaints -- Until I rebooted.  As previously in the past when I had tried to install KnoppMyth, after a reboot on it's booting up, it seemed to 'tank' (for a lack of better terms) on the ivtv initilizing.  I'm uncertain what caused this, everything functioned fine, but after that reboot, it was done for.  I was getting stressed at this point.  Strike Two!  

I like Ubuntu, and always seem to come back to it.  It has actually been on my notebook for almost a year now (if not longer), and I'm very pleased with it.  So I figure, why not use the distro I like the most?  Well I started with a copy of 6.06 I had burned here.  I did the cdtest and was successful with no errors.  Everything installed fine and functioned as it should.  

First attempt of install MythTV, failure.  Per the number of how-to's on the WWW, I seemed to get stuck at the linking of directories when uncompression/compiling ivtv drivers.  No big deal, lets start over. 

2nd attempt...Failure.  Environment all set up, everything seems to be going smoothly (I'm excited), but for some reason I am unable to connect to the database.  After a number of attempts to COMPLETELY uninstall Mysql/phpmyadmin and everything associated with it (as well as Mythtv at that time), I was unsuccessful, and felt like I was running around in circles.  Still not giving up.  Per a few searches on this site, one that said that MythTV .20 was supported in Edgy, why not upgrade?  

Upgraded to Edgy, personally I cannot tell a difference between Edgy and Dapper, but that's for another topic.  MythTV .20 is in the repositories and everything appeared to be functioning wonderfully, again until MySQL setup.  I'm not sure why I'm lost here.  I have setup and used Mysql on a few servers that hosted wordpress, phpbb as well as Invisionboard.  So though I am not a 'master' when it comes to Mysql, I knew that I should be able to successfully setup mysql w/o issues.  Stike 3 -- I gave up on Ubuntu :(  

Now this is like 10PM Sunday night, I've been sitting in front of this computer for a LONG time hoping to make something work.  Google showed me Mythdora.  Now I had Fedora Core 3 on a small server set on my home's DSL for over a year w/o ANY issues, so I liked it, but left it for Ubuntu 5.04/5.10.  Again, I liked apt-get, and hated rpm-based distributions.  But I wasn't really worried about the distrobution as I was getting a solid/functioning MythTV box up and running.  

Typical Fedora Core install, nothing spectacular, longer than KnoppMyth, like the GUI installer a lot, very professional.  A step ahead of Ubuntu, and a step behind SuSE.  Installed, restarted, configured....SUCCESSFUL.  

Here are my final thoughts on this little adventure.  
KnoppMyth is a great idea, love that it is based on Knoppix (debian based), it seems dated though (compared to Zenwalk, Ubuntu, MythDora).  I personally cannot say much more as I could never seem to get a good install.  

Per the 'how-to's on installing/configuring MythTV, there is no consistency from one how-to to another. I realize that there is always more than one way to do something, but for a 'newbie' it is challenging and confusing making heads or tales on what the next step should be per the how-to you're following.  And if you messed up somewhere along the lines during the install, and look at another how-to, which one is right, which one is wrong?  Essentially neither are wrong or right because I'm assuming the author was successful in their installations because that is why they're writing they're how-to.  It was also sort of evident that either a couple of how-tos were written by the same person verbatim or a copy/paste had taken place.  

So why did I write this.  I needed to vent to ppl I hope could understand the stresses.  This is not so much a rant/hateful post in anyway.  

I like Ubuntu too much to give up.  I'm gonna take what I've learned, what I CAN learn and try and create Mythbuntu.  I recently read on Digg that KnoppMyth was going to be converted over to Ubuntu, but no official release had been given yet, and I don't believe everything on the internet, so I'll believe it when I see it.  

This is something I've wanted to do, I honestly have no idea what I'm getting myself into, but i hope a great experience that with a great return.  I want to create something that is based on *buntu, and allows for a simpler means of installing/configuring MythTV.  

So for those of you who are still reading...Thanks!  For those of you who scrolled to the bottom, you didn't miss anything.  

Thanks for the space to vent.

---

### Post by prizrak on 2006-10-18
I feel you man. I actually had a thread somewhere on here about how Ubuntu needs to have an HTPC version to take the guess work out of installing MythTV. The downside of course is that you will be behind the official release a little bit.

---

### Post by basketcase on 2006-10-18
In the past, I've always tried to keep up with the latest and greatest.  Essentially what I'll be going for on this project is the MOST stable, and not necessarily the most current. 

Though Edgy will be the current release here soon, I'll probably try and build off of 6.06 as it is LTS.  I don't know enough about .19 and .20 to know the differences, but will do more research and see what comes of it.

---

### Post by lerrup on 2006-10-19
Well, I'm not sure what happened for you as I've just re-installed Myth on a Dapper setup without any big problems but lirc - but that's not Myth.

I would suggest that:
a) you make sure the cards etc are detected before the myth install
b) You install the MySQL before the myth-backend and not touch any of the configuration at this point.
c)  You use Mario's repository for 0.20 .debs.
d)  You install the basic setup first and make sure that you install ALL the dependencies and suggested packages (synaptic is your friend).
e)  go through the mythtv-setup screens very carefully
f) Start the backend before starting the frontend

It should then work.  It is not perfect (yet), but when it is up and running it is bloody brilliant.

---

### Post by DoctorMO on 2006-10-19
MythTV reminds me of windows, as long as everything isn't touched your ok and everything is done by an ultra slow screen.

I dumped it because tvtime has far better screen rendering abilities and delacing filters that don't need to be some how switched on by reading a ton of configuration.

The other problem is that I use MySQL for website development and yet MythTV wanted me to remove my databases, reinstall mysql just so I could get a default myself install... yep far too windows like.

Sorry but mythtv rates a 2/10.

---

### Post by dannyboy79 on 2006-10-19
> **lerrup said:**
> Well, I'm not sure what happened for you as I've just re-installed Myth on a Dapper setup without any big problems but lirc - but that's not Myth.

I would suggest that:
a) you make sure the cards etc are detected before the myth install
b) You install the MySQL before the myth-backend and not touch any of the configuration at this point.
c)  You use Mario's repository for 0.20 .debs.
d)  You install the basic setup first and make sure that you install ALL the dependencies and suggested packages (synaptic is your friend).
e)  go through the mythtv-setup screens very carefully
f) Start the backend before starting the frontend

It should then work.  It is not perfect (yet), but when it is up and running it is bloody brilliant.

Per lspci -v, I have 
0000:00:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR-350
        Flags: bus master, medium devsel, latency 32, IRQ 7
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2
and have wanted to make a dvr out of my ubuntu box ever since I installed my first linux distro ever about 6 months ago. Is there a particular guide that you can suggest for a linux newbie like myself that would result in a successful mythtv install? Also, I have already posted this in the forums 2 different times, but what would be the reason that sound is only coming out of the left speaker. They both work in winbloz xp. they both worked to start with but right around the time I used xvncviewer to control my ubuntu desktop running xmms using my xubuntu laptop wirelessly, the sound out of the right channel stopped working? The threads are both here, [http://ubuntuforums.org/showthread.php?t=242123&highlight=si7012](http://ubuntuforums.org/showthread.php?t=242123&highlight=si7012)
[http://ubuntuforums.org/showthread.php?t=250140&highlight=si7012](http://ubuntuforums.org/showthread.php?t=250140&highlight=si7012)

maybe you could help me troubleshoot this cause no one else else.

---

### Post by prizrak on 2006-10-19
> **DoctorMO said:**
> MythTV reminds me of windows, as long as everything isn't touched your ok and everything is done by an ultra slow screen.

I dumped it because tvtime has far better screen rendering abilities and delacing filters that don't need to be some how switched on by reading a ton of configuration.

The other problem is that I use MySQL for website development and yet MythTV wanted me to remove my databases, reinstall mysql just so I could get a default myself install... yep far too windows like.

Sorry but mythtv rates a 2/10.

Well it is a pretty ambitious project considering the amount of features it has and the quality of the artwork. It is also very immature and seems to be worked on by a very low number of people. I mean if you gonna compare HTPC software you can throw XP MCE in the mix, which happens to be a great product for what it does. If it weren't Windows it would have been awesome :)

---

### Post by dannyboy79 on 2006-10-20
> **lerrup said:**
> Well, I'm not sure what happened for you as I've just re-installed Myth on a Dapper setup without any big problems but lirc - but that's not Myth.

I would suggest that:
a) you make sure the cards etc are detected before the myth install
b) You install the MySQL before the myth-backend and not touch any of the configuration at this point.
c)  You use Mario's repository for 0.20 .debs.
d)  You install the basic setup first and make sure that you install ALL the dependencies and suggested packages (synaptic is your friend).
e)  go through the mythtv-setup screens very carefully
f) Start the backend before starting the frontend

It should then work.  It is not perfect (yet), but when it is up and running it is bloody brilliant.
Is there a particular guide that you can suggest for a linux newbie like myself that would result in a successful mythtv install?

---

### Post by PapaWiskas on 2006-10-20
Forgive me if I am missing something...but...

tvtime = TV viewer only NO RECORDING

MythTV = TV RECORDING and viewing

I would rather be able to record and I think the original author of this thread wants to as well.

So in actuality the two programs are not real similar in overall purpose.

---

### Post by awakatanka on 2006-10-20
I had a pain to get it to work with (k)ubuntu. I use mepis now and it was simply install ivtv from repo's and installed the new mythtv 0.20 and the depency's from the repo lines i found on this forum and everything working smooth. got a haupage pvr-500 with 2 tuners on it.

I watch TV on my laptop my main has the mythbackend and send it wireless to the laptop. I watch TV and the main record on the same time.

Planning what to record. 

I find it a great piece of work. Only thing i missing is that i can't play mp3's with my lapto that are on my main . (stream)

---

### Post by basketcase on 2006-10-20
> **awakatanka said:**
> I had a pain to get it to work with (k)ubuntu. I use mepis now and it was simply install ivtv from repo's and installed the new mythtv 0.20 and the depency's from the repo lines i found on this forum and everything working smooth. got a haupage pvr-500 with 2 tuners on it.

I watch TV on my laptop my main has the mythbackend and send it wireless to the laptop. I watch TV and the main record on the same time.

Planning what to record. 

I find it a great piece of work. Only thing i missing is that i can't play mp3's with my lapto that are on my main . (stream)
So you're saying that installing on Mephis is better than (k)ubuntu?  

What would be the difference?

---

### Post by M7S on 2006-10-20
I love mythtv. The startup time is quite slow but other than that it's wonderful. Automatic ad skipping and the posibility to sceduel from any computer using mythweb are especially nice features. It took a while to set it all up, but it has been well worth it.

I followed this guide when I installed [http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv](http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv) and it has been working great.

---

### Post by awakatanka on 2006-10-21
> **basketcase said:**
> So you're saying that installing on Mephis is better than (k)ubuntu?  

What would be the difference?
I had to follow guides to get it up in (k)ubuntu. And every guide was different none of them give me the total guide that was easy to work with.

With mepis i installed the ivtv deb and installed mythtv and it worked without big troubles. I didn't know there was a deb in first place so i started the way i did in kubuntu, but someone showed me the way.

---

### Post by DoctorMO on 2006-10-21
Perhaps we ort to make some kind of install script thing (sort of like atomix) but dedicated to mythtv. click language, click region, click tv channel package, click update every day from online, click put recordings here... etc etc.

---

### Post by basketcase on 2006-10-21
That'd work also, can we take it one step further, base it off of the server install, and let someone pick their desktop (xfce, gnome, kde, etc)?

---

### Post by atezun on 2006-10-21
The main problem I have with mythtv is that it's all well and fine when I just use it and nothing else on my machine. Unfortunately, I have only one computer, and whenever I try to set it up on my normal desktop it never seems to work.

---

### Post by M7S on 2006-10-21
> **atezun said:**
> The main problem I have with mythtv is that it's all well and fine when I just use it and nothing else on my machine. Unfortunately, I have only one computer, and whenever I try to set it up on my normal desktop it never seems to work.
Make a new user called mythtv, which you use for running the frontend. I have no problem running mythtv on my only computer.

---

### Post by lerrup on 2006-10-22
> **dannyboy79 said:**
> Is there a particular guide that you can suggest for a linux newbie like myself that would result in a successful mythtv install?

I've got dvb cards, which were straightforward to setup.  The Hauppage cards seem common, so I'd start with the guides reference from the ubuntu wiki and move on. The Myth wiki is also good for multimedia help.  

But your problem with sound seems fundamental.  Does it work properly playing music in ubuntu with a different player to xmms?

I'm no expert, but the above helped me.

---

### Post by basketcase on 2006-10-22
Well....I played with Reconstructor-2.0 today.  

I basically got an ISO to 830MB, and don't have a DVD burner, so no ISO yet.  

What I did see when I needed to edit /etc/modules there was nothing there.  So IVTV configuration may need to be done once something is installed, but I wonder if the rest of it would work? 

I'm out of town till Sunday, so I'm a sitting duck.  Anyone with experience with Reconstructor?  

Any advice/suggestions?  Creating a distro is something that is new for me.  I tried UCK, but was completely lost!  

The thing I don't like about Reconstructor, is it is for ubuntu (gnome), and I'd like to build it off of Xubuntu (or some other lightweight distro).  I'm also wondering if tossing in Automatix or something similar for a means to install nvidia/ATI/etc. easier.

---

### Post by basketcase on 2006-10-22
I also wondered about basing the install off of the server install, and during the install giving people the opportunity to choose what windowmanager (gnome, xfce, kde) they want to use.  

More researching I go...

---

### Post by Titus A Duxass on 2006-10-23
Basket Case - I agree 100% with (refering to first post). I tried the guides for Myth that can be found on/in this forum.

They do work, but must be followed to the letter.

There is a thead here that is supposed to describe how to with Dapper but it is so long (300 odd replies) that it is impossible to use.

I did, as you did, achieve a great deal of success with MythDora.  But the downside is that it only uses MythTV-0.19 and not 0.20.

I have a spare PC with a BT878 TV card in, I will start with an Xubuntu install at first.  I believe that a server install would lead to a lot of work.

---

### Post by basketcase on 2006-10-23
I'm working with an extra computer as well, so no worries on breaking it.  That is what it is there for.  

The post that is on this forum is what I'll be trying to go off of next, but like you said, so many pages/replies, it is hard to make heads/tails.  

I'll just take my time and start over, but like I said, out of town till Sunday.  

I'm using a PVR-350 card if it makes any difference.  I know in Mythdora everything worked.

---

### Post by basketcase on 2006-10-30
I played with Reconstructor over the week, but have not yet had a chance to test it on my testing box.  The one thing I don't like about it is it is for gnome, and I'd rather base it off of XFCE, but I'm watching their mailing list and there has been discussion regarding Xubuntu, so maybe soon.  I did try apt-get remove ubuntu-desktop, and per their mailing list, it seems that takes too many packages, not just gnome.  I was able to get Xfce window manager installed, just a matter of setting it as default when a person goes to run the Live CD or install.  The problem I also see is that a number of configuration files are written during/after the install which could affect the necessary files for Myth.  Something I'll have to explore more.  

Work is backed up to Wednesday, so no time till then to work on this further...just wanted to update this thread a little.

---

### Post by PapaWiskas on 2006-11-01
I for one would be very very happy if someone could make some sort of install script like automatix for MythTV on XFCE.

I love my Xubuntu very very much, and my OpenBox...

If I could somehow get Myth installed on Xu, that would be awesome.

I have tried reading through that thread on the Dapper install and I got lost, frustrated and gave up, it's too long.

---

### Post by basketcase on 2006-11-14
> **PapaWiskas said:**
> I for one would be very very happy if someone could make some sort of install script like automatix for MythTV on XFCE.

I love my Xubuntu very very much, and my OpenBox...

If I could somehow get Myth installed on Xu, that would be awesome.

I have tried reading through that thread on the Dapper install and I got lost, frustrated and gave up, it's too long.
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Follow the above...MUCH simpler.  I'm sure it will be a *little *different when you go to install a window manager, but don't know why you couldn't apt-get install xubuntu-desktop or something of the sorts to get it setup on Xubuntu.

---

