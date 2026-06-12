---
title: "give some advices on setting up Ubuntu server :)"
date: 2011-03-24
forum: Server Platforms
---

### Post by fang0319 on 2011-03-24
We have 5 servers here. What we are going to setup is not a Web server.  We want to combine these servers to parallel calculating. I have searched for some information. May be  cloud computing would be our choice.  I don't know whether I am right.and if I decide to use the cloud, is Ubuntu server my best choice? Can anyone give me some clue about this? or any advices? 

Thank you very much!:)

---

### Post by tgalati4 on 2011-03-24
You will need to describe more completely what calculations that you are performing.  Is this a custom application?  Is it multithreaded and can it take advantage of multiple processors?

apt-cache search cluster

mpich
beowulf

eucalyptus-cc - Elastic Utility Computing Architecture - Cluster controller
eucalyptus-cloud - Elastic Utility Computing Architecture - Cloud controller

There are several cluster frameworks.  The one you choose depends on what exactly you are trying to do.

---

### Post by fang0319 on 2011-03-24
> **tgalati4 said:**
> You will need to describe more completely what calculations that you are performing.  Is this a custom application?  Is it multithreaded and can it take advantage of multiple processors?

apt-cache search cluster

mpich
beowulf

eucalyptus-cc - Elastic Utility Computing Architecture - Cluster controller
eucalyptus-cloud - Elastic Utility Computing Architecture - Cloud controller

There are several cluster frameworks.  The one you choose depends on what exactly you are trying to do.

We use the commercial software FLUENT(If you know what i mean:)) . it's using the ssh or rsh to start the calculation simultaneously on several machines. So I guess it won't be very difficult. All I need to do is install the software in all the machines in the same path and make sure the ssh and rsh working correctly. But it's only my deducing, I'm not very experienced.:D

---

### Post by tgalati4 on 2011-03-24
Well, a google search brought up a bunch of random links, but there were a few related ones:

[http://beren.engr.udel.edu/doku.php?id=documentation:fluent-setup](http://beren.engr.udel.edu/doku.php?id=documentation:fluent-setup)

It's been several years since I've used Ansys products, and not in cluster computation mode, so I can't be of much help on this software.

I would revise the title of your thread:  "Need help setting up FLUENT on 5 ubuntu servers--clustered."

---

### Post by fang0319 on 2011-03-25
> **tgalati4 said:**
> Well, a google search brought up a bunch of random links, but there were a few related ones:

[http://beren.engr.udel.edu/doku.php?id=documentation:fluent-setup](http://beren.engr.udel.edu/doku.php?id=documentation:fluent-setup)

It's been several years since I've used Ansys products, and not in cluster computation mode, so I can't be of much help on this software.

I would revise the title of your thread:  "Need help setting up FLUENT on 5 ubuntu servers--clustered."

thank you :)

---

