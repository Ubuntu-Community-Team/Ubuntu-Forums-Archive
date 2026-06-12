---
title: "Headless FUSE?"
date: 2011-02-09
forum: Server Platforms
---

### Post by doublemeat on 2011-02-09
I have a very specific requirement outside the typical use case of "enterprise server". 

If possible, I need to run a FUSE filesystem on a headless server, and share it via Samba.

Physical security is a non-issue.

I see two challenges with this, that Google and I have been unable to figure out:

[LIST=1]
[*]I'm assuming that in order to mount a FUSE system, a user must be logged in. (Hence the "U" in "FUSE".) So the first challenge is how to get Ubuntu to automatically login, on the physical console, to a user terminal session. (I know this can be trivially done in GNOME, but this won't have X-Windows or GNOME installed.) This has to happen automagically after boot-up; manually logging in locally or via SSH isn't an option.
[*]Second challenge (?), how to share a FUSE file system via Samba?
[/LIST]
Maybe I'm making some incorrect assumptions (which would explain the lack of search results).

Thanks,
Jim

---

### Post by bab1 on 2011-02-09
> **doublemeat said:**
> I have a very specific requirement outside the typical use case of "enterprise server". 

If possible, I need to run a FUSE filesystem on a headless server, and share it via Samba.

Physical security is a non-issue.

I see two challenges with this, that Google and I have been unable to figure out:

[LIST=1]
[*]I'm assuming that in order to mount a FUSE system, a user must be logged in. (Hence the "U" in "FUSE".) So the first challenge is how to get Ubuntu to automatically login, on the physical console, to a user terminal session. (I know this can be trivially done in GNOME, but this won't have X-Windows or GNOME installed.) This has to happen automagically after boot-up; manually logging in locally or via SSH isn't an option.[/LIST]
FUSE has more to do with how the file system relates to the Linux kernel.  You can run systems in *"kernel space" * or in *"user space"*(e.g outside of the kernel). See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://en.wikipedia.org/wiki/Filesystem_in_Userspace")for more information. A user being logged in has nothing to do with FUSE operations.  The file system can be mounted via FSTAB upon boot up.  I assume the partition is physically connected to the host; correct?> 

[LIST=0]
[*]Second challenge (?), how to share a FUSE file system via Samba?
[/LIST]


The file system can be shared via Samba in the normal fashion after it is mounted.  See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://samba.org/samba/docs/man/Samba-Guide/") for a complete howto.

---

### Post by doublemeat on 2011-02-09
Ah. Not having to be logged in to mount FUSE is the key. Dang, I should have known that...after all, I already mount NTFS-3G volumes in fstab. That would also explain the lack of search results. Yeah, then sharing from Samba is nothing special. Thanks!
-Jim

---

