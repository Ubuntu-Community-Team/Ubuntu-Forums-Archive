---
title: "Services not starting when booting"
date: 2010-09-29
forum: Server Platforms
---

### Post by trundlenut on 2010-09-29
I have a server running 64bit lucid and while trying to get a script to run on boot to start Davmail I appear to have broken something.

I have webmin installed but I have been trying to do the majority of things via the command line.

I now have davmail starting at boot but a lot of other services don't start anymore, including apache, mysql and webmin.  Fortunately SSH still works and I can start apache and webmin from the command line without any problems.

Any pointers on where to start looking for the source of the problem?

---

### Post by Vegan on 2010-09-29
Sounds like your system has trashed the autorun script to start services.

I recently had to do a fresh install after my own server crapped out.

---

