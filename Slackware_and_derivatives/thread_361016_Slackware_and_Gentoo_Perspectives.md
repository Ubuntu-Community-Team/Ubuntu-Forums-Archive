---
title: "Slackware and Gentoo Perspectives"
date: 2007-02-13
forum: Slackware and derivatives
---

### Post by OlineSixtyOne on 2007-02-13
Hello everyone. I am a current Xubuntu Edgy user and I am contemplating a switch to Slackware Linux. 

First off, a brief history of my Linux experience. I started with SuSE Linux on a suggestion from a friend and successfully used it for about 2 weeks before I decided it was too much like Win XP to be worth permanent use. After that I looked for a new disto on my own and found Ubuntu. I installed Ubuntu Warty (IIRC) and used it for quite some time, learning how to get around in Linux using the terminal and whatnot. I upgraded to Breezy when it came out and used it for another while. 

After spending some time with Breezy I decided I wanted to try something more advanced. I grabbed a Gentoo Minimal Install CD and followed the guide, configured my own kernel manually and had a successful install. Feeling very proud of myself, I used Gentoo for a month over the summer when I had plenty of time to maintain it. I eventually decided that maintaining Gentoo would be too time consuming to use it during the school year, and I switched back to Ubuntu Dapper (IIRC). From that point I moved to Xubuntu Edgy and here I am today. I enjoy XFCE much more than GNOME. It feels much snappier to me. 

Although I like Xubuntu more than Ubuntu, I still want more simplicity. That brings me around to Slackware. I haven't actually done any research on it myself, but I know it follows the KISS philosophy, and is one of the oldest remaining distros. I understand it will be more work than Xubuntu. I would like to see it put in perspective with Gentoo. Is it more work? Does it take as long to install as Gentoo?

Thanks for your time and assistance,
OlineSixtyOne

---

### Post by tubasoldier on 2007-02-13
I like Slackware a lot! The only reason I am not using it is because it is not as supported as Ubuntu is. The amount of packages available is much less than that of other major distros. 

Instead of Slackware I would direct you towards [Arch Linux]("http://www.archlinux.org"). It would be more along what you want. I think. Arch is source based, like Slackware. It is community driven, and has tons of packages available. It is also a rolling distro like Gentoo. So you always have the newest version. But unlike Gentoo it is much easier to maintain because you dont have to compile all your software.

---

### Post by OlineSixtyOne on 2007-02-13
Arch Linux looks very interesting. I will most certainly give it a shot (hopefully this weekend). It sounds like it might be a winner for me. I'll keep this thread updated with my impressions. Until then I am open to suggestions on what else to try.

Thanks for your help,
OlineSixtyOne

---

### Post by pcalvert on 2007-02-14
You should probably also consider Zenwalk and Vectorlinux (the "standard" version).  Both are based on Slackware, and use Xfce.

I'd also like to mention a distro that is not based on Slackware:  Debian.  :)
Seriously, I think you should also give Debian testing, aka "Etch" (at the moment) a try.  I have noticed, from reading the Debian forums, that many people who started with Ubuntu and eventually became dissatisfied with it have switched to Debian and are quite happy that they did.

Phil

---

### Post by manmower on 2007-02-14
> **tubasoldier said:**
> Instead of Slackware I would direct you towards [Arch Linux]("http://www.archlinux.org"). It would be more along what you want. I think. Arch is source based, like Slackware.
Neither Arch nor Slackware are source based, they both use binaries, although they do allow for easy compiling (especially Arch). I would wholeheartedly recommend Arch though. It's what I use.

---

### Post by OlineSixtyOne on 2007-02-14
> **pcalvert said:**
> You should probably also consider Zenwalk and Vectorlinux (the "standard" version).  Both are based on Slackware, and use Xfce.

I'd also like to mention a distro that is not based on Slackware:  Debian.  :)
Seriously, I think you should also give Debian testing, aka "Etch" (at the moment) a try.  I have noticed, from reading the Debian forums, that many people who started with Ubuntu and eventually became dissatisfied with it have switched to Debian and are quite happy that they did.

Phil

I never actually thought of trying out Debian, surprising as that may seem. Can I install it with XFCE as the default environment? If I can then it will certainly get installed and tested. 

Now Zenwalk and Vectorlinux are two distros I haven't heard of. I'll give their websites a browse and see if they are what I'm looking for. 

Thanks for the suggestions,
OlineSixtyOne

---

### Post by pcalvert on 2007-02-14
> **OlineSixtyOne said:**
> I never actually thought of trying out Debian, surprising as that may seem. Can I install it with XFCE as the default environment? If I can then it will certainly get installed and tested. 


Yes, you can set up Debian just about any way that you want.  The installer won't automatically do it for you, though.  The way I would do it is to first do a "server install"-- I'd choose "mail server" when that choice is offered by the installer.  I'd also tell the installer to set up the mail server for localhost since I only need local mail and don't want anyone on the Internet to be able to connect to it.  When the installation is finished, you'll have a very basic system-- everything must be done from the command line.  You'll then need to log in as root and use aptitude to install xfce.

If the above hasn't scared you off, I'll see if I can find some instructions or tutorials with better details for you. :)

Phil

---

### Post by OlineSixtyOne on 2007-02-14
> **pcalvert said:**
> Yes, you can set up Debian just about any way that you want.  The installer won't automatically do it for you, though.  The way I would do it is to first do a "server install"-- I'd choose "mail server" when that choice is offered by the installer.  I'd also tell the installer to set up the mail server for localhost since I only need local mail and don't want anyone on the Internet to be able to connect to it.  When the installation is finished, you'll have a very basic system-- everything must be done from the command line.  You'll then need to log in as root and use aptitude to install xfce.

