---
title: "Ubuntu is getting more and more horrible with everyrelease"
date: 2011-04-13
forum: Testimonials &amp; Experiences
---

### Post by mvalviar on 2011-04-13
I started with 8.04 and things are fine. I guess I don't have to complain about since I'm not familiar with it at all. Months passed and everything is cool. But as I upgraded with every release things started to look ugly.
[B]
Pidgin to Empathy[/B]

Why does ubuntu always making it a point to include half-baked apps? I thought ubuntu is supposed to include "the best the opensource community has to offer." Pidgin was booted but empathy is no where near the feature set of Pidgin. Empathy has been around for a long time yet when the icon blinks it still flashes a missing icon. I'm willing to move to empathy if I can import my pidgin logs but this feature is yet to be added to empathy.

**Notification Area, Indicator Applet**
Is it right click or left click? Some apps sit on the indicator applet some don't. So you have to have both applets on the panel. Problem is some apps require a right click to open their menu and some require a left click. You may choose to remove the indicator applet and the icons will all be on the notification area applet. You'd have to guess if it's a right click or left click. Grrr...

**Gwibber**
Gwibber is by far the worst application I've ever encountered yet it is shipped and integrated in the ubuntu desktop. If you ever plan to use it adding accounts is a pain. Plus it likes to sit on the background and use up 100% CPU. You can try to kill it but it starts up again. It's a big problem when your machine is running on batteries. Everyday notice the cpu fan going full throttle because gwibber is hogging the cpu. Removing it is a pain as well. I remember doing sudo apt-get remove gwibber and it wants to take the whole desktop along with it. Curses...

**Evolution**
Opening emails with attachments is a pain. The whole thing freezes. When you try to kill it and start it up again it picks up the same message and freezes again. The only way to fix it is to login to your email account via webmail and move the message somewhere else. 

**Next Release -- Global Menu Applet**

In line with the tradition of including buggy apps to releases the next release will include the global menu applet by default. I tried it. I doesn't work on firefox or any other non gtk app and it's quirky on some. If you try to remove it your apps will not have menus and you'd have to dig through gconf to bring those back.

Overall ubuntu is a fine desktop. But devs always make it a point to make non-linux enthusiasts say "yuck."

I guess I'll try kubuntu's next release since ubuntu will be even more frustrating in the next release.

---

### Post by mikewhatever on 2011-04-13
Replying to each point seems pointless, cause it would turn into an argument (probably will, regardless), so just an observation - if I had had your experience with Ubuntu, I would have switched a long time ago. Don't fight it, and love yourself a little.

---

### Post by XubuRoxMySox on 2011-04-13
It's so easy to remove apps which you think are lame and install ones you like!

And have a look at the other 'buntus while you're at it. Xubuntu ships with Pidgin and Thunderbird (try Seamonkey too!) and the standard Xfce equivalents to the Gnome apps you apparently despise. All the power of Ubuntu but with a sweet, lightweight interface and good ol' reliable, stable Xfce apps and gadgets.

-Robin

---

### Post by itisbasi on 2011-04-13
You could try an Ubuntu minimal install and add only those applications which you like...

---

### Post by KegHead on 2011-04-13
Hi!

It sounds like you would be happy w/Xunbuntu.

It's light weight and fast.

Try 10.10 and give it a solid chance.

I think you'll be happy with it!

Xunbuntu is my backup distro.

KegHead

---

### Post by Version Dependency on 2011-04-13
Install the Ubuntu Server Edition...all you will have after installation is the command line.  From there you can *sudo aptitude install* everything you want and nothing more.

---

### Post by 3Miro on 2011-04-13
Every distro that I have tried always came with a bunch of applications that I wouldn't want/need. They just stood there, while I installed the apps that I would use. I just ignore Evolution, Empathy and Gwibber (I have never seen your 100% CPU problem and I always keep an eye on my CPU with the applet; try troubleshooting, researching, uninstalling, asking for help on the help forum).

Eventually I fond two distros that wouldn't have this problem: Gentoo and Arch. Unfortunately, there aren't many people that can even install those two, much less run them. There are also plenty of people that can run those, but think they are too much hassle ... Use whatever Linux works for you and if you have bad default apps, just uninstall/ignore them, all the good apps are but a click away in the Software Center. (see above for Gwibber, which is the only "real" problem that I read)

Also, note that you are wrong about the global menu in Unity. There is a global menu, but there is also the standard categorized one, just right-click on the menu applet on the Unity dock (should be the icon right after "show all workspaces" and before "files and folders/external media/partitions" part).

