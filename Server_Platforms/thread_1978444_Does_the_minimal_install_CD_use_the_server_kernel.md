---
title: "Does the minimal install CD use the server kernel?"
date: 2012-05-11
forum: Server Platforms
---

### Post by MakOwner on 2012-05-11
If it doesn't, what are the differences between the server install kernel and the mini install kernel?

---

### Post by oldfred on 2012-05-11
this was in the server release notes:
I would then assume that every version has same kernel?


[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer)
> 
The [amd64 -generic and -server kernel flavors have been merged]("https://lists.ubuntu.com/archives/kernel-team/2011-October/017471.html")  into a single -generic kernel flavor for Ubuntu 12.04.  Given the few  differences that existed between the two flavors, it only made sense to  merge the two and reduce the overall maintenance burden over the life of  this LTS release. 

---

### Post by wilee-nilee on 2012-05-11
Use the advanced cli and you have a choice of kernels.

---

