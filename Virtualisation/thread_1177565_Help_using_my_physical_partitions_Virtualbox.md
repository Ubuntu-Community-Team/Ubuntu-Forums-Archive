---
title: "Help using my physical partitions Virtualbox"
date: 2009-06-03
forum: Virtualisation
---

### Post by alphageek89 on 2009-06-03
i used virtual box to install xp inside 9.04.it installed properly.got usbs to work too but my partitions aren't detecting inside xp?help!

---

### Post by bodhi.zazen on 2009-06-03
> **alphageek89 said:**
> i used virtual box to install xp inside 9.04.it installed properly.got usbs to work too but my partitions aren't detecting inside xp?help!

Virtual machines do not directly use your hard drive.

---

### Post by alphageek89 on 2009-06-03
but I want to see those drives to copy some drivers from my c drive to the virtual drive to install them otherwise i have to copy it to a usb and then use it.is it not possible for my partitions to show up inside the virtual drive

---

### Post by bodhi.zazen on 2009-06-03
I am concerned you misunderstand how virtualization works.

Your virtual machine does not use your hard drive, video card, wireless card, etc directly and the windows drivers are therefore of little or no use.

You do not directly use your hardware , so it is extremely unlikely you need to do any of that.

To answer your question, you can use your hard drives directly, but FYI that is in "beta".

---

### Post by alphageek89 on 2009-06-03
thanks a lot!
so at the moment there is no work around for using your hard drives directly?

---

### Post by bodhi.zazen on 2009-06-03
> **alphageek89 said:**
> thanks a lot!
so at the moment there is no work around for using your hard drives directly?

I did not say that.

IMO the best option for file sharing is samba. The samba protocol works out of the box on both windows and Ubuntu.

The second option , IMO, is any other network protocol, ssh (scp), ftp, http, take your pick.

Last you can use your physical partitions. It is not as easy and I would not advise you mount the partition on both windows and Ubuntu at the same time as a shared disk/partition (that will almost certainly cause data loss).

There are how to's in the sticky at the top of the forum - there is a reason they are stickies ;)

I will give you a direct link :

[http://ubuntuforums.org/showpost.php?p=6122463&postcount=6](http://ubuntuforums.org/showpost.php?p=6122463&postcount=6)

---

