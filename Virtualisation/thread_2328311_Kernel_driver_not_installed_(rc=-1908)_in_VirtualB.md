---
title: "Kernel driver not installed (rc=-1908) in VirtualBox"
date: 2016-06-19
forum: Virtualisation
---

### Post by cblnchat on 2016-06-19
Hey there,

I Googled this a bit and found a few answers, but none that worked. As well as a few places that found the answer somewhere, but the link was dead :lolflag:

Anyways, I've never come across this issue before and I have no idea how to fix it.

Thanks for any help!

---

### Post by QDR06VV9 on 2016-06-20
This might be a different method, but not that different:

```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

For myself the install _**virtualbox-dkms**_ command was actually failing applying the fix. By fully purging the package things got back to normal.
Any way I hope this works for you too.
Regards

---

