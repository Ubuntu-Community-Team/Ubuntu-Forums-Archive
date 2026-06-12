---
title: "Help needed with group setting"
date: 2008-10-20
forum: Virtualisation
---

### Post by kjbox on 2008-10-20
Hi, I have installed and configured SUN xVM VirtualBox with the help of this great HowTo: []("http:http://ubuntuforums.org/showthread.php?t=433359")

I have got as far as Step 3 but when I attempt to start my Virtual Machine I get the following error message:

Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either run 'chmod 0666 /dev/net/tun' or change the group of that node and make yourself a member of that group. Make sure that these changes are permanent, especially if you are using udev.

I have checked the permissions for /dev/net/tun and found: 'Owner: root' and 'Group: root'. 

I cannot change the the group, and going to Users and Groups then adding my username to root group still gives the same error on retry.

Any help would be greatly appreciated.

Thanks in advance :)

---

### Post by Iowan on 2008-10-20
> **kjbox said:**
> I cannot change the the groupYou tried **sudo chgrp mygroup /dev/net/tun** (mygroup being YOUR group, of course)? The group existed already? If not, check **man addgroup** - it has better explanation of options - even for adduser.

BTW, your link didn't get attached.

---

### Post by kjbox on 2008-10-21
Thanks Iowan, that got it sorted :D

---

