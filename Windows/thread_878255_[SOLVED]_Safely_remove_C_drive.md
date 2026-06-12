---
title: "[SOLVED] Safely remove C: drive?"
date: 2008-08-02
forum: Windows
---

### Post by coffeecat on 2008-08-02
I'm posting from Windows XP. :oops: I have to keep XP going for one single specialist app that doesn't run in wine. Anyway, I booted into Windows to check something out so that I could post help in a support thread elsewhere and I was just about to close it down when I noticed the little 'Safely Remove Hardware' icon you get when you have a removable drive plugged in, down there bottom right in whatever Windows calls the lower panel. But I don't have a removable drive plugged in. :? So I clicked on the icon, and this is what I see:

> Safely Remove USB Mass Storage Device - Drives (E:, G: )
Safely Remove SAMSUNG SP2504C - Drive (D: )
Safely Remove SAMSUNG HD160JJ - Drive (C: )This is a machine I built myself. E: and G: would be the internal card reader - no cards in at the moment. The two Samsungs are the two SATA drives, sda=160GB with Windows and various Linux partitions, and sdb=250GB one NTFS shared data partition.

So - why is Windows inviting me to unmount my C: drive? Linux has never let me unmount my root partition. :wink:

I ask because I've never seen this before in Windows and I'm genuinely curious.

---

### Post by insane_alien on 2008-08-02
i have no idea. click it and see.

---

### Post by fiddledd on 2008-08-03
> **coffeecat said:**
> I'm posting from Windows XP. :oops: I have to keep XP going for one single specialist app that doesn't run in wine. Anyway, I booted into Windows to check something out so that I could post help in a support thread elsewhere and I was just about to close it down when I noticed the little 'Safely Remove Hardware' icon you get when you have a removable drive plugged in, down there bottom right in whatever Windows calls the lower panel. But I don't have a removable drive plugged in. :? So I clicked on the icon, and this is what I see:

This is a machine I built myself. E: and G: would be the internal card reader - no cards in at the moment. The two Samsungs are the two SATA drives, sda=160GB with Windows and various Linux partitions, and sdb=250GB one NTFS shared data partition.

So - why is Windows inviting me to unmount my C: drive? Linux has never let me unmount my root partition. :wink:

I ask because I've never seen this before in Windows and I'm genuinely curious.

I have the same on my XP boxes. It's because SATA is hot swappable, but obviously it won't let you actually unmount the drive with the OS on it. If you click it you'll get a message box telling you it can't remove it.

---

### Post by coffeecat on 2008-08-03
> **fiddledd said:**
> It's because SATA is hot swappable

Yes, I understand now. Thanks. The reason I hadn't seen this before is that I had only used XP on machines with ide drives before.

---

