---
title: "Webmin Raid Setup and Testing"
date: 2010-08-06
forum: Server Platforms
---

### Post by ptmuldoon on 2010-08-06
I'm going to be setting a 4 x 1TB raid5 array this weekend, giving me 3TB of storage.

I'm pretty sure setting up the Raid Array in Webmin is pretty straight forward.

But before I begin to move data onto the array.  How can you test the array and simulate a disk failure?

---

### Post by kevin11951 on 2010-08-06
> **ptmuldoon said:**
> I'm going to be setting a 4 x 1TB raid5 array this weekend, giving me 3TB of storage.

I'm pretty sure setting up the Raid Array in Webmin is pretty straight forward.

But before I begin to move data onto the array.  How can you test the array and simulate a disk failure?

Create the array, copy something into it.  Then run the command:

```
mdadm --fail /dev/sd<a/b/c/etc...>
```

I have not done raid in a while, so YRMV as the kids say.

---