---

### Post by kn0w-b1nary on 2011-04-13
I'd say give Xubuntu a shot. But then it comes with parole and exaile which I replace with VLC. Everything needs a little tweaking to be completely suited for YOU. Ubuntu out-of-the-box suits many people, but not all.

---

### Post by wolfen69 on 2011-04-13
> **Version Dependency said:**
> Install the Ubuntu Server Edition...all you will have after installation is the command line.  From there you can *sudo aptitude install* everything you want and nothing more.

No need for the server edition. There are 12mb iso's for cli installs. [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Then you won't have the server stuff installed.

---

### Post by cgroza on 2011-04-13
Try a different distro, it is not like you are stuck with Ubuntu.

---

### Post by 3rdalbum on 2011-04-13
> **mvalviar said:**
> 

**Notification Area, Indicator Applet**
Is it right click or left click? Some apps sit on the indicator applet some don't. So you have to have both applets on the panel. Problem is some apps require a right click to open their menu and some require a left click. You may choose to remove the indicator applet and the icons will all be on the notification area applet. You'd have to guess if it's a right click or left click. Grrr...

Notification area icons are inconsistent - some open with a left-click, some open with a right-click, some have left-clicks and right-clicks, some appear as GTK and some appear as Qt.

Indicators were invented to bring some consistency. If it's an indicator, it appears as GTK in Gnome or Qt if you're running KDE. All indicators work with left-clicks only.

And you'll be pleased to know that, with the Unity desktop in 11.04, the notification area has been well and truly depreciated. Only a couple of programs can display old-skool notification area icons anymore, the rest are now indicators or absent.

> **Evolution**
Opening emails with attachments is a pain. The whole thing freezes. When you try to kill it and start it up again it picks up the same message and freezes again. The only way to fix it is to login to your email account via webmail and move the message somewhere else.

Hmm... I haven't had this problem. Have you tried reporting this bug?

> In line with the tradition of including buggy apps to releases the next release will include the global menu applet by default. I tried it. I doesn't work on firefox

```
sudo apt-get install firefox-globalmenu
```

Questions?

---

### Post by Tamlynmac on 2011-04-14
> mikewhatever
Replying to each point seems pointless, cause it would turn into a  pointless argument (probably will, regardless), just an observation - if  I had had your experience with Ubuntu, I would have switched a long  time ago. Don't fight it, and love yourself a little. 	

Wow, all kidding aside - IMHO that is a great response.

It addresses the OP's statements as arguable opinion, without  participating. While noting that the odds are it will occur  "regardless". Ending your post with polite words of wisdom.

Since the T&E is theoretically a section of the forums designed to  promote members feedback (not debate) with respect to their experiences.  You made no effort to engage in argument with the OP or attempt to  provide support in a section that states it's not for that purpose. See  T&E header and this [sticky]("http://ubuntuforums.org/showthread.php?t=1343965").

Excellent post, for what it's worth.

Just my $0.02

---

### Post by pinballwizard on 2011-04-14
> **mikewhatever said:**
> Replying to each point seems pointless, cause it would turn into a pointless argument (probably will, regardless), just an observation - if I had had your experience with Ubuntu, I would have switched a long time ago. Don't fight it, and love yourself a little.


+1

Life's to short to fight, and especially to short to fight an OS. Find one that works. There are plenty of linux flavours, *BSD's, even Windows if that suits you better. Good luck.

---

### Post by mvalviar on 2011-04-14
Thank you for your insights. Yes I did file bug reports and a little googling long before but my evolution and gwibber problems never get solved.

