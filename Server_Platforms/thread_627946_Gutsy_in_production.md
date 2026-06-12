---
title: "Gutsy in production?"
date: 2007-11-30
forum: Server Platforms
---

### Post by CheShA on 2007-11-30
Hi Folks,

At work, we are migrating to a VMWare ESX platform. I am responsible for a number of Debian, BSD and Slackware servers, but none of these distros is officially supported by VMWare. With this in mind, as part of the migration, I'm going to be moving to the only free distro that VMWare do support - yup, Ubuntie of course.

It's obviously a bad time to have to do this; 6 months down the line I'd have few qualms migrating to a Hardy base, but obviously Gutsy is a different question. I'm also reluctant to install Dapper and then be required to rebuild again in 6 months or so to get the best codebase so I guess the best middle ground is to install Gutsy and hope everything goes OK for the next 6 months until I can upgrade. Peak demand won't hit until next September anyway so I'm in the clear in that respect.

So basically, the long and short of it is this: does anyone have any experience running Gutsy in a production environment? It is a viable option for running business critical web services upon for thousands of users? Am I being over cautious? I mean, it wouldn't be a server edition if it weren't meant to be used on servers, right? But, can I really replace three of the most stable and secure distros with Gutsy?? Don't get me wrong, and I mean no disrespect; I'm an avid Ubuntu / Mint Desktop user, but server wise, comparatively speaking, I already feel like I'm going out on a limb moving to Ubuntu, let alone to an "unstable" release.

---

### Post by TheIdiotThatIsMe on 2007-11-30
Has your migration started yet? Since  you're already on free software, would it be impractical to wait until Hardy Heron? I understand your concern about going from 6.06 to 8.04, but I would heavily recommend using an LTS release since they are usually focused very heavily on stability and bug-fixing, and make for great operating systems, and for production use I would suggest waiting for a stable 8.04.

---

### Post by CheShA on 2007-12-01
It is impractical to wait since the hardware that the physical servers are running is now out of warranty. I have a vague plan which I think will work out OK:  Since we have redundancy for both production servers and load balancers, I can build one or two VMs off Dapper and leave the physical boxes running, This ensures VM  redundancy for the next few months until Hardy when I can build the rest.  Since this is only the second LTS relesase, does anyone know if there a dedicated effort to ensure a clean, highly tested ugrade path from Dapper > Hardy?  Will it be a single upgrade or will it be a case of going Dapper > Edgy > Feisty > Gutsy > Hardy ?

---

### Post by kesomir on 2007-12-01
I think it depends on what the server will be doing and under what load.

I had kernel panicks on gutsy running as an nfs server, which I now believe to be down to the gutsy clients (nautilus probs and runaway processes), but debian appears to perform better than gutsy in this regard.

I believe each LTS will have a direct upgrade path to the next LTS, skipping the intermediaries, but best check.

I run a debian NFS server as a VM without probs btw. I don't know what support contract you have with vmware, but I've not had a prob running debian, *buntu, suse, fedora etc in vmware machines if that's your concern.

My datacentre web server runs dapper, which I use for mail, apache2, php and mysql on the live internet websites. Can't comment on tomcat et al, but dapper has no problems dealing with that load.

I think that the best advice is to run anything mission critical on the LTS versions. I'm fairly sure it's a straight jump upgrade between them. Since you're using virtual machines,even worst case: rebuild should be no real issue if it were necessary, since you have an easy rollback on standby when you hotswop the live machines.

I don't know what web apps you'll be using and hence exactly what your build requires, but for my needs, web server build is less than 30 minutes from scratch.

Good idea with the standby servers btw - might it be worth having a couple of hot-standby builds in the wings? 

-> One set with ubuntu and the others an exact mirror of the distros and setup that's on the production hardware? - after all that's the beauty of VM, the ease of replication.

---

### Post by CheShA on 2007-12-03
Hi kesomir, thanks for the message .

> I run a debian NFS server as a VM without probs btw. I don't know what support contract you have with vmware, but I've not had a prob running debian, *buntu, suse, fedora etc in vmware machines if that's your concern.
Indeed; I run a bunch of stuff of varying distros on VM without any problems, but with a migration to VMWare ESX, I need to use officially supported distros or the gold support contract won't be worth the paper it's printed on.

> "My datacentre web server runs dapper"
Have you any stats as to how much traffic you get through it?  All in all it sounds like you've got quite a nice set up for a primary school :D

> I think that the best advice is to run anything mission critical on the LTS versions  

I know, i was just hoping someone else had given it a go and found Gutsy to work fine :-S  Having mapped out the project time lines and stuff, I might even get away with it and not need to build anything before April, but in order to be such an early Hardy adopter I was hoping to get some Gutsy testimonials to back me up.  FWIW I've been running a Gutsy (VMware) server in production for internal SNMP monitoring (i.e. non critical, non public, low traffic - we have several SNMP systems running on various platforms) and it's got 100% uptime.  The external stuff is a wholly different matter though. I'll miss the comfort of my Slackware boxes, but hey that's progress; it's much more appropriate to be running a managed distro in the kind of environnment I'm in.

> for my needs, web server build is less than 30 minutes from scratch.
Yes, i'm *really* looking forward to reducing admin overhead quite a bit but there will still be a lot to do to match the current setup!! I reckon a day or two for the build, then a week's testing before it can be brought online properly.... for each server!  Never mind the #@£#&%* paperwork :( :( :( 

> One set with ubuntu and the others an exact mirror of the distros and setup that's on the production hardware? 
I'd like to do that; have you any experience going P2V on Linux?  I've looked at it and it sounds hacky-at-best to me. I think the best thing is going to be to have fresh builds.  I'd be interested to hear any stories you might have though?  I'll be giving it a bash in the next couple of weeks before I start anything else, as a potential disaster recovery plan, but at the minute i'm not confident enough on it working that I feel I can rely on it!

Thanks again for your input.

---

### Post by ronald.higgins on 2007-12-03
> 

I'd like to do that; have you any experience going P2V on Linux?



Hmmm .... to date i've attempted a few linux P2V migrations using the VMWare P2V client .... note "attempted", none of those to date have been successfull, I have however been pointed to Platespin's PowerConvert which supposedly handles *nix P2V's a lot better, perhaps it'll help you.

rH

---

### Post by CheShA on 2007-12-04
Cheers for that, i'll take a look.

---

