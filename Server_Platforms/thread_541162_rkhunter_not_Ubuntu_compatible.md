---
title: "rkhunter not Ubuntu compatible?"
date: 2007-09-02
forum: Server Platforms
---

### Post by blue_mantra on 2007-09-02
Hi,
I installed rkhunter (Rootkit Hunter 1.2.9) from the repos and did a run: sudo rkhunter -c --display-logfile
and I always get :
```

  Performing 'known good' check...
Info: Check skipped - no hashes available

```

But I updated before sucessfully:
```

sudo rkhunter --update
Running updater...

Mirrorfile /var/lib/rkhunter/db/mirrors.dat rotated
Using mirror http://rkhunter.sourceforge.net
[DB] Mirror file                      : Up to date
[DB] MD5 hashes system binaries       : Up to date
[DB] Operating System information     : Up to date
[DB] MD5 blacklisted tools/binaries   : Up to date
[DB] Known good program versions      : Up to date
[DB] Known bad program versions       : Up to date

Ready.

```
Is Ubuntu Feisty Fawn not supported by rkhunter or why does it not find any 'kown good'-hashes ?

Everything else of these checkes is working but not the scanning for the knowngoods.

---

### Post by euler_fan on 2007-09-02
Re-run the check and it should work out fine now.

I installed from source and it does the hash checks on system files.

---

