---
title: "Comment on my Technology Puzzle for small office"
date: 2008-07-25
forum: Server Platforms
---

### Post by jimcooncat on 2008-07-25
I suppose in the end that it would get limited use. I'm the only one in the office using ubuntu at home and work. Rest prefer XP (I use it for some things) so I'm going to publish Ubuntu apps to them, probably through xming. 

I wanted to do it the other way around, giving them a gnome-panel and using seamlessrdp to show them Win apps, but I can't grok the MS side of the equation. 

I feel stuck in a technology wireframe puzzle on this.

I've got three servers ready to go, and a few thin clients and win 98 boxes. 
Been running two Win sessions under virtualbox, one I export to an offsite worker (plus she has a thin client to use at work) with vnc within one of the sessions. The other session I use for Quickbooks and my MS Access databases I build for them.

Two of the servers are going to (among other things) host a /home partition using drbd. The other server I'm reserving for developing, testing, and deployment. It will also be my offline backup.

I'll start loading them next week, using the dev server to preseed netboot installations to the others. I'm going to keep installing and tweaking the preseed until I get it right.

I've been somewhat impressed by virtualbox, but I'd like the opportunity someday to be able to migrate vm's from one server to the other, so I can take them down and clean dust bunnies without downtime or me working on weekends.

Plus I'm not sure that I'm getting the best performance out of it, so I'm going to give KVM a shot. 

VMWare ESX or whatever is probably what I need, but I don't have the resources to commit I believe.

Any comments from anyone on these topics are not only welcome, but much appreciated.

---

