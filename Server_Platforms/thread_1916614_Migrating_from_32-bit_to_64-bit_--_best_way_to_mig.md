---
title: "Migrating from 32-bit to 64-bit -- best way to migrate all files/settings?"
date: 2012-01-28
forum: Server Platforms
---

### Post by rage_311 on 2012-01-28
I'm currently in the process of migrating my Ubuntu server from 10.04.1 32-bit to 10.04.3 64-bit.  I'm doing the new setup on a different drive, so I currently have both drives hooked up in the machine.  I just completed the partitioning/installation of the 64-bit version of Ubuntu server on the new SSD.  The /home directory was already on a separate partition on the original drive, so that will be the easy part (just mounting that same drive/partition on the new install).  Now, I'm trying to figure out the best way to get all of the programs/settings and OS config files to the new install.  What is the best way to go about this?

The server's duties include: MythTV master backend, SSH, SMB, FTP, Apache, Ampache, Ventrilo, Transmission...

Any help is greatly appreciated!

---

### Post by oldfred on 2012-01-28
I do not know if myth & its apps have data in other places than /home.

But you can reinstall all the applications, by exporting the list and reinstalling. It is just a list of names so you can manually edit it if necessary and it will just install the correct version for the system you have installed.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by rage_311 on 2012-01-29
That was VERY helpful.  Thank you.

That is essentially all I did.  Then, I actually just copied my entire /etc folder from the old installation to the new one.  I had a few minor hiccups to fix, but I've got the majority of it up and running flawlessly now!

Almost there...

---

