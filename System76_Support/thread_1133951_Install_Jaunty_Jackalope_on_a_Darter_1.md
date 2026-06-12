---
title: "Install Jaunty Jackalope on a Darter 1"
date: 2009-04-23
forum: System76 Support
---

### Post by shaft350x on 2009-04-23
I am going to be installing Jaunty Jackalope on my wife's Darter 1.  It has been taking some time to boot up.  Right now it has the i686 version on it (I did a "uname -m" to find out).

What would be the easiest way to get the updated drivers?  I'm thinking about doing a reinstall instead of an upgrade, which I think I did the last time and may be the reason for the slow boot times.  Besides I would like to make use of the ext4 format.

---

### Post by thomasaaron on 2009-04-23
Just FYI, there are some bugs with the ext4 formatting...

From...
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

> Ubuntu 9.04 Beta supports the option of installing the new ext4 file system. ext3 will remain the default filesystem for Jaunty, and we will consider ext4 as the default for the next release based on user feedback. There has been extensive discussion about the reliability of applications running on ext4 in the face of sudden system outages. Applications that use the conventional approach of writing data to a temporary file and renaming it to its final location will have their reliability expectations met in Ubuntu 9.04 beta; further discussion is ongoing in the kernel community.

Ext4 support in GRUB was provided by Colin King. If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the ext4 wiki), then you must also use the grub-install command after upgrading to Ubuntu 9.04 Beta to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot.

Ext4 support in gparted has been provided by Curtis Gedak. 

Here are instructions for installing Ubuntu and the System76 Driver...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by shaft350x on 2009-04-23
Thanks for the quick reply...I'm going to have to reconsider using ext4 on both of our machines.  

(Also following you on Twitter now too, :-) very cool)

---

