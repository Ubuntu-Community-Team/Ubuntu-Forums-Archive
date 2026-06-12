---
title: "Virtualbox and already existing Windows partition"
date: 2008-04-05
forum: Virtualisation
---

### Post by cangel0612 on 2008-04-05
Is there a way to mount and virtualize an already installed Windows Vista from another partition in Virtualbox?

Thanks

---

### Post by sparkguitar05 on 2008-04-05
I would like to do this as well.  Anyone?

---

### Post by p_quarles on 2008-04-05
Moved to Virtualization.

---

### Post by steve8track on 2008-04-06
I did manage to get a Windows XP partition to be seen by vmware by using the following method:

[http://oopsilon.com/Running-a-Windows-Partition-in-VMware]("http://oopsilon.com/Running-a-Windows-Partition-in-VMware")

There is a catch though:  After all of the work I put into getting it to work, I found that Windows needs to be reactivated every time a significant hardware change occures, including alternating between booting natively and virtually.  In other words, unless you find a work around, you will probably only be able to use it virtually after reactivating, because if you reactivate too many times, it may require you to call Microsoft.

Good luck, and I hope that helped.  Sorry my solution isn't for VirtualBox...

---

### Post by xstation on 2008-04-06
Steve 
nice howto i need to ask a few questions

if i am not useing gentoo say i am useing ubuntu or etch
what would this line be ?

emerge vmware-player vmware-modules parted

xstation

---

### Post by steve8track on 2008-04-06
It's been a while since I followed that tutorial, but I believe it is gentoo's equivolent for 
```

sudo apt-get install <list of programs here...>
```

The whole process took me about 19 hours of work even with someone helping me.  I'm just letting you know what you are getting yourself into.  I was only a noob at the time though, and I didn't want to mess anything up.

---

