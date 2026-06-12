---
title: "Keyboard problems on brand new Bonobo Extreme"
date: 2013-02-26
forum: System76 Support
---

### Post by shawnduffy on 2013-02-26
I just received my Bonobo Extreme yesterday afternoon.  Unfortunately, I've been having terrible keyboard issues where certain keys completely stop working.  They occasionally come back but I can't quite replicate what brings them back, even across reboots and restarting X.  Among the keys not working or having recurring problems.

TAB, UP-ARROW, t, g, h, j, b, n

I'm running Ubuntu 12.10, driver version 3.2.3.  Like I said, this is fresh out of the box.  I've run software update, reinstalled System76 driver.  Nothing seems to work.  It wasn't as bad yesterday but appears to be getting worse.

I will attach the logs.tar file in a follow up comment.  I was forced to type this post from another computer since my keyboard is almost unusable.

Any help would be greatly appreciated.

---

### Post by shawnduffy on 2013-02-26
Logs

---

### Post by shawnduffy on 2013-02-26
It's no longer intermittent.  The keys mentioned above have completely stopped working.

I even went into grub to try and boot to a different kernel and I discovered that the same keys don't work there either.  At this point, it looks like a hardware issue.

---

### Post by J_we on 2013-02-27
> **shawnduffy said:**
> It's no longer intermittent.  The keys mentioned above have completely stopped working.

I even went into grub to try and boot to a different kernel and I discovered that the same keys don't work there either.  At this point, it looks like a hardware issue.

I'd be skeptical that this is a hardware defect. It sounds more like a bug.

---

### Post by shawnduffy on 2013-02-27
I hope you're right.  But I also discovered that the keys do not work in the BIOS set up either.  Not good.  

I did have them randomly start working for about 5 minutes last night.  I didn't do anything special.  I was paging through dmesg when I noticed that they started working again.  A few minutes later, I lost them.

---

### Post by jbelmonte on 2013-02-27
It sounds like the connection from the keyboard to the motherboard came partially loose during shipping. You should go to the System76 site and open a support ticket. They may walk you through making securing the connection, but I would let them decide how to proceed.

---

### Post by shawnduffy on 2013-02-27
> **jbelmonte said:**
> It sounds like the connection from the keyboard to the motherboard came partially loose during shipping. You should go to the System76 site and open a support ticket. They may walk you through making securing the connection, but I would let them decide how to proceed.

Thanks.  I have a support ticket open and I'm working with them now.

---

