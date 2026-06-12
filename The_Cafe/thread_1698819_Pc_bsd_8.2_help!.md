---
title: "Pc bsd 8.2 help!"
date: 2011-03-02
forum: The Cafe
---

### Post by dh04000 on 2011-03-02
I have successfully installed PCBSD 8.2 onto a 27.5gb partition on my msi wind u100 in a dual boot combo with Lubuntu 10.10. Since PCBSD did not make a grub entry, I followed an online guide and made my own, and it works! :)

Once I boot PCBSD I get to the selection page, where I can pick Default Boot(1), Safe Boot(2), (3), (4), (5), ect. I get about 5 seconds into the boot sequence and I see [GAINT-LOCKED], and a few more lines I can't read in time (~1/3 second worth). At which point my computer screen goes blank and the whole thing reboots, going back to bios.............   :(

Does anyone know what this means? And how to get around it? I really want to test PCBSD. I tried the PCBSD forums but they are not the "nicest" bunch of people.

Please help.

---

### Post by dh04000 on 2011-03-02
The problem occurs around second 27 of this video for me. This isn't my computer, but I found where in the boot I fail in relation to this videos booting sequence.  [http://www.youtube.com/watch?v=8W79hBsE1dI&feature=player_embedded](http://www.youtube.com/watch?v=8W79hBsE1dI&feature=player_embedded)

---

### Post by dh04000 on 2011-03-02
Bump!

---

### Post by dh04000 on 2011-03-02
Bump!

---

### Post by dh04000 on 2011-03-03
Bump!

---

### Post by howefield on 2011-03-03
Moved to the Cafe should anyone wish to help, and please, one bump per 24 hours(ish) is really sufficient.

---

### Post by boydrice on 2011-03-03
> **dh04000 said:**
> I have successfully installed PCBSD 8.2 onto a 27.5gb partition on my msi wind u100 in a dual boot combo with Lubuntu 10.10. Since PCBSD did not make a grub entry, I followed an online guide and made my own, and it works! :)

Once I boot PCBSD I get to the selection page, where I can pick Default Boot(1), Safe Boot(2), (3), (4), (5), ect. I get about 5 seconds into the boot sequence and I see [GAINT-LOCKED], and a few more lines I can't read in time (~1/3 second worth). At which point my computer screen goes blank and the whole thing reboots, going back to bios.............   :(

Does anyone know what this means? And how to get around it? I really want to test PCBSD. I tried the PCBSD forums but they are not the "nicest" bunch of people.

Please help.

Have you tried one of the other boot options, safe boot, acpi disabled etc?

---

