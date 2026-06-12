---
title: "Encrypting swap space breaks standby/lock screen"
date: 2010-01-07
forum: Security
---

### Post by dogdo on 2010-01-07
Hi

As part of making a encrypted private folder i told encfs to encrypt swap space on my pc knowing that this would probably break sleep and hibernation. That said i just turned on ubuntu for 5 mins, had to go away for a bit, when i came back to unlock the screen my password was not being accepted, and another 5 mins later the screen said that my session had timed out-i had to do a cold reboot :( Does this mean i cant lock the screen anymore?

---

### Post by BkkBonanza on 2010-01-07
Maybe related to encrypted swap but definitely not encrypted private or home. 
I have that and can lock/unlock screen fine, and sleep no problem either.

---

### Post by dogdo on 2010-01-07
> **BkkBonaza said:**
> Maybe related to encrypted swap but definitely not encrypted private or home. 
I have that and can lock/unlock screen fine, and sleep no problem either.

But is your swap drive encrypted or just your home folder? i was told that not having the swap encrypted might mean that some data might be retrievable as clear text.

---

### Post by BkkBonanza on 2010-01-07
I don't encrypt swap. It is possible to recover info from swap. 
You don't have to have swap. If you monitor how much you are using you may find it is hardly touched anyway.

to see how much is being used in swap,

free

to disable swap for the current session and see how it impacts your work,

sudo swapoff -a

---

### Post by dogdo on 2010-01-07
But what does swap do in the first place? i have all my important files backed up but before executing that sudo command id like to know what exactly im doing to my hard drive first.

---

### Post by BkkBonanza on 2010-01-07
The swap partition is an area of the drive that is used as virtual memory swap space. When not enough memory is availble the kernel will move pages of memory to disk and back to provide the appearance of having more memory.

If you have enough memory then nothing much gets swapped out. If you don't have swap space then the worst that happens is you don't have enough memory and either things won't be able to run or they run slower.

Nowadays most people have so much RAM that they hardly touch the swap. It is a hangover form the days when RAM was costly and less was available. 

I have 2 GB on my notebook and that's not much today. But even so I use conky to view my system stats on my desktop and I never see more than a few MB in swap, and likely even that doesn't need to be there.

There is no permanent data in swap - isn't kept intact across boots.

That swap command simply unmounts the swap partition so that it is not available to the kernel any more. To make the change permanent you have to comment out the swap line in /etc/fstab

---

### Post by dogdo on 2010-01-07
So is the data stored in swap basically volatile memory-once you turn off or reboot the data if stored here is erased? 

If swap is a throwback to when ram was expensive then why is it still used today? im using ubuntu 9.10 with 3 gb of ram though i do have 4gb but the last gb cant be seen for some reason.

---

### Post by BkkBonanza on 2010-01-07
It isn't erased. It is just left behind and new allocations are made next time you boot. This is the reason why some people like to encrypt it - because remnants of old data are still lingering around. But when they encrypt it they use a "session key" only good for one boot, so that any time later the data is non-decryptable.

Look, if you don't get what I'm saying try reading up on it at Wikipedia. They have an extensive write up here,

[http://en.wikipedia.org/wiki/Swap_partition](http://en.wikipedia.org/wiki/Swap_partition)

I'm not suggesting you disable your swap if you need it. I'm saying you can see how much is being used (with "free" command) and if none or very little then disabling it will have no effect and it will mean your precious data isn't being left laying around  after you shut the power off.

---

