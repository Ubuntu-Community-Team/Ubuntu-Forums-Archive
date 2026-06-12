---
title: "Problems when two nfs clients share /home at same time"
date: 2018-01-30
forum: Server Platforms
---

### Post by bogeyman2 on 2018-01-30
ClientA and ClientB have /home mounted from ServerX using nfs and autofs. The mount appears to be working ,albeit a little slow; however, the problem that I am seeing is when I log into xfce on both clients at the same time. One problem from this as an example is when i run Firefox. It runs fine on one client, but when I run it on the other it says it cant run because another instance of Firefox. I get the problem. If i am using the exact same /home fs, then it will be using the exact same app files/lock file, etc. My question is not so much how to fix the Firefox issue, but rather have I done this NFS configuration wrong or is that just the downside of sharing /home folders? TIA

---

### Post by wildmanne39 on 2018-01-30
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by SeijiSensei on 2018-01-31
Do Clients A and B have separate home directories on the NFS share? They should.

---

### Post by bogeyman2 on 2018-01-31
No they do not. Just separate directories for each user. The reason I wanted to share the same home is so that I have the same desktop and files no matter which client I sign in to. Is this not possible (without involved scripting) through NFS?, Is it not recommended ?

---

### Post by volkswagner on 2018-02-02
As you have discovered you will run into issues with lock files for programs like Firefox, if
your user home profile is shared between physical hosts.

You should keep separate profiles for each user. A single user should not be accessing two 
workstations at the same time (how can he be in two places at once).

If you have a need to have the same user log into multiple machines at the same
time, while accessing shared desktop files, you should perhaps create separate share
outside users ~/home/username to share between systems, but have local profile
on each machine.

---

