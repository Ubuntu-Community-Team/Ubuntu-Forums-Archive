---
title: "Erase Swap at Shutdown?"
date: 2010-01-04
forum: Security
---

### Post by gobbles414 on 2010-01-04
I want Ubuntu 9.10 to automatically erase all data on the swap partition during shutdown. I understand that will increase shutdown time, but the security benefits are worth the extra time. Thanks in advance for your help!

---

### Post by garryknight on 2010-01-04
The sswap utility from the secure-delete package is possibly the best tool for this.

---

### Post by BkkBonanza on 2010-01-04
Probably the way you want to do this is to create an upstart script that unmounts the swap device and wipes it.

I can give you a sample of how this would work but I haven't tried this on my system so it's just something to work from. In particular I don't know if this will hold up the shutdown until it's completed. The docs for upstart may help further at,

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)
[http://upstart.ubuntu.com/wiki/](http://upstart.ubuntu.com/wiki/)

Create a file /etc/init/wipeswap.conf containing,
```

# upstart config - wipes swap space on shutdown

description  "Wipes swap space on shutdown"

start on (runlevel [016] and stopped gdm)

script
  swapoff -a
  sswap -lz /dev/sda3
end script

```
Notes: 
I put in /dev/sda3 as swap device - yours may be different.
I used the sswap command from the secure-delete package to wipe the swap. 
You could do it differently and likely faster with dd.

---

### Post by gobbles414 on 2010-01-06
Thank you garryknight and BkkBonaza for your ideas. I will post again after I've had time to experiment with the sswap utility. Thanks again!

---

### Post by Mister.Vash on 2010-01-07
You may want to instead look at setting up your system to encrypting your swap partition.  It can be setup so that the encryption key for the swap is randomly generated each time linux is started, which means that the data in the swap will only be accessible during that session. 

A starting place withe some information about it can be found here.

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)


The reason I make that recommendation versus doing the wipe as your were thinking is that it leaves open scenarios where it won't happen.  First, and probably mostly likely, thing that came to mind was a power outage - you loose power and the script does run.  Utilities can go out, someone trips over the cord, etc...  Just thought I would bring that up as another option for you.

---

### Post by dmizer on 2010-01-07
Or, you could just not use swap at all.

Many modern computers have more than enough memory, so swap is not really needed.

---

### Post by BkkBonanza on 2010-01-07
I tend to favour this last one - no swap. I have found that nowadays so little swap is used anyway that it wouldn't even be noticeable.

---

### Post by gobbles414 on 2010-01-07
Thanks Vash, dmizer, and BkkBonaza for your ideas!

What would be the performance penalty for encrypting swap? That is, how much slower would my computer run with encryption enabled than it does with encryption disabled?

My current computer has only 2 GB of RAM. Without swap, could I still do tasks such as photo editing (raw files) while simultaneously listening to music and surfing the internet? I also use my computer to play DVDs on an external monitor while surfing the internet on the computer's built-in screen. Would I need swap for that?

Thank again!

---

### Post by BkkBonanza on 2010-01-07
Encryption has barely a noticeable speed penalty. I've heard reports of from 1% to 5% so I'd put it in that range.

I'd do a test. Get a bunch of things going and edit a couple photos at once. Open the system monitor, menu item System, Admin, System monitor and let it run while you do this. Check in now and then and watch the resources graph for swap usage, and for free memory usage. If swap goes way up then you may have issues when it's gone. If swap hardly changes then you're not going to notice it missing. As programs need more memory they allocate it via system calls. When there isn't enough real memory the kernel starts to page memory out to swap and supply new allocations from the memory freed up by the paging.

---

### Post by HermanAB on 2010-01-08
Yup, encrypt your swap.  Read the swapon man page for details. There is no performance penalty.

Running without swap can cause a lock-up condition if some process runs out of memory, so it is best to always have swap defined even if you have so much RAM that it doesn't seem to get used.

---

### Post by Jordanwb on 2010-01-08
On one machine what I did was used /dev/urandom as a keyfile with luks. Everytime the machine started luks but read 128 bytes and recreated a swap volume on the encrypted partition.

---

### Post by gobbles414 on 2010-01-26
Thanks for all your ideas! I've gotten really busy at work, so it'll be at least a few weeks before I can try any of them. Until then...

---