If the above hasn't scared you off, I'll see if I can find some instructions or tutorials with better details for you. :)

Phil
That actually sounds ideal to me. After my experiences with Gentoo I'm quite comfortable booting to a bash prompt and getting X and a desktop environment running. I think I actually like this approach to installation better because you can have everything you need and nothing you don't. 

Debian and Arch are both looking pretty good right now. Trying out two new OSes will give me a great excuse to sit in front of the computer instead of study :).

Thanks for the help everyone,
OlineSixtyOne

---

### Post by pcalvert on 2007-02-16
Okay, here are some links to more information, some of which doesn't relate directly to Xfce, but *is* related to setting up a Debian system:

[HOWTO: Install X Window System and a Desktop Environment]("http://forums.debian.net/viewtopic.php?t=12256")
[http://forums.debian.net/viewtopic.php?t=12256](http://forums.debian.net/viewtopic.php?t=12256)


[GuNNiX's GNU/Linux Debian]("http://users.skynet.be/six/gpure/tech/linux/debian.html")
[http://users.skynet.be/six/gpure/tech/linux/debian.html](http://users.skynet.be/six/gpure/tech/linux/debian.html)


Also, consider IceWM as a lighter alternative to Xfce:

[HOWTO: IceWM Basic Configuration]("http://forums.debian.net/viewtopic.php?t=5450")
[http://forums.debian.net/viewtopic.php?t=5450](http://forums.debian.net/viewtopic.php?t=5450)

NOTE:  Where you see "apt-get" in tutorials, you should replace that (most of the time) with "aptitude" if you are setting up a new system, and use it from then on.  However, if you've been using apt-get on your current system, don't switch or you may end up with a broken system (see [Tips on using aptitude]("http://forums.debian.net/viewtopic.php?t=4180")).


Now, here's how *I* would install Xfce on Debian:

First, like I said above, I'd do a "server install" of Debian, setting up a mail server for local mail only (server listens on localhost only).

Next, I'd log in as root.

Finally, I'd use aptitude to install the "X Window System" and Xfce:

Install the "X Window System":
**# aptitude install x-window-system-core**

Install the Debian menu:
**# aptitude install menu**

Install Xfce:
**# aptitude install xfce4 xfce4-goodies**


Since I started with Knoppix and got used to using KDE, I like to use some KDE applications under other window managers, so I would also install part of KDE:
**# aptitude install kdebase kdm**

If you like GNOME applications, you could do this instead:
**# aptitude install gnome-core gdm**

If you don't install either kdm or gdm, then you'll probably want to install xdm:
**# aptitude install xdm**


After I finished installing packages using aptitude, I would log out and then log back in under my regular (non-root) user ID.

Then I would start X11:
**$ startx**


If everything worked right, I should then get a GUI login window.

Well, that's enough for now.  I think you should be able to take it from here.  :)

Phil

---

### Post by OlineSixtyOne on 2007-02-16
Thanks very much. Those aptitude commands will be very helpful. Hopefully Debian should be going up tonight after school.

---

### Post by RAV TUX on 2007-02-18
> **OlineSixtyOne said:**
> Hello everyone. I am a current Xubuntu Edgy user and I am contemplating a switch to Slackware Linux. 

First off, a brief history of my Linux experience. I started with SuSE Linux on a suggestion from a friend and successfully used it for about 2 weeks before I decided it was too much like Win XP to be worth permanent use. After that I looked for a new disto on my own and found Ubuntu. I installed Ubuntu Warty (IIRC) and used it for quite some time, learning how to get around in Linux using the terminal and whatnot. I upgraded to Breezy when it came out and used it for another while. 

After spending some time with Breezy I decided I wanted to try something more advanced. I grabbed a Gentoo Minimal Install CD and followed the guide, configured my own kernel manually and had a successful install. Feeling very proud of myself, I used Gentoo for a month over the summer when I had plenty of time to maintain it. I eventually decided that maintaining Gentoo would be too time consuming to use it during the school year, and I switched back to Ubuntu Dapper (IIRC). From that point I moved to Xubuntu Edgy and here I am today. I enjoy XFCE much more than GNOME. It feels much snappier to me. 

Although I like Xubuntu more than Ubuntu, I still want more simplicity. That brings me around to Slackware. I haven't actually done any research on it myself, but I know it follows the KISS philosophy, and is one of the oldest remaining distros. I understand it will be more work than Xubuntu. I would like to see it put in perspective with Gentoo. Is it more work? Does it take as long to install as Gentoo?

Thanks for your time and assistance,
OlineSixtyOne

Wolvix Hunter is by far the single best Slackware based distro....Zenwalk is a close second but needs a bit of work.

If you want to try Gentoo, start with Sabayon, if you can't stomach a DVD install, start with the Sabayon mini-edition

---

### Post by OlineSixtyOne on 2007-02-25
Alright everyone, sorry I've neglected to update this thread for so long. I decided to go with Arch first instead of Debian, and I'm still using it. I installed the base system then slapped XFCE on it. After installing Mplayer, Java, and a few other miscellanies I found myself with a fully functional OS. My total combined uptime with Arch is probably around 96 hours now. I've got almost everything working the way I want it too, and don't forsee changing soon. This was supposed to just be an exploratory test install, but I'm hooked now.

OlineSixtyOne

---

