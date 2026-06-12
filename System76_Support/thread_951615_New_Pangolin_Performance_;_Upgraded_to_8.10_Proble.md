---
title: "New Pangolin Performance ; Upgraded to 8.10 Problems"
date: 2008-10-18
forum: System76 Support
---

### Post by gbutler69 on 2008-10-18
Hello All,

I just purchased my third laptop through System76, a Pangolin Performance. It came with Ubunutu 8.04 64-Bit pre-installed.

After receiving it, the first thing I did was to upgrade to Ubuntu 8.10. After doing so, I am experiencing the following problems:

    1. Upon first rebooting after the upgrade, the xorg.conf was messed up and it went into screen recover mode. After examining the errors and looking at the xorg.conf file, I found that the upgraded had commented out the device section for the synaptics touch pad, but, left the reference to the commented out section in the "ServerLayout" section. I fixed that and managed to boot up to the desktop with full graphics enabled.

    2. Now, when I try to run firefox or epiphany, it fails. When I run firefox from the command line, I get the following:

```

gbutler@ubuntu:~$ firefox
Couldn't load XPCOM.
gbutler@ubuntu:~$ 

```    So, I looked at why I might be getting this error and tried:

```

gbutler@ubuntu:~$ xpcshell-1.9 
xpcshell-1.9: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
gbutler@ubuntu:~$ 

```    OK, now this tells us something. So, I did a search for "libmozjs.so"

```

gbutler@ubuntu:/$ sudo find ./ -type f -name "libmozjs.so"
./usr/lib/xulrunner-1.9.0.3/libmozjs.so
./usr/lib/xulrunner-1.9.0.1/libmozjs.so
gbutler@ubuntu:/$ 

```    Ah-ha! So it's there, but, not in the library path. So, I next did the following:

```

gbutler@ubuntu:~$ export LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.0.3/
gbutler@ubuntu:~$ firefox

```    BAM! That works! OK, so the problem is with an incorrectly configured installation of "xulrunner". NOTE: Epiphany Webkit version works correctly obviously.

    I've searched the forums and Google and see no evidence that this problem is being experienced in general. Is anyone else seeing this issue? I just upgraded to 8.10 last night (October 17, 2008 at around 9:30 PM EDT).

    3. The other problems I am seeing after the upgrade are as follows:

        3.1. "Cheese" no longer works. Seems to be having trouble seeing the camera. Haven't been able to get to the bottom ofthis yet.

        3.2. On "shutdown" the screen does a weird sort of thing with a splotchy dimming area on the screen and then stays white and the laptop doesn't power down. I have to turn the power off.

        3.3. Sounds is awfully quiet, even with the volume control turned all the way up.

The main thing I want to understand are whether these issues are:

    1. Pangolin specific problem/related

    2. Ubuntu 8.10 Beta general problem that others are having

    3. Something I've done wrong

Please Help!

Kind Regards,

Gerry B.

---

### Post by thomasaaron on 2008-10-18
Thanks. We're not quite there with testing 8.10 on the Pangolin.
I'll keep an eye out for those things when we get to them.

---

### Post by AlchemyMan on 2008-11-02
Hey, 

