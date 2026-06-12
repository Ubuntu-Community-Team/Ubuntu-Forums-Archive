---
title: "Disk Cleaners"
date: 2019-08-07
forum: Virtualisation
---

### Post by merlot160 on 2019-08-07
Do VMs need CCleaner or something similar to keep them unclogged?

---

### Post by sevendogs1337 on 2019-08-07
No, Linux doesn't need anything like this. Windows does because it is horribly designed.

---

### Post by rbmorse on 2019-08-07
I think he was asking about a Windows VM running under some VM manager on a Linux host.  

I can't imagine running Windows in a VM would be different than running it directly on the hardware in this regard, but I don't know for sure.

---

### Post by #&amp;thj^% on 2019-08-07
Quick answer: every time you virtualize something, you get a penalty over running it on the bare hardware. That means that the OS running in virtual machine will run slower than if it would run directly on that same machine without virtualization layer.
That's true for any OS on commodity hardware, with exception for some exotic hardware that is purposefully built to support virtualization from the ground up - and that's not the off-the-shelf computer.
EDIT: I may have jumped the gun here, and rbmorse is right as far as the same needed tools IE: AntiVirus, DiskTools, and anything else the user would need to have in a Windows environment.

---

### Post by sevendogs1337 on 2019-08-07
OK, that makes sense. I should have asked what OS the VMs were - assumed Linux...

---

### Post by cruzer001 on 2019-08-07
Whether it be Linux guest or host the only gui cleaner I have used is Bleachbit.  Its a convenience, not a necessity.

[https://www.bleachbit.org/features](https://www.bleachbit.org/features)

```
sudo apt install bleachbit
```

---

### Post by merlot160 on 2019-08-07
Apologies, Windows 10 host, VM with Ubuntu.

---

### Post by TheFu on 2019-08-07
> **merlot160 said:**
> Do VMs need CCleaner or something similar to keep them unclogged?

I treat VMs just like physical machines.  My Windows VM is for just a few purposes and I install 1 new software item every year on it to do my taxes.  I don't leave important data on Windows and don't use it for email, web, or anything outside about 3-5 very specific uses, which don't involve the internet.

As for Linux/Ubuntu VMs, I treat them exactly the same as physical machines and basically do this:  [https://blog.jdpfu.com/linsysmaint](https://blog.jdpfu.com/linsysmaint) with 2018 updates to my 2011 LH article.

---

