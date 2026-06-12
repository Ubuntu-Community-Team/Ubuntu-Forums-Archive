---
title: "Symlinking system files in a chroot jail - bad idea?"
date: 2018-12-27
forum: Security
---

### Post by InThane on 2018-12-27
I'm setting up a chroot jail for remote users to back up their data via scp/Duplicati. I'd like the system to be as low-effort and to "just work" with minimal interactivity on my part. I've already set up unattended-updates to constantly update the system. What I'm concerned is that the system files in the chroot jail will get out of date and stop working, since all the directions I've found on setting up chroot jails involve copying system files to the directory, rather than symlinking the files. Is there an implicit security threat in symlinking the system files rather than copying them over?

---

### Post by spjackson on 2018-12-29
I could be wrong here, but I wouldn't expect it to work. A program (e.g. a shell) running under the chroot wouldn't be able to follow the symlink to files outside the chroot.

---

### Post by TheFu on 2018-12-29
Symbolic links outside a chroot do not work. You must copy the files needed. That usually includes any libraries and the passwd/groups/shadow files too.  Follow the guides.  There are many subtle security issues in using chroot environments which aren't intuitively obvious. If you don't follow the guides exactly, it is highly likely you will leave a way for someone inside a chroot to break out.  That would defeat the purpose.

---

