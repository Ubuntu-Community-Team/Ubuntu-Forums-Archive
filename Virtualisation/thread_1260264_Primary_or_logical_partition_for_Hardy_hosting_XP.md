---
title: "Primary or logical partition for Hardy hosting XP?"
date: 2009-09-07
forum: Virtualisation
---

### Post by Eldera on 2009-09-07
I read somewhere that in dual boot between Ubuntu and Windows, Windows had to go on a primary partition. (That information may be out of date.)

Is the situation different in virtualization? I would like to set up VirtualBox with Hardy as the host and XP as the guest. Will Hardy have to be on a primary partition?

Thank you to anyone who answers, Eldera

---

### Post by Ocxic on 2009-09-08
it is always preferable to use primary partitions whenever possible, logical partitions are linked:

logical partition 1 has a link to partition 2, 2 to 3, 3 to 4, etc...  if you loose partition 2 you will also lose 3,4,5, at the same time.

---

### Post by Eldera on 2009-09-08
Thank you, Ocxic, that was very helpful. I am very new to Linux. I didn't know logical partions were linked. Now I can make better, more intelligent, decisions about my partitioning.

---

### Post by longtom on 2009-09-08
I have XP on a primary partition in a dual boot.  I also have XP in a virtual setup in VB.

I can not see what difference it will make on what partition your host setup is when you virtualise.  In virtualisation you create a separate hd in form of a vdi file.  Once that is done of you go.

In summary:

I doesn't make any difference as what your host OS is located on your system.  If it starts up and you can run VirtualBox in it, you are good to go.

Good luck!

---

