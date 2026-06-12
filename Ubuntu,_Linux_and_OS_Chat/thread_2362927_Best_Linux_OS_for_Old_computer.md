---
title: "Best Linux OS for Old computer"
date: 2017-06-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Camilia on 2017-06-03
Updates of Ubuntu 16.04 are slowing my PC down. For example when I open up thunderbird mail it takes longer to receive mail. My PC is 
HP bought in 2005. It has Memory 2.7 GIB and Processor AMD Athlon(tm) II X2 250 Processor × 2 and Disk 627.0 GB. Requirements of mint 17.3 are 512MB RAM (1GB recommended for a comfortable usage). 9GB of disk space. There are so many versions of mint and Ubuntu, such as mint mate and ubuntu mate, that I don't know which is best. 

Suggestions?

---

### Post by poorguy on 2017-06-03
I would give Lubuntu 16.04 a try as I have always had good results using it on older computers.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by Camilia on 2017-06-03
> **poorguy said:**
> I would give Lubuntu 16.04 a try as I have always had good results using it on older computers.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
I wrote I have that 1 and the updates are slowing my PC down. This thread is for finding something different.

Please excuse me I see now it is Lubuntu not ubuntu

---

### Post by Bucky Ball on 2017-06-04
Yes, Lubuntu. That or Xubuntu would be your best hope, probably Lubuntu. Not surprised Ubuntu is slowing down your machine. Lucky its grinding along at all! ;)

---

### Post by RobGoss on 2017-06-04
On older machine the full Ubuntu desktop like 16.04, will run as intended because it requires more resources to run efficiently. If this is something you really want to do you can always try increasing your Ram

The lighter distributions are the best choice for older machines and may do a lot better. It's also good to try different OS's to see which ones will perform the best

---

### Post by LastDino on 2017-06-04
Hardware dating back to 2005 is tough cookie, you will need to go Lubuntu way, could also try others like eOs,  Pixil or Puppy. Imo, on such a machine, I would even try to start with bare-minimum Arch and then install lx gui. 

I would personally suggest to spend some on SSD and try to get recycled RAM (that will be tough and useless investment for longer term as it is going to be older model), but SSD is good investment. Could even put SWAP on it. 

On this machine running even modern web browser is going to eat up all your RAM.

Mate desktop is light, but it is not as light as Lxde.

---

### Post by kurt18947 on 2017-06-04
> **LastDino said:**
> Hardware dating back to 2005 is tough cookie, you will need to go Lubuntu way, could also try others like eOs,  Pixil or Puppy. Imo, on such a machine, I would even try to start with bare-minimum Arch and then install lx gui. 

I would personally suggest to spend some on SSD and try to get recycled RAM (that will be tough and useless investment for longer term as it is going to be older model), but SSD is good investment. **Could even put SWAP on it. **

On this machine running even modern web browser is going to eat up all your RAM.

Mate desktop is light, but it is not as light as Lxde.

I was under the impression that putting a swap partition on an SSD wasn't a great idea; the thinking being that the swap partition may have a lot of write activity thus creating rapid wear on a small portion of the SSD. Personally, if I feel the need for swap, I create a swap **file** rather than a swap **partition.** I think Ubuntu is going this route starting perhaps with 18.04(?). Hibernation wouldn't work but my understanding is that hibernation doesn't work well anyway so no real loss.

---

### Post by vasa1 on 2017-06-04
> **kurt18947 said:**
> ... I think Ubuntu is going this route starting perhaps with 18.04(?). ...
Looks like it is in 17.04 already:
[http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)

---

### Post by LastDino on 2017-06-04
> **kurt18947 said:**
> I was under the impression that putting a swap partition on an SSD wasn't a great idea; the thinking being that the swap partition may have a lot of write activity thus creating rapid wear on a small portion of the SSD. Personally, if I feel the need for swap, I create a swap **file** rather than a swap **partition.** I think Ubuntu is going this route starting perhaps with 18.04(?). Hibernation wouldn't work but my understanding is that hibernation doesn't work well anyway so no real loss.

That is true. But its a trade off I do with less than 2GB RAM machines so system doesn't crash. Honestly though, even with older hardware and 2 GB RAM with systems intended use of light net browsing and taking prints, it has never used the SWAP partition, just for sake of safety I do it. Plus, I can easily use it to run different machines with same SSD without having to make new SWAP and editing fstab

Though, your point is valid, lot of write activity can indeed put wear on that SSD. I've never tried SWAP File, so can't comment.

---

### Post by poorguy on 2017-06-04
> **kurt18947 said:**
> I was under the impression that putting a swap partition on an SSD wasn't a great idea; the thinking being that the swap partition may have a lot of write activity thus creating rapid wear on a small portion of the SSD.

That being the case why not just lower the [COLOR=#0000ff]unreasonable high swappiness of 60 [/COLOR]down to a [COLOR=#0000ff]more reasonable # 1[/COLOR]. This will reduce the amount of write activity to the SSD.

---

### Post by Camilia on 2017-06-04
> **LastDino said:**
> 
I would personally suggest to spend some on SSD and try to get recycled RAM (that will be tough and useless investment for longer term as it is going to be older model), but SSD is good investment. Could even put SWAP on it. 

Mate desktop is light, but it is not as light as Lxde.
What is SSD? What do you me by SWAP?

---

### Post by Camilia on 2017-06-04
> **kurt18947 said:**
> I was under the impression that putting a swap partition on an SSD wasn't a great idea; the thinking being that the swap partition may have a lot of write activity thus creating rapid wear on a small portion of the SSD. Personally, if I feel the need for swap, I create a swap **file** rather than a swap **partition.** I think Ubuntu is going this route starting perhaps with 18.04(?). Hibernation wouldn't work but my understanding is that hibernation doesn't work well anyway so no real loss.
Creating a swap is not something I want to do for I don't understand it. Thus I will be probably do more harm with it than good.

---

### Post by poorguy on 2017-06-04
SSD
[https://en.wikipedia.org/wiki/Solid-state_drive](https://en.wikipedia.org/wiki/Solid-state_drive)

> **Camilia said:**
> What do you me by SWAP?

[https://rudd-o.com/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](https://rudd-o.com/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

---

### Post by wxboss on 2017-06-04
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm) This is a different distro, but it looks good for older machines.

[https://www.youtube.com/watch?v=mUdEI2bDWFQ](https://www.youtube.com/watch?v=mUdEI2bDWFQ)

---

### Post by kurt18947 on 2017-06-04
My machines have 4 GB+ so I don't generally worry about swap. One time I did create a swap file was with Ubuntu Gnome running Virtualbox and a Windows 10 64 bit guest given 2 GB RAM. Having both OSs working would pretty much fill 4 GB so I had a 4 GB swap file just in case. No instability or other problems but a Core i5 would get pretty warm:).

---

### Post by Camilia on 2017-08-17
I had been putting off installing new software for that means I have to reset passwords for my email address. After a problem occurred making it impossible to download any programs I installed Mint 17.3 Rosa MATE. 

Since installed Mint everything is running faster.

---

### Post by kurt18947 on 2017-08-19
> **Camilia said:**
> I had been putting off installing new software for that means I have to reset passwords for my email address. After a problem occurred making it impossible to download any programs I installed Mint 17.3 Rosa MATE. 

Since installed Mint everything is running faster.

Very good! Was it as hard as you expected? I'll bet not but there were unfamiliar terms.

---

