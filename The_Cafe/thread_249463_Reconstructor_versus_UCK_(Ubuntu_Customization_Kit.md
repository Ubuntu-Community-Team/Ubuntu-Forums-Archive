---
title: "Reconstructor versus UCK (Ubuntu Customization Kit)"
date: 2006-09-02
forum: The Cafe
---

### Post by KermitJr on 2006-09-02
Ok guys... been awhile since I posted, but I'm interested.

 I'm wondering if many of you have compared these two programs for remastering.  Basically, I want to remaster one of the Live/Install CDs.  

Both seem to have some strengths/weaknesses.  I'm looking for fast and simple... preferably gui packagemanagement, etc.

Thanks and I'm looking forward to the debate!

KermitJr

---

### Post by KermitJr on 2006-09-29
Well, UCK doesn't seem to be working... and no support reply. A real shame since it looked best.

---

### Post by bertoldic on 2006-11-03
New release ok UCK is out!!!It seems it works!!! What we should do for suggesting canonical to let uck enter into the official repositories.It's a very useful tool!!!

---

### Post by 3rdalbum on 2006-11-03
Yes, but how does UCK compare to Reconstructor? I've used the latter and I was quite impressed.

---

### Post by sorcererx84 on 2006-11-03
There is very good guide about livecd customization [here]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e06"). It is written for Dapper, but I used it to build a custom Edgy livecd and it worked great.

---

### Post by bertoldic on 2006-11-04
Well I think that the guide is useful but softwares are great.I didn't know reconstructor. But which are the differences?

---

### Post by bertoldic on 2006-11-04
I've now tested also reconstructor! Reconstructor code is superior!
Clear and also modules are easily understandable.UCK has good the fact that it uses synaptic.

---

### Post by Rashid584 on 2007-01-01
does reconstructor work with kubuntu?

i looked at the site briefly and it appears that it only allows you to customise gnome splash screens etc. can you use it to change kde themes?

Also, how do you add software with uck? all i can see from the screenshots in the site is custom locale settings... :S

-Rashid

---

### Post by drbongo on 2007-10-01
I have been experimenting with both UCK and Reconstructor and they do have different strengths and weaknesses. Reconstructor offers a nice GUI and makes it easy to change the way your remastered CD looks! But I have had problems getting some of the modules to work. On the other hand UCK offers you the option of a Synaptic GUI which makes installing new apps a breeze! It would be nice if there was a tool that combined both of these features.

However in an very important respect they both do the same thing: Mount the LIve CD image in a chroot environment which allows you to change whatever you like. In order to do this you merely have to use the terminal to do things. e.g. you can type gnome-app-install into the terminal if you want to add remove programs with a simple GUI, or type alacarte if you want to change the menus etc. In other words you can do anything you can do to an installed version using either of these applications by simply loading the tools you want from the terminal. The only thing you cannot do is use these tools to escape from the chrooted environment. So if you want to add apps or files from your home drive you will need to open a normal terminal, type sudo nautilus and place them in the root folder of the chrooted directory.

If you want to add remove apps/files I would personally recommend UCK. If you want to change the way it looks use Reconstructor!

drbongo

---

### Post by pocketchange on 2008-06-06
Personally, I've used UCK (v2) and it works pretty well.  I wrote a few lines into my .bashrc so I have a function for "prep" and "function".  I use "prep" that unpacks the iso and preps it, then I do whatever customizations I want, then "package" to finalize and re-pack the iso.  It breaks things down into 2 steps rather than 4, which I find simplifies UCK advanced configurations.  I had to have a preseed file so I had to have an alternate install disc, which I know UCK handles, but I'm not sure if Reconstructor does.  

Bottom line, if you need to add packages, you can always use UCK to collect all the packages into a folder for you, then just grab them all out and put them in whatever your favorite LiveCD creator is.  I would at least use uck to grab all the .debs.

---

### Post by benner on 2008-08-14
i used remastersys and it was a piece of cake. worth trying. just one command, i think it was, and that was it.

---

### Post by ingo on 2008-11-19
remastersys has never worked for me. God knows what it does with the dist option.

UCK is a very useful tool as it handles all the locale stuff perfectly, guiding one around potential pitfalls! It also gives one access to the chroot environment which is all I need :)

reconstructor would be a nice tool for gnome if it worked properly in its entirety. Some modules like the usplash one required that the image was pre-built - in itself quite a task. At least a help file would have been useful. And of course it cannot work for Kubuntu.

This article is quite nice if you want to know what happens behind the scenes or want more control about where to stick your remastering environment ;) 

