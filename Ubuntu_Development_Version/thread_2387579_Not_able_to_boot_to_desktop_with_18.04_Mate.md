---
title: "Not able to boot to desktop with 18.04 Mate"
date: 2018-03-20
forum: Ubuntu Development Version
---

### Post by Mark Phelps on 2018-03-20
I'm running both Ubuntu 17.10 Mate 64-bit and Mint 18.3 64-bit on my desktop, so I thought it would be no problems to create boot media using the current 18.04 Mate and boot from that to check it out -- but that is not happening.

When I boot from the USB stick, I get the MATE symbol, the dots, the screen clears, I get a brief flash of text (too fast to read) and then a black screen with a mouse cursor.

I have tried various kernel parms using the following process ...

Pressing SHIFT while booting brings up a menu, then pressing F6 opens up an editor on the kernel parms line.

So, I tried selecting only NOMODESET -- same result

In desperation, I also tried acpi_os-Linux and acpi_backlight=vendor -- same result

I am running an AMD R7 240 video card and it works fine in Mint 18.3 -- but that is an older kernel version because I think it's based off 17.04, not 17.10.

My guess is that the problem is LightDM -- since that is new -- but I don't know how to work around that.

With 17.10, I was able to boot to a desktop with no issues.

---

### Post by este.el.paz on 2018-04-09
@Mark:

Any updates on this thread?  

I have a somewhat similar issue, also with U-MATE 18.04, but in my case the recent dailys boot into live session just fine, but after install I can't log in to the installed desktop/GUI . . . .  You mentioned "lightdm" as a possible point of concern, and I was also thinking the same thing for my problem, something to do with the log in manager, as several years back there was something with perhaps 14.04, or possibly it was with Linux Mint, when there was a switch from lightdm to gdm and people were having a problem logging into the GUI . . . .  I also have a LM 18.3 or so install on another computer, which I believe that is built on LTS 16.04???

I've done 4 fresh installs of recent iterations of U-MATE 18.04 . . . so far that, and a number of update/upgrades via TTY have not worked around the problem . . . I guess at this point I'm waiting until the "right" daily comes along and fixes my personal problem with it??  Posted a bug report and posted on the U-MATE community forum, so far no comment that points to a way out . . . .  : - )

eep

---