[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/548540](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/548540)
[http://ubuntuforums.org/showthread.php?t=1608925](http://ubuntuforums.org/showthread.php?t=1608925)

Yes, I'm fine with ignoring apps I don't use. But I the case of gwibber. It runs on the background and hogs the CPU whenever he feels like it. Removing it wasn't all that easy too since it's tied to the desktop.

Adding the global-menu applet is just another big mistake. To make it work with firefox you'd need to install another package? How about for the other apps that doesn't work with it install packages for them as well? 

It's odd that ubuntu isn't a solid desktop system yet devs choose to put more features that will just be another source of bugs and confusion.

It just seems that the ubuntu user experience is just one of frustration unless you have a lot of patience. It's the #1 Linux distro but it's really not taking off because of these quirks.

---

### Post by coffeecat on 2011-04-14
> **mvalviar said:**
> Adding the global-menu applet is just another big mistake. To make it work with firefox you'd need to install another package?

Yes and no. My main Natty installation, which I installed early December around alpha 1 time, I missed out on the package firefox-globalmenu and had to install it myself. I have another Natty installation on a laptop that I installed from a daily live CD at around the alpha3 mark. That came with firefox-globalmenu - I didn't have to install it. So it seems that firefox-globalmenu comes in the box with a fresh install. I'm going to download the Beta2 once the rush is over and I'll test this.

Did you upgrade to Natty from an earlier release, or did you install it from an early alpha? Because if so, and based on my experience, the failure to include firefox-globalmenu in updates would appear to be a bug in the updates and needs to be reported as such (if not already).

---

### Post by tlcstat on 2011-04-14
Greetings,
My suggestion would be to download the four Debian install DVD's its only 16Gig and you should most certainly have the software you like somewhere in there [or not].  Gee! how can a 698Meg Ubuntu install compete with that!  Seems to me that the end user will have to open Synaptic and meet his needs [or not].   
tlcstat

---

### Post by 3rdalbum on 2011-04-14
> **mvalviar said:**
> Thank you for your insights. Yes I did file bug reports and a little googling long before but my evolution and gwibber problems never get solved.

[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/548540](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/548540)
[http://ubuntuforums.org/showthread.php?t=1608925](http://ubuntuforums.org/showthread.php?t=1608925)

I'm surprised the Gwibber problems haven't been addressed, and not so surprised that the Evolution problem hasn't been addressed.

> Adding the global-menu applet is just another big mistake. To make it work with firefox you'd need to install another package? How about for the other apps that doesn't work with it install packages for them as well?

What other programs? Firefox and Thunderbird require the extension because they're neither GTK nor Qt (Qt/KDE programs also use the global menubar by default). Libreoffice has an extension available too. Firefox and Thunderbird now ship with the extension enabled, and Libreoffice will have the extension in 11.10 (or you can use a PPA today). For anything else that can't use the global menu today, then you still get a menu in the window.

---

### Post by mvalviar on 2011-04-14
> **3rdalbum said:**
> ...For anything else that can't use the global menu today, then you still get a menu in the window.

That is my point. There are programs that doesn't work with that applet. When you're one of those apps you'd have to remember to find the menu  on the window and not the global-bar. Same problem with the indicator-applet/notification area issue in a word -- consistency.

Not only do users need to get used to the global-menu they have to get used to it not working on some apps.

---

### Post by d3v1150m471c on 2011-04-14
It'd make absolutely no sense for ubuntu to:
1.) Install every package in hopes the installation meets the demands of every end-user immediately
2.) Not make a decision as to what packages come as a default.

Personally, I don't like empathy nor unity...and I don't even use evolution. Problem? I think not:
```

sudo apt-get remove empathy evolution
sudo apt-get install blackbox pidgin

```There is not one OS on the planet that will meet the demands of every end-user out of the box. Thankfully, we're using Linux. We have the power to effectively and often easily modify things to our needs.

---

### Post by rabideau on 2011-04-14
I for one beg to differ... Ubuntu is not getting worse.  Natty runs better on my 6 different PC platforms then any release I have ever used before including Windoze.  Installing and uninstalling apps is not a problem.  You can test and use the ones you like best.  If all else fails you can work with developers to make certain they understand your needs/ desires.  Pretty cool stuff actually... or you could spend cash for those truly reliable Windoze apps or even more money to watch Apple adverts. 

Oh and if this distro doesn't work you, there are just a few others to select from...

---

### Post by wolfen69 on 2011-04-14
> **rabideau said:**
> I for one beg to differ... Ubuntu is not getting worse.  Natty runs better on my 6 different PC platforms then any release I have ever used before including Windoze.  Installing and uninstalling apps is not a problem.  You can test and use the ones you like best.  If all else fails you can work with developers to make certain they understand your needs/ desires.  Pretty cool stuff actually... or you could spend cash for those truly reliable Windoze apps or even more money to watch Apple adverts. 

Oh and if this distro doesn't work you, there are just a few others to select from...

I agree. One of the main reasons I use linux is because of all the choices I have. I wouldn't want it any other way.

---

### Post by fillintheblanks on 2011-04-14
Thats why I switched to Archbang. No more Ububloat for me :)

---