[http://www.linux.com/feature/137524](http://www.linux.com/feature/137524)

---

### Post by red_team316 on 2008-11-21
ingo: 
That's not neccessarily correct. You can use reconstructor with Ubuntu/Kubuntu/Xubuntu/etc...What you cannot do currently is customize the KDE and XFCE desktop environments. Although if you know how to use kwriteconfig, then customizing KDE is not a problem.

---

### Post by ingo on 2008-11-22
Cheers red_team316,

perhaps I phrased it in too blanket a way. Indeed one can change anything for Kubuntu on the command lline, incl. KDM. But then again you might as well not use reconstructor in the first place.

As great a tool as it is for gnome it was not written for KDE (sadly :(). BTW, is there something in the pipeline?

---

### Post by red_team316 on 2008-11-22
Yes there is, chrooted Xnest/Xephyr is in development although not finished yet, and when it is stable enough for testing, the user will need to use the -e(experimental switch). In theory it should work with all desktop environments. My testing has been on KDE so far though. Finding the time to finish it is the hard part :/

I was working on KDE customization long ago but dropped it when I realized that it would be too complex to encapsulate every aspect of KDE into a GUI and that a Nested X environment would be much more beneficial.

---

### Post by Riffer on 2008-11-22
I've had great luck with remastersys.  Great tool for building a OS from the ground up and also for backing up your system.

---

### Post by ingo on 2008-11-22
> **red_team316 said:**
> Yes there is, chrooted Xnest/Xephyr is in development although not finished yet, and when it is stable enough for testing, the user will need to use the -e(experimental switch). In theory it should work with all desktop environments. My testing has been on KDE so far though. Finding the time to finish it is the hard part :/

I was working on KDE customization long ago but dropped it when I realized that it would be too complex to encapsulate every aspect of KDE into a GUI and that a Nested X environment would be much more beneficial.

That is good news indeed! Thanks for sharing that :) I've been playing around a lot with remastering Kubuntu including doing something like reconstructor but came to the same conclusion as you - Xnest is the only way forward for a gui experience. Mind, how are you going to use Xnest? Is it possible to run an entire new KDE instance in it which you can then clean up and dump into /etc/skel? I'll be looking out for that one.

Keep up the good work.

---

### Post by red_team316 on 2008-11-22
/etc/skel is what I've been toying with so far. Forget copying it over, the $HOME will be /etc/skel.

Customizing /etc/skel isn't always the best option in several cases so later on I'd like to try to add the option to have it modify the default configs somehow. Not quite sure how that would be handled since GNOME/KDE/XFCE are all different. Not to mention customizing some program settings really has nothing to do with /etc/skel or the users home directory. So it will take some thought as to whether it is practical or not...

It's funny that I've been noticing little bugs within k/ubuntu from hardy on. Such as in Hardy(8.04) for some reason, the / directory appears on the desktop even though when opening the file browser the home is set correctly. Also I've noticed some other bugs that do not allow you to log out if you are in a fullscreen chroot(not using Xnest or Xephyr). Fullscreen chroot also can cause some graphical problems depending on your gfx card. Most of these bugs have made me lean toward Xnest/Xephyr as default. Plus, it's nice as you can keep on working on other things while it's running. There are many pluses.

---

### Post by ingo on 2008-11-23
> /etc/skel is what I've been toying with so far.Same here. It works a treat as far as I'm concerned although it does add to the overall size of the iso.

> Not to mention customizing some program settings really has nothing to do with /etc/skel or the users home directory.Hm, I can't think of any examples here. You can theme firefox, add extensions, change openoffice, all kde apps - everything afaik - and it will remember how it looked and behaved in ~. So copying ~ to /etc/skel does work. Or what is it you are referring to?

Unfortunately I cannot confirm any of the bugs you are experiencing. My 8.04 was and my 8.10 is running as smoothly as a baby's bottom :)

---

### Post by red_team316 on 2008-11-23
Everytime a new user is added, that directory is copied over and over. It's unclean. Not to mention it will take up extra space unneccessarily.

Also, every user added may be able to see files information that the person customizing did not intend for them to see. Such as a browsing history... 

Every single KDE(and I'm pretty sure GNOME works this way too) configuration option found in ~/.kde can be found or added to the default config files.

Keeping things clean is the goal.

-----

I haven't tried out the new usb-creator at all, but I've heard that remastersys breaks it somehow. I've always viewed remastersys better as a backup utility rather than a LiveCD creator. It's just not practical for me to do a fresh install just to customize it and then back it up.

-----

The logout bug can only be seen in a fullscreen chroot. Again, this may have to do with gfx cards causing the display to hang. Sometimes it doesn't but it almost always tends to end up with a reboot.

Graphical glitches in fullscreen chroot. This is directly influenced by your graphics card. Trust me, if you've got a fancy driver loaded, most likely it's not going to work 100% correctly as Xorg isn't configured yet nor is there a module in the chroot kernel.

Fullscreen chroot in Intrepid boots great, one big problem though, you have no keyboard and mouse lol. This IS a bug in Intrepid, see this:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/271138](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/271138)

Attached is a screenshot of the odd hardy chroot bug. Whatever caused it must have been fixed for intrepid. It's present on 8.04 as well as 8.04.1.

---

### Post by ingo on 2008-11-25
It has taken me some time and you may already be aware of this site, but have a look: [http://docs.kde.org/stable/en/kdebase-runtime/userguide/kde-for-administrators.html](http://docs.kde.org/stable/en/kdebase-runtime/userguide/kde-for-administrators.html)

BTW, of course, dumping stuff in /etc/skel is unclean and wastes space, no two ways about it. Rather the quick and dirty option :) and I'm glad I found the above link for KDE. But how about firefox or openoffice? Any pointers there?

I've used Xnest successfully on tty8 - it is handy for checking immediately on changes made to KDE's core. 

I'd be happy to discuss more ways of freeing space, customisation of usplash, splashy, grub or gfxboot but am off for a week now (with only very intermittent internet access). Perhaps a new thread? If so, please point to it here :)

---

### Post by red_team316 on 2008-11-26
I am very interested in any usplash customization ideas you may have for usplash/bootsplashes. I'm very familiar with usplash and C/C++ programming. If you haven't tried my parallax usplash(link in sig), please do as it is very different than 90% of the usplashes I've seen.

One thing I have not figured out yet is how to customize Xephyr's window title such as you can do with Xnest...

Just fire up adept, and find the firefox package, and go to details, then you can see a list of every installed file. Some I saw in the /etc directory look possibly useful. First thing I do when I have a question about a package is find out what files are installed where, regardless of if man says they dont exist.

ingo, let us continue this discussion here. It seems as though you have much knowledge that may benefit many other than me.
[http://ubuntuforums.org/showthread.php?p=6253629#post6253629](http://ubuntuforums.org/showthread.php?p=6253629#post6253629)

---

### Post by ingo on 2008-12-11
Done, I've finally replied :) Please forgive the long delay!

---

