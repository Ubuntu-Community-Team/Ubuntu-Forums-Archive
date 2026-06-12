---
title: "rkhunter detect kernel problem?...please help"
date: 2008-10-09
forum: Security
---

### Post by AmbientOcclusion on 2008-10-09
I ran rkhunter today using this switch:

> sudo rkhunter --check --pkgmgr dpkg

It did not detect any rootkits but did display these results that have me worried, I am not sure how to interpret them (I have only including the Warnings):

> 


[22:05:45] /usr/bin/sudo                                     [ Warning ]
[22:05:45] Warning: The file properties have changed:
[22:05:45]          File: /usr/bin/sudo
[22:05:45]          Current inode: 3424317    Stored inode: 2932
[22:05:45]          Current file modification time: 1221075776
[22:05:45]          Stored file modification time : 1210812278



[22:05:45] /usr/bin/sudo                                     [ Warning ]
[22:05:45] Warning: The file properties have changed:
[22:05:45]          File: /usr/bin/sudo
[22:05:45]          Current inode: 3424317    Stored inode: 2932
[22:05:45]          Current file modification time: 1221075776
[22:05:45]          Stored file modification time : 1210812278



[22:05:55] /usr/sbin/unhide                                  [ Warning ]
[22:05:55] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat f
ile.



[22:05:56] /usr/sbin/unhide-linux26                          [ Warning ]
[22:05:56] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunt
er.dat file.


[22:08:19]   Checking for hidden files and directories       [ Warning ]
[22:08:19] Warning: Hidden directory found: /etc/.java
[22:08:19] Warning: Hidden directory found: /dev/.static
[22:08:19] Warning: Hidden directory found: /dev/.udev
[22:08:19] Warning: Hidden directory found: /dev/.initramfs

I'm somewhat of a Ubuntu security N00b, my girlfriends Vista laptop was compromised recently and she plugs it into our home lan, so this made me decide to run a scan. 

Should I be worried about these warnings?

---

### Post by jlfallaw on 2008-10-09
I don't use rkhunter, but it doesn't seem to be a problem, according to [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5733628").

---

### Post by AmbientOcclusion on 2008-10-09
Hey thanks for the link, I'll give it a shot.

You recommend something better than rkhunter for me to try instead?

*UPDATE


I ran code: **sudo rkhunter --propupd**

and then code: **sudo gedit /etc/rkhunter.conf**

I uncommented the following lines under the following section:

# Allow the specified hidden directories.
# One directory per line (use multiple ALLOWHIDDENDIR lines).
#
[b]ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/dev/.udev
ALLOWHIDDENDIR=/dev/.udevdb
ALLOWHIDDENDIR=/dev/.udev.tdb
ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.initramfs[/b]
#ALLOWHIDDENDIR=/dev/.SRC-unix


..and it worked. No warnings at all!

---

### Post by jlfallaw on 2008-10-09
Sweet! Unfortunately I don't know of any other rootkit finding programs- I have only ever heard of rkhunter. I just don't use one. But I think I might give rkhunter a try. From what I can tell it's one of the best out there. I think AVG has a rootkit finder, too.

---

### Post by Dave_Connor on 2008-10-09
There was an update of sudo awhile ago so you don't need to worry about that and just have rkhunter update the files.

---

### Post by AmbientOcclusion on 2008-10-16
Yeah it does seem like rkhunter is at the top of the heap currently. 

I have an older AVG linux edition that is fairly stripped down, I'll check it out and see.

---

