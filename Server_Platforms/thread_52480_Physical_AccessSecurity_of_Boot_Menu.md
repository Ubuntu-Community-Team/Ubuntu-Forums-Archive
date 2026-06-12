---
title: "Physical Access/Security of Boot Menu"
date: 2005-07-27
forum: Server Platforms
---

### Post by sinbad782 on 2005-07-27
Hi all,
     I've got Ubuntu deployed on a couple of machines in public areas in a series of student hostels at my University. Each machine has only a single regular user account which isn't a sudoer,  plus one for me (that is a sudoer) and of course, the root user itself. I administer these machines remotely via SSH. SSH access to port 22 is set up via the local firewall to only be allowed from certain pre-defined hosts that I use for remote admin. Root login to SSH is not allowed, but I have not yet gotten around to disabling keyboard interactive logins and setting up passwordless logins using public keys etc. 

My problem is that I want to set a password to prevent people with physical access from powering down the machines then booting Ubuntu into recovery (sometimes called single user) mode and gaining local root access by default. Unless I am mistaken, this can be done from the grub menu if Ubuntu is like Debian in this respect. 

I have set a password on the BIOS and disabled booting from CD-ROMs or floppies in order to prevent people from coming along and booting up Knoppix or similar and then messing with the (captive) filesystem. 

As it stands, the grub menu is hidden by default and I already know how to set an md5 encrypted password to interactive editing of this in order to stop people from messing with the grub boot menu, however, this still leaves the possibility of people exploiting recovery mode as a means of getting local root access. 

I have installed Debian before and included in Debian's version of GNOME is an app called boot-admin which lets you set a boot password for each individual kernel image you have installed. I normally use this to add an additional layer of security by putting a password on the recovery mode image. I have noticed that this app is not included in Ubuntu 5.04, although it *does* appear in the Debian menu under Debian->Apps->System->Boot Admin.

Is there any chance of boot-admin (I think this is part of gnome-system-tools package in Debian) appearing in Breezy?

In the meantime, does anyone know of a corresponding command-line technique to put a password on recovery mode?

Thanks, PJS

---

### Post by amohanty on 2005-07-28
if you are the only login that can interact with grub, why not take away the recovery mode option from the menu? 

If you need to fire up in recovery mode, you can always do it from grub, logging into interactive mode and then launching the relevant kernel image.

AM

---

### Post by sinbad782 on 2005-07-29
Done - thanks. I put an md5 password on interactive editing of the grub menu and also commented out the entry for the recovery mode kernel image. Works fine. 

The problem now is that the BIOS has a bug which means that when a password is set, the keyboard doesn't get recognised at boot time - nightmare!

---

### Post by amohanty on 2005-07-30
Umm... GRUB has nothing to do with the BIOS, its loaded after POST. Also dont set a password on boot, you only need to setup a password for the CMOS setup, so that no-one can mess with the boot order.

AM

---

