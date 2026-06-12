---
title: "Can't boot, plymouthd crash"
date: 2015-11-08
forum: Ubuntu Studio
---

### Post by tbrann2 on 2015-11-08
Hi

I used a program called Ubuntu Tweak to clean up my system, and it must have removed some important stuff, because now ubuntu won't boot anymore. Here's a link to a post with the exact problem: [http://ubuntuforums.org/showthread.php?t=1847297](http://ubuntuforums.org/showthread.php?t=1847297). I tried to do what is suggested in this thread, but it won't work. 

It is ubuntu studio with the KX studio repos. (Should I ask there..?)

---

### Post by ajgreeny on 2015-11-08
It is impossible to know if that answer helped or not as the OP did not say.

What part of what is suggested did not work?

Can you boot to recovery mode from grub, then use command ```
mount -o rw,remount /
``` to mount the filesystem as read/write and then try installing, or reinstalling if already installed, the following packages, which is a list in part from my Xubuntu 14.04.:-
libplymouth2
plymouth
plymouth-label
plymouth-theme-ubuntustudio
These may be the correct packages for Ubuntustudio, which I know uses xfce and I hope will solve your problem.

You could also try hitting "E" key when the grub menu appears, navigating to the line where "quiet splash" is shown and deleting those two words, then Ctrl+X to boot.  As that removes the splash screen from the boot process you may be lucky, but I am not sure if plymouth is needed even in a text style boot.

---

### Post by tbrann2 on 2015-11-09
Well, I pressed ctrl+alt+f6 and then: 
 sudo apt-get install plymouth-theme-ubuntu-text

That did not work.

Those packages were already installed, so I tried to reinstall them, but that didn't work either. still the same message: 
Could not start boot splash because can't access a needed shared library 

What does "mount -o rw, remount" do? 

I've also tried to remove "quiet splash" and that results in a blinking cursor..... 

BTW, I forgot to mention that I also  have XP and Linux Mint on this computer.

---

### Post by ajgreeny on 2015-11-09
Where were you in the boot process when you used the Ctrl+Alt+F6, as if you managed to get there you must have been able to boot?  I am confused about what exactly is happening.  Did you use that in recovery mode?  Not needed if you did.

The ```
mount -o rw,remount /
```command re-mounts the root filesystem as read/write, allowing commands issued in recovery mode to write to the system and make edits to files.  By default recovery mode mounts it as read-only and therefore changes can not be made without that remount command.

If you did not run it or if you missed the final / as you show it in post #3, it will not have worked, and the installation or reinstalation of any plymouth packages will have failed.

---

### Post by tbrann2 on 2015-11-09
I'm sorry, i'm confused and to be honest, I don't really know what I'm doing....

After the message "could not start...." a blinking cursor appears. If I then  press Ctrl+Alt+F6, I get "computers name bla bla  login:"
From there I can somehow log in to a terminal (i think...) and do commands.

I did try the mount remount from recovery mode too with the same result as before.

---

### Post by deadflowr on 2015-11-09
Perhaps a better alternative to the mount command would be to first run the networking option that is listed in recovery mode's menu.
When you do this it automatically resets the system to read/write, so no need to invoke said mount command.
then try
```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```
since this environment is root, no need for sudo.
It is also quite possible that it'll output errors, in which case try
```
apt-get install -f
```
It's a long shot, though.

You might also look at your apt log files which should tell you what packages where removed, if any.
I suggest using tail and/or less to view the log file
somethings like
```
tail /var/log/apt/history.log <<<this will show the end section of the log file, which has the most recent activity.
less /var/log/apt/history.log <<< shows the whole log file, but starts at the top and you can simply press the enter to move down; q to quit
```
Not that any of this will help but they could...

---

### Post by tbrann2 on 2015-11-09
When rebooting without "quiet splash", I managed to see some text flashing by, it can't find a shared file: libGL.so.1
Tried "sudo apt-get install libGL.so.1", but it couldn't find such a package...?

---

### Post by deadflowr on 2015-11-09
the libGL.so.1 is part of a package, not a an actual package, so to speak.
It's in libgl1-mesa-glx
```
sudo apt-get install libgl1-mesa-glx
```

---

### Post by tbrann2 on 2015-11-10
Ok, I'm starting to think that I've misunderstood the whole thing, and that it actually DOES boot, just without desktop.

So, I tried to install libgl1-mesa-glx, but it was already installed. Then I tried to reinstall, and that gave me a couple of 
warnings (this is probably not completely right, because I couldn't copy/paste and also had to translate (from swedish)):

```
warning forcing reinstallation of alternative/usr/lib/pxpress/ld.so.conf when the link group X86_64-linux-gnu_gl_conf is broken
update-alternatives:warning:skipping to create /etc/x11/xsession.d/10fglrx when the associated file /usr/lib/fglrx/10fglrx (from the link group X86_64-linux_gnu_gl_conf) doesn't exist
update-alternatives:warning:skipping to create /usr/lib/xorg/modules/driver/fglrx_drv.so when the associated file /usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
 (from the link group X86_64-linux_gnu_gl_conf) doesn't exist
```

Also, when rebooting there was some text flashing by with one of the lines: SMB/CIFS file and active directory server FAIL (in red)

Thanks for bearing with me! :oops:

---

### Post by tbrann2 on 2015-11-11
After some googling, I found that it is probably the graphics cards driver (AMD/ATI RADEON HD6450) that is broken. 
Found a thread where a guy tried to install the driver, seemed like a lot of work, especially when I can't copy/paste.
Is there somekind of "standard ubuntu" graphics driver I could install with some easy commands?

---

### Post by tbrann2 on 2015-11-11
I used this guide [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx) to remove the ATI driver, and actually got the desktop back! :p

System still reports some errors when booting, but at least I can copy/paste in terminal now! 

Don't know if it's a good idea to try to reinstall ATI drivers again....maybe sometime later

Thanks for all help!):P

---

