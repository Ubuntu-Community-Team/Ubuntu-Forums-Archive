---
title: "Exim Maildir symlink"
date: 2010-12-15
forum: Server Platforms
---

### Post by c01e on 2010-12-15
Hi,

In my exim setup. I have a Maildir that I would like to make a symlink to an external drive. However every time I check my email, it says error (iff I make the Maildir a symlink). I've read that I could use "allow_symlink". I put that in /etc/exim4/conf.d/transport/30_exim4-config_maildir_home under maildir_home. But it still doesn't work.

Any ideas?

---

### Post by WinstonChurchill on 2010-12-16
> **c01e said:**
> Hi,

In my exim setup. I have a Maildir that I would like to make a symlink to an external drive. However every time I check my email, it says error (iff I make the Maildir a symlink). I've read that I could use "allow_symlink". I put that in /etc/exim4/conf.d/transport/30_exim4-config_maildir_home under maildir_home. But it still doesn't work.

Any ideas?
Is there some reason you can't just mount the external drive on the Maildir directory? 
```
mount /dev/driveX /your/mail/directory
```Mount it somewhere else first and copy the current contents of the Maildir to the drive, as they will not be accessible once you mount the drive on the directory.
You'll have to fiddle with permissions - but it should be easy to figure out.

---

### Post by c01e on 2010-12-16
Wow, I didn't know I could do that. Try answering the question dumb ****. If I could mount an external disk, I would...

---

### Post by WinstonChurchill on 2010-12-16
> **c01e said:**
> Wow, I didn't know I could do that. Try answering the question dumb ****. If I could mount an external disk, I would...
The open(...) syscall in Linux works with symlinks unless you explicitly tell it not to with the O_NOFOLLOW flag, and the C function mirrors this behaviour. Pull the source code for exim4 off the package repo and take a look at the file exim_lock.c: "A program to lock a file exactly as Exim would, for investigation of interlocking problems."

Sure enough, we find: (at line 435)
```

    mbx_tmp_oflags = O_RDWR | O_CREAT;
#ifdef O_NOFOLLOW
    mbx_tmp_oflags |= O_NOFOLLOW;
#endif
    md = open(tempname, mbx_tmp_oflags, 0600);
/// mbx_tmp_oflags is used for all subsequent open(...) calls

```For obvious reasons, exim doesn't want to allow symlinks when attempting to get locks on files. Read some of the source and see if it tries to get a lock on the maildir when it is running (or perhaps just when checking mail?) - my hunch is that it does and the lock fails because it's a symlink. Mounting would avoid this problem.

---

### Post by c01e on 2010-12-16
Cool. Thx. Unfortunitly I'd rather avoid a solution that requires a hack of the code and a recompile. Do you know anything about this "allow_symlink" option? Surely there is a solution via config files, so I can have symlinks. 

If there is no solution. I guess I will nfs mount just my Maildir... But I would prefer a symlink solution.

---

### Post by c01e on 2010-12-16
Well an nfs mount didn't work either? I'm doubled check the user/group/rwx permissions and all is good. Any ideas why the ***** that would happen? FYI I nfs mounted server:/home/user/Maildir to mail:/home/user/Maildir

---

