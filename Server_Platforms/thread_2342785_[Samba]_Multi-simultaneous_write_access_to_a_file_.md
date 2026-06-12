---
title: "[Samba] Multi-simultaneous write access to a file on a Samba share"
date: 2016-11-09
forum: Server Platforms
---

### Post by mdewhirst on 2016-11-09
I am running Ubuntu 16.04 LTS Server (no GUI) upgraded from 12.04 via 14.04 with Samba providing disk space as a Windows file server. Plain vanilla local area network, no Windows domain.

I am also successfully running an application written in Paradox 7 for Windows on the Windows workstations (7 and 8.1) which requires write access to a file called PDOXUSRS.LCK and all other files in the directory in which it lives. The application runs separately on each workstation and Paradox 7 accesses the database in that directory using Borland BDE. 

Currently only one user at a time can have that application open. It is vital for my business so I'm stuck with it. C'est la vie.

Some years ago before discovering Ubuntu,  I had OpenSUSE with a Novell Netware VM providing the file serving for that application. That was successfully running multiple simultaneous Paradox users. Novell (and Windows for that matter) was able to permit this. 

Thanks for reading this far. Here is my question:

How can I set up Samba (and/or directory permissions) to do the same thing?

Thanks in advance

Mike

---

### Post by cariboo on 2016-11-09
Close duplicate thread.

---

