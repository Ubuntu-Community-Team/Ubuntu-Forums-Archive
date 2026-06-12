---
title: "vbetool dpms off ---&gt; &quot;real mode call failed&quot;"
date: 2024-09-14
forum: Server Platforms
---

### Post by ulpin on 2024-09-14
Hello,

I have set up Ubuntu server 24.04 on a Fujitsu E558 Laptop. As the screen is almost never needed, I normally make use of ```
vbetool dpms off
``` by script to save energy. *All *works fine. After swapping the NVMe SSD into another and identically equipped E558, all behaves the same and works fine, *except *the vbetool command. It now throws a "real mode call failed" error.

The most common advice I found on the net is to temporarily remount /dev as exec instead of noexec before executing the vbetool command. As expected, that doesn't work in my case, as it's the very same software situation in both scenarios, so it can't be the reason. There must be differences in hardware or BIOS settings, I thought. I checked the latter and naturally, I found some differences, but nothing suspicious.

Any ideas on how to narrow down the cause further? Thanks in advance!

---

### Post by ulpin on 2024-09-14
Okay, after a more meticulous investigation, I found the solution myself: I changed two settings in the BIOS boot configuration. With Fast Boot disabled and CSM (Compatibility Support Module) enabled, the vbetool command works as expected. (I didn't check which of the two - or maybe both - was really responsible.)

---

