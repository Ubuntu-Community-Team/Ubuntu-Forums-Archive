---
title: "Lubuntu 13.10 beta 1 installation review"
date: 2013-09-12
forum: Ubuntu Development Version
---

### Post by santosh83 on 2013-09-12
Hello all,

After sticking with 10.10 long beyond its EOL I finally decided to try the latest and greatest Ubuntu. Due to a low memory (for these days!) system I decided to give Lubuntu 13.10 beta 1 a spin.

There were three major problems I encountered during installation.

Just after selecting the language in the installer a welcome windows appears and tells me that I need at least 4.7 Gb disk space to install Lubuntu and also need a working Net connection. As I have disk space that field is 'ticked' while the row indicating whether a Net connection is up is marked with a 'cross.'

Now I have a DSL connection and obviously the installer has no idea of the username/password to establish the dial-up, and hence no connection. But the unhelpful thing here is that the installer does nothing after telling me of that. Ideally the Network connections window (or wizard) should appear and it should ask the person if they want to configure a Net connection. After making it sound as if a Net connection is essential to complete the install (which it is not I think) the installer simply gives up when it doesn't detect one already up.

So I'd to open a terminal, do 'sudo nm-connections' to configure the DSL details before proceeding. A average Joe wouldn't know about this?

The second major error was the formatting step of the root partition simply crashed after I instructed the installer to use btrfs as the filesystem. If it isn't supported yet, it should degrade gracefully, not crash with a message saying "formatting error or Partition so and so" and lock-up the whole machine as well, needing a hard reboot. The second time around I selected ext4 for the root FS and things proceeded without problems.

Finally after the install was done and a message popped up asking me to remove the CD, the process froze there again. Once more I'd to manually reboot.

PS. Another thing. The system asked before the partitioning stage whether I wanted to upgrade the Ubuntu 10.10 system already existing on disk. Correct me if I'm wrong, but isn't upgrading possible only between successive releases??

---

### Post by sudodus on 2013-09-12
1. I think you spotted some new bugs in the installer. It would help improving 13.10, if you report these problems as bugs at Launchpad :-)

2. What about the Lubuntu 13.10 beta 1 system, once you had it running? I guess you might have found both good and bad things. How does it play with your hardware?

---

### Post by santosh83 on 2013-09-12
> **sudodus said:**
> 1. I think you spotted some new bugs in the installer. It would help improving 13.10, if you report these problems as bugs at Launchpad :-)

Okay but is there any specific section on Launchpad that I should create the bug report in?

> 
2. What about the Lubuntu 13.10 beta 1 system, once you had it running? I guess you might have found both good and bad things. How does it play with your hardware?

Yes. When PCManFM fails to mount a volume due to authentication failure (I'd cancelled giving it the password), it'll crash when I close it later. This happened repeatedly.

Also when a window is close in a virtual desktop, the pager still shows it as open in the small 'square'... Only when I navigate to the other virtual desktop, or open another window that this 'square' representing an already closed window disappears.

No reliable way to make nm-applet show up in LXPanel it seems. I added it manually by typing 'nm-applet' in terminal, but it disappears once I log out.

Also after a bit of fiddling around with LXPanel by adding applets and removing them, the Panel crashed and restarted. But can't reproduce that again so far.

And the menus in evince (Document Viewer) are horribly deviating from the default Lubuntu theme. They are black in background with text in dark gray. Unusable.

Finally a random single character on the screen is often "garbled"... this is redrawn when I move a window over it or minimise and maximise the window, but until then this character stays garbled. Guess it's a bug in font rendering?

I'd appreciate it if someone points me to a document explaining how I can create bug reports and where I should create it for problems in Lubuntu 13.10 beta. When the crash reporter automatically opens then it's simple, but what if I want to sumbit a bug which crash reporter doesn't detect?

---

### Post by sudodus on 2013-09-12
You need a user-ID at Launchpad, if you want to write personal notes describing each bug, not only send the automatic text. I think that when apport is started manually, it is important to write personal notes. This is the way to tell the developers about the bug.

Use
```
apport-bug <package-name>
```
For the installer (if you used the desktop iso) you can try with
```
 apport-bug ubiquity
```
and for pcmanfm
```
apport-bug pcmanfm
```

You are also welcome to take part in the beta testing and report your results for the daily build at

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

### Post by santosh83 on 2013-09-12
> **sudodus said:**
> You need a user-ID at Launchpad, if you want to write personal notes describing each bug, not only send the automatic text. I think that when apport is started manually, it is important to write personal notes. This is the way to tell the developers about the bug.

Use
```
apport-bug <package-name>
```

You are also welcome to take part in the beta testing and report your results for the daily build at
[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

Thanks, I already have a Launchpad account and have submitted bug reports on the btrfs formatting crash, obconf crash and mismatching menu colours in evince.

The daily build testing seems an involved process! I'll read those instructions and see if I can cope with it. :-)

---

### Post by sudodus on 2013-09-12
If you want more personal discussion and feed-back, there are also email discussion forums for Lubuntu at 

<lubuntu-qa at lists.launchpad.net> and <Lubuntu-users at lists.ubuntu.com>

---

### Post by cariboo on 2013-09-12
I install different distributions on my netbook all the time without a network connection, as it needs bcmwl driver. The only thing that doesn't get installed are the language packs. You'll get notification to install them, as soon as you have a working network connection, after the installation has been finished.

---

