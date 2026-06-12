---
title: "Virtualization on server for isolation and development"
date: 2013-03-06
forum: Server Platforms
---

### Post by rzj on 2013-03-06
I've been "playing around" with ubuntu server in a XEN VPS, exploring a number of different technologies and getting them working. I now need to move towards a production system yet still have the facility to explore new applications.

My good intentions about recording everything I did on the prototype system fell victim to the reality of rapid changes to config files as I went through problem solving to get things to work.

I need to get a clean install and add in all the tools in a more controlled way, but I also want to be able to try new things then migrate them to the production system. I also like the idea of being able to sandbox applications if possible to isolate them from each other.

I don't want to destroy my prototype system so I'm thinking I need a second VPS to build a better controlled system.

I've been thinking it would be good to use some sort of virtualization on the new VPS to clone a system locally, add to it and then subsequently migrate features to the "live" container. It seems like LXC might deliver that, but there's little documentation and also suggestions that it is not yet mature.

I also can't quite figure out what gets duplicated in an LXC instance - is it a clone of the whole directory tree from / downwards, or do all the systems share some files? 

The suggestion that one could run different releases in different containers suggests it's the whole FS but I'm not sure if that's right.

If I create an LXC system can I then clone it to a peer level copy and then modify that peer, and finally clone it back to "release" the modified system into the "live" one. 

I can see that I could use virtualbox to achieve something along these lines but would it suffer too much of a performance hit? I'm thinking that virtualbox would be running two or more complete systems each with their own kernel out of the memory and CPU resource of my VPS, whereas LXC I think is using a single kernel so if I'm running the same number of applications just split into separate containers that I would use the same total resources (maybe some duplication for say 2 copies of mysql etc, but only one copy of, say, tomcat and one copy of dovecot).

I'm thinking maybe I can use rdiff-backup to clone systems from one LXC container to another and to identify changes from a saved baseline (maybe on a cloud server or my NAS at home). Could I do that with virtualbox peer level systems? Either by cloning them and comparing them to external stores or even finding someway that they can see each other through a network connection bridged through the host VPS system?

I'm also hoping that if I build a second system with the same version of ubuntu server fully updated and the same additional packages that rdiff-backup can help me identify what I've modified from stock distributions


Thanks,
Ray

---

