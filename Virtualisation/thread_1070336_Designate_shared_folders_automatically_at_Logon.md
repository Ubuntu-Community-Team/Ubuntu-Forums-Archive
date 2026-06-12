---
title: "Designate shared folders automatically at Logon?"
date: 2009-02-15
forum: Virtualisation
---

### Post by ERoe on 2009-02-15
Hey all, I hope this is the right place to post this question, but I apologize in advance if it is not.

After trying numerous configurations, I have settled on a Windows host with an Ubuntu guest in Virtualbox. I finally figured out how sharing folders works, and use this command to enable it every time I fire up Ubuntu:

sudo mount -t vboxsf nameofshare /home/user/sharefolder

I have two different folders I share in this way, and it works great, without any third party programs clogging up the works. But I am fairly certain in researching this that I came across one tutorial that mentioned there was a way to get Ubuntu to "keep" these settings by running them automatically at Logon, so I don't have to manually enter it every time. I just can't remember where it was, though I am pretty sure it wasn't here.

Thanks in advance for any help :)

---

### Post by Perryg on 2009-02-15
> **ERoe said:**
> Hey all, I hope this is the right place to post this question, but I apologize in advance if it is not.

After trying numerous configurations, I have settled on a Windows host with an Ubuntu guest in Virtualbox. I finally figured out how sharing folders works, and use this command to enable it every time I fire up Ubuntu:

sudo mount -t vboxsf nameofshare /home/user/sharefolder

I have two different folders I share in this way, and it works great, without any third party programs clogging up the works. But I am fairly certain in researching this that I came across one tutorial that mentioned there was a way to get Ubuntu to "keep" these settings by running them automatically at Logon, so I don't have to manually enter it every time. I just can't remember where it was, though I am pretty sure it wasn't here.

Thanks in advance for any help :)



You can put it in your fstab.

(share name) what you called it in vbox , then the complete path to the share folder then vboxsf defaults 0 0.  example below

Shared /mnt/shared vboxsf defaults 0 0  <these are zeros>

---

### Post by ERoe on 2009-02-15
Thanks Perryg! That is exactly what I needed, and the way you explained it was very clear. Worked like a charm.

:D

---

### Post by Perryg on 2009-02-15
> **ERoe said:**
> Thanks Perryg! That is exactly what I needed, and the way you explained it was very clear. Worked like a charm.

:D

You are welcome.  Have fun with your Ubuntu!  It rocks!

---

