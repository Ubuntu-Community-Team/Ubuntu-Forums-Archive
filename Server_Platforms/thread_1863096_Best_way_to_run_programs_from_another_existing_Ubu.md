---
title: "Best way to run programs from another existing Ubuntu installation/partition"
date: 2011-10-17
forum: Server Platforms
---

### Post by sohelmk on 2011-10-17
Hi All,
Can someone please advise on following case :

I have 2-3 Ubuntu installations on my machine in different partitions. Now in one installation/partition (call it "ub64"), I want to run the programs installed in second partition (call it "ub32"). Now I have mounted ub32 paritions root as /ub32 inside ub64 installation. I was able to run java programs straight away as /ub32/opt/soapUI/soapUI.sh, but running programs that depend on linux binaries failed, for eg :/ub32/usr/bin/audacity

So is the above possible with chroot? (by configuring chroot with /ub32 directory instead of default /var/chroot )

Is this the best approach to use or are there better options?

With this approach are there any risks to the ub32 installation?

Thanks a lot,
Sohel.

---

### Post by vasile002 on 2011-10-17
can you please tell us why it failed? What error did you get? Most probably you can't run them because those need 32bit libraries installed.

Running from within the chroot will not do any harm so you can try that

---

