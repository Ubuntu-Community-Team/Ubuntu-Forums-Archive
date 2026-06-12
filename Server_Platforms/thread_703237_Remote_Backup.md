---
title: "Remote Backup"
date: 2008-02-21
forum: Server Platforms
---

### Post by ravagilli on 2008-02-21
What i'm looking to achieve here is a complete backup solution that will enable me to run some sort of backup software on windows machines, then upload the backup files to a ubuntu server over the internet at a differant location. The windows machine would have to have a mapped network drive.

---

### Post by MJN on 2008-02-21
I would recommend using rsync running under Cygwin on the Windows machine (cwrsync is one such package to achieve this).
 
I'm not sure I understand your requirement for a mapped drive.
 
Mathew

---

### Post by ravagilli on 2008-02-21
well its just for ease of use, with a total automated backup on the windows machine, where the user doesnt have to do anything once the intial set-up is complete. mapping the drive just seemed like an idea, or something along that sort of basis.

---

### Post by MJN on 2008-02-21
Ah okay.
 
A mapped drive is one way (and hence just use any local backup solution) however I would expect this to be sub-optimal particularly given the finite bandwidth available.
 
Rsync is designed, indeed optimised, to work over a network (Internet) and can be easily configured to run automatically using the Windows scheduler.
 
Some of the advantages with using rsync are that it can be started/stopped as required and it will pickup gracefully from where it left off, it will only transfer files that have changed (indeed it will only transfer the *parts* of files that have changed - but this will be done transparently to the user), it is secure, widely used, platform-agnostic, and probably more besides.
 
Mathew

---

