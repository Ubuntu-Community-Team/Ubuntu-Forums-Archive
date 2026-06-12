---
title: "Need help going from 16.10 to 16.04"
date: 2018-02-01
forum: Server Platforms
---

### Post by pmd5700 on 2018-02-01
I have a headless server running 16.10. I need to go to 16.04 since it's a LTS version. Is there a better way to handle this other than connecting the server to a keyboard, monitor, and mouse and redoing the entire thing?

---

### Post by wildmanne39 on 2018-02-01
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by TheFu on 2018-02-02
> **pmd5700 said:**
> I have a headless server running 16.10. I need to go to 16.04 since it's a LTS version. Is there a better way to handle this other than connecting the server to a keyboard, monitor, and mouse and redoing the entire thing?

You could backup the data, settings, and list of installed packages, then do a fresh install, and selectively put the data back, put the settings for programs back which don't conflict with newer, 16.10 versions, then install all the packages from the list and hope for the best.

Going backwards really isn't supported, so if you have any server programs moving backwards, it is likely that internal data structures aren't compatible.  Never know until you do the research on each and every program.  For a DBMS, you might get away with a dump/export of the database(s) involved, then import those back into the older release used on 16.04.

I'm a huge believer in using virtualization, so I would load up a minimal Ubuntu 16.04 server as a VM host, then create a new VM for this other system to run inside.  VMs provide amazing flexibility.  For example, you could have both the 16.10 version running and a 16.04 version concurrently. This way you can slowly migrate services over and validate the migration is working as needed.  Plus backups and recovery testing is much easier with virtual machines.  No harm in testing a restore process 50 times on a VM, since it is just storage that gets eaten, not an entire physical machine.  

Lots of reasons to use virtualization. Lots.  IMHO.

---

### Post by LHammonds on 2018-02-02
I saw the title of this thread and was going to answer but TheFu has already said it all and I'll just reaffirm what he said especially the part about running a VM even if you plan to run just a single host.  Migrations to a new host are MUCH more easier when the time comes and you have the option to run more than one VM if you need later as well as all the possible testing scenarios...but you could do tests on your PC in the same way using VMs.

Every time there is a new version of the OS, I always create a new server with the new OS and re-create the old server from scratch...then I migrate the data and ensure it works on the new platform...then swap IP addresses when I want to make the new server permanent.  This kind of re-install/migration is supremely easier if you document exactly how to install your servers.  Example: [Ubuntu Server]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220"), [MariaDB]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=225"), [NextCloud]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=239"), etc.

LHammonds

---

