---
title: "Ubuntu, LXD &amp; Samba with AD integration - sys_setgroups error and solution"
date: 2016-10-05
forum: Ubuntu, Linux and OS Chat
---

### Post by alvils on 2016-10-05
Hi all,

Originally I posted this in Ubuntu community chat, but then I thought it would better be located here.

Recently I have started playing around with LXD and, generally, like it.  Yet, I wanted to set up Samba with AD integration on the container and  this is where the trouble started.

As soon as I would try to connect to Samba (with any client), it would not connect, and the following would appear in log.smbd:
[2016/10/05 12:14:51.277701,  0] ../source3/lib/util.c:789(smb_panic_s3)
  PANIC (pid 796): sys_setgroups failed
[2016/10/05 12:14:51.278618,  0] ../source3/lib/util.c:900(log_stack_trace)
  BACKTRACE: 26 stack frames:
   #0 /usr/lib/x86_64-linux-gnu/samba/libsmbregistry.so.0(log_stack_trace+0x1a) [0x7ff6256d871a]

Searching for this sys_setgroups error didn't return anything meaningful  (old forums threads, questions without answers etc), so I understood I  have to figure this out on my own.

Basically, it turned out to be the fact that you need to specify the  range of available UIDs/GIDs for your container - or, to be more  precise, the host user that owns the container. In my case, Samba was  willing to use very large UIDs and GIDs and the default setting allows  for just 65536 UIDs/GIDs to be used. You need to modify them in the  /etc/subuid and /etc/subgid files.

I actually wrote a blog article about this topic to share the results of  my research with the world; and I described everything in detail there.  The full article can be found here: [https://techblog.devlat.eu/2016/10/0...-failed-error/]("https://techblog.devlat.eu/2016/10/05/ubuntu-lxd-samba-and-the-dreaded-sys_setgroups-failed-error/")

Containers are here to stay, and I hope that this post would be useful for someone.

---

### Post by howefield on 2016-10-05
Not a support request, so moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

