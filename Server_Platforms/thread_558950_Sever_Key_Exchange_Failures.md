---
title: "Sever Key Exchange Failures"
date: 2007-09-24
forum: Server Platforms
---

### Post by jbMSU on 2007-09-24
I'm the LINUX system administrator for the CS department at my university.  I've been having a big problem with key exchange failures when trying to access remotely.  We just updated the sever to OpenSSH 4.2p1 from 4.1p1 and it's apparently causing the problem.  All students and lab computers are using SSH Secure Shell 3.2.9 (build 283) to connect and for file transfers.  We know this version worked with the server before we updated, but now displays:

     Server responded "Key exchange failed.".
     
     Key exchange with the remote host filed.  This can happen for         
     example if the remote host computer does not support the selected
     algorithms.

Updating the lab computers to a newer version of SSH Secure Shell is not possible because of our IT department.  Is their anyway to make the sever's OpenSSH compatable with the lab PC's SSH Secure Shell?  Is there a way to downgrade back to OpenSSH 4.1p1?

---

### Post by jmori on 2008-06-28
Hi, i am having the same problem, i noticed that this thread was created a while back. Did you ever managed to fix it? 

I made a windows virtual machine from my Ubuntu computer, and i installed ssh secure shell 3.2.9 so i can transfer some files.

Thanks, 

Jorge

---

