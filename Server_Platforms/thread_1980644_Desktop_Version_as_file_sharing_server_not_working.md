---
title: "Desktop Version as file sharing server not working"
date: 2012-05-15
forum: Server Platforms
---

### Post by BoarderDog5 on 2012-05-15
I recently set up a new computer with 12.04 to serve as a basic home file sharing/Time Machine system.  My main systems are Macs (MBP and standard MacBook).  I set it up using Netatalk and Avahi, using these posts as guidelines:

[http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html](http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html)
[http://nerdoftherings.net/wp/?p=13](http://nerdoftherings.net/wp/?p=13)
[http://ubuntuguide.net/ubuntu-10-10-setting-up-mac-os-time-machine-server](http://ubuntuguide.net/ubuntu-10-10-setting-up-mac-os-time-machine-server)

It works on and off, but a few things are weird.  It shows up in the Mac sidebar as two different computers, both one with the hostname (as the designated type in the XML file), and one as just '#'  (as an iMac).

Also, if anyone has any tips on how to automatically mount the various share drives when the computer boots, that would be extremely helpful.  I modified /etc/fstab, but it won't mount the external drive and the internal drives mount and show up in the sidebar as mounted, but unmounted versions also show up.


Thanks

---

