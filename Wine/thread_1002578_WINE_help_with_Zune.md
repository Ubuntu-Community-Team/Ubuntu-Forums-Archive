---
title: "WINE help with Zune"
date: 2008-12-05
forum: Wine
---

### Post by mollydoggy1971 on 2008-12-05
Could someone please assist me in how to get WINE to work?  I know NOTHING about Linux, so I'll need very detailed instructions as to how to get something to work.  I specifically want to make my Microsoft Zune software to work under Ubuntu.  I work nights, so I won't be able to post until about 4am Central time daily.  Thank you in advance for your help!

---

### Post by Grolsche on 2008-12-05
is wine already installed or are you asking for help on how to install it?

If it's installed, then we would need a bit more information on what you mean by "how to get wine to work".

---

### Post by jocheem67 on 2008-12-05
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

The official documentation regarding wine in ubuntu....

If you are really new to ubuntu/linux, I suggest you leave using wine for the moment. Aren't there equivalents to your needed windows-software in the repo's???
That would be the easiest and safest way, when you're a 'new kid on the block'......

Ahhhhh, it's about the zune, hmmmm....don't know 'bout that device to b honest.
Googling suggsta you need to connect the zune in a virtual environment, that is some advanced stuff....

---

### Post by mollydoggy1971 on 2008-12-06
> **jocheem67 said:**
> [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

The official documentation regarding wine in ubuntu....

If you are really new to ubuntu/linux, I suggest you leave using wine for the moment. Aren't there equivalents to your needed windows-software in the repo's???
That would be the easiest and safest way, when you're a 'new kid on the block'......

Ahhhhh, it's about the zune, hmmmm....don't know 'bout that device to b honest.
Googling suggsta you need to connect the zune in a virtual environment, that is some advanced stuff....

I don't know if there is a Linux equivalent to the Microsoft Zune software.  How would I go about finding out that information?  I Googled how to use WINE, but I don't understand a lot of what I've read.  I think as I learn more about Ubuntu I'll understand more, but I was hoping someone could give me a quick step by step on how to do it for this one program.  I get the feeling it may not be quite that easy though :(

Jeff

---

### Post by p_quarles on 2008-12-06
Moved to the Wine area. 

Getting Wine to work correctly can be difficult, but the initial step is pretty easy: make sure Wine's installed, then go to the installation media and right-click the install file. It should give you the option to "Run with Wine."

If it works very well with Wine, it will start installing. If it works anywhere between not-at-all and okay with Wine, you'll have to jump through more hoops to find out exactly which end of the spectrum it's on.

---

### Post by russofris on 2008-12-06
I would like to save the OP some time.

winehq.org has an applications database where users can report whether software works with wine, how well,, and things like version and installation steps.   Unfortunately, it does not appear that the Zune software is installable.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13795&iTestingId=31356](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13795&iTestingId=31356)

Save yourself some time.  Give up on wine/zune for the time being, bookmark the appdb and check back periodically, and begin your quest for an alternative audio manager.  I believe Amarok with a newish libMTP may work

[http://ubuntuforums.org/showthread.php?t=316246](http://ubuntuforums.org/showthread.php?t=316246)


Another option is virtualization:
[http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php](http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php)

Frank

---

### Post by stinger30au on 2008-12-06
dunno if this will help you any, but you may be better to load up virtual box and insall your copy of xp or vista in to it and setup your zune in xp in virtual box

wine is a marvellous bit of programming, dont get me wrong, but it does have some short falls with some programs

---

### Post by mollydoggy1971 on 2008-12-07
> **russofris said:**
> 

Another option is virtualization:
[http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php](http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php)

Frank

This appears to be doable...but how do I find VMware?  It's not in my list of programs in Ubuntu.  Is this something I'd need to download and install from somewhere else?  If so, how do I install software in Ubuntu that's not in the list?

Jeff

---

### Post by mollydoggy1971 on 2008-12-08
> **mollydoggy1971 said:**
> This appears to be doable...but how do I find VMware?  It's not in my list of programs in Ubuntu.  Is this something I'd need to download and install from somewhere else?  If so, how do I install software in Ubuntu that's not in the list?

Jeff

Anyone?

---

### Post by jocheem67 on 2008-12-09
Being new to ubuntu, installing vmware is a big step. If you really need to use virtualization, it may be better to go for virtualbox. This is in the repo's and is not likely to **** up your system, I feel. 
You should ofcourse check if your zune works with virtualbox, ie usb-connections.

It's been a while since I used it.

---

### Post by deputy on 2008-12-17
I have been able to successfully use Zune software inside virtual XP with VMWare Server 2.0. VMWare Server 2.0 supports USB 2.0 which is a big plus. I am able to sync music, vids, pics, use marketplace, update firmware, etc. Only thing I haven't tested is wireless sync. I own an 80gb Zune btw. First thing you need though is a copy of XP on a cd. Second you need to install VMWare Server 2.0. What version of Ubuntu do you have and is it 32-bit or 64-bit? Go here for a how-to install vmware server 2.0 in ubuntu intrepid. Should also work for older versions of Ubuntu. [http://maketecheasier.com/how-to-install-vmware-server-20-in-ubuntu-intrepid/2008/11/18](http://maketecheasier.com/how-to-install-vmware-server-20-in-ubuntu-intrepid/2008/11/18)

Let me know how it goes.

---

