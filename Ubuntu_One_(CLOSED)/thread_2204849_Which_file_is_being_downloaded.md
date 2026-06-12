---
title: "Which file is being downloaded?"
date: 2014-02-10
forum: Ubuntu One (CLOSED)
---

### Post by schmitta on 2014-02-10
Is there any way to tell from ubuntu1 which file is being downloaded? Either a big one is being downloaded or ubuntu1 is stuck trying to sync up a file.

---

### Post by schmitta on 2014-02-10
For the past week ubuntu1 has not been resyncing. It has been up for hours and still says FILE SYNC IN PROGRESS in the upper right hand corner on the machine that needs to download to resync.

---

### Post by thnewguy on 2014-02-11
I suspect the command you want to run from the command line is

```

u1sdtool --waiting

```

That should show you a list of files waiting to be synced.

---

