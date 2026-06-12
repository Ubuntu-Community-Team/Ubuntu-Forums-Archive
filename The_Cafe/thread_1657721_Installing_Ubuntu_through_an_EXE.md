---
title: "Installing Ubuntu through an EXE?"
date: 2011-01-01
forum: The Cafe
---

### Post by Cam! on 2011-01-01
I have no CD's or USB storage devices lying around. Is there a way I can install Ubuntu from within Windows?

---

### Post by unknownPoster on 2011-01-01
This is just off the top of my head but if I remember correctly this should work.

1. Download the Ubuntu .iso as normal.
2. Download and install a .iso mounting program such as Daemon Tools.
3. Wubi, (Ubuntu's in-windows installer) should run and you can proceed as normal from there.

FYI, I have not tried this method myself, but it should work.

---

### Post by Marlonsm on 2011-01-01
> **unknownPoster said:**
> This is just off the top of my head but if I remember correctly this should work.

1. Download the Ubuntu .iso as normal.
2. Download and install a .iso mounting program such as Daemon Tools.
3. Wubi, (Ubuntu's in-windows installer) should run and you can proceed as normal from there.

FYI, I have not tried this method myself, but it should work.

Wubi is the way to go.
You don't even need to download the .iso yourself.
Just download and run Wubi that it will do the rest for you.
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

Keep in mind that a Wubi install is a little bit different: Instead of making a separate partition for Ubuntu, it will install inside Windows' partition and use the Windows boot manager for you to choose if you want to use Ubuntu or Windows. Which means you can't exclude Windows and while keeping Ubuntu.

---

### Post by Starks on 2011-01-01
Wubi is also slow as hell compared to a true installation.

---

### Post by aysiu on 2011-01-01
> **Starks said:**
> Wubi is also slow as hell compared to a true installation.
Not in my experience.

Kind of a moot point if the OP has no CD/DVD or USB.

---

### Post by sdowney717 on 2011-01-01
wubi is slower a little but not noticeably slower.

what about some type of netboot installer?
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

This document describes how to install Ubuntu through your network without having to access to an existing linux TFTP / DHCP server. This method is especially useful for installing Ubuntu onto a machine that does not have removable drives.

---

### Post by sdowney717 on 2011-01-01
[http://ubuntuforums.org/showthread.php?t=427793](http://ubuntuforums.org/showthread.php?t=427793)
another one
> Purpose

This is meant for people who want to install Ubuntu but don't have a CD-R to burn, lack a CD writer, or they want to install on a computer that doesn't have a CD-ROM drive, like an ultra-portable laptop.

What it does

UNetbootin uses an Windows-based or Linux-based installer to install a small modification to the Windows or Linux bootloader (grldr and boot.ini for NT-based systems, grub.exe and config.sys for Win9x, or grub for Linux), uses the bootloader to boot the netboot initrd and kernel, then uses that to download and install Ubuntu directly from the internet, no CD required. After Ubuntu is installed, the modification to the bootloader is then undone,

Requirements/Dependencies

Linux or Microsoft Windows 95-XP (Vista support is in the works)
A broadband internet connection (dial-up will take way too long to download)
3GB or more of spare hard drive space to install Ubuntu in


---

### Post by sdowney717 on 2011-01-01
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

this should work and looks interesting

> Requirements

    * Microsoft Windows 2000/XP/Vista/7, or Linux.
    * Internet access for downloading a distribution to install, or a pre-downloaded ISO file

Features

UNetbootin can create a bootable Live USB drive, or it can make a "frugal install" on your local hard disk if you don't have a USB drive. It loads distributions either by downloading a ISO (CD image) files for you, or by using an ISO file you've already downloaded. 

---

### Post by Lancro on 2011-01-01
I have the solution for you, first install it with wubi, and then you take your wubi installation to partitions using the script on this thread...

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

And you are done, ubuntu install in ext4 partitions with your grub and everything working perfect, thats how I have my ubuntu installed, I tried first with wubi and then when I liked it I went into partitions, it works perfect.

---

