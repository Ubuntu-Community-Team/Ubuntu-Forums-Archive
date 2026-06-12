---
title: "Error with freenx"
date: 2005-05-28
forum: Ubuntu Backports
---

### Post by Leif on 2005-05-28
I've got freenx installed on two computers, and on one, I got the error : "E: freenx:  subprocess post-installation script returned error exit status 1". I'm not too bothered, but I get this error message every single time I use apt for anything. I've tried removing all nx related packages I could find and reinstalling, but nothing changes. Any ideas ?

---

### Post by valnar on 2005-06-16
I have the same problem, so it also prevents me from reinstalling freenx.  I took the advice of one of the posts on this forum and tried to remove it manually by deleting *nx* related files and I think I messed it up.  So how can we kill everything related to Freenx and start over again?

Robert

---

### Post by jdong on 2005-06-16
[QUOTE=Leif]I've got freenx installed on two computers, and on one, I got the error : "E: freenx:  subprocess post-installation script returned error exit status 1". I'm not too bothered, but I get this error message every single time I use apt for anything. I've tried removing all nx related packages I could find and reinstalling, but nothing changes. Any ideas ?[/QUOTE]
try: 

nxsetup --uninstall --purge

*Remove everything NX/freenx related*
edit /var/lib/dpkg/status , remove all nx/freenx stanzas.

Install FreeNX again.

---

### Post by valnar on 2005-06-16
Doesn't work.  Same error.   ](*,) 

-Robert

edit:  I got it working.  Clearing the VAR cache did it.  Thank you!

---

