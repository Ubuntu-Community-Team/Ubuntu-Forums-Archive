---
title: "Reinstall problem."
date: 2015-07-04
forum: Ubuntu/Debian BASED
---

### Post by LanaDelRey on 2015-07-04
Hi.
First of all, let me just say that my issue is with regards to Kali Linux but their forums are so inactive that I have gotten no responses.
Here's basically what happened. I dualbooted Kali Linux alongside my Windows 8 and had an issue with the bootloader. (The GRUB bootloader doesn't show Windows when the boot mode is in Legacy).
So I decided to reinstall Kali.
I basically booted into Windows and removed the volumes that were associated with Kali and I thought the uninstallation was successful.
But now when I try to reinstall Kali by putting in the CD and changing the boot mode to Legacy, this thing called Grub Rescue opens up and doesn't let me boot from the CD/USB.

Just to clarify:
1. I can still boot from Windows without any issues if I change the boot mode to UEFI.
2. I need to change the boot mode to Legacy to boot from USB/CD but now it just opens up the GRUB rescue.

Can someone please help me get rid of grub completely so I can do a fresh install of Kali?
Thank you.

---

### Post by howefield on 2015-07-04
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by LanaDelRey on 2015-07-04
> **howefield said:**
> Thread moved to the "*Ubuntu/Debian BASED*" forum.
Can you help me with my issue?

---

### Post by LanaDelRey on 2015-07-04
[COLOR=#000000][FONT=Verdana]Now something else has come up.[/FONT]
[FONT=Verdana]I went ahead and uninstalled Kali by deleting the volume in which it was installed in the hopes of doing a fresh install.[/FONT]
[FONT=Verdana]I did the uninstallation successfully but now when I try to boot from anything in the Legacy mode, the GRUB Rescue opens up.[/FONT]
[FONT=Verdana]How do I uninstall the GRUB Loader completely? Here are my partitions:[/FONT][/COLOR][COLOR=#CCCCCC][FONT=Verdana]
[/FONT][/COLOR][IMG]http://i.imgur.com/ELzKDON.png[/IMG]

---

### Post by NLinTKO on 2015-07-04
Did you remove the CD from the CR-ROM player? It could be that it holds a CD with Ubuntu and your computer tries to boot from it.

---

### Post by LanaDelRey on 2015-07-05
> **NLinTKO said:**
> Did you remove the CD from the CR-ROM player? It could be that it holds a CD with Ubuntu and your computer tries to boot from it.
The CD-ROM only contains the setup of Kali Linux(which is pretty much what I want since I want to do a reinstall), it will only show the installation screen, not the GRUB menu.
I just need a way to get rid of GRUB, preferably using Windows?

---