### Post by boydrice on 2011-03-03
I am assuming you are already aware of [http://wiki.pcbsd.org/index.php/Installation_Troubleshooting]("http://wiki.pcbsd.org/index.php/Installation_Troubleshooting") but if not here are some things to try.

"ACPI

If unplugging all of your external devices does not solve your problem, try selecting the menu option to disable ACPI.

Computer Freezes

If your computer freezes after the installation boot menu (while probing hardware) and unplugging extra devices or disabling ACPI does not fix the problem, it is possible that the installation media is corrupt. If the MD5 on the file you downloaded was correct, try reburning the file and double-check that you are using your burning software correctly (e.g. are not choosing a burning speed faster than your DVD drive supports).

If the system freezes after the PC-BSD boot splash screen loads and you suspect that configuring the video card is causing the system to freeze, review your system's BIOS settings. If there is a setting for video memory, set it to its highest value.

If that change did not help, try rebooting and selecting option 7 from the boot menu. This will open the boot loader prompt where you can type the following commands:

unload
disable-module vesa
set module_path=/boot/kernel;/boot/modules;CONSOLE
boot

That will disable the vesa splash screen and boot the system to an emergency console. From there you can try vesa mode, or drop to a shell and modify /etc/X11/xorg.conf to change settings.

LBA

A not uncommon cause for problems is the LBA (Logical Block Addressing) setting in the BIOS. If your PC is not booting up before or after installation, check your BIOS and turn LBA off (don't leave it on automatic).

Monitor Detection

It is possible to rerun the display settings utility again if PC-BSD starts up with the wrong resolution or video card driver. To rerun this utility, reboot the computer and select "7. Run the Display Wizard" from the welcome to PC-BSD menu. This will toggle the "disabled" to "enabled". After making this selection, press enter to continue booting the system. "

---

### Post by juancarlospaco on 2011-03-03
Install Debian BSD

---

### Post by dh04000 on 2011-03-03
I checked the md5sum and it matches the value given on pcbsd.org. I tried the suggestions you gave me and it did not fix the problem, but it gave me more information. Instead of rebooting on its own, it instead tells me to reboot by hitting at key. Right before this, it tells me:

panic: page fault
cpuid=0

That sounds bad..... I have no idea what it means, but it sounds bad. Does that mean anything to you?

---

### Post by dh04000 on 2011-03-03
> **juancarlospaco said:**
> Install Debian BSD

I heard that has no GUI. I need gnome/kde/xfce/something.

I really want to try pcbsd, because I heard it was the friendliest of the bsd.

---

### Post by juancarlospaco on 2011-03-03
It has gnome/kde/xfce/something.
Im using KDE 4 on it.

---

### Post by dh04000 on 2011-03-03
> **juancarlospaco said:**
> It has gnome/kde/xfce/something.
Im using KDE 4 on it.

Is is apt-get and .deb based? Cuz that maybe an option to try. Post me a link to a download page.


I'll try to get pc bsd working, and if I can't I'll try that next.

---

### Post by juancarlospaco on 2011-03-03
theres apt-get, and its .deb based.

It uses the same Repos as Debian, and Ubuntu Packages works on it too.

It has the Software-Center to install software.

---

### Post by dh04000 on 2011-03-03
> **juancarlospaco said:**
> theres apt-get, and its .deb based.

It uses the same Repos as Debian, and Ubuntu Packages works on it too.

It has the Software-Center to install software.

OK, you've sold me into trying it next. But, I still want to get pcbsd working. Does anyone know what that error message means?

---

### Post by dh04000 on 2011-03-03
Going to try a reinstall, to see if that fixes it.


BTW, it works in Live CD mode perfectly.

---

### Post by boydrice on 2011-03-03
> **dh04000 said:**
> I checked the md5sum and it matches the value given on pcbsd.org. I tried the suggestions you gave me and it did not fix the problem, but it gave me more information. Instead of rebooting on its own, it instead tells me to reboot by hitting at key. Right before this, it tells me:

panic: page fault
cpuid=0

That sounds bad..... I have no idea what it means, but it sounds bad. Does that mean anything to you?

this might help, sounds like it could be a file system issue or just kernel panic [http://forums.freebsd.org/showthread.php?t=19515]("http://forums.freebsd.org/showthread.php?t=19515")

---

### Post by dh04000 on 2011-03-03
Lol, turns out a reinstall was all it needed. Thanks for the help! :)

---

### Post by boydrice on 2011-03-03
Glad you got it working.  If you ever get curious you should give plain FreeBSD a try, very interesting OS.

---

### Post by jerenept on 2011-03-03
> **juancarlospaco said:**
> theres apt-get, and its .deb based.

It uses the same Repos as Debian, and Ubuntu Packages works on it too.

It has the Software-Center to install software.

Ubuntu packages won't work on BSD. And, I do not believe that the USC has been added to the Debian repos yet.

---

### Post by juancarlospaco on 2011-03-03
> **jerenept said:**
> Ubuntu packages won't work on BSD. And, I do not believe that the USC has been added to the Debian repos yet.

**uname -a** and** apt-cache search software-center** on Debian BSD:
[IMG]http://img227.imageshack.us/img227/5314/bsdebian.jpg[/IMG]

And trolls say Ubuntu dont collaborate, loooool, even BSD is using the SC

---

### Post by NightwishFan on 2011-03-04
> **jerenept said:**
> I do not believe that the USC has been added to the Debian repos yet.

Certainly. It is actually installed by default for Debian Gnome. :)

> Ubuntu packages won't work on BSD

Yup, you are quite correct. They have to be specifically built for BSD. Only a bit more than half of the packages on Debian Linux are in the BSD version. Might be more by now though.

---

### Post by juancarlospaco on 2011-03-04
Ubuntu packages work on Debian BSD, Ubuntu packages works on Debian Linux,
it uses the same repos as Debian, i've tried.
Even more, a lot of proyects i package for are working nicely there (ninja-ide, etc)

---

