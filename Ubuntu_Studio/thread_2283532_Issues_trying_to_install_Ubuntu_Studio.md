---
title: "Issues trying to install Ubuntu Studio"
date: 2015-06-22
forum: Ubuntu Studio
---

### Post by victor63 on 2015-06-22
Hi all,

I am trying to fully install ubuntu studio on my acer aspire m5641. I manage to get in liveCD, but I can't install as it doesn't see my SATA harddrive (Gpart doesn't see it either, but the BIOS setup page is fine with it). It only see the USB, and so there's not enough space for it to install. 

I couldn't find valuable help looking around in forums, could anyone of you help me with that? What would be the most common issue?
Cheers

---

### Post by jejeman on 2015-06-23
Usually it is because malformed partition table, or GPT table.
Give
```
sudo parted -l
```

---

### Post by victor63 on 2015-07-01
Thanks a lot, that is what it was indeed.
I have deleted a partition and extended my C:/ drive (I don't know why it was there in the first place) in Windows and then Gparted recognised my HDD. 
I have another issue now... I will post as a new thread.

---

