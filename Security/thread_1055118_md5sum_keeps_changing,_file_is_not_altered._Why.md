---
title: "md5sum keeps changing, file is not altered. Why?"
date: 2009-01-30
forum: Security
---

### Post by etlpkby on 2009-01-30
I'm running 8.10 on x86_64 and I've downloaded all updates etc. I'm trying to get the latest VMWare Workstation, and everytime I download I seem to get a different checksum with MD5SUM.

After about 6 attempts, I finally got a matching checksum. I left it there and came back a few hours later and re-did the checksum - it had changed! Repeated tries, and it keeps changing!

```
patb@serverwuss:~/News/Pan$ md5sum VMware-Workstation-6.5.1-126130.x86_64.bundle 
d51424f7b6dae9a255a4dee16fa09250  VMware-Workstation-6.5.1-126130.x86_64.bundle
patb@serverwuss:~/News/Pan$ md5sum VMware-Workstation-6.5.1-126130.x86_64.bundle 
63782cdc5119ad40cc1364e81a213eaf  VMware-Workstation-6.5.1-126130.x86_64.bundle
patb@serverwuss:~/News/Pan$ md5sum VMware-Workstation-6.5.1-126130.x86_64.bundle 
63782cdc5119ad40cc1364e81a213eaf  VMware-Workstation-6.5.1-126130.x86_64.bundle
patb@serverwuss:~/News/Pan$ md5sum VMware-Workstation-6.5.1-126130.x86_64.bundle 
63782cdc5119ad40cc1364e81a213eaf  VMware-Workstation-6.5.1-126130.x86_64.bundle
patb@serverwuss:~/News/Pan$ md5sum VMware-Workstation-6.5.1-126130.x86_64.bundle 
63782cdc5119ad40cc1364e81a213eaf  VMware-Workstation-6.5.1-126130.x86_64.bundle
patb@serverwuss:~/News/Pan$ md5sum VMware-Workstation-6.5.1-126130.x86_64.bundle 
63782cdc5119ad40cc1364e81a213eaf  VMware-Workstation-6.5.1-126130.x86_64.bundle
patb@serverwuss:~/News/Pan$ md5sum VMware-Workstation-6.5.1-126130.x86_64.bundle 
869f3c1d3a05245395670ea90485db1a  VMware-Workstation-6.5.1-126130.x86_64.bundle

```

Any ideas why? I hope it's not virus related nor hackers...

---

### Post by Dr Small on 2009-01-30
So, are you saying that the checksums are changing when you download, or while on your server?

---

### Post by etlpkby on 2009-01-30
They are changing whilst on my server. (see my attempts in 1st post above - those md5sum's changed 3 times within 30s of repeated cmds)

It also took about 6 attempts to download that VMware bundle from their official site that matched their published md5sum.

---

