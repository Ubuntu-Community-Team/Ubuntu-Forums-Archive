---
title: "Help setting up Ubuntu Servers"
date: 2012-01-08
forum: Server Platforms
---

### Post by Jwag598 on 2012-01-08
I'm working on building a render farm for the Blender 3d suite. I have three computers (more to come later) for the farm. I was wanting to be able to control all three computers from a single laptop that mounted on the render farm case and the three computers wouldn't have any monitors/keyboards/mice, they would all be controlled from the laptop. Is this possible and if so how am I able to do it. I googled and found synergy, but while the program is pretty cool it's not quite what I'm looking for

Thanks in advance

JWag

---

### Post by oldos2er on 2012-01-08
Moved to Server Platforms.

---

### Post by rubylaser on 2012-01-08
This is very easy.  I manage a Blender render farm at work for our Archviz renders.  I have 24 machines in the cluster with almost 200 physical cores.  Personally, I either use Blender via the cli with the no touch option on via a shared NFS directory, and launch the nodes via shell script, and I've used XGrid in the past, but with Blender 2.6x, you can just use Blender's built in [network rendering]("http://wiki.blender.org/index.php/Doc:2.6/Manual/Render/Performance/Netrender").  Or, there are tons of render farm apps like [Farmerjoe]("http://farmerjoe.info/"), but frankly, I've always liked the simplest method, because when it breaks, you need to quickly be able to get it functioning again if it's a production environment.

---

### Post by Jwag598 on 2012-01-08
[LEFT]Ok that sounds pretty simply if it's built in blender itself. Could I do that from a window's machine on the three linux or do they all need to linux? And am I able to have the windows machine render the scene to?

That sounds like an insane farm
[/LEFT]

---

### Post by Ramdhandwi on 2012-07-04
Hi, are there any tutorials to setup an ubuntu server for blender? I've googled, but found only a few related solutions. I'm a newbie in this. Please help.

Thank you.

---

