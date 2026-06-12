---
title: "[SOLVED] Rebuilding degraded raid 5 array on a different system."
date: 2008-12-05
forum: Server Platforms
---

### Post by Duge Hong on 2008-12-05
I was trying rebuild my mdadm raid 5 array on a different system but one of the drives failed and I don't have access to the machine that the array was original on. 

So is it possible to rebuild the array with only 2 of the 3 drives on a different machine. I don't know exactly how to go about this and any help would be greatly appreciated.

---

### Post by hyper_ch on 2008-12-05
I can't quite follow what you want/need to do. What do you mean you don't have access to the machine that th array way original on?

---

### Post by stefangr1 on 2008-12-05
> **Duge Hong said:**
> I was trying rebuild my mdadm raid 5 array on a different system but one of the drives failed and I don't have access to the machine that the array was original on. 

So is it possible to rebuild the array with only 2 of the 3 drives on a different machine. I don't know exactly how to go about this and any help would be greatly appreciated.

Yes, that should indeed be possible. If the os is on the RAID5 array you can just boot, enter grub and continue in repair mode, than further start your system normally, end than rebuild your array from the gui.

If the os is on a different partition, the problem is even less, since you can just add a disk an rebuild from there.

---

### Post by Duge Hong on 2008-12-05
What I'm trying to do is build the array on a different system but only have 2 working drives of the 3 original and the system it was on to start with is now in a different state.

The array doesn't contain the OS.

I figured I could still rebuild it seeing how it was raid 5 but I don't know how to do it, everything I try doesn't seem to work.

---

### Post by hyper_ch on 2008-12-05
2 out of the 3 are sufficient to rebuild the array.

Is it a hardware of software raid?

---

### Post by Duge Hong on 2008-12-05
Its software.

---

### Post by Duge Hong on 2008-12-05
Never mind I was able to figure it out it wouldn't assemble because the device names changed. Thanks for your help.

---

