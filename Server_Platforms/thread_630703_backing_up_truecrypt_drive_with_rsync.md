---
title: "backing up truecrypt drive with rsync"
date: 2007-12-03
forum: Server Platforms
---

### Post by PetePete on 2007-12-03
I've had rsync setup correctly for ages to backup my /home to an external disk, but I recently started using truecrypt to create an encrpyted file which I then mount as a drive (so its not a hidden volume in truecrypt)

problem is that rsync doesn't seem to notice that the encrypted file (containing my encrypted directory) has changed, so it doesn't update it. .... i'm assuming this is because of the security of truecypt that it doesn't show when the file was last modified. 

any ideas how to overcome this?
maybe id just have to manually specify it to write that file each time?

---

### Post by PetePete on 2007-12-03
doesn't matter... found the answer (after looking for F***ing ages, make a post, then i stumble accross it, typical!)

for anyone else looking at this, ..
you need to use the --checksum option (-c flag) takes a LOT longer, but needed to termine if the truecrypt volume has changed.. so prob better to have 2 rsync commands, one which does the main drive, then one which does the folder containing truecrypt drives.

---

