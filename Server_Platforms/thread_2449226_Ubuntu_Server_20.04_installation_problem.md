---
title: "Ubuntu Server 20.04 installation problem"
date: 2020-08-22
forum: Server Platforms
---

### Post by richieserver on 2020-08-22
I cannot figure how to get Ubuntu server to work properly again

The ethernet worked once, but has now stopped working altogether. I noticed this while I was trying to install a package from the ubuntu repository, it just wasn't downloading anything

Re-installed server again, because I had messed up big time doing something to get a RAID setup

The DHCP v4 is constantly disabled

When I get to the CLI after installation, and type in

```

sudo lshw -class network

```
it keeps saying it's been disabled

I have enabled the ethernet in the BIOS, but it's not doing anything to resolve it

---

### Post by richieserver on 2020-08-22
OK, found the problem. Not down to Ubuntu, but down to the way I connect to the internet and the erratic behaviour of a certain other well known OS

---

### Post by Bashing-om on 2020-08-22
richieserver - hey hey :D

Thanks for that feed back.
As this issue is resolved:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

-keep it clean behind us-

---

### Post by richieserver on 2020-08-22
OK, didn't know that will do in the future

---

### Post by TheFu on 2020-08-22
May find [https://ubuntu.com/server/docs](https://ubuntu.com/server/docs) helpful.

---

