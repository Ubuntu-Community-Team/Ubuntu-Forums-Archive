---
title: "Cluster from Scratch - pcs equivalent"
date: 2013-10-14
forum: Server Platforms
---

### Post by flickerfly on 2013-10-14
I'm working my way through Cluster Labs frequently recommended documentation [Clusters from Scratch]("http://clusterlabs.org/doc/en-US/Pacemaker/1.1/html/Clusters_from_Scratch/_install_the_cluster_management_software.html") and trying to modify it for Ubuntu, from the RH directions. It instructs the user to install pcs, but that doesn't appear in the repos. What is the equivalent? cman seems like it would be similar, but am I correct that it is an entirely different tool?

```
$ sudo apt-get install pcs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pcs
```

---

### Post by houstonbofh on 2013-10-16
It has a different name.  Search the packages for "pacemaker" and look at the option there.  Also, there are some Ubuntu specific instructions from the main page at [http://clusterlabs.org/doc/](http://clusterlabs.org/doc/)

---