Just wanted to add my voice to this. I am having the same problems with both Firefox and cheese. The sound seems ok (I haven't checked that thoroughly, but it sounded fine to me on login) and the shutting down is fine (except it seems I now have to log out first and then shut down, which is a bit annoying but which I take to be something to do with Intrepid). 

So yeah. I'm having the same issues after the upgrade.

My model code is panp4n.

---

### Post by Lee_Machine on 2008-11-02
I was having the same problem with cheese on the Pangolin also. Model# Panp4n.

Upon the upgrade to 8.10.

My main problem is the occasional system freeze.

I was going to just do a fresh down grade to the 8.04LTS but I get that annoying busybox error.

I dont know about sound as I didnt use it before upgrading but it does seem low. I figured it was the speakers.

---

### Post by roscoetuff on 2008-11-02
I have an FL90... whatever animal that is. Upgraded to 8.10 when I kept getting the triangle that SYSTEM76 driver was out of date. Regrets? Yes.

Firefox is basically non-functional. Freezes. Stinks. Am trying Opera which is much, much faster now, but I get no sound with it.
Tried loading 8.10 on a Dell... that doesn't even get to opening screen and just freezes.... kind of like Firefox only worse.

So the FL90's a good machine. The operating systems is... well... I'm thinking about junking the whole Linux thing and going with a Mac. They just work.

---

### Post by Derath on 2008-11-03
> **Lee_Machine said:**
> I was having the same problem with cheese on the Pangolin also. Model# Panp4n.

Upon the upgrade to 8.10.

My main problem is the occasional system freeze.

I was going to just do a fresh down grade to the 8.04LTS but I get that annoying busybox error.

I dont know about sound as I didnt use it before upgrading but it does seem low. I figured it was the speakers.

Lee: Download the 8.04.1 release disk, iirc the original 8.04 had boot problems.

---

### Post by Lee_Machine on 2008-11-03
> **Derath said:**
> Lee: Download the 8.04.1 release disk, iirc the original 8.04 had boot problems.

That is the only image available at the ubuntu web site.  8.04.1

Same busy box error.

but thanks man

---

### Post by thomasaaron on 2008-11-03
> 3.1. "Cheese" no longer works. Seems to be having trouble seeing the camera. Haven't been able to get to the bottom ofthis yet.

Cheese is broken in Intrepid.

> 3.2. On "shutdown" the screen does a weird sort of thing with a splotchy dimming area on the screen and then stays white and the laptop doesn't power down. I have to turn the power off.

Not seeing that on shop machines. Probably a hosed config somewhere during the upgrade. Have a look in /var/log/syslog and /var/log/messages. Can you see what the messages are when it fails to shutdown?

> 3.3. Sounds is awfully quiet, even with the volume control turned all the way up.

Double-click the speaker icon, click the Preferences button, and make sure all of the checkboxes are selected. Then make sure the Master, PCM and Front sliders are not turned down too low.


```
2. Ubuntu 8.10 Beta general problem that others are having
```

Are you really running the Beta version? If so, that's probably your problem. You should be running the final version.

---

### Post by roscoetuff on 2008-11-03
Cheese - don't use it. Don't know it. Okay.. it don't work with Intrepid. Fine.

Now about Firefox.... slower than molasses... so slow... you can read the Sunday NYTimes, work the cross word puzzle and still drink three cups before it's ready to freeze up on the next site load. Tried deactivating all the "add ons". No improvement. Whatever the issue is... it's not obvious.

But then Opera is very,very fast. Can't hear a thing on any web videos... and no sound period through this browser or Firefox on Intrepid... when the same worked fine on Hardy. So this is a new problem.

What about down grading until this so-called release version is ready for primetime? Where do I learn to do that?

Thanks for the help in advance.

---

### Post by nadamsieee on 2008-11-05
I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/294247](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/294247)

As a workaround, I created a launch script and edited the launcher on the panel to use it:

```
$ cat bin/myff

#!/bin/bash
export LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.0.3
/usr/lib/firefox-3.0.1/firefox.sh
```

Note that firefox-3.0.**1** seems more stable.

---

### Post by nadamsieee on 2008-11-06
It looks like the original poster found another clue/work-around here:

