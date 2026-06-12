---
title: "Upgrading 19.04 to 19.10 python3 install corrupted"
date: 2019-10-17
forum: Server Platforms
---

### Post by chipmand on 2019-10-17
I am attempting to upgrade 19.04 to 19.10 using 'sudo do-release-upgrade -d' It gets to 'checking package manager' then prints 'Can not upgrade. Your python3 install is corrupted. Please fix '/usr/bin/python3''. 'usr/bin/python3' is a symlink to /usr/bin/python3.7. How should I fix this? Thanks, 

-David

---

### Post by TheFu on 2019-10-17
Is the 19.04 system fully, completely, patched without any package errors?  That is step 1.
Step 2 is to have 100% know-you-can-restore backups BEFORE beginning.  Sometimes bad things happen. 

Did anyone on the system try to manually upgrade python3 outside the package manager?

---

### Post by chipmand on 2019-10-17
It is up to date. I just loaded python3, and it's version is 3.7.3  and it's build date is October 7 2019. No one ha updated python outside the package manager. I did try fixes from early versions of Ubuntu where people had had similar errors, and apparently in doing so, I *did* remove python2.7. Reinstalled it and things seem to be working now.

---

