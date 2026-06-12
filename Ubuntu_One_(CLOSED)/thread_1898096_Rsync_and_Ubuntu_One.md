---
title: "Rsync and Ubuntu One"
date: 2011-12-20
forum: Ubuntu One (CLOSED)
---

### Post by Lars Noodén on 2011-12-20
I've looked around and not found any info on whether Ubuntu One works with rsync or sftp.  Is it possible to use either of them or both with Ubuntu One?

---

### Post by Lars Noodén on 2011-12-21
bump

Searches have not turned up more info yet.

---

### Post by Lars Noodén on 2011-12-27
bump

---

### Post by Lars Noodén on 2011-12-30
bump

I can't be the only user trying to do this.

---

### Post by oldos2er on 2011-12-31
> **Lars Noodén said:**
> bump

I can't be the only user trying to do this.

You're not. I'm keeping an eye on this thread.

---

### Post by Nemo_bis on 2012-01-01
[This german user]("http://forum.ubuntuusers.de/topic/ubuntu-one-mit-rsync/#post-3718897") says that there's no option currently, but developing your own using the API: [https://one.ubuntu.com/developer/](https://one.ubuntu.com/developer/)

---

### Post by Lars Noodén on 2012-01-07
> **Nemo_bis said:**
> [This german user]("http://forum.ubuntuusers.de/topic/ubuntu-one-mit-rsync/#post-3718897") says that there's no option currently, but developing your own using the API: [https://one.ubuntu.com/developer/](https://one.ubuntu.com/developer/)

Those appear to be web APIs

[https://one.ubuntu.com/developer/files/store_files/](https://one.ubuntu.com/developer/files/store_files/)

I'm looking for something that will connect directly with **rsync** via SSH.  I suppose it is time to file a bug report with a feature request.  Fortunately Ubuntu One is not the only hosting service out there and the others nearly all support **rsync**.  It's just that it would be nice to have the option of using Ubuntu One, too.

---

### Post by Lars Noodén on 2012-01-21
It looks like [Ubuntu One is only a front end for a database](http://linux.slashdot.org/story/11/11/22/171228/canonical-drops-couchdb-from-ubuntu-one), U1DB.  That complicates matters.  rsync is probably not going to be supported natively without some work.  

Where should the feature request be posted?

---

