---
title: "Can't seem to remove wine"
date: 2006-08-30
forum: Repositories &amp; Backports
---

### Post by Zoglarfy on 2006-08-30
Okay, I'm trying to get wine installed properly in order to run WoW.  I have all the guides and everything, but the problem is that had I initially installed a version of wine that was too old.  The later versions of wine will work, but not the one I have.

So, I *thought* that I had removed the older version, then used Synaptic to install the newer version.  But everytime I run wine, it still sees the old version.  Doing "wine --version" ALWAYS lists the wrong version.

I guess what I'm asking is, how the heck do I REALLY get rid of the old version?  I notice that it still has files in the /usr/locab/lib directory.  I'm afraid to just go on some mad deleting spree without really knowing how I'll affect the system.

Thanks for the help! And sorry for the total newb question.  I know; can't even uninstall programs?  Yeesh... :rolleyes: :D

---

### Post by Anonii on 2006-08-30
I guess you installed them with APT, right?

Can you paste the output of:
_sudo apt-get remove wine_
please?

---

### Post by Zoglarfy on 2006-08-30
> **Anonii said:**
> I guess you installed them with APT, right?

Can you paste the output of:
_sudo apt-get remove wine_
please?
Unfortunately, apt-get doesn't recognize it as an installed package.  Neither does Synaptic or dpkg.

:confused:

---

### Post by Zoglarfy on 2006-08-30
Heh.  Forgot to post the output of "sudo apt-get remove wine".  :rolleyes:

> Reading package lists... Done
Building dependency tree... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 171 not upgraded.


---

### Post by Anonii on 2006-08-30
So, you compiled wine from a tarball?
Never really interested in source installs, afaik the only way to fully uninstall it is to find that wine folder in which you installed it from and execute:
"sudo make uninstall".
But there may be another way too :/

Well, its not good to install things in APT or any package-manager based systems from the source without using "check install" or anything :/

---

### Post by Zoglarfy on 2006-08-30
Hmm... looks like I did.

That sounds weird, but I've reinstalled an uninstalled wine so many times that I've forgotten what I initially did! :) 

However, it looks like you're right.  I found the guide I first used and it looks like I *did* compile from a tarball.  I completely forgot.  Doing a "make uninstall" did the trick.  

Boy, nothing like switching from Windows to Linux to make you feel like a computer illiterate again.  :rolleyes: :-D 

Thanks for your help, Anonii!  :)

---

### Post by rocketsami on 2010-12-16
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)  <<<<------use this link then i are okay ,you will remove

---

