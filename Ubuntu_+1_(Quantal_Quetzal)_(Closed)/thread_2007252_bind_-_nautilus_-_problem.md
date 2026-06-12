---
title: "bind - nautilus - problem"
date: 2012-06-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by SpaceCeph on 2012-06-20
Hi, 
I'm new to ubuntu. I don't really know what i'm doing but only if I try i can learn it.
i have 12.04 and 12.10 installed. Both of them share a data partition.
I bind Downloads, Videos... from the data partition to the home directory of them.
With 12.04 i had no problems. But now I add the same lines to 12.10 fstab and all of the binded folders appear as devices.

[IMG]http://img96.imageshack.us/img96/9480/bildschirmfotovom201206.png[/IMG]

What I added in fstab:

```
# DatenPartition daten
UUID=770c57f5-a58d-4324-a35f-d1d6d20cf9fa /mnt/daten     ext4    defaults        0       2
/mnt/daten/Bilder  /home/spaceceph/Bilder none bind  0  0
/mnt/daten/Dokumente  /home/spaceceph/Dokumente none bind  0  0
/mnt/daten/Downloads  /home/spaceceph/Downloads none bind  0  0
/mnt/daten/Musik  /home/spaceceph/Musik none bind  0  0
/mnt/daten/Videos  /home/spaceceph/Videos none bind  0  0
/mnt/daten/Vorlagen  /home/spaceceph/Vorlagen none bind  0  0
/mnt/daten /home/spaceceph/BUp none bind  0  0
```Don't know where the problem is.

thanks in advance!

---

### Post by ventrical on 2012-06-20
I just updated and I got apport trying to send an error and a fail:

---

