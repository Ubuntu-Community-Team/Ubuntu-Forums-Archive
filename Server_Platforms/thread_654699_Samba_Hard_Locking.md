---
title: "Samba Hard Locking"
date: 2007-12-31
forum: Server Platforms
---

### Post by calandryll on 2007-12-31
I just upgraded to 7.10 with a fresh install on my home server.  My previous install was 6.04, I think, it has been a long time since I installed.  My server stores all of my music and I have samba set up correctly so that I can access my shares.

I currently have two problems.  The first problem is I get an error with winbindd.
```
Dec 31 09:46:07 miriam winbindd[3987]: [2007/12/31 09:46:07, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:07 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
Dec 31 09:46:07 miriam winbindd[3987]: [2007/12/31 09:46:07, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:07 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
Dec 31 09:46:07 miriam winbindd[4194]: [2007/12/31 09:46:07, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:07 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:07 miriam winbindd[4194]: [2007/12/31 09:46:07, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:07 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:07 miriam winbindd[4194]: [2007/12/31 09:46:07, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:07 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:07 miriam winbindd[4194]: [2007/12/31 09:46:07, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:07 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:07 miriam winbindd[3987]: [2007/12/31 09:46:07, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:07 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-22-1-65534 with passdb backend
Dec 31 09:46:07 miriam winbindd[3987]: [2007/12/31 09:46:07, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:07 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
Dec 31 09:46:07 miriam winbindd[3987]: [2007/12/31 09:46:07, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:07 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
Dec 31 09:46:07 miriam winbindd[3987]: [2007/12/31 09:46:07, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:07 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-5-11 with passdb backend
Dec 31 09:46:08 miriam winbindd[4194]: [2007/12/31 09:46:08, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:08 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:08 miriam winbindd[4194]: [2007/12/31 09:46:08, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:08 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:08 miriam winbindd[3987]: [2007/12/31 09:46:08, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:08 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
Dec 31 09:46:08 miriam winbindd[3987]: [2007/12/31 09:46:08, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:08 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
Dec 31 09:46:08 miriam winbindd[4194]: [2007/12/31 09:46:08, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:08 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:08 miriam winbindd[4194]: [2007/12/31 09:46:08, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:08 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:08 miriam winbindd[4194]: [2007/12/31 09:46:08, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:08 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:08 miriam winbindd[4194]: [2007/12/31 09:46:08, 0] nsswitch/idmap.c:idmap_alloc_init(735)
Dec 31 09:46:08 miriam winbindd[4194]:   ERROR: Initialization failed for alloc backend, deferred!
Dec 31 09:46:08 miriam winbindd[3987]: [2007/12/31 09:46:08, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:08 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-22-1-65534 with passdb backend
Dec 31 09:46:08 miriam winbindd[3987]: [2007/12/31 09:46:08, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:08 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
Dec 31 09:46:08 miriam winbindd[3987]: [2007/12/31 09:46:08, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:08 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
Dec 31 09:46:08 miriam winbindd[3987]: [2007/12/31 09:46:08, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Dec 31 09:46:08 miriam winbindd[3987]:   Possible deadlock: Trying to lookup SID S-1-5-11 with passdb backend

```

If I stop winbind I don't get this error, my previous install I didn't have this problem.  Since I'm not running a domain do I really need winbind?  How do I disable it if I don't require it?

My second problem is after about 2 minutes of listening to a song, or transferring a file my server goes into a hard lock.  Any suggestion on fixing these problems?

---

### Post by cdenley on 2007-12-31
to remove winbind:
```

sudo apt-get remove winbind

```

I'm not sure how to fix your other problem, if removing winbind doesn't.

---

### Post by gfowler on 2007-12-31
> **calandryll said:**
> I just upgraded to 7.10 with a fresh install on my home server.  My previous install was 6.04, I think, it has been a long time since I installed.  My server stores all of my music and I have samba set up correctly so that I can access my shares.

[Snippage here]

My second problem is after about 2 minutes of listening to a song, or transferring a file my server goes into a hard lock.  Any suggestion on fixing these problems?

In your smb.conf file for your music share you might add:
  strict locking = no

Jerry

---

### Post by calandryll on 2007-12-31
> **gfowler said:**
> In your smb.conf file for your music share you might add:
  strict locking = no

Jerry

What does strict locking do?

I think I found my problem, it looks like it was caused by a bad hard drive.  I ran fsck on it and it hard locked my system.  Thanks for the help.

---

### Post by calandryll on 2007-12-31
> **calandryll said:**
> What does strict locking do?

I think I found my problem, it looks like it was caused by a bad hard drive.  I ran fsck on it and it hard locked my system.  Thanks for the help.

I spoke too soon.  Taking a look at my samba logs this is what I see.

```
[2007/12/31 12:26:12, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2007/12/31 12:26:12, 0] lib/util_sock.c:send_smb(769)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2007/12/31 12:35:37, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 10.0.0.70. Error Connection reset by peer
[2007/12/31 12:35:37, 0] lib/util_sock.c:send_smb(769)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2007/12/31 13:23:28, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 10.0.0.70. Error Connection reset by peer
[2007/12/31 13:23:28, 0] lib/util_sock.c:send_smb(769)
  Error writing 4 bytes to client. -1. (Connection reset by peer)

```

I have nothing else in my syslog.  The only thing that has changed is I removed my hard drive, which was reiserfs, perhaps it's a problem with that.

---

### Post by calandryll on 2008-01-02
Well after two days of working on it.  I have narrowed it down to my motherboard starting go.  No matter what RAM I put in it it came up with errors.  Another old motherboard is working fine now.  I will miss my BP6.

---

### Post by analog8x on 2008-04-11
> **cdenley said:**
> to remove winbind:
```

sudo apt-get remove winbind

```

I'm not sure how to fix your other problem, if removing winbind doesn't.

Just wanted to say thanks, I was getting the same error for 2 days now; this corrected the problem for me.

---

### Post by draxbear on 2008-06-02
Encountered the same error in Heron after joining a domain (security = domain) successfully.

[2008/06/03 11:08:42, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
[2008/06/03 11:08:42, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend

After removing the winbind package everything kicked into life.

Thanks from me too!

---

### Post by ceege on 2008-07-15
This worked for me too, but uninstalled wine.  When I tried to reinstall wine, it says that winbind is required.  Anyone have any idea how I can get wine w/o winbind?  Or get samba to work with winbind installed?

---

