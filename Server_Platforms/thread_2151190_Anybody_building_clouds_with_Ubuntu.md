---
title: "Anybody building clouds with Ubuntu?"
date: 2013-06-03
forum: Server Platforms
---

### Post by sangsterthegangster on 2013-06-03
Hey everyone,

I'm an intern for a small firm. My boss bought a multi-node server and wants me to set up a cloud environment for virtual machines. 

Ive been experimenting with Rackspace Private cloud software because the install is SOOOOOOOO easy. However, the web based GUI kind of... well... sucks. It just doesn't have any real functionality. Since, I'm not the only person that's going to be using this, a good functional GUI is a MUST. And the software is set up for an environment that is way bigger than what we have which makes it terribly ineffecient. So with all that in mind I have decided against Rackspace's Private Cloud Software. ( I know its based on cloudStack, but what they have done to it makes it unusable in my environment.) 

I plane Jane install of (the open source version) OpenStack or Cloudstack seems to be what I need. I tried DevStack and LOVED IT! However when I go to do a real install of the software... its SOOOO tedious! You have to do so much stuff manually! Stuff that I feel could be done with a script. Same with CloudStack! I just don't understand why there can't be a script to install the software automatically? I mean the main node install is bad enough; but then I have to do a similar install on 3 more nodes! 

So I guess my main question(s) is: Is there an easy way to install (plane Jane) Openstack or CloudStack on all nodes? 

Other questions: Is Ubuntu cloud based on OpenStack? And if there is no easy way to install, could DevStack be used in a small environment reasonably? 


I know this question doesn't relate to Ubuntu directly, but since I'm using ubuntu server for my controller node ( in openstacks case on the compute nodes as well) I was just wondering if anyone else has had any cloud experiences. If you do; please share! 

Thanks in advance!

---

### Post by sandyd on 2013-06-03
Slightly offtopic - tried OpenStack as well - was a huge pain to setup.

Im using proxmox now, which supports KVM and OpenVZ and I StackOPS. For someone whose tried to setup OpenStack, StackOps is much much simpler.

---

