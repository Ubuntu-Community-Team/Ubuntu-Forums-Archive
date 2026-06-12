---
title: "Should I use encryption for this?"
date: 2008-10-31
forum: Security
---

### Post by Digitbig on 2008-10-31
I plan on updating to 8.10 in the near future and discovered that the new version allows for folder encryption. I have some personal files that I don't want anyone getting into, so I was pretty excited, needless to say. However, I'm not sure if this will actually suit my needs.

[LIST]
[*]The encrypted folder will consist of image and video files.
[*]I'll be adding downloaded files to this folder on a regular basis.
[*]I'm the only user.
[/LIST]

Is encryption the right way to go for protecting my files?

---

### Post by Gamma746 on 2008-10-31
Is your machine in a secure place?  How difficult would it be for someone to gain physical access to it?

Encryption only protects against people trying to examine your disks; it won't help if they can exploit your box while the encrypted files are mounted.  If you're using a laptop or your machine is in a public/easily accessible place, then I'd suggest encryption.  If you're confident that no one can get physical access, don't bother.

---

### Post by cariboo on 2008-11-01
Why not just hide the directory by putting a . at the start of the the directory name, most users don;t know enough about linux to know there are hidden files and directories in their home directories.

Jim

---

### Post by hyper_ch on 2008-11-01
if you're the only user, why not fully encrypt your computer? then you don't have to worry about where you put anything.

However if you want to go the encryption route, then backups are mandatory - preferrably encrypted backups.

---

### Post by cb951303 on 2008-11-01
> **Digitbig said:**
> I plan on updating to 8.10 in the near future and discovered that the new version allows for folder encryption. I have some personal files that I don't want anyone getting into, so I was pretty excited, needless to say. However, I'm not sure if this will actually suit my needs.

[LIST]
[*]The encrypted folder will consist of image and video files.
[*]I'll be adding downloaded files to this folder on a regular basis.
[*]I'm the only user.
[/LIST]

Is encryption the right way to go for protecting my files?

it seems like you're hiding your pr0n :lolflag: just kidding...

EDIT: oh and I would definiyely try encrypting them just for the sake of learning something new even though its not necessary :)

---

### Post by amac777 on 2008-11-01
> **cb951303 said:**
> it seems like you're hiding your pr0n :lolflag: just kidding...

Haha, that's what I thought too!

If it's true, beware! 8.10 uses EcryptFS, which does not encrypt filenames and directory names according to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/264977](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/264977)

---

