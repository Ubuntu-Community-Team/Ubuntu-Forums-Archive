---
title: "Has GNU tar syntax changed?"
date: 2006-05-14
forum: Server Platforms
---

### Post by mjgumbley on 2006-05-14
Hi, my backup script used to work fine with:

cd /
tar czvf mybackup.tar.gztar czvf mybackup.tar.gz . --exclude ./proc --exclude ./lost+found --exclude ./nobackup

but now this causes the nobackup directory to be archived. This is with GNU tar 1.15.1 on Breezy. Used to work fine on Hoary...

If I change to:
tar czvf mybackup.tar.gz --exclude ./proc --exclude ./lost+found --exclude ./nobackup .

i.e. specify what I want to back up at the end of the command, it works as expected. Has this intentionally changed? Or is it a bug?

Regards,
Matt

---

