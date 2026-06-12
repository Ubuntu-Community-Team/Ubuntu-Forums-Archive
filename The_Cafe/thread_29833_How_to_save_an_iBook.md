---
title: "How to save an iBook"
date: 2005-04-26
forum: The Cafe
---

### Post by poofyhairguy on 2005-04-26
Introduction:  

When the original iBook was released back in 1999, its design was unlike any laptop on the planet. My father bought one in 2000 just because he was capivated by its looks and its promising technology. The iBook sported a 300 Mhz G3  (IBM's name-PowerPC 750) processor that I originally thought was too slow to be of use, but I have been known to be wrong about things (more on that later).  It was the first laptop I knew about to be wireless capable (802.11b) and this function, which can be achieved by purchasing an original Airport card, (expensive even today) is what makes this old laptop worth saving- besides its design of course! At the time the iBook caused a fuss by leaving out a floppy. Even though this sucked back when it was launched (no cd burner or other way to get data off besides networking), now cheap HUGE use pen drives make this no problem. The old iBook has a sturdy USB port!

It came with 3.2 gigs of hard drive space at first, which was so little that in Feburary 2000 Apple conceeded to demand and started shipping with 6 gigs. It also shipped with 32 Mbs of RAM, which even at the time was not much. So Apple upped this to 64 Mbs in Feburary as well. I am lucky enough to be working with    an iBook that was bought after Feburary (but the before the first big revision- the iBook SE). But my steps can revive any iBook, as these original specs can be upgraded.  The only major limitation of the iBook is the fact that its screen can only go to a resolution of 800x600. I have never heard of a successful hack to fix this and it would be hard to do. All clamshell iBooks are affected by this.  I have found ways to make this limitation tolerable to me.  After the iBook and the iBook SE, the Firewire iBooks came about in September 2000. These have more powerful processors, and the later models are the only iBooks of that design with a DVD player. History and specifications of the “Clamshell” iBooks can be found at 

[http://www.apple-history.com/](http://www.apple-history.com/)

this delightful site.

After my father bought an iBook in mid-2000, it quickly fell out of use because its operating system OS9 drove him crazy. I also disliked this predesssor to OSX, and so the iBook went into the room of my sister. She put up with his quirks and used it as a journal. My dad bought a Toshiba laptop soon after and never gave Apple another thought. I too only possessed IBM compatible computers since that iBook, but I always remembed its great design.

Fast forward to 2005. In the past few months, I have been using Ubuntu Linux on my desktop as a way to learn some Unix while improving my quality of life. I have had fun installing it on my desktop, my dad's old Toshiba laptop, and my girlfriend's new toshiba laptop. One day, when I was looking on the Ubuntu ftp server to download a development release, I noticed that Power PC install ISOs. I remebered that last time I read those words (in the iBooks documentation) and set about merging the two and Saving the iBook! My sister decied to give it up Easter 2005, knowing I would max it out. I promised to give it back to her when I'm done, but by then she might have a new iBook and won't care as much!

Why use linux: Apple fans probably wonder why I decied to use Linux on the iBook instead of Apple's most tasty OSX. Well, the honest answer comes like this:

1.Using Linux allows me to FINALLY directly compare x86 hardware and PPC hardware by using the same software on it! I was pleasantly suppreised.

2.I know now after reading many Minimac reviews that OSX really needs 512mb of RAM to run well, and I know from experience that Ubuntu in its default configuration can run very well in 256mb. The difference in price between the two sticks (and a new copy of OSX) is not worth it to me. Also, the 800x600 resolution is a limit no Clamshell can overcome, and Ubuntu has features that allow you use use maximum space (hiding toolbars, virtual desktops). If you wish to use OSX, just do the same thing I did but add another 256mb of RAM.

3.I really like Ubuntu. Ubuntu is free, and so are the applications that come with it. By default it gives you an office suit, a chat program, a web broswer. And thousands more programs are availible- fairly easy to install! Plus the community is really helpful, and the work is high quality. Yet you can use other versions of Linux if you like. Off the top of my head, Gentoo, Debian, Yellowdog and Kubuntu are Linux Distrobutions (or flavors) that have PowerPC versions. I recommend Ubuntu because it is easy, and its default install works great with the 
iBook!

Materials Needed to save iBook:

1.First thing you need is an iBook. They can be found on ebay (buyer beware) or they can be bought through resallers. Look in Google. Any Clamshell iBook will work, but you want a “Paris” one if you want thing like DVD playback and a faster CPU.
2.Secondly you need some more RAM. Badly. 256 MB is recommended, and Ubuntu REALLY likes that much in its default, and its not a lot cheaper than 128mb sticks. You could get a 512mb stick, and I would consider it if I had a DVD drive version.
 [http://www.amazon.com/exec/obidos/tg/detail/-/B00006BA04/002-6921306-6635265?%5Fencoding=UTF8&v=glance](http://www.amazon.com/exec/obidos/tg/detail/-/B00006BA04/002-6921306-6635265?%5Fencoding=UTF8&v=glance)

-Here is the stick I got, but a cheaper stick with the same specifications will work the same.
3.Thirdly you need a Power PC Ubuntu install CD. As of April 6, 2005, the current version is Hoary and that is what this writing is based on. Either download the ISO and burn it yourself using another computer, or <a href=http://shipit.ubuntulinux.org/>order for free a Power PC install CD</a>. The fact that Ubuntu ships free CDs is nice, but it takes a while.

Optional Materials:

4.Airport card for wireless. You need this to use the iBook's wireless network capacity. With this card, the iBook can become a wireless MP3 streamer, or a discussion piece at the local coffee shop (with wifi). 

[http://www.amazon.com/exec/obidos/tg/detail/-/B0000899ZD/002-6921306-6635265?%5Fencoding=UTF8&v=glance](http://www.amazon.com/exec/obidos/tg/detail/-/B0000899ZD/002-6921306-6635265?%5Fencoding=UTF8&v=glance)

I got mine here, but they can be found for cheaper on ebay. Be sure not to get an Airport Extreme card, they will not work at all...

5.New hard drive. This is by far the hardest thing to install. By FAR. But a newer hard disk (like 5400 RPMs at least), will speed up things (I think, I didn't get this). If you want to upgrade the harddisk before installing Ubuntu (or OSX or whatever), a href=http://www.pbfixit.com/Guide/49.13.0.html use this guide.

Steps to save the iBook:

First of all, you need to take the new RAM out of its package (and the airport card too if you got one) and 

[http://www.pbfixit.com/Guide/49.0.0.html](http://www.pbfixit.com/Guide/49.0.0.html)

install it as this guide shows how. Very nice guide, with pictures and all. Also install the hard drive at this stage if you got one.

Then you need to pluggin the iBook, and make sure it boots. It it did,  you installed everythign right. then open up the CD drive and put in the Ubuntu install CD. Reboot the iBook, and hold cmd-opt-shift-delete. If done correctly the Ubuntu CD will boot. Hit enter, then begin to answer the installer's easy questions. Just hit enter or yes if there is a question you doesn't know. The installer default are great!

It might take a while for Ubuntu to install instelf, and you must stick with it if you plan to fix this thing! After its done, it will boot into the login screen. Type in your user name and your password, and enter the Ubuntu desktop! 

I suggest hiding the panels when you do not need them, as that makes the 800x660 screen more tolerable. Also hit f11 in Firefox to use the fullscreen mode.

The only problems I've had are with Flash and windows media codecs. I use Firefox's 

[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

flashblock pluggin
to turn flash items into nice play buttons. Its sad you can't really use flash, but in all honesty I don't miss it much (its mistly used for ads on sites I visit).

The other problem is lack of window's media codecs. I try to convert files to OGG on my desktop if I want them on my iBook. Its not to big of a pain, hopefully I'll make a FAQ for it soon.

EDIT: I know this is about PPC, but I thought that section was mostly for help. Move if need be mods...

---

### Post by J D Wijbenga on 2005-04-26
Very interresting, thanks!

JD

---

### Post by tommyr on 2005-04-26
Funny you mention the ibook. I've tried the ppc liveCD on my 500mhz ibook with 320m RAM and it works GREAT. Now I just have to get the nerve up to install it. 

I'm writing this on my Dell 2200 from the Ubuntu live CD, slow but it works fine. Well, except for playing wmv files...

Tom

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=tommyr]Funny you mention the ibook. I've tried the ppc liveCD on my 500mhz ibook with 320m RAM and it works GREAT. Now I just have to get the nerve up to install it. 

I'm writing this on my Dell 2200 from the Ubuntu live CD, slow but it works fine. Well, except for playing wmv files...

Tom[/QUOTE]

look to the ubuntuguide for help with that.

---

