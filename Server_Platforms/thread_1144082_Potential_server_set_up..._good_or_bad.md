---
title: "Potential server set up... good or bad?"
date: 2009-04-30
forum: Server Platforms
---

### Post by BluShift on 2009-04-30
I've wanted to run a simple HTTP server to download stuff from. I have done it before with XAMPP and Windows XP, but like the network transparency of Linux and I love everything open-source (I have been running Kubuntu for almost 6 months)
 This is what I'm planning on doing:
 First machine with Xubuntu (Makes it easier on me, because I suck with Bash/Ash/Dash etc. and XFCE frees resources for the actual server processes) running XAMPP/LAMP stack, to handle the actual webpage and images.
 


 Have all remaining machines connected to the the network, again running Xubuntu, but without the LAMP/XAMPP stack, but have each of them having seperate types of media on each, ex: one machine handling webpage and image requests, one handling game download requests, one handling movies etc.
 


 I would virtually mount all the other machines to the “head” machine (the one handling the pages) to the same directory as the XAMPP/LAMP stack's http documents folder (should be /opt/lampp/htdocs/) using pyNeighborhood and have the links on the page directly reference the mounts for total transparency, while still splitting work between all the different machines. I understand the idea of topping out the head's network adapter, but I'm doing this mainly because downloading anything from our single head (everything on the head; how we used to have it set up) results in serious hard disk thrash; every subsequent simultaneous download *halves *the download speed.
 


 One other idea I had was having the actual webpage reference the other machine directly... so that the download is done entirely through the other machine, rather than all requests coming from one machine and bottlenecking through the head before getting to the user. I haven't investigated if this is even POSSIBLE, however. I get the feeling it isn't.
 


 Thoughts? Suggestions? Is this a bad way of doing it?

---

