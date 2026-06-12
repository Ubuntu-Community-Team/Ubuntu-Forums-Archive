---
title: "intel xeon problems."
date: 2006-05-14
forum: Server Platforms
---

### Post by warlocky on 2006-05-14
Im having problems with my processors.
Im using intel xeon 3.0 64bits (2 of these) and 2gb ram.

Only one is working, Atleast it looks like it.
Im not a pro in ubuntu, nor am i very familiar with it eaither.

I installed this ubuntu version:
ubuntu-5.10-install-i386.iso

Is there a way to fix this without having to reinstall everything?
If so, how?
And if not, what version should i use and how can i configure it to get it to work?

((please note, Im not a pro at ubuntu, I just know the basics.

---

### Post by zac1333 on 2006-05-14
I'm no expert, but normally when I have dual processors, once Ubuntu is initially installed, I have to load the SMP kernel to get it to recognize both processors.  To do this, go to a terminal and type:
```
sudo apt-get install linux-image-2.6.12-10-686-smp
```

Then reboot and you should be good to go.  Anyone feel free to correct me if i'm wrong.  I'm not sure if it's the same kernel for 64-bit?

---

### Post by LerninLinux on 2006-05-16
Is there a default kernel, for the live cd, that could work with as many as four processors?  I am trying to find a version for hardware that needs to be booted to check for damage, when the normal software on it, is propriatary and locked down.

---

