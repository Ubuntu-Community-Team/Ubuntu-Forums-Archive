---
title: "No sound............"
date: 2009-11-04
forum: Ubuntu Moblin Remix
---

### Post by Harshana on 2009-11-04
Hi everybody........
I netbook is HP mini 110-1001tu.I installed UNR and i like it very much.It is faster and easier than windows.And also i think powerfull.But the problem is there are no sound.No any sound.With speakers or with headphones.Absolutly mute.What should i do?

---

### Post by maged_295 on 2009-11-05
hey evryone i have the same problem , i instaled ubunto on my pc and when i open any mp3 file it's not running i don't know why .,  can anyone help me please!

---

### Post by Jackyboy86 on 2009-11-05
This worked for me:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```and paste this into the bottom of the file:

```

options snd-hda-intel model=basic
```

Reboot, and the sound should work
Let me know the outcome!

---

### Post by waspbr on 2009-11-08
thanks for the tip, the fix worked on my hp tx1320us with karmic. I have been looking forever for this fix, now the sound works. 

cheers

---

### Post by Jackyboy86 on 2009-11-09
> **waspbr said:**
> thanks for the tip, the fix work on my hp tx1320us with karmic. I have been looking forever for this fix, not the sound works. 

cheers

Cha-ching! Good to hear :D

---

