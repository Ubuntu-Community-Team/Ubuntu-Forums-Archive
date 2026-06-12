---
title: "Iso testing"
date: 2020-03-23
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-03-23
Made some Iso testing and installed on a desktop with Nvidia gpu. Installed in legacy BIOS mode.
Yesterday's ISO crashed, but today's ISO20200323 worked OK except for one minor bug
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/966480](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/966480)

Used mkusb on Ubuntu 20.04 to make the USB boot device and got a security problem. However everything worked OK.

---

### Post by P-I H on 2020-03-24
Downloaded and installed [COLOR=#000000]ISO20200324[/COLOR]. This time on a desktop with AMD gpu and installed in UEFI mode.
This is a triple boot system with Ubuntu, Windows 10 and Fedora 32. All installations booted OK.

---

### Post by sudodus on 2020-03-24
> **P-I H said:**
> Made some Iso testing and installed on a desktop with Nvidia gpu. Installed in legacy BIOS mode.
Yesterday's ISO crashed, but today's ISO20200323 worked OK except for one minor bug
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/966480](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/966480)

Used mkusb on Ubuntu 20.04 to make the USB boot device and got a security problem. However everything worked OK.

> **P-I H said:**
> Downloaded and installed [COLOR=#000000]ISO20200324[/COLOR]. This time on a desktop with AMD gpu and installed in UEFI mode.
This is a triple boot system with Ubuntu, Windows 10 and Fedora 32. All installations booted OK.

I would like to debug the problem with mkusb, and I need some details:

Did you get the sudo problem when running mkusb? Or when running the system created by mkusb?

Did you use mkusb-dus version 12.4.3 (from ppa:mkusb/ppa) or 12.4.4-1ubuntu5  (from ppa:mkusb/unstable)? Or mkusb-plug version 2.6.1 (which comes with 2.4.4-1ubuntu5)? 

What kind of system did you create? A live system or a persistent live system?

Do you get the same problem also with the current daily iso file (dated 2020 03 24 or later)?

---

### Post by P-I H on 2020-03-24
I got the security problem when I used mkusb to create the USB boot device on Ubuntu 20.04
I used version 12.4.3-1ubuntu1 installed from the wiki page [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
I used the "i" alternative "Install (make a boot device)
The log message seems to be created when mkusb asks for the password.
It doesn't impact functionality, it's only a little bit strange to get that kind of message.

---

### Post by sudodus on 2020-03-24
Thanks, I will try to reproduce the bug, and find a way to squash it.

I tested mkusb 12.4.4-1ubuntu5 very recently in a persistent live Ubuntu Focal system (and as we all know, such a system does not ask for a password). I will try in an up to date *installed* Ubuntu Focal system.

By the way, the coding where mkusb (mkusb-dus) asks for the password has not been modified for years, and I ported that coding to mkusb-plug, so it should work the same way. Maybe something has changed in Focal, for example some feature in sudo.

---

### Post by sudodus on 2020-03-24
I tested in a Lenovo V130 with a generation 7 Intel i5 and an NVME drive.

- UEFI mode
- Ubuntu Focal installed from focal-desktop-amd64.iso dated 2020 03 24
- Swedish
- Fully up to date
- Installed the 3 packages mkusb mkusbplug usb-pack-efi from ppa:mkusb/unstable
- Ran mkusb (mkusb-dus) and mkusb-plug from the icons in the gnome desktop system via the nine dots at the bottom left corner.

Result: I could not see any problem with the security system, when running mkusb. It works as I expect it to work all the way to finiishing with Done [noparse]:-)[/noparse]

But I must admit, that I don't know how to get the window 'Logs' that you show in the attached screenshots. Maybe there is a problem, that I have never understood because I never looked there. Please explain how you get that window and also if you see something directly on the desktop (a window that pops automatically).

Edit: screenshot

---

### Post by P-I H on 2020-03-24
It's from the Logs application. It's installed by default. The easiest way to start Logs is click Activities, search for logs and start Logs. 
[https://wiki.gnome.org/Apps/Logs](https://wiki.gnome.org/Apps/Logs)

---

### Post by sudodus on 2020-03-24
Thanks :-)

Here is the Logs window from my run. I expanded the log window, and I recognize the text of the echo command:

```
echo live system or temporary superuser permissions
```

and in this case there are temporary superuser permissions in the 'console window', the terminal window from where the various tasks of mkusb is launched. Early during the execution sudo is run via that small Enter password window, and that creates the temporary superuser permissions. If there would be a very long delay (I think there is a 15 minutes limit), you would have to log in for the next task that needs elevated permissions.

So it *is* text from mkusb. I will look more in those details.

The security system is not happy with my way to run the sub-shellscripts with sudo. Maybe it is a real problem, maybe 'only' a warning, that elevated permissions are used automatically, but as long as *you* started the 15-minute-interval for it, it might be OK, just like if you ran [FONT=Courier New]**sudo apt install htop**[/FONT] (and entered the sudo password, and after that you can install other programs (for example [FONT=Courier New]**sudo apt install mkusb**[/FONT]) without entering the password again.

---

### Post by P-I H on 2020-03-28
Installed iso  [COLOR=#3B3B3B][FONT=&quot]20200327[/FONT][/COLOR]. The installation crashed on my old system with Nvidia gpu. Installed OK on a newer system with UEFI and AMD gpu.

The new Snap Store refuses to install Chrome. Get the message "Failed to install: not supported".
Had to download Chrome, unpack, change directory and run **sudo dpkg -i *.deb**
Perhaps worth a bug report.

---

### Post by sudodus on 2020-03-28
- Did you use mkusb-dus or mkusb-plug?
- Did you create a persistent live system or a [cloned ]live-only system?
- Was it a normal installation to an internal drive that crashed?

I am asking in order to decide where to look for the bug.

If it is a normal installation from a cloned drive to an internal drive that crashed, I think the bug is independent of mkusb, otherwise mkusb may be part of the problem.

(C.S.Cameron has found [problems when shutting down a focal persistent live drive made with mkusb](https://ubuntuforums.org/showthread.php?t=1958073&page=45&p=13941718#post13941718), so I am aware of problems and ready for more ...)

---

### Post by P-I H on 2020-03-28
I don't think there is a problem with mkusb. When the installation crashed on the old system, I got the message that is already was reported.

---

### Post by sudodus on 2020-03-28
So there is already a bug report about it. Thanks for sharing this information :-)

---

