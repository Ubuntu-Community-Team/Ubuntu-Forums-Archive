---
title: "Folder premissions issue"
date: 2010-08-28
forum: Security
---

### Post by lembi2001 on 2010-08-28
Hi All

I have been playing with Ubuntu 10.04 for a few weeks now and as I am triple booting my Laptop I have got a seperate partition purely for my Documents and other such things.

My HDD looks like this:

/dev/sda1 - 54GB - NTFS - windows
/dev/sda2 - 27GB - HFS+ - Mac OS X
/dev/sda3 - 154GB - FAT - Storage Drive
/dev/sda4 and sda5 - linux
/dev/sda6 - swap space

Under Windows i have redirected everything to the relevant folders on my storage drive. by everything i mean:

Desktop
Downloads
Documents
Videos
Music
Pictures

I have been trying to do the same in Ubuntu and succeded to a point. I have used a piece of software - Ubuntu Tweak - to carry out the change and also used pysdm to ensure that the drive is mounted at boot! Great i thought all done. NOT!!!

I do not have permission to write to these folders from ubuntu. I checked the permissions and they are all set to root. The Other users is listed as Access files only. I have tried using terminal and sudo chmod and sudo chown with no luck and have also set a root password and tried doing it whilst logged in as root. no joy. i get opereation not permitted.

I have tried changing the main group of my account when logged in as root and completely stuffed the account up so have created another admin account. this time around though i have left the permissions as they were set.

can anyone help me with getting it so that i have full access to these files from within ubuntu??

Thanks

---

### Post by lembi2001 on 2010-08-28
Managed to fix it using the pysdm tool. changed the permissions in there.

---