[http://ubuntuforums.org/showthread.php?t=951659](http://ubuntuforums.org/showthread.php?t=951659)

```
$ ls -l /etc/gre.d/
total 12
-rwxr-xr-x 1 root root 76 2008-07-28 16:56 1.9.0.1.system.conf.bak
-rwxr-xr-x 1 root root 76 2008-09-25 07:24 1.9.0.3.system.conf
-rwxr-xr-x 1 root root 68 2008-06-10 14:03 1.9.system.conf.bak
$ sudo mv /etc/gre.d/1.9.0.1.system.conf /etc/gre.d/1.9.0.1.system.conf.bak
$ sudo mv /etc/gre.d/1.9.system.conf /etc/gre.d/1.9.system.conf.bak
```

Now I can start firefox without using the work-around script above.

---

### Post by gbutler69 on 2008-12-19
As a follow-up to my earlier post (see below), please enjoy:

Firefox/Epiphany borked/broken by latest Firefox 3.0.5 Upgrade on Ubuntu 8.10 Intrepid Ibex!

Yes, the problem is back! Firefox and Epiphany were both broken by the latest Firefox upgrade on December 18, 2008 @ approximately 7:00 PM EST.
When try to run Firefox, would get the following:

```

gbutler@ubuntu:/etc/gre.d$ firefox
Couldn't load XPCOM.

```
and Epiphany would get the following:

```

gbutler@ubuntu:/etc/gre.d$ epiphany
** (epiphany-browser:10803): WARNING **: Could not startup XPCOM glue!

```

Now, after examining the contents of the /etc/gre.d I made a "leap of faith" and did the following:

The contents of the folder after the update were:

```

gbutler@ubuntu:/etc/gre.d$ ls -al
total 28
drwxr-xr-x   2 root root 4096 2008-12-19 00:01 .
drwxr-xr-x 153 root root 8192 2008-12-18 23:00 ..
-rwxr-xr-x   1 root root   76 2008-07-28 16:56 1.9.0.1.system.conf
-rwxr-xr-x   1 root root   77 2008-12-18 23:58 1.9.0.3.system.conf
-rwxr-xr-x   1 root root   77 2008-12-18 23:48 1.9.0.4.system.conf
-rwxr-xr-x   1 root root   76 2008-12-16 18:32 1.9.0.5.system.conf
gbutler@ubuntu:/etc/gre.d$ 

```

So, I edited the 1.9.0.3.system.conf and made it point to the 1.9.0.5 lib path as follows:

```

gbutler@ubuntu:/etc/gre.d$ cat 1.9.0.3.system.conf 

[1.9.0.3]
GRE_PATH=/usr/lib/xulrunner-1.9.0.5
xulrunner=true
abi=x86_64-gcc3

gbutler@ubuntu:/etc/gre.d$ 

```

Then, I did the same for the 1.9.0.4.system.conf as follows:

```

gbutler@ubuntu:/etc/gre.d$ cat 1.9.0.4.system.conf 

[1.9.0.4]
GRE_PATH=/usr/lib/xulrunner-1.9.0.5
xulrunner=true
abi=x86_64-gcc3

gbutler@ubuntu:/etc/gre.d$ 

```

This fixed the problem. This seems to be a problem with the packaging of Epiphany/XULRunner/Firefox for Intrepid x86_64.

I don't think this is the correct fix, merely a work-around to make Epiphany and Firefox work after the Firefox 3.0.5 upgrade.

The package maintainers are going to need to fix this I imagine.



> **gbutler69 said:**
> Hello All,

I just purchased my third laptop through System76, a Pangolin Performance. It came with Ubunutu 8.04 64-Bit pre-installed.

After receiving it, the first thing I did was to upgrade to Ubuntu 8.10. After doing so, I am experiencing the following problems:

    1. Upon first rebooting after the upgrade, the xorg.conf was messed up and it went into screen recover mode. After examining the errors and looking at the xorg.conf file, I found that the upgraded had commented out the device section for the synaptics touch pad, but, left the reference to the commented out section in the "ServerLayout" section. I fixed that and managed to boot up to the desktop with full graphics enabled.

    2. Now, when I try to run firefox or epiphany, it fails. When I run firefox from the command line, I get the following:

```

gbutler@ubuntu:~$ firefox
Couldn't load XPCOM.
gbutler@ubuntu:~$ 

```    So, I looked at why I might be getting this error and tried:

```

gbutler@ubuntu:~$ xpcshell-1.9 
xpcshell-1.9: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
gbutler@ubuntu:~$ 

```    OK, now this tells us something. So, I did a search for "libmozjs.so"

```

gbutler@ubuntu:/$ sudo find ./ -type f -name "libmozjs.so"
./usr/lib/xulrunner-1.9.0.3/libmozjs.so
./usr/lib/xulrunner-1.9.0.1/libmozjs.so
gbutler@ubuntu:/$ 

```    Ah-ha! So it's there, but, not in the library path. So, I next did the following:

```

gbutler@ubuntu:~$ export LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.0.3/
gbutler@ubuntu:~$ firefox

```    BAM! That works! OK, so the problem is with an incorrectly configured installation of "xulrunner". NOTE: Epiphany Webkit version works correctly obviously.

    I've searched the forums and Google and see no evidence that this problem is being experienced in general. Is anyone else seeing this issue? I just upgraded to 8.10 last night (October 17, 2008 at around 9:30 PM EDT).

    3. The other problems I am seeing after the upgrade are as follows:

        3.1. "Cheese" no longer works. Seems to be having trouble seeing the camera. Haven't been able to get to the bottom ofthis yet.

        3.2. On "shutdown" the screen does a weird sort of thing with a splotchy dimming area on the screen and then stays white and the laptop doesn't power down. I have to turn the power off.

        3.3. Sounds is awfully quiet, even with the volume control turned all the way up.

The main thing I want to understand are whether these issues are:

    1. Pangolin specific problem/related

    2. Ubuntu 8.10 Beta general problem that others are having

    3. Something I've done wrong

Please Help!

Kind Regards,

Gerry B.

---

