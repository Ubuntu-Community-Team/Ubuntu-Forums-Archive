---
title: "SSD filesystem project?"
date: 2011-07-21
forum: The Cafe
---

### Post by del_diablo on 2011-07-21
Obligatory text:
The reason TRIM exists is because filesystems tend to have the idea that they are ran on a normal HD, which among other thing means that the SSD always gets incorrect flags on files(apparently a issue related to deleting files and where to allocate files).
Another problem is that the garbage collection now takes a back seat from trim, even if the garbage collection is several magnitudes more importantan than TRIM.
[/quote]

But back on the issue: I heard whispers about btrfs planning some SSD flags, but does there currently exist any project that just forks a filesystem, and adapts it for SSD use?

---

### Post by disabledaccount on 2011-07-21
The only reason why SSD controllers exist in today's form and need TRIM is NTFS (it cannot work efficiently with SSD due to many reasons, like internal misalignments in data structures )
YAFFS, LOGFS and other were ready for Flash/SSD years ago. Even Ext4 can be configured to work nicely with SSD. If FS is aligned to SSD's internal pages and uses block size equal to (or multiply of Flash page size then garbage collection algorithms are useless/not needed. This is almost the same effect like in HDDs with 4KB block size, although HDDs are invoulnerable to write amplification "cataclysm" ;)

---

### Post by del_diablo on 2011-07-21
Yeah, there is a reason the OP post starts with a minor elaboration, [sarcasm]please ignore it please.[/sarcasm]

YAFFS, LOGFS? Going by what I managed to get to on wikipedia thanks to your keyboards, both seems "state of the art".
As for Ext4: Does it or does it not have flags for flash units yet? I am well aware of align, but does it or does it nor pass on the correct flags to the flash or SSD unit?

---