### Post by sr712 on 2018-04-10
I have similar issues after installation. If I change the grub entry during boot menu (press left shift  then "e" and remove "quiet splash" the Ctrl+x to boot. For me the OS boots then. Later you have to ammend the /etc/default/grub entry and issue "sudo update-grub".
At least for me it works in normal Ubuntu 18.04 daily. I  think I noticed this issues after the 03.04.2018 daily build.

---

### Post by sudodus on 2018-04-10
The current Ubuntu MATE amd64 daily iso file proceeds to the desktop as it should when tested live (booted from a cloned USB pendrive) in [this Toshiba laptop with Intel i5 (and Intel graphics)](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

I tested both in UEFI mode and BIOS alias legacy mode.

Maybe there is a problem with the graphics driver for your AMD card (I would suspect that rather than lightdm, but I am not sure).

Have you tried some other light desktop version daily build (Lubuntu, Ubuntu Budgie or Xubuntu)? They all work for me (with some bugs, but all reach to the desktop, most things work really well).

This command brings you a mini version of Xubuntu, small and quick to zsync:

```
zsync http://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
```

[hr][/hr]
Have you tried your Ubuntu MATE live in another computer?

---

### Post by este.el.paz on 2018-04-10
> **sudodus said:**
> The current Ubuntu MATE amd64 daily iso file proceeds to the desktop as it should when tested live (booted from a cloned USB pendrive) in [this Toshiba laptop with Intel i5 (and Intel graphics)]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/")
I tested both in UEFI mode and BIOS alias legacy mode.
Maybe there is a problem with the graphics driver for your AMD card (I would suspect that rather than lightdm, but I am not sure).
Have you tried some other light desktop version daily build (Lubuntu, Ubuntu Budgie or Xubuntu)? They all work for me (with some bugs, but all reach to the desktop, most things work really well).
This command brings you a mini version of Xubuntu, small and quick to zsync:
```
zsync http://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
```

[HR][/HR]
Have you tried your Ubuntu MATE live in another computer?

@sudodus:

Not sure if you were replying to my post on this thread that relates to issues with U-MATE 18.04, but if so, thanks . . . .   

In my case I have no problem booting the live session via dvd & now usb flashdrive, in live session it logs into the GUI with no problem . . . and the video/display rendering is fine.  

My problem is logging into the **installed** system's GUI, the password is entered and the screen flashes to black and then back into the log in window.  However I can log into a TTY using the same password, and I can "ls -l /home/username" and it shows the contents of what was previously a home folder for a U-MATE 16.04 install, and then over to a LEAP xx install . . . and now the MATE 18.04.  I can run update/upgrades via TTY, but so far nothing after 4 fresh installs has gotten me passed this problem.

I figured that if "ls -l /home/username" wouldn't show any data at all that would indicate that the system isn't recognizing the piggybacked home folder and perhaps then it would be worth "adding a user," but in this case it does show the regular home directories, as well as the olde LEAP iso . . . .

In one of the first two or three installs I added the "lxde" DE to check if that would get me around the problem . . . nope . . . .

I haven't tried the live session on another computer, both because the live session is working on this computer and because I don't have another partition to try an install into for it . . . as the problem seems to be with the installed system . . . the live session is fine.

On another partition I am now running an installed version of Lubuntu 18.04 . . . which I also used an old home folder to link up with the data I had there, and that installer "crashed" on the grub2 section, but because I have other linux distros installed the grub dude found the Lubuntu install and it boots up and runs with a few errors at the beginning, running update/upgrades seems to report that "it can't find the swap" since the U-MATE install "switched" the swap to it's control . . . .  

Point being that I have a running Lu 18.04 on this computer, as well as Gecko Rolling, and Tumbleweed . . . spread across two int HDs . . . .  The Lu 18 & the U-MATE 18 are both installed on the same HD, one works perfectly fine, the other one just gets me to TTY . . . .

eep

---

### Post by sudodus on 2018-04-10
@este.el.paz,

I was replying to Mark Phelps (and only about problems with the live session).

I have seen *problems similar to yours, which are probably problems with grub*, that the new grub does not work with the computer, but an older (or at least another) version of grub can do the job for the distro/version it belongs to but also for Bionic Beaver (to become 18.04 LTS).

---

### Post by este.el.paz on 2018-04-10
> **sudodus said:**
> @este.el.paz,

I was replying to Mark Phelps (and only about problems with the live session).

I have seen *problems similar to yours, which are probably problems with grub*, that the new grub does not work with the computer, but an older (or at least another) version of grub can do the job for the distro/version it belongs to but also for Bionic Beaver (to become 18.04 LTS).

@sudodus:

Thanks for the reply . . . appreciate it . . . and indeed my issues don't relate to the "boot" problems of this OP . . . the only connection is the "development of u-MATE 18.04" . . . and generally "having problems with it" . . . otherwise I am the "jack of all threads" . . . .  : - ))

eep

---

### Post by Mark Phelps on 2018-04-10
Sorry I had not replied sooner ... but I forgot about this thread and moved my concerns over to the Ubuntu Mate forums ...

I did download a newer daily build -- and it booted to the desktop just fine.

I also tried the 18.04 Beta 2 yesterday -- and it did even better, so much so, that I am think of installing it in place of 17.10.

---

### Post by oldfred on 2018-04-11
Is your Mate install also sharing /home?
You mention sharing /home with other installs.

The sharing of /home across distributions can lead to issues as each may update settings in /home and cause issues for other installs.
Better to create a /mnt/data shared data partition with just your data, but not /home and its mostly hidden settings. Since small, I then keep /home inside / (root) but have large data partition(s).

---

