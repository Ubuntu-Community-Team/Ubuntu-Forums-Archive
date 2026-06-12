---
title: "keys stored in ram as plaintext during hibernation?"
date: 2016-05-10
forum: Security
---

### Post by PaulBx on 2016-05-10
I installed Lubuntu a while back, now at 14.04LTS, using full disk encryption. It was the automated process so I ended up with swap which I normally do not use, so I just went in /etc/fstab and commented the swap line out. I was just reading about a less automated process here:

[https://thesimplecomputer.info/full-disk-encryption-with-ubuntu](https://thesimplecomputer.info/full-disk-encryption-with-ubuntu)

I ran into this which was rather disturbing:
> These instructions give you an encrypted swap with working hibernation.  If you don't want a swap partition, skip where it's mentioned but know  that when the computer is sleeping, your decryption key(s) will be  stored in RAM as plaintext.

I'm not sure if what happens when I close my laptop lid is hibernation, but I'm guessing so. I also know my key is in ram during normal computer use - can't do much about that - but when it is sleeping I don't want it there. So, I was thinking of re-enabling swap just to get around this. But now I remembered I have 4 zram devices that are also used as swap so maybe it is storing the key there? Unfortunately these are cleartext (although compressed) so that is no help.

I'm guessing zram is what I am seeing when I type the "free" command:
```
$ free
             total       used       free     shared    buffers     cached
Mem:       5974904    1936528    4038376      77192     170792     806320
-/+ buffers/cache:     959416    5015488
Swap:      2987440          0    2987440

```

My question is, how do I get the OS to store the key in my encrypted swap partition rather than in zram?

---

### Post by HermanAB on 2016-05-16
It is best to encrypt all of your disk, as well as all the swap space.

How to encrypt swap is explained in the swapon man page.

---

