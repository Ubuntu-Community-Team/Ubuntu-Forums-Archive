---
title: "Anybody dual booting Debian and Ubuntu?"
date: 2017-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by yoshii on 2017-10-15
I'm currently in the process of fixing up a fresh Debian install.  
Is anybody dual booting Debian and Ubuntu?  

What are your experiences with Debian?  
How do you feel about the similarieties and differences?

---

### Post by yetimon_64 on 2017-10-15
Yes I'm currently triple booting with Trusty, Xenial and Debian Stretch.

I have found installing nvidia drivers much harder on Stretch than on Trusty or Xenial to the point where I have dumped them altogether and gone with the nouveau drivers only in Stretch, though I do have hybrid graphics (intel/nvidia). I have tried the "bumblebee" packages etc with no luck at all.

No matter what graphics drivers I use in Stretch (nvidia or nouveau) I seem to have a constant problem with lightdm dumping me back to the log in screen which can get pretty annoying when it starts playing up. No such problems with the nvidia drivers or lightdm in either Ubuntu installs. I have tried to install gdm instead of lightdm in Stretch but it just won't seem to take; I haven't been able to fix that hassle yet, but am still trying.

Apart from the graphics drivers I don't find much in the way of differences between the systems, at least not that I've noticed as yet.

I have in the past dual booted debian wheezy and ubuntu trusty on a non hybrid graphics desktop with no problems at all. May have to set up a dual boot on my desktop tower as well to see if it is hardware specific (I suspect it may well be so here).

Cheers, yeti.

---

### Post by Tadaen_Sylvermane on 2017-10-16
I run both in my laptop. Generally logged into Debian, haven't heard as much as a whisper from it, just works. When I run Ubuntu I usually get some type of errors popping up. Last time I ran Ubuntu Gnome it had an uptime of 6 days until I tried to open Minecraft, full hard lock of the system. Back to Debian I went. I use Ubuntu for my server, I'd call it bulletproof for that purpose. Gui stuff is where the problems I have come from so I stick with Debian for that.

---

### Post by yoshii on 2017-10-16
Thanks for the replies.  It's odd and almost interesting how so many of us get such widely different results.  
I had an extremely horrible time with the Debian so-called graphical installer.  It even claimed it didn't have the wifi driver even though it was clearly in the same DVD-ROM because that's what I used to test with!  (the LiveDVD couldn't find it's own wifi driver!)

After I finally got it installed after literally the worst install experience of my adult life, it ran OK and seemed mostly nice and minimal.  But I must say that there was WAY too much international support stuff installed, and it lacked english for some stuff though it had polish and french and tons of asian stuff installed.  I don't mind that there was support for blind people too.  But I didn't request any of that stuff and my local is US-eng.  so it was frustrating.  

Then today, I was busy upgrading and downloading basic stuff and I had to quit because it told me it was going to pretty much REMOVE everything that I wanted just because I wanted to install LMMS.  So the dependency hell is an issue.  

I gave up.  LMMS and VLC media player aren't in competition but Debian or apt seems to think they are.  
And I don't know why they don't install file-roller instead of xarchiver and gdebi instead of having to rely blindly upon dpkg.  it's odd.  

But I was thankful that it had 7zip support out of the box.  

But I also hit the wall trying to install wine of any type.  In Xubuntu, it was a lot easier.  I depsise Ubuntu's installer but Debian's was a lot worse.  Lubuntu's text-based installer is pretty good though.

---

