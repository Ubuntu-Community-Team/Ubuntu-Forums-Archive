---
title: "New netbook acting strangely"
date: 2010-03-26
forum: System76 Support
---

### Post by likescookies on 2010-03-26
My System76 netbook arrived last night and appeared to work just great. Today, though, all the menus are unresponsive to the mouse. For example, I click on Games, and double-click on Nibbles, everything is fine up until that point. If I click on Game to access the menu to start a new game, the menu fails to open. CTL-N does work to start a new game.

Same story in Firefox. I can open the program but I can't use the mouse to do anything.

Some of the Ubuntu desktop controls act the same way. For instance, any of the icons at the top (e.g. volume or wireless networking) are unresponsive to the mouse. When I CTL-ALT-DEL to reboot, I have to arrow down to "Reboot" because it won't accept mouse clicks. But, again, it isn't completely a mouse problem because I can double-click on programs to launch them.

Warning: I'm a newbie with Linux.

The only thing I've done to the system so far is that when I got the icon up at the top to install updates, I told the system to go ahead and update. It rebooted and seemed to work fine for awhile until Firefox started acting "funny"--and now everything is acting funny.

Any advice? Thanks!

---

### Post by satsujinka on 2010-03-27
It sounds like you had a bad update, but I'm not too familiar with the mouse problems (so I don't know of any commands you could run to fix it.) To make sure that it isn't a hardware problem, could you boot into a live cd (or usb) and check to see if the mouse works there. Here's the link to download a netbook remix image if you don't have one:

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook) 

If you need help booting it feel free to pm me for help.

EDIT:
Never mind the above.
It seems other people have had this problem, there's another thread on this topic: [http://ubuntuforums.org/showthread.php?t=1393126](http://ubuntuforums.org/showthread.php?t=1393126)
Read it. Your problem seems to be the same. In the future, please search for threads on the topic before creating a new one.

---

### Post by likescookies on 2010-03-27
I did search, I swear; the referenced thread didn't seem to apply because I was not losing complete mouse support like the poster there. Nonetheless, I tried the prescribed solutions with no luck:

When I tried to "apt-get remove winbind" I get a message that I don't have winbind installed.

When I tried to "apt-get install grub-pc" I get a message that grub pc is already the newest version.

And when I tried to reinstall hal, I get a message that it will reinstall 0 files.

I can try the liveboot, though it means I'll have to go out and buy a larger flash drive. My suspicion is a software problem because the mouse seems to be sending clicks because some parts of the UI consistently receive them. I'm open to further suggestions!

At least I'm learning a lot. I learned how to boot into safe mode and I learned what "sudo" means.

---

### Post by likescookies on 2010-03-27
Well, I've got Ubuntu 9.10 running from a USB drive and I get the same behavior. That means it could be hardware.

Another thing I noticed is that if I run, say, Chess as a test case and I click on the board, the machine launches whatever program whose icon happens to be sitting under the board. It's like the machine is sending the mouse click to the wrong level, if that makes sense.

Anyway, I guess I'll contact System 76 directly.

---

### Post by satsujinka on 2010-03-27
Sorry then. It's simply that posting before searching is pandemic on the internet, especially among "newbies."

Btw, you wouldn't happen to have a usb mouse would you? If so does that work?

Also did you remove hal before trying to reinstall it? Personally, I prefer to remove something first. So try:

```
sudo apt-get autoremove --purge hal
sudo apt-get install hal
```
On the other hand, your window-click-through problem seems to imply that something is wrong with x11. However, we would need a different version of x11 in order to test that, which ultimately is just going to end with a distro-hopping wild goose chase. So it's probably best to just get system76 to fix it.

---

### Post by likescookies on 2010-03-27
Yes, I discovered after I wrote my last message that the machine works fine if I plug a USB mouse in before booting. If I pull it out, then it reverts to the strange behavior, even if I plug it back in.

I tried as you suggested and uninstalled Hal before reinstalling. This may have been a mistake! Hal uninstalled successfully but fails to reinstall, which is a problem as the machine now won't launch the GUI. I never get to the GUI login, only "system76-netbook login:" in text. 

The error I got when trying to install was "hal_0.5.13-1ubuntu8_i386.deb is not a debian format archive."

It sounds like my copy of Hal is corrupt? It looks like I can download the package here: [http://packages.debian.org/squeeze/i386/hal/download](http://packages.debian.org/squeeze/i386/hal/download)

If I boot into safe mode, what's the command to install from that location?

Thanks much!

---

### Post by satsujinka on 2010-03-27
Try doing this first:

```
sudo apt-get install ubuntu-netbook-remix 
```

This package should have been uninstalled when you removed hal, and installing it should fetch hal, as well as all other packages that are part of the netbook remix. If that doesn't work the code to download and install hal is:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/h/hal/hal_0.5.13-1ubuntu8_i386.deb
sudo dpkg -i hal_0.5.13-1ubuntu8_i386.deb
```

Please note that the Debian package is not compatible with Ubuntu (well, it may work, but it's unlikely.) So the above uses an Ubuntu package.

You may wish to try vanilla ubuntu to see if that detects your touch pad better. Also try 8.04 to see if that works better.

---

### Post by likescookies on 2010-03-27
Just installed Ubuntu from scratch and reset to factory settings, which seems to have cleared the problem with the trackpad.

I've learned a lot in this process, though I wish I could have solved it without resetting as I probably would have learned more. Like I'm still confused why the trackpad was acting funny even when I was running off the live USB stick if it was a software/driver issue.

When the system asked me to update once everything was installed, I declined since I'm heading out of town tomorrow and it seemed like the current updates are what caused the problem the first time around. Is there a problem with Hal and the current Ubuntu updates?

Thanks for your help!

---

### Post by likescookies on 2010-03-27
[satsujinka]("http://ubuntuforums.org/member.php?u=914974"), just saw our replies crossed in mid-air. Thanks for your help--I do appreciate you taking the time.

---

### Post by satsujinka on 2010-03-27
No problem.

Honestly, I have no clue whether there's a problem with Ubuntu's hal at the moment. I would suppose so, considering there was another group with similar problems. All in all, it may just be a side effect of the switch to device kit and udev.

---

