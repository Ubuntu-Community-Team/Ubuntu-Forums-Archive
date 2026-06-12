---
title: "EnergyXT 2.5 problem"
date: 2010-04-28
forum: Ubuntu Studio
---

### Post by gnerdman on 2010-04-28
I'm trying to start up EnergyXT 2.5 on a Eee PC 1001P running Ubuntu Studio 9.10. Startup fails with:

X Error of failed request: BadImplementation (server does not implement operation)

It lists Op Codes and serial numbers, then:

X Error of failed request: BadDrawable (invalid Pixmap or Window Parameter)

Then another list of Op Codes and serial numbers. It seems to be a common enough error, with the KVR forum suggesting an edit of /etc/X11/xorg.conf with the following:

Section "Extensions"
    Option         "MIT-SHM" "no"
EndSection 

Unfortunately, there is no xorg.conf anywhere on the box. What's the cure? Thanks in advance.

---

### Post by sgx on 2010-04-28
> **gnerdman said:**
> I'm trying to start up EnergyXT 2.5 on a Eee PC 1001P running Ubuntu Studio 9.10. Startup fails with:

X Error of failed request: BadImplementation (server does not implement operation)

It lists Op Codes and serial numbers, then:

X Error of failed request: BadDrawable (invalid Pixmap or Window Parameter)

Then another list of Op Codes and serial numbers. It seems to be a common enough error, with the KVR forum suggesting an edit of /etc/X11/xorg.conf with the following:

Section "Extensions"
    Option         "MIT-SHM" "no"
EndSection 

Unfortunately, there is no xorg.conf anywhere on the box. What's the cure? Thanks in advance.
Try the windows EXT2.5 using wine and wineasio. It has worked for me in several distros, with the standard non-dongle/pace/ilok vst plugins.

If you absolutely want or need a linux version, you can get xorg.conf examples to copy/edit by google matching your video card/chip and monitor
names like this (put the main video in quotes):

"nvidia 6600" samsung syncmaster-456 xorg.conf example

/etc/X11/xorg.conf is where it often goes, maybe a slightly different path
in your linux.

Cheers :)

---

### Post by gnerdman on 2010-04-28
> **sgx said:**
> Try the windows EXT2.5 using wine and wineasio. It has worked for me in several distros, with the standard non-dongle/pace/ilok vst plugins.

If you absolutely want or need a linux version, you can get xorg.conf examples to copy/edit by google matching your video card/chip and monitor
names like this (put the main video in quotes):

"nvidia 6600" samsung syncmaster-456 xorg.conf example

/etc/X11/xorg.conf is where it often goes, maybe a slightly different path
in your linux.

Cheers :)

Thanks sgx. I'd prefer to use the Linux version just on matters of principle.  ;-)  What's got me boggled is that I can't imagine how the desktop is working *without* an xorg.conf. I did a find from /, and there isn't one anywhere on the system. How can gnome run at all without it?

---

### Post by angelsguitar on 2010-07-09
I realize the last post on this thread was a while ago, but I just stumbled on it.  Did you solved the issue?

By the way, recent versions of the X server don't need the xorg.conf anymore, as it handles X configuration by other means.  That's why you won't find a xorg.conf file on modern Linux distros.  However, if needed for any reason (like in this case), you can use one - Xorg doesn't need the xorg.conf file, but will used if it finds it on /etc/X11/.  You can search the Internet for examples of standard xorg.conf files. Then, just copy the found xorg.conf file to /etc/X11/ and add the modification mentioned on the KVR forums.  That should take care of the problem.

---

