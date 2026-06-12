---
title: "Hardware upgrade and existing RAID"
date: 2011-04-20
forum: Server Platforms
---

### Post by erasmix on 2011-04-20
Hello There,

I have an old server I build 7 years ago. I have a RAID5 with 5x2TB HD's and I'm planning a major hardware overhaul. My server currently runs on a Pentium4 3.2 Ghz (pre multicore technology) on a SuperMicro mobo. I'm planning to switch to an AMD Phenom II X6 1100T Black Edition Thuban 3.3GHz, 3.7GHz Turbo 6.

So here's the question. Can I just plug my drives to the new board and restart the RAID like nothing happened? I don't have space to backup all my data if I have to recreate the RAID from scratch.

Thanks,
Erasmo.

---

### Post by falko on 2011-04-20
I think this is a trial and error thing. Sometimes it works, sometimes not.

---

### Post by usatonycuba on 2011-04-20
Almost certainly not.. but as falko says
> **falko said:**
> ...Sometimes it works, sometimes not.

---

### Post by Grenage on 2011-04-20
> **erasmix said:**
> Hello There,

I have an old server I build 7 years ago. I have a RAID5 with 5x2TB HD's and I'm planning a major hardware overhaul. My server currently runs on a Pentium4 3.2 Ghz (pre multicore technology) on a SuperMicro mobo. I'm planning to switch to an AMD Phenom II X6 1100T Black Edition Thuban 3.3GHz, 3.7GHz Turbo 6.

So here's the question. Can I just plug my drives to the new board and restart the RAID like nothing happened? I don't have space to backup all my data if I have to recreate the RAID from scratch.

Thanks,
Erasmo.

A 'proper' RAID solution will store the RAID metadata on both the drives and controller - I don't know if 'fake' RAID solutions do it that way.  If it was the exact same controller on a new board, you might have a chance, but I'd work on the assumption that it will fail.

---

