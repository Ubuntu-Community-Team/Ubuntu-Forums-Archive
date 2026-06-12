---
title: "Swap partitions and Swap Files and truecrypt"
date: 2010-09-29
forum: Security
---

### Post by keljaden on 2010-09-29
When I install ubuntu, (or another Linux OS such as arch), I know I usually create a swap partition.  Is a swap file also created on the root or home partition by default as well that I do not know about?

If just the swap partition is created, can I just unmount it so when I mount a truecrypt container, it will now have the swap to accidentally write my password to it. Then after I unmount the container, I can just turn my swap back on.  (and yes I am aware if my system runs out of ram and no swap it will crash).

To clarify, if I unmount my swap before I use my truecrypt container, there is no way my password will end up on my hdd?

---

### Post by BkkBonanza on 2010-09-29
I don't believe a swap file is created separate from the swap partition.

See **man swapon** for info on turning on/off swap partitions.

Some users also setup encrypted swap partitions so that any data there is secured. 

Lastly, it's possible to wipe the swap partition as well. In the secure-delete package along with sfill, srm there is sswap and sdmem for swap and memory.

If you do use those tools don't use the default 39 pass crazy mode. Using -flz is adequate and a thousand times faster.

It would be very irresponsible for any program to put a password in a memory location that could end up in swap space. There's just no reason for it to end up there. Nowadays very little swap is ever used because we all have so much RAM. Documents containing large chunks of data could end up there but a few bytes for a password "on the stack" is just never going to end up in swap. Well, the conditions would have to be very extreme for program stack memory to be moved to swap. I'm sure that Truecrypt was designed with this in mind as well. However, there's no harm in keeping yourself busy with turning on/off your swap as far as I know. 

Well, except you may as well turn it off for the whole session because if data could end up in swap at all then you can't predict when it will do that. It could be moved to swap an hour after you turned it off and then on. I'm not saying it will do that but if being paranoid about swap then you have to go that far as well. Even if it did get to disk in swap there also has to be a way to identify it after using some known signature surrounding the password. Just speculation here.

---

### Post by keljaden on 2010-09-29
Thanks so much.  That's exactly what I was hoping to hear.

---

