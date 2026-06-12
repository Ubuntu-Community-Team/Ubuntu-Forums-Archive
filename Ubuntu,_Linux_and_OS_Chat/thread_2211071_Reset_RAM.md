---
title: "Reset RAM"
date: 2014-03-14
forum: Ubuntu, Linux and OS Chat
---

### Post by mayagrafix on 2014-03-14
TIL that if you log out and log back in, the RAM and SWAP memory are reset to zeros or minimums for system. Great if you only reeboot every once in a while and use sleep mode all the time.

---

### Post by Donut50 on 2014-03-14
Really helpfull tip lad, thanks.

---

### Post by howefield on 2014-03-14
Not really a support thread, so moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by ssam on 2014-03-14
Linux uses otherwise unused RAM for caching disk. This makes things much faster, because retrieving thing from disk is slow. Try rebooting your computer (to clear the RAM), then launching a large program life libreoffice. Now close libreoffice and launch it again. The second time will be fast because the files required to start libreoffice were already cached in RAM.

If i run free -m in a terminal
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:         11835      10957        877       1515         22       6020
-/+ buffers/cache:       4915       6920
Swap:        15997         26      15971

```
It shows that I am using 10957 MB out of  11835 MB (basically 11GB of 12 GB). But you can also see that 6020 MB is caches, so really only 4915 MB are being used be programs. This is a good thing because it means that the system can avoid waiting for disk for any of the files that are already in RAM. If I were to launch a large program that needed to use several GB of RAM then linux can throw away some of the cache to make space.

---

### Post by forrestcupp on 2014-03-14
I'm not trying to be mean; I seriously want to know. But what is the benefit of clearing the data in the RAM? If the system needs the RAM, it should intelligently use unused space, even if it's not cleared to 0's. Unless you're worried about privacy issues, the only thing really important is how much RAM the OS registers as being used.

---

### Post by mayagrafix on 2014-03-25
My experience has showed me that the larger the SWAP file, the less responsive the CPU is. Reseting the SWAP to Zero is a cheap way of upping performance. I also have a newer desktop with 16 gb of RAM and it hardly ever uses SWAP (it also loads in 30 seconds so reebooting is an easy option), but my laptop is older and slower, and I mostly use the suspend mode instead of turning it off to save time and consecuently the SWAP file grows and grows. The RAM does not regroup on its own (this is known as memory leaks), so resetting to Zero is good practice.

---

### Post by 3rdalbum on 2014-03-26
Mate, if you have sixteen gigs of RAM on the computer, why on earth do you even have a swap partition? It'll never get used! You doing fluid dynamics modeling or something?

Just run 'sudo swapoff'.

---

### Post by mayagrafix on 2014-03-27
Tempting offer, but the SWAP file (and partition) does have its justification. Primarily needed for suspend option and or Vbox. However, if this desktop box were used only for gamming, I would turn off SWAP or adjust the "swappiness" (sudo vm.swappiness = x) to 10 or 15 instead of the normal 60 to use less of SWAP file function. My other PC, an older laptop, does use the SWAP file often and its good to clear once in a while to regain zippyness.

---

### Post by mayagrafix on 2014-03-27
> **3rdalbum said:**
> 
Just run 'sudo swapoff'.

This is not a bad idea. TIL that running "swapoff -a" and then "swapon -a" as root clears the SWAP file without reebooting. Yayy!

---

### Post by 3rdalbum on 2014-03-28
Suspend doesn't touch the swap at all. You're thinking of hibernation.

Even if you are using virtual machines, for a desktop computer 16 gigs of ram can run a LOT of VMs. 

Anyway I'm glad you found the swapoff command to be useful.

---

