---
title: "unable to install ubuntu server 16.04.3 lts on n3150 based board"
date: 2017-08-11
forum: Server Platforms
---

### Post by bigdennis on 2017-08-11
For days, i'm trying to get ubuntu 16.04.3 server to install on an asrock n3150-itx board/system. I've made an usb install media and am trying to install it from that. I've created the usb installer with Rufus (windows) and also tried writing the iso with image writer (win32diskimager, windows)

The installer refuses to run, it displays the initial menu, but when choosing the first option to start the installer some data is loaded, the usb optical mouse flickers, and nothing happens (screen stays black).

My main goal was to get it to boot from uefi. When this didnt seem to work, i've tried legacy bios/csm mode. Even this didnt work.

What i've done so far:

-try to boot from usb in uefi mode (with/without secure boot)
-try to boot from usb in legacy bios mode
-manually created the esp partition and tried booting in uefi again, same result
-tried booting with cpu c-state limited to s1 or s7, no difference
-tried booting with different displays, connected with hdmi or dvi, 1680p display and 1080p display, same result

What does work:
-boot windows 10 in uefi mode
-boot dban in legacy mode
-boot knoppix, this gives a LOT of errors, freezes on acpi not recognised, after altering boot parameters disabeling  acpi knoppix boots
-boot ubuntu desktop in legacy mode

-what doesnt work:
-boot ubuntu server in uefi mode (black screen)
-boot ubuntu server in csm legacy mode (black screen)

The system consists of a n3150-itx board, two identical sodimms (2x4gb), two ssd's . The goal was to use an extra hardware raid controller, but i left it out of the initial setup no to complicate matters further. Bios of the board was updated to latest 1.8 version. 

I'm really pulling my hair out.  Exactly the thing that this machine was build for, running ubuntu server , seems to be impossible.

Does anyone have an idea how i can get this thing to work?

---

### Post by darkod on 2017-08-11
Have you tried booting the stick on another machine? Just to see if it will actually start the installer.

Have you another ubuntu desktop system maybe that you can use to create the usb with the server iso? I am asking because usb creating with rufus, win32diskimager, etc in many cases adds small linux part that is supposed to kick of the ubuntu part. If this step does not work correctly, you might not even be getting to the ubuntu part when you boot with the stick.

Also double check that the iso hasn't been corrupted or something during download.

---

### Post by bigdennis on 2017-08-12
I've booted an ubuntu desktop livecd in another computer, created a ubuntu server usb stick from there with the ubuntu tool, and tried again. The usb stick wont boot in uefi on the n3150 machine, and also not in uefi on the "other" computer (asus laptop, 2nd gen i7,pga988). The laptop boots the usb stick in legacy mode fine. The n3150 wont even boot ubuntu server in legacy csm mode. I'm really confused.

---

