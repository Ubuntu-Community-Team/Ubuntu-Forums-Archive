---
title: "Don't make the same mistake I did..."
date: 2005-02-09
forum: Server Platforms
---

### Post by diegomontoya on 2005-02-09
Beware of running Ubuntu or any other Distro using the 2.6.8, 2.6.10, 2.6.11rc kernels on a setup with A LOT of tcp connections.

I have a 4 servers in a forwarding facing http proxy cluster and Ubuntu and Fedora have given me anything but Kernel Panics with failed to sync errors on apparent tcp interrupt. This has happened daily in the last 4 weeks and considering the 4 servers are all different machines, ranging from Athon to AMD64 to Xeon, and different NIC cards, the only common thread is the recent 2.6 kernels. It is highly unlikely all of them conspired to give me the exact same kernel panic out of spite. Upgraded to Hoary to no fix. Even a manually compiled 2.611rc kernel did not do the trick as the same kernel panics raged on. Considering that my 4 server redudant cluster suffers at least 2 kernel panics every 12 hours, it is quite a nightmare for any admin.

This is not a knock on Ubuntu but the latest kernel series in general when it comes to stability. 

On the positive side, these kernel panics only appear to happen to this cluster of 4 servers which face tcp connections several magnitude larger in volume then any other servers I have and the other less tcp chatty servers using the same 2.6.X distros have not gone down yet.

I can only resonably assume the error is triggered in a high volume short-term tcp creation/tear-down.

The 4 servers have now being installed with CentOS 3.4 and have been panic free since. 

I don't want to make this a thread as a "don't use" cry as panics are selective in the environment you put the servers in so for most people, you will never see them. However, if you do, and often, learn from my trials, and stop using 2.6 altogether as a fix is not in 2.6.11rc branch and thus not in the near-term horizon. Grab CentOS 3.4 and run with it.

---

