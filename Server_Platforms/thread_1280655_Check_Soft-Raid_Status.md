---
title: "Check Soft-Raid Status"
date: 2009-10-02
forum: Server Platforms
---

### Post by computerwiz_222 on 2009-10-02
I have a home server running two 1tb hard drives in a Raid1 Configuration.

How can I check the status of this Raid?

Thanks

---

### Post by Akita on 2009-10-02
cat /proc/mdstat

---

### Post by |{urse on 2009-10-02
theres a lot of useful info and a few different ways to view the raids status in the man pages for mdadm.

man mdadm

---

### Post by computerwiz_222 on 2009-10-02
Thank you very much. I wasn't sure where to start.

---

### Post by fjgaude on 2009-10-02
The one I use most of the time is:

```
sudo mdadm -D /dev/md0
```

where the md0 is the name of your array.

---

