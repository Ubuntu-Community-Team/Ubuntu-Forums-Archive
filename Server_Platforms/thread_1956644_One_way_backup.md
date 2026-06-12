---
title: "One way backup?"
date: 2012-04-11
forum: Server Platforms
---

### Post by phillips321 on 2012-04-11
Hi guys,

I have a 1TB drive(ext4) storing VMs and Large Rainbow tables located at /media/1TB

I would like to clone this onto my 1TB USB drive(ext4) located at /media/USB1TB.

I do not change all of the files on the source(/media/1TB) and only some are changed between backups, thus, i do not need to sync all of the files, just those that have changed.

Also some files are ~20GB in size, if only small areas of these files are changed i would only like to update the changed bits instead of the whole 20GB.

I presume this is all possible with RSync.

Can anyone point me in the direction of the command i should be using to perform this back up?

Many thanks

P.s. rsync --delete -va /media/1TB /media/USB1TB doesn't do the bit level checking

---

### Post by Habitual on 2012-04-11
Unison is my suggestion. In a repo near you.

---

### Post by rubylaser on 2012-04-11
I imagine it's the sparse virtual machine images that are getting re-copied every time.  Can you try something like this?

```
rsync -avPSI /media/1TB/ /media/USB1TB/ --stats --itemize-changes --delete --existing --modify-window=2 --no-whole-file
```

This will still take a while to complete, because it will still need to checksum all of the files.  Here are a couple pages that discuss these topics.

[http://www.barricane.com/rsync-vm-sparse-inplace-kvm-vmware]("http://www.barricane.com/rsync-vm-sparse-inplace-kvm-vmware")
[http://serverfault.com/questions/279290/has-anyone-achieved-true-differential-sync-with-rsync-in-esxi]("http://serverfault.com/questions/279290/has-anyone-achieved-true-differential-sync-with-rsync-in-esxi")

---

### Post by papibe on 2012-04-11
When backing up using rsync, I run 2 different commands with different options. A regular one that excludes VirtualBox's vdis, and other exclusively for vdi (fixed sized) using the --inplace option.

Just a thought.
Regards.

---

### Post by dankdave on 2012-05-02
I'm curious to hear what ends up working for you.  I use 'rsync -avz <source> <dest>' all the time, but not for large files.  The largest files I ever move are 1Gb, but those aren't actually being backed up for me ...

---

