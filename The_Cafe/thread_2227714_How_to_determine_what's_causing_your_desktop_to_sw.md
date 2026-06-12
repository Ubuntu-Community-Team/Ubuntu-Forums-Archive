---
title: "How to determine what's causing your desktop to swap?"
date: 2014-06-03
forum: The Cafe
---

### Post by m-dw on 2014-06-03
It's Google Chrome and/or Chromium browser.

Discuss!

---

### Post by cariboo on 2014-06-04
I think if you want some discussion, you'd better explain what it is you want to discuss. My system has 16GiB of ram, and the only time it even comes near to using any swap is if I have a couple of VM's running, I have allocated 4 cores and 8GiB of ram to Windows 8, and all other VM's have 2 cores and 4GiB of ram:

```
free -m
             total       used       free     shared    buffers     cached
Mem:         15946      15551        394         45        105      13537
-/+ buffers/cache:       1908      14037
Swap:         1999          1       1998
```

---

### Post by DuckHook on 2014-06-09
If it's purely about swap and swap is hitting the HD hard, then the best way I've found is to install/run iotop using the -o option and look for what processes hog the HD.```
sudo apt-get install iotop && sudo iotop -o
```It's not the be-all-end-all. In *cariboo907*'s case, it won't tell you what specific processes *within* a VM are the culprits and will just maddeningly cite the *general* VM process instead. But for most independent Linux processes, it will give at least an idea of what is causing the logjam.

---

### Post by SeijiSensei on 2014-06-10
Not enough physical memory.  What else?  ;) Many apps have such large footprints these days that I think 4GB is becoming the minimum memory size needed to avoid a lot of swapping.

If you're seeking culprits, browsers are probably a good place to start.  If I have both Firefox and Thunderbird running on my 1.8 GB Atom machine, switching between them can sometimes take a minute or two.  I have a lot of mail folders so my TBird instance is also fairly large.

---

