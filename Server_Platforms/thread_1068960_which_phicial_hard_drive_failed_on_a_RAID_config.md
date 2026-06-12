---
title: "which phicial hard drive failed on a RAID config"
date: 2009-02-13
forum: Server Platforms
---

### Post by rgotten on 2009-02-13
one of my 3 hard driive RAID is saying that has faild, being identicall hard drive, how do i kno wwhich one failed, so i can removed it? I have a RAID 5 i I knoiw that sdc has failed, but how do i know which one faild physically to remove it and replace?

---

### Post by HittingSmoke on 2009-02-13
> **rgotten said:**
> one of my 3 hard driive RAID is saying that has faild, being identicall hard drive, how do i kno wwhich one failed, so i can removed it? I have a RAID 5 i I knoiw that sdc has failed, but how do i know which one faild physically to remove it and replace?

I would imagine sdc would be the drive hooked up to your SATA port 3. They should be labeled on your mother board and Linux labels them sequentially on my machine. I don't know how this translates over to a RAID config though so don't take my word for it. I've never set up an array with Linux and don't know how they work here.

For me configuring RAID was just a matter of using whatever RAID console came with the controller but that was with a Windows machine.

---

### Post by fjgaude on 2009-02-13
Knowing the name of the drive, e.g., /dev/sdb you can get its SN using this command:

```
sudo hdparm -i /dev/sd[n]
```

From there you can look for the SN on the physical drive, take it out, and replace it.

But first, if using **mdadm**, you have to fault it, remove it, and then add the new one in. Read the man pages for the commands to do these three things.

Let us know how you are doing.

---

### Post by rgotten on 2009-03-28
Thanks so much...i got it

---

### Post by fjgaude on 2009-03-30
Great, we learn something new each day, eh?

---

