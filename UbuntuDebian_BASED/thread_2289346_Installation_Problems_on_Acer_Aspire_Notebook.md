---
title: "Installation Problems on Acer Aspire Notebook"
date: 2015-08-03
forum: Ubuntu/Debian BASED
---

### Post by Blacky6 on 2015-08-03
I bought an Acer Aspire E 15 E5-511-C145 Notebook for using it with Linux.
Since i bought it, I probably tried installing Linux on it at least 20 times (I'm not exaggerating).
I  tried installing Elementary OS Freya, LXLE 14.04.2, Ubuntu Mate 15.04  & Lubuntu 14.04.2 (all amd64 versions) in different ways.
With UEFI, Legacy BIOS, Secure Boot enabled and disabled.
USB created with UNetbootin and Linux Live USB Creator.
I also disabled fast Boot in Windows 8.1 before trying to install any Distro.

I always encounter at least one of the following problems:

-  The Live USB gets recognized and when I boot from it it displays the  options like 'Try Ubuntu Mate without installing', 'Check disk for  errors' etc.
But when I choose 'Try without installing', it gets  stuck at the Splash Screen with the error '[    27.191771] dw_mac  INTL9C60:00: invalid resource'
(This happened with Elementary OS Freya, Ubuntu Mate 15.04 & Lubuntu 14.04.2)

- I can boot into the live system but cannot shutdown properly (The Screen goes black but the notebook is still turned on.
The  fan then goes on like crazy for about 10 seconds every half a minute  and it won't shutdown so I have to press & hold the power button to  kill it.)
This only Happened with Elementary OS Freya.

- I can boot into the live system but when i choose to install  everything goes well until the installation of GRUB where I get this  error:
'The 'grub-efi-amd64-signed' package failed to install into  /target/. Without the GRUB boot loader, the installed system will not  boot.'
(Happened with Ubuntu Mate 15.04, LXLE 14.04.2 & Elementary OS Freya)

- I can't boot into Elementary OS Freya after installing it in Legacy BIOS mode because it gets stuck at the Splash screen.


With UEFI & Secure Boot enabled:
In  LXLE 14.04.2 as well as Ubuntu Mate 15.04 everything works (also  shutdown), except the installation where i get the above mentioned  error.
In Elementary OS Freya, I can boot the system but can't shut  it down properly and the right click doesn't work. (The installation  only works in Legacy BIOS mode)
In Lubuntu 14.04.2 I can't even boot  into the live system because it gets stuck at the Splash screen with the  error mentioned above.

LXLE 14.04.2 uses the 3.13.0-49 Kernel  and i never encountered any problems except the GRUB installation error.  (GRUB rescue does not seem to help as far as i have read on forums)
I  think it has got something to do with the Kernel and I also read  something about ACPI and blacklisting some drivers (but then some  components of the notebook will not work).

I really hope somebody with more Linux knowledge than me can help with the information provided.
I normally solve problems myself using the Internet and trying out but my patience is exhausted.
Thank you in advance for any help you can provide.

Specs of the Notebook:

Acer Aspire E5-511-C145
Intel Celeron N2840 (2.16 GHz)
4 GB DDR3 L Memory
Intel HD Graphics - 64 MB RAM - dedicated
500 GB HDD
15.6" HD (1366 x 768) Display

---

### Post by Vladlenin5000 on 2015-08-03
Hi and welcome.

A quick Google search found this: [https://bugzilla.kernel.org/show_bug.cgi?id=85931](https://bugzilla.kernel.org/show_bug.cgi?id=85931)

---

### Post by Blacky6 on 2015-08-03
Thank you so much! You'll have to excuse me for being frustrated - I really wanted this to work!

[SIZE=3]**Here is the Solution:**[/SIZE]

-When you boot the live system, move your selection to 'Try Elementary OS without installing', then press 'E' on your keyboard (for editing the boot options).
Move the cursor to the line where it says "Linux ....... splash screen" at the end of the line insert a space and then write 'modprobe.blacklist=dw_dmac,dw_dmac_core'.
Hit F10 for booting. Now install Elementary OS and reboot.

-Turn on your notebook and do all the updates (sudo apt-get update && sudo apt-get upgrade).
Next open a terminal and write 'sudo nano /etc/default/grub', go to the line where it says 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"' and change it to 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modprobe.blacklist=dw_dmac,dw_dmac_core"'. On your keyboard press 'Control + X', then 'Y' and 'Enter' to save and exit. Now write 'sudo update-grub' in the terminal.

Reboot and you should be done!

If you're interested in what you have changed on your computer read this:
[http://www.differencebetween.net/technology/difference-between-dma-and-pio/](http://www.differencebetween.net/technology/difference-between-dma-and-pio/)

---

### Post by howefield on 2015-08-03
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Airdeu on 2016-02-21
Thank you! This solution worked for installing Ubuntu Mate on a Acer Extensa 2509 also. Before, it was freezing during the first two dots.

---

