---
title: "how do you remove raids and restart?"
date: 2008-02-17
forum: Virtualisation
---

### Post by gprime27 on 2008-02-17
I am currently installing ubuntu on a backup server for a virtualized server. The problem is when I setup the raids it set up two vs one. I now cannot get the second raid or even the first one removed. I've tried all the remove options on the partitioner but, I'm getting no where. Anyone have any ideas?

---

### Post by fjgaude on 2008-02-17
Partitioner? What partitioner?

---

### Post by gprime27 on 2008-02-17
I should have been a little more direct in this. We went through and set up the raids in ubuntu. However, my friend here didn't realize he did it twice. now we have two raids. i cant remove them :(

---

### Post by fjgaude on 2008-02-17
Well, you have to zero the superblocks before you can use software raid drives as normal ones.

In a terminal window use this command on each of the drives in each of the raid arrays:

```
sudo mdamd --zero-superblock /dev/sd[nn]
```

The "sd[nn]" would be each device, one at a time, like sdb1, sdc1, hda1, etc.

Let us know how you do.

---

