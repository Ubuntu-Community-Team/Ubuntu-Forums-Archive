---
title: "lucid server: Is there any need of a swap partition?"
date: 2010-08-13
forum: Server Platforms
---

### Post by _teo_ on 2010-08-13
While installing Ubuntu servers I am always dedicating a partition of the size of the RAM the machine has for swap. However colleagues of mine told me that they do not see any need for that and simply are not using a swap partition. It all depends of the type of applications that are working on the server, but they are giving it enough RAM and that's it. I read somewhere that for the desktop installation Ubuntu is using the swap for suspending and hibernation, but servers are different.

So, do I need a swap partition for Ubuntu Lucid Server (32 and 64 bit versions)?

PS: I googled but found no satisfying answer

---

### Post by arrrghhh on 2010-08-13
You technically don't *need* a swap partition on a server, no.  If you ignore hibernation, you don't really need it on the desktop either.

However, why wouldn't you create one?  It's not like it takes up that much hdd space, and it's there if it's needed.  Unlike Windows, Linux will ONLY swap when it needs to.  It won't just use swap at random, only if you run out of RAM.

Just seems like a bad idea to run without any sort of a swap.  If your RAM fills, what do you do?  I'm assuming the server would crash or hang... definitely wouldn't be happy.

---

### Post by CharlesA on 2010-08-13
> **arrrghhh said:**
> You technically don't *need* a swap partition on a server, no.  If you ignore hibernation, you don't really need it on the desktop either.

However, why wouldn't you create one?  It's not like it takes up that much hdd space, and it's there if it's needed.  Unlike Windows, Linux will ONLY swap when it needs to.  It won't just use swap at random, only if you run out of RAM.

Just seems like a bad idea to run without any sort of a swap.  If your RAM fills, what do you do?  I'm assuming the server would crash or hang... definitely wouldn't be happy.

+1 to that.

I'm running 6GB of RAM on my server so the swap partition is around 12GB in size. The OS drive is a 320GB drive, so 12GB isn't going to be missed. 

You can run fine without swap, but if you run out of memory, yer server is not going to be very happy.

---

### Post by druhboruch on 2010-08-13
You could also use a swapfile instead.
It is as good as swap partition and you can configure/change the size as needed

Just install dphys-swapfile from the repo.

In lucid you must manually create configuration file before you install the package due to a bug. 
It doesn't calculate default size and builds very large file on the disk.  It may be fixed by now,

---

### Post by HermanAB on 2010-08-14
Howdy,

You don't even need to install anything to use a swapfile.  Just read 'man swapon'.

---

### Post by _teo_ on 2010-08-14
So, technically it is possible, but not recommended. Thank you all for taking time to answer.

> **CharlesA said:**
> I'm running 6GB of RAM on my server so the swap partition is around 12GB in size. The OS drive is a 320GB drive, so 12GB isn't going to be missed.

@CharlesA: Why are you allocating twice as much swap as the RAM you have?

Another question that I am asking myself is: let's say I have a small server with just 2GiB RAM and I have a swap partition of 2GiB. After some time I decide to double its RAM to 4GiB. What should I do with the swap?

---

### Post by CharlesA on 2010-08-14
> **_teo_ said:**
> 
@CharlesA: Why are you allocating twice as much swap as the RAM you have?

Another question that I am asking myself is: let's say I have a small server with just 2GiB RAM and I have a swap partition of 2GiB. After some time I decide to double its RAM to 4GiB. What should I do with the swap?

I just left it at the default when I installed, and the default is 2x the amount of RAM.

If you are going to upgrade the RAM later, might as well have a set it to have a larger swap if you want. You could mess with the partitions, but that can get messy.

---

### Post by nmaster on 2010-08-14
> **arrrghhh said:**
> Linux will ONLY swap when it needs to.  It won't just use swap at random, only if you run out of RAM.

not true.  linux will use swap when it needs to, but the need is defined by the swappiness. read more here: [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

### Post by Bachstelze on 2010-08-14
> **_teo_ said:**
> 
Another question that I am asking myself is: let's say I have a small server with just 2GiB RAM and I have a swap partition of 2GiB. After some time I decide to double its RAM to 4GiB. What should I do with the swap?

Nothing. 2 GiB is probably much more swap than enough already. I say "probably" because obviously that depends on what you do with your server, but if 2 GiB was enough swap with 2 GiB of RAM, I can't see how it suddenly wouldn't be enough when you add more RAM.

---

### Post by _teo_ on 2010-08-15
> **nmaster said:**
> not true.  linux will use swap when it needs to, but the need is defined by the swappiness. read more here: [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

Thanks for the URL.

Obviously using a swap partition is preferred above a swap file. I will continue using swap partitions regardless what my colleagues are doing

---

### Post by conradin on 2010-08-15
I was just at a Linux Server Performance conference where we discussed this. I would go with keeping a swap space for 2 reasons. 1, to have some reserved space for an OS if the FS ever got too buggy and crashed, i could install to the swap space and do a quick recovery. & 2, obviously if you need it its there. 

The Confrence I attended was more about system performance and ensuring your computer is rarely working the swap space. 
[http://events.linuxfoundation.org/slides/2010/linuxcon2010_hoch.pdf](http://events.linuxfoundation.org/slides/2010/linuxcon2010_hoch.pdf)

I'm really not sure about the back end of the swapiness, but it would seem more proficient to control system performance enough to know just what will be forcing files into sawp, or to know how effective / efficient the system is using its resources. To know if a swap space is being effectively utilized alongside other system components is the real question. 

OoB, Ubuntu has vmstat, but the sysstat package is also useful to monitor system performance.

---

