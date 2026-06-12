---
title: "I might be a bit paranoid (rootkits)"
date: 2009-02-05
forum: Security
---

### Post by SpinningAround on 2009-02-05
Well this might be slightly hardcore but I was thinking if I run a program in wine can that program scan my computer then in the background? I was wondering if I'm forced to configure apparmor to get enough protection or is't even possible to block?

I'm thinking about things like this
[http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal](http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal)

---

### Post by cdenley on 2009-02-05
Programs run in wine have access to any paths you have mapped as drives, which by default includes the entire filesystem.
```

winecfg

```
Of course, it can only access the filesystem as the user you're running wine as.

---

### Post by e1mer on 2009-02-05
This looks like a job for VMWare.
If you run your CD in a virtual machine, then the rootkit
is installed in the virtual boot sector.

If you take a snapshot before you run it, then revert to the
snapshot, you are free from any malware.

I sometimes get my virtual machine infected on purpose just
for fun.

---

### Post by Koori23 on 2009-02-05
Don't ya love that? "Hey, I wanna install Windows 2000, not update it at all and see how many websites I can it before I get nailed with something"

When you've had your fun, just kill the VM. 

I've managed to have spybot report over 1000 malware (not tracking cookies) infections before Windows wouldn't work anymore. I was proud of myself. At the end I decided that porn sites really were "dirty" in more ways than one.

---

### Post by abn91c on 2009-02-05
If you are really paranoid install **rkhunter** to scan your computer

---

### Post by jrusso2 on 2009-02-05
> **SpinningAround said:**
> Well this might be slightly hardcore but I was thinking if I run a program in wine can that program scan my computer then in the background? I was wondering if I'm forced to configure apparmor to get enough protection or is't even possible to block?

I'm thinking about things like this
[http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal](http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal)

Are you running an SSH server or any other server facing the internet? If so this is the most likely way you can get a root kit.

---

### Post by SpinningAround on 2009-02-08
> **jrusso2 said:**
> Are you running an SSH server or any other server facing the internet? If so this is the most likely way you can get a root kit.

No I only was thinking that some program that I installed in wine might install a rootkit also, like Sony's CD did.

I don't think I have any server running, unsure if Deluge can be counted as one it at lest got ports open to the internet?

---

### Post by zerofool2005 on 2009-02-09
I used to run VM with a unpatched SP1 xp. With all my ports open. See how long it would take to get infected and log all the traffic to the otnet. And go on their IRC to say hi. And to remove the bots.

Oh skiddies these days

---

