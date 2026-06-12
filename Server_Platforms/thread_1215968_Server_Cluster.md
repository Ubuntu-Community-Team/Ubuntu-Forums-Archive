---
title: "Server Cluster"
date: 2009-07-17
forum: Server Platforms
---

### Post by megahost on 2009-07-17
I want to cluster 2 servers so basically it's 1 powerful server. How would i do this?

---

### Post by megahost on 2009-07-17
anyone? please

---

### Post by jerrrys on 2009-07-17
[http://www.google.com/search?q=clustering+two+computers+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=clustering+two+computers+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://www.google.com/search?q=clustering+two+computers+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=clustering+two+computers+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by ktrnka on 2009-07-18
What is exactly the purpose of your cluster?

It is not as simple as slapping 2 computers together. The quickest way to mess around with a basic cluster, with a SSI cluster and the only active one is Kerrighed using kernel 2.6.20.

[http://www.kerrighed.org/wiki/index.php/Main_Page]("http://www.kerrighed.org/wiki/index.php/Main_Page")

Again this subject goes very deep. You could also setup a dvdrip cluster with dvd::rip

[http://www.exit1.org/dvdrip/]("http://www.exit1.org/dvdrip/")

You will need to google info on the subject as there is a ton of info.

---

### Post by Advice Pro on 2009-09-25
the following link gives instructions on how to install Kerrighed on Ubuntu:

[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

---

### Post by openfly on 2009-09-25
Yeah what exactly or to the best of your ability to describe... is your use case?

---

### Post by Advice Pro on 2009-09-25
I've Wanted to build a load-balancing cluster for more than just education and scientific use.  I think an SSI cluster can do this and I chose Kerrighed because I hear it's the best.  Though I don't have any experience with Linux, I choose Ubuntu because I hear that it's the best distribution!

---

### Post by openfly on 2009-09-25
Okay I think we might need more information...

are you planning on using this cluster for processing large floating point math operations?  are you using it to parse full text databases?  are you attempting to decode chunks of the gnome?

I meant depending on the use case how you choose to cluster can have pretty heavy impact on how easily / functionally your use case will be met.

---

### Post by Advice Pro on 2009-09-25
I'll use the cluster for 3D authoring and databasing in addition to general PC use such as using the Internet and debugging.

---

### Post by openfly on 2009-09-25
Uhm... zoof?

---

### Post by Advice Pro on 2009-09-25
What? Do you mean that I can't do the the stuff I mentioned?

---

### Post by openfly on 2009-09-25
> **Advice Pro said:**
> I'll use the cluster for 3D authoring 

Well 3D render farms are pretty interesting.  What software are you using and does it have a batch rendering system.  How that batch rendering system works will probably suggest how your cluster should work.


> **Advice Pro said:**
> 
and databasing 

I've never seen database used as a verb before.  What do you mean by "databasing".  I mean if you are using mysql as excel 2.0 odds are you don't need a cluster and wouldn't benefit from one anyways.  In terms of clustering something like mysql... you don't need a traditional cluster anyways as mysql-cluster is kind of a bundled solution.

> **Advice Pro said:**
> 
in addition to general PC use such as using the Internet

That's just silly.

> **Advice Pro said:**
>  and debugging.

Debugging what?  Your databasing or your 3d rendering?

---

