---
title: "Which is the quickest parts of disks, 'beginning' or 'end'?"
date: 2008-06-07
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-06-07
Hi all, Ive just recieved my new SATA drive and pci SATA controller as I wanted to take my server out of the stone age. 
I'm running through set up and I was just wondering should I place my root + swap at the begining or the end of the drive? I know one is faster than the other because the head doesn't have to move so much so which ends that?

Also I'm still plugging IDE drives in, should I leave the jumpers as they are? Does it affect SATA drives in anyway?

Hope someone can clear this up for me.

Cheers

---

### Post by azadpanchi on 2008-07-25
Swap should be the very first parition as it is faster to access.

I think it would be best to refer to the manufacturer of your mother board on how to set your SATA as primary with IDE hdd installed.

---

### Post by garethsimpsonuk on 2008-07-28
it turns out that swap shouldn't be at the front, it shouldn't be used that much anyway and sata drives have no affect on ide drives and don't need jumpers,

thanks

---

### Post by azadpanchi on 2008-08-02
> **garethsimpsonuk said:**
> it turns out that swap shouldn't be at the front, it shouldn't be used that much anyway and sata drives have no affect on ide drives and don't need jumpers,

thanks
Yeah, you are right.  I guess I am just an old timer and need to get with new technology.

---

