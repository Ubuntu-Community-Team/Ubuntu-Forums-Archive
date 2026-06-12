---
title: "Mounting /usr and /var partitions read only for system security checkers."
date: 2006-07-26
forum: Server Platforms
---

### Post by RavenOfOdin on 2006-07-26
I've seen that some system checkers such as Tiger and Tripwire recommend that the partitions which they are installed to be set read-only.  I am not aware that these programs can be installed on a floppy by themselves so I'll have to ask if this is a good trade off to make. After all, setting these partitions to read only would kill some user functionality.

Is it a good thing; this is for an old computer which may not have floppy drives, to set another partition to mount read only (such as /mnt) and store security checkers - not talking about Tiger and Tripwire now, just any checker in general - on there?  Or would this be a problem?

---

### Post by LordHunter317 on 2006-07-26
It's ultimately a worthless measure, so I don't know why they recommend it. 

If I have the privilege to mess with the IDS then I also have the privilege to remount the partition R/W.

---