### Post by mvalviar on 2011-04-15
> **d3v1150m471c said:**
> It'd make absolutely no sense for ubuntu to:
1.) Install every package in hopes the installation meets the demands of every end-user immediately
2.) Not make a decision as to what packages come as a default.

Personally, I don't like empathy nor unity...and I don't even use evolution. Problem? I think not:
```

sudo apt-get remove empathy evolution
sudo apt-get install blackbox pidgin

```There is not one OS on the planet that will meet the demands of every end-user out of the box. Thankfully, we're using Linux. We have the power to effectively and often easily modify things to our needs.

It's not about satisfying the needs of every end-user. Its about selecting default apps that work. So gnome decided for empathy to be the default IM client. Ubuntu choose to do so as well even though clearly pidgin is better. They decided to include gwibber by default worse integrate it with the desktop when it has a nasty bug. Did it ever get fixed? No. Now that gnome is moving in another direction they decided to create unity.  Oh and since gwibber is taking up space they decided no to include GIMP by default. 

Yes, this is linux and we can do stuff but new users can't do much.

My point is ubuntu would be better if the devs decides on including better applications by default.

---

### Post by mvalviar on 2011-04-15
Sorry for the double post. I just want to conclude.

I didn't post here to start a flame. It says "Ubuntu Testimonials & Experiences" so I just posted what I think about ubuntu. I can always choose another distro if I don't like it and that's what I'm doing.

---

### Post by NightwishFan on 2011-04-15
> **mvalviar said:**
> Ubuntu choose to do so as well even though clearly pidgin is better.> 
Opinion (though fear not I happen to agree). Also Fedora chose to use Empathy by default as well. I think that perhaps Telepathy has more goals in line with the social focus of Ubuntu. It takes only a few minutes to download and install Pidgin.

[QUOTE]They decided to include gwibber by default worse integrate it with the desktop when it has a nasty bug. Did it ever get fixed? No.
Gwibber seems to work great for me, though I have little use for it. I am not much of a microblogger.

[QUOTE]Now that gnome is moving in another direction they decided to create unity.
I think it is a great opportunity. I happen to agree with what was said about more competition being good. Gnome 3 and Unity both are pretty awesome so far and I am willing to bet they will continue to do so. And also both be available. This goes a long way towards making Ubuntu more unique from Joe-Distro

> Oh and since gwibber is taking up space they decided no to include GIMP by default.
GIMP is not exactly the best piece of software for normal users. Granted I really liked it being included, though again, it is only a few clicks away. Default applications are impossible to cover the full range of tasks, so they have to include a decent base set of software.

> Yes, this is linux and we can do stuff but new users can't do much.
Ok. :)

> My point is ubuntu would be better if the devs decides on including better applications by default.
Certainly. However try to think about it from the perspective of the one who decides what goes into it. You have to sometimes modify packages to fit into the 700mb space, it has to cover a decent range of functionality, and you have to ensure most of it works well together. Seems like a job that is not to be underestimated.

> **mvalviar said:**
> Sorry for the double post. I just want to conclude.

I didn't post here to start a flame. It says "Ubuntu Testimonials & Experiences" so I just posted what I think about ubuntu. I can always choose another distro if I don't like it and that's what I'm doing.

Yes, you certainly can. I do not use Ubuntu myself either. Yet I still agree with and defend it because it does what it tries to do well in my opinion. I respect it.

---

### Post by azurehi on 2011-04-16
> **3rdalbum said:**
> Notification area icons are inconsistent - some open with a left-click, some open with a right-click, some have left-clicks and right-clicks, some appear as GTK and some appear as Qt.

Indicators were invented to bring some consistency. If it's an indicator, it appears as GTK in Gnome or Qt if you're running KDE. All indicators work with left-clicks only.

And you'll be pleased to know that, with the Unity desktop in 11.04, the notification area has been well and truly depreciated. Only a couple of programs can display old-skool notification area icons anymore, the rest are now indicators or absent.



Hmm... I haven't had this problem. Have you tried reporting this bug?



```
sudo apt-get install firefox-globalmenu
```

Questions?

I don't like the global menu in firefox4...will "sudo apt-get remove firefox-globalmenu"  get rid of it in the firefox4 installation in Natty?

---

### Post by howefield on 2011-04-16
> **mvalviar said:**
> Sorry for the double post. I just want to conclude.

I didn't post here to start a flame. It says "Ubuntu Testimonials & Experiences" so I just posted what I think about ubuntu. I can always choose another distro if I don't like it and that's what I'm doing.

Thank you for your testimonial, thread closed.

---

