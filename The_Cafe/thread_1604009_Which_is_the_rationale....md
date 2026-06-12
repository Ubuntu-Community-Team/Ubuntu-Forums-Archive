---
title: "Which is the rationale..."
date: 2010-10-23
forum: The Cafe
---

### Post by franzmaximilian on 2010-10-23
...behind the fact that Ubuntu by default creates a single partition when installed?  Personally I have the habit of creating a separate partition for /home, but this is a bit more complicated and hard to implement for newbies.  I find this much safer and practical. Some distros do this by default, so I wonder which rationale is behind Ubuntu's choice?

---

### Post by CraigPaleo on 2010-10-23
You said it yourself regarding multiple partitions: 

> but this is a bit more complicated and hard to implement for newbies.

Ubuntu is all about being newbie-friendly.

---

### Post by aysiu on 2010-10-23
You can see the rationale here:
[Idea #5390: Offer to create a separate /home partition and use existing ones](http://brainstorm.ubuntu.com/idea/5390)

I happen to think a separate /home by default is a great idea, and you can have different defaults (with a slider people can change if they know what they're doing) depending on the size of the hard drive.

For example...

<60 GB hard drive - don't create a separate /home partition
60 to 120 GB hard drive - create a / partition of 10 GB and set the rest aside for /home
120 GB or more hard drive - create a / partition of 15 GB and set the rest aside for /home

---

### Post by FuturePilot on 2010-10-23
You answered your own question.

> **franzmaximilian said:**
> creating a separate partition for /home, but this is a bit more complicated and hard to implement for newbies.

---

### Post by aysiu on 2010-10-23
> **FuturePilot said:**
> You answered your own question.
The idea is that it is too complicated for new users to do on their own but that the installer would do it for them by default so they don't have to be bothered--the same way the current installer creates a swap partition for them by default without asking.

---

### Post by franzmaximilian on 2010-10-23
> **FuturePilot said:**
> You answered your own question.

Not exactly. Should Ubuntu create two partitions automatically, the newbie wouldn't even notice it.

Of course an algorithm would be need in the installer to decide which size to assign to the two partitions. I'm not a programmer and I cannot say if this would be very hard to do or if it would make the installer much heavier, but I doubt it would. Of course the option to operate manually (Advanced Setup) should remain.

---

### Post by perspectoff on 2010-10-23
The answer is in the clouds, my friend.

There are a lot of people who set up a distro then make a copy of the entire distro for re-creation in the cloud (e.g. in a virtual machine), or on another computer.

This is harder to do with multiple partitions. It is much easier to merely have one partition to copy from one place to the next.

Besides, the newer Ubuntu installer (at least in the "Regular Download" Desktop version) allows you to easily create multiple partitions (including a /home partition). Perhaps you didn't see that option?

---

### Post by aysiu on 2010-10-23
> **perspectoff said:**
> 
There are a lot of people who set up a distro then make a copy of the entire distro for re-creation in the cloud (e.g. in a virtual machine), or on another computer.

This is harder to do with multiple partitions. It is much easier to merely have one partition to copy from one place to the next. If you use CloneZilla, it'll automatically copy and restore all the partitions. If you use Remastersys, it ignores /home completely anyway (whether it's a folder or a separate partition).

> Besides, the newer Ubuntu installer (at least in the "Regular Download" Desktop version) allows you to easily create multiple partitions (including a /home partition). Perhaps you didn't see that option? Well, this would be the opposite behavior. By default Ubuntu would set up multiple partitions and people like you who insist on having just one whole partition would have the option to easily do so and see that option.

The proposal is a change in defaults, not a change in functionality.

---

### Post by perspectoff on 2010-10-23
There is a movie called Midnight Express where the guy tries to walk the opposite direction of the wheel.

Quote:

Ahmet: Where are you going? Why dont you walk the wheel with us? What is the matter my American friend?

---

