---
title: "BSOD on hibernate and resume"
date: 2015-11-09
forum: Ubuntu Development Version
---

### Post by Hoeze on 2015-11-09
Hi, i recently installed Kubuntu 16.04 on my Acer V5-573G (i5 4200U, 8GB ram, NVIDIA GT 750M).  
I'm using only the Intel IGP: 
```
 # glxinfo |grep -i "opengl vendor"
OpenGL vendor string: Intel Open Source Technology Center
```

Now everytime I hibernate and resume, the Kubuntu logo appears, I can enter my encryption password, but after some seconds my display simply gets powered off.  

Is there any solution / workaround for this problem? 
I already tried some tricks, like directly hibernating from virtual terminal, but these did not help. I noticed, that, when pressing F12 at the password prompt, the display does not show any boot info.

---

### Post by howefield on 2015-11-09
Thread moved to the "*Ubuntu Development Version*" forum.

Assuming that you know 16.04 has barely begun development.

---

### Post by syntaxerror74 on 2015-11-09
Wait...a BSOD in Linux? ;-) Must be redefined as "Black Screen of Death", methinks. :p

---

### Post by grahammechanical on 2015-11-09
> **Hibernation** (or **suspend to disk**) in computing is powering down a computer while retaining its state. Upon hibernation, the computer saves the contents of its [random access memory]("https://en.wikipedia.org/wiki/Random_access_memory") (RAM) to a [hard disk]("https://en.wikipedia.org/wiki/Hard_disk") or other [non-volatile storage]("https://en.wikipedia.org/wiki/Non-volatile_storage").  Upon resumption, the computer is exactly as it was before entering  hibernation. Like a powered down system, the power source from a system  in hibernation can be removed without any state loss risk.

    

[https://en.wikipedia.org/wiki/Hibernation_%28computing%29](https://en.wikipedia.org/wiki/Hibernation_%28computing%29)

So, on the principle of eliminating the obvious, I will ask the stupid questions? How large is the swap partition? Larger than 8 GB?

Regards.

---

### Post by Hoeze on 2015-11-09
> **syntaxerror74 said:**
> Wait...a BSOD in Linux? ;-) Must be redefined as "Black Screen of Death", methinks. :p

Yes, thats what I meant :D

> **grahammechanical said:**
> [https://en.wikipedia.org/wiki/Hibernation_%28computing%29](https://en.wikipedia.org/wiki/Hibernation_%28computing%29)

So, on the principle of eliminating the obvious, I will ask the stupid questions? How large is the swap partition? Larger than 8 GB?

Regards.

8071MB swap and 7864MB ram says htop.

---

### Post by Hoeze on 2015-11-14
Nobody a hint?

---

### Post by ronacc on 2015-11-14
if you can , try increasing your swap , 2 times ram is a good  rule of thumb .

---

### Post by Hoeze on 2015-11-15
I did some further testing:
Resuming works, as long as I am not logged in, so I assume it's a problem with the KDE desktop...

By the way: Why kills Kubuntu disk encryption my ssd performance?
Using 512bit aes-xts-plain64 my transferrates reduce to 130Mb/s copying a large file, and IOPS to 6K (Crucial M500 240GB), compared to only using ext4 with 170Mb/s.
Cryptsetup benchmark says, my cpu can handle 1400Mb/s...

---

