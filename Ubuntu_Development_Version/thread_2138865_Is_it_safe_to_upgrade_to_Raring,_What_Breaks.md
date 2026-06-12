---
title: "Is it safe to upgrade to Raring, What Breaks ??"
date: 2013-04-25
forum: Ubuntu Development Version
---

### Post by tlan on 2013-04-25
just backed up my home and ready to upgrade but i know something is going to break and i just got 12.10 to be stable

Does anyone have any feedback,

does it break conkycolors
cairodock
 should we change theme to default
Nvidia driver issues
disable thiurd party ppa's 
etc

any advise or issues encountered would help all of us.

---

### Post by pqwoerituytrueiwoq on 2013-04-25
if you have a nvidia gpu, use the mainline kernel
relevant thread
[http://ubuntuforums.org/showthread.php?t=2138590]("http://ubuntuforums.org/showthread.php?t=2138590")

when i upgraded i used the Debian method, changing the sources to point to raring
i did not disable any ppas (getdeb/medibuntu)
i just made them point to raring (if they exist yet, if not leave then on qunatal)
0 issues with upgrading, but i did it during the beta phase
if you upgrade now, just install the mainline kernel 3.8.8 or 3.9 rc8 (my install script makes this easy, see above)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/) (all .deb and the 2 ending in amd64 or i386, depending on 64bit or 32bit install)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.8-raring/) (all .deb and the 3 ending in amd64 or i386, depending on 64bit or 32bit install)

---

### Post by tlan on 2013-04-25
i updated my nvidia drivers to 319.12 via xorg-edgers ppa which also updated my kernel to 3.7.0.7
using 12.10 64bit btw

xorg does have sources for raring already so i think i am ok there.

---

### Post by pqwoerituytrueiwoq on 2013-04-25
the bug is on the 3.8.0-19-generic kernel (stock on raring)
xorg edgers has a raring source

---

### Post by tlan on 2013-04-25
Well Excellent, so far not one issue with my upgrade, i only had to re-enable my third party ppa's, update and upgrade and reinstall xscreensaver,

using kernel 3.8.0-19 and Nvidia driver 319.12

There is the totem full screen issue which will be patched eventually, no big issue and several PPA's that need to update there sources for Raring.
also the lock/switch account function does not appear to work, locking my screen via xscreensaver and custom Ctl-Alt-L shortcut

so far so good, and this OS is much more snappier, apps do load much faster.

---

### Post by Rob Sayer on 2013-04-26
Tried the official release from live usb stick yesterday.  Installed it on my netbook early this morning.

I've been eagerly awaiting 13.04 because the netbook doesn't nvidia but the notorious cedarview graphics.  The drivers weren't moved into the kernel proper until 3.7.  I actually tried the alpha 2 and beta versions before.  Which is quite unike me.  I'm conservative with repos and in windows I wouldn't generally install beta app software, let alone the OS.

While I'm not saying there aren't any bugs, it seems to work a lot better than 12.04.  The video I expected, but the wireless (broadcom 4313) seems to work better than it ever did before.

So I'm quite happy.  There may be some bugs ... there usually are ... but at least they don't try to hide linux bugs from you.  Unlike some other OS's I could mention.  And they do pretty much get fixed in timely fashion.

It's always a good idea to make a list of all your devices and search for related bugs in ubuntu.  The only thing about that is, if you search the web for someone having a problem with something you're going to find it.  I've usually found that those problems had been fixed by the time I installed ubuntu on the machine.

---

### Post by bluepicaso on 2013-04-26
here is my story, is downloaded the 64bit 13.04 ISO from ubuntu website. All checksum matched, vaerified, made a USB with UNETBOOTIN, 
gave me damn error it was something like "Partman error.... exit code 10"
made a DVD, 
started boot from CD/DVD
it showed ubuntu loading with dots and then black screen with flickering cursor.

so ended up with installing 12.04.

this reminds me of 11.10 crap
now i am really sad.

---

### Post by Carl H on 2013-04-26
any reports of any ATI driver issues?

---

### Post by fragtion on 2013-04-26
[rebooting 13.04 fails]("http://ubuntuforums.org/showthread.php?t=2139160") for me since 'successful' upgrade from 12.10 - drops to management console requiring hard-reset. anyone else with this problem / know a workaround ?

---

### Post by Frogs Hair on 2013-04-26
A friend upgraded a Wubi installation and did the usual disabling of 3rd party software . This upgrade was via the update manager and there were something like 800 + package replacements. disable suspend and keep the monitor on . Don't be tempted to use the computer while upgrading this will reduce the chance of freeze. It takes a long time to replace and set up packages and this is the first time I have watched the process which worked. A clean installation takes less time but it's not for everybody.

---

### Post by kevpan815 on 2013-04-26
If you have an Unstable 12.10, than I personally recommend a Clean Install of 13.04. Just my 2 cents.

---

