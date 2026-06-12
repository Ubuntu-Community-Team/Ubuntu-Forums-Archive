---
title: "Dell PowerEdge Servers - Random Networking Issues"
date: 2007-05-01
forum: Server Platforms
---

### Post by malave on 2007-05-01
Hello everyone,

I am experiencing some very odd issues with my Dell Servers running Ubuntu 6.10 Server.  The built-in network interface cards in these servers seem to become unresponsive at random intervals and the networking services need to be restarted.  Once the networking services are restarted the server functions normally until the issue repeats itself again.  DNS seems to be the service that becomes upset the most.  The service will remain running however, will not accept incoming request until the networking has been restarted.  I am experiencing this behavior on my Dell PowerEdge 1950, 2850, and 2950.

I have tailed the logs, cat'ed and grep'ed them for certain phrases associated with nic failures but I can not find anything that would explain this weird behavior.

Where do I go from here?  This issue is affecting my DNS services, Web Services, Internet Proxying, and Content Filtering as these services all run on Ubuntu 6.10 Server on Dell Servers.

Any help would be appreciated.

Thanks!

---

### Post by garlik42 on 2007-05-01
We had similar issues at my previous job, with older units (3 or so years ago) using Windows and Redhat. The issues could not be resolved by Dell, but seemed to be related to the broadcom embedded controllers that dell uses because they cost less. So we started using Intel addon network cards and the problems went away.

---

### Post by malave on 2007-05-01
Is there a way to update the drivers for the broadcom card?  Any suggestions on how to fix these intermittent networking issues?

---

### Post by malave on 2007-05-02
I thought it might be an auto negotiation problem and I tried locking the card to autoneg off and 1000 Full and we set the ports on its switch to 1000 Full.  However, the problem still exist.  We even tried moving the server to different switches to rule out a possible switch problem.  No matter what we do the problem remains.  What am I missing?

---

### Post by garlik42 on 2007-05-02
We were unable to get anything to work with any reliability, not sure why the broadcom drivers are a bit wonky, but they are. I have similar issues with my broadcom wireless under linux, it works, but "goes away" every once in a while.

The only solution I am aware of is to replace the cards with a card that has better support in linux. While in my previous job, Dell was able to fix most of the windows related issues eventually the linux issues remained outstanding, and since we had a standard hardware platform, when we changed cards for linux we changed them for windows also.

The intel cards we used were like $40 a piece, and were well worth it, they had NO problems like the broadcoms. I personally will not purchase a piece of equipment with broadcom embedded controllers any more unless I can put another card in it.

The why I cannot give you, but my guess is that broadcom is not sharing the information nesessary to make a decent linux driver, and the driver writers are trying to reverse engineer. And while the driver has improved over the past couple of years, if broadcom would be a little more cooporative, it would only benefit them.

---

