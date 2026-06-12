---
title: "Computer cluster"
date: 2014-06-09
forum: The Cafe
---

### Post by Tristan_Williams on 2014-06-09
I have been looking at the RPi clusters people are building with 32 nodes and an extra "main" node.
I would like to build something like this but with normal desktop motherboards, probably one similar to [this]("http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh87mc.html").

My plan is to "cluster" 4 or 8 of these boards to multiply processing power.



Can anyone point me to any resources such as tutorials, tips, blueprints, etc, as to how I would do this?

---

### Post by RichardET on 2014-06-10
A quick search yields much info on Beowulf clusters:

[http://en.wikibooks.org/wiki/Building_a_Beowulf_Cluster](http://en.wikibooks.org/wiki/Building_a_Beowulf_Cluster)

---

### Post by grahammechanical on 2014-06-10
Here is a similar project that may give you ideas.

[https://insights.ubuntu.com/2014/05/13/the-orange-box/](https://insights.ubuntu.com/2014/05/13/the-orange-box/)

insights.ubuntu.com is developing into a resource of information and tutorials.

I think that the Orange Box is made by these people using Intel NUCs

[http://tranquilpc.co.uk/nuc_story.html](http://tranquilpc.co.uk/nuc_story.html)

Regards.

---

### Post by DuckHook on 2014-06-10
> **Tristan_Williams said:**
> ...Can anyone point me to any resources such as tutorials, tips, blueprints, etc, as to how I would do this?I have a lot of old HW complete with CPUs and MOBOs lying around, so got the same idea in my head about a year ago. Did my research and discovered the following:

1. Though perhaps beyond reach for a newbie, it really isn't that hard for a seasoned Linux veteran to build a beowulf cluster.
2. The problem isn't the physical assembly, the connection topology or gathering together the apps; it's what to do with the cluster once it is built.
3. My initial rationale was to run folding@home and contribute to a good cause. I soon discovered that it is more CPU efficient to run eight separate instances of F@H than one instance in a cluster of eight CPUs.
4. Same is true for virtually all standard apps: they are not designed to run efficiently in a cluster. The only apps that do are exotic and highly specific-use apps like the imaging software in CGI render farms or nuclear explosion modeling on supercomputers.
5. Unless you are prepared to write similar code, your cluster will be more an intellectual curiosity than a real-world tool.
6. Clusters are very finnicky. As only one example, they don't mix and match well. Unless your nodes are absolutely identical, the entire cluster will run at the speed of its weakest node. Or the choke point may be the network switch. Or whichever is the weakest link in your chain.

[Here's]("http://www.lsm.cic.ipn.mx/sites/all/themes/danland/files/cluster.pdf") the small article that started me down the clustering road. It has links to other relevant sites. But peek under the initial surface layers, and you will start discovering the limitations of clusters. I'm still somewhat curious about the concept and may even try it out one day seeing as how I've already got most of the pieces &#8213; but all of that additional inquiry sure took most of the wind out of my sail.

---

### Post by HermanAB on 2014-06-11
If you google for "linux high performance cluster" then you will find everything you need really quickly.

As pointed out above, the problem is what to do with it.  Stock market pattern prediction, horse racing, weather reporting, seismic processing, passive radar... all rather specialized.

---

