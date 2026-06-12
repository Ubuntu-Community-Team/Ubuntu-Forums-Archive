---
title: "whole-disk encryption with pre-boot authentication"
date: 2012-11-29
forum: Security
---

### Post by blm14 on 2012-11-29
I am currently running ubuntu 12.04 LTS. I have a full backup of my data, so if necessary, I can copy my home directory and other important stuff to a secondary drive and restore it after the fact.

My work is requiring that I have pre-boot authentication with full disk encryption. Is it possible to do this with ubuntu? Is there a guide for it?

---

### Post by Stonecold1995 on 2012-12-01
You have to set up whole-disk encryption at install.  You can do that by downloading the alternate install CD for 12.04 (sadly I don't think there's an alternate install CD for 12.10).

Also you won't need home directory encryption if you already have whole-disk encryption unless you want to prevent other users (who have access to the disk's encryption key) from spying on your stuff.

Also, even with whole-disk encryption, you have to be careful because it's not truly "whole-disk".  /boot must remain unencrypted, and that opens up the possibility of installing kernel rootkits.

---

### Post by zombifier25 on 2012-12-02
I have read some time ago that a possible workaround for this to to run a script that checks the integrity of /boot.

---

### Post by Stonecold1995 on 2012-12-02
There is.  I forget where the original script is, but I made an improved version taking some of the original script (it was licensed under the GPLv2).  It's not totally done yet so it only supports KDE, but it's probably easy to get to work with other DEs.  Currently its features are:

-Installs itself, can re-install/repair itself, verify itself to make sure it hasn't been messed with, and can uninstall itself.
-Checks files hashes against the last boot
-Checks inodes to make sure nothing moved in the filesystem
-Checks the MBR against the last boot
-Performs backups of /boot at each successful boot
-Keeps logs of every boot
-Alerts you to changes at login, and allows you to set the changes as the new standard (e.g. after updating your kernel) or manually repair it from the automatic backup

I attached it to the post.  It's not done yet, and I'm not great at scripts so if you use it there may be bugs, but it's more effective than the original from what I remember.

---

### Post by Cheesemill on 2012-12-02
I think I recall pointing you to the original, it was the chkboot package from Arch.
[https://aur.archlinux.org/packages/chkboot/](https://aur.archlinux.org/packages/chkboot/) (download link in the sources section at the bottom of the page).

Also you are correct that there is no alternate installer for 12.10, but all of the encryption functionality has been moved to the standard desktop installer.

---

### Post by Stonecold1995 on 2012-12-02
> **Cheesemill said:**
> I think I recall pointing you to the original, it was the chkboot package from Arch.
[https://aur.archlinux.org/packages/chkboot/](https://aur.archlinux.org/packages/chkboot/) (download link in the sources section at the bottom of the page).

Also you are correct that there is no alternate installer for 12.10, but all of the encryption functionality has been moved to the standard desktop installer.

Yeah, I think you were the one who gave the link to the script I used.

I miss the alternate installer. :(  Just curious, are there any unofficial alternate installers at all?

---

### Post by Cheesemill on 2012-12-02
If you have a network connection on the machine you are installing to then you can use the Mini CD, it's identical to the alternate installer but it downloads all packages for the installation from the internet so you start with a fully updated system straight after installation.
[http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)

Another solution to the unencrypted /boot situation is to encrypt the entire hard drive and have the /boot partition separate on a USB stick that stays with you at all times. I've used this method before on my laptop.

---

