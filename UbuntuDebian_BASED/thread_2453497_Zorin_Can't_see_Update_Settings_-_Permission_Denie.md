---
title: "Zorin: Can't see Update Settings - Permission Denied"
date: 2020-11-11
forum: Ubuntu/Debian BASED
---

### Post by Rick St. George on 2020-11-11
Latest Zorin - Can't see Update Settings, see following Error;

```

apt-get update
Reading package lists... Done
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)

```

Any idea what happened??? Was able to run update anyway, but cannot see SETTINGS.
I suspect another version is available, but may need to change settings!

Thanks!
Rick
:confused:

---

### Post by howefield on 2020-11-11
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by #&amp;thj^% on 2020-11-11
I did not see **"sudo"** used Rick.
Also what dose this return:
```
ps -e | grep -e apt -e adept | grep -v grep
```

---

### Post by Rick St. George on 2021-10-02
> **1fallen said:**
> I did not see **"sudo"** used Rick.
Also what dose this return:
```
ps -e | grep -e apt -e adept | grep -v grep
```

I get NOTHING ...

```

Elite-6930p:~$ ps -e | grep -e apt -e adept | grep -v grep
Elite-6930p:~$ 


```

To reiterate - After opening Software Updates, then Settings ... NOTHING happens. Can't bring up Repositories, not even iin Synaptic Pkg Mgr.

Is there another way to access and select repositories in Zorin ???
Thanks!

---

### Post by Dennis N on 2021-10-02
> Is there another way to access and select repositories in Zorin ???
Search for the "Software & Updates" application (not "Software Updater"). It's the same as used in Ubuntu. 
Screenshot (from Zorin 16) attached. Zorin has its own PPAs in the "Other Software" tab, and also taps into the Ubuntu repository.

---

