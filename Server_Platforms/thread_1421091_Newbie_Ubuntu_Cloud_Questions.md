---
title: "Newbie Ubuntu Cloud Questions"
date: 2010-03-03
forum: Server Platforms
---

### Post by Volomike2 on 2010-03-03
I'm new to this whole Ubuntu Private Cloud thing as discussed here:

[http://www.ubuntu.com/cloud/private-steps](http://www.ubuntu.com/cloud/private-steps)

It's called UEC.

Here are my newbie questions. Realize I'm not really a hardware guy. I sort of know bits and pieces of hardware. My focus has mostly been on LAMP Development. I'm trying to work with a project manager and some hardware guys and all of us are trying to get a grasp on the UEC.

1. Can a VM span multiple nodes?

2. If a website scales beyond 100% CPU on a node, does it automatically spill over to another node and start using processing power there?

3. Do I have to rewrite the code of my web app (such as WordPress) so that it works in a private cloud?

4. Does KVM support virtual memory such that when I run out of RAM it uses paging?

5. How is UEC any different than me bringing up several servers with several VMs inside, and then moving VMs around as I need? Is it really a cloud where the VMs exist in a cloud, not necessarily a node?

6. If I power off a node while it's hot, how can I assure myself that the data will be okay?

7. Do I want to use SCSI attached RAID, or NAS, or NFS? We're simply trying to host thousands of blogs and LAMP sites in a way that we can handle spike loads.

8. Do I attach the disk volumes to the cluster controller and then run a command such that the nodes can mount those virtual volumes?

9. Do I need to run another command on the VMs to mount volumes that the nodes can see?

10. What is the role of the storage controller and how is it separate from the cluster controller?

11. How many systems, minimum, do we need to get this tested out?

12. For testing purposes, can I install UEC on an Intel P4 server and then a node on Intel P3 server -- even with some limitations?

13. Let's imagine I have 5 node servers, and one catches fire and is a total loss. Can I get those VMs back and get that data back? What would have to be the proper config to make that happen?

---

### Post by Volomike2 on 2010-03-04
Here's what I found out:


1. Can a VM span multiple nodes?

> Nope.

2. If a website scales beyond 100% CPU on a node, does it automatically  spill over to another node and start using processing power there?

> Nope.

3. Do I have to rewrite the code of my web app (such as WordPress) so  that it works in a private cloud?

> Yep. If you want to take advantage of the cloud's main goals. Otherwise, you could achieve the same thing with LVS (Linuxvirtualserver.org) + perhaps (depends on your needs) some VMs using Xen.

4. Does KVM support virtual memory such that when I run out of RAM it  uses paging?

> Still don't know. I do know that Xen gives me this, though, and is an option.

5. How is UEC any different than me bringing up several servers with  several VMs inside, and then moving VMs around as I need? Is it really a  cloud where the VMs exist in a cloud, not necessarily a node?

> VMs exist on a node, not spread across multiple nodes.

6. If I power off a node while it's hot, how can I assure myself that  the data will be okay?

> By having the VM point to a central database or shared file source hosted on the CLC and made available to the VM, or for the VM to connect to a shared file source inside itself such as an NFS mount.

7. Do I want to use SCSI attached RAID, or NAS, or NFS? We're simply  trying to host thousands of blogs and LAMP sites in a way that we can  handle spike loads.

> Then a cloud is not your best choice. Instead, go with LVS + perhaps (depends on what you want to do) a set of VMs using Xen. WordPress is not a REST-ful service without a code rewrite.

8. Do I attach the disk volumes to the cluster controller and then run a  command such that the nodes can mount those virtual volumes?

> Yep. Not certain if this is done on the CC (Cluster Controller) or on the CLC (Cloud Controller).

9. Do I need to run another command on the VMs to mount volumes that the  nodes can see?

> Yep.

10. What is the role of the storage controller and how is it separate  from the cluster controller?

> Long discussion.

11. How many systems, minimum, do we need to get this tested out?

> Two.

12. For testing purposes, can I install UEC on an Intel P4 server and  then a node on Intel P3 server -- even with some limitations?

> Only some P4s may work because they have VT support. Best to go with a processor that came after that.

13. Let's imagine I have 5 node servers, and one catches fire and is a  total loss. Can I get those VMs back and get that data back? What would  have to be the proper config to make that happen?

> VMs pointing data to a central database or to a shared file source either mounted and made available to the nodes and thus the VMs through the CLC, or through a shared file source mounted inside the VMs, such as an NFS connection.

In the end, however, this is what I determined:


- Unless you're rebuilding your web app to use cloud APIs so that  overload spreads among multiple VMs, you're really not on a suitable  platform.

- If you're expecting to have VM CPU or RAM overload to just spill  over in other VMs, or have a VM span multiple nodes -- this isn't  possible in UEC or any cloud for that matter.

- So, if you're  wanting to host like 1000 WordPress blogs and were hoping a cloud would  help you handle spike loads -- guess again because it won't. The RAM and  CPU of the cloud is limited by which VM serves your domain, and which  node that VM resides on. It does not span that VM across multiple nodes  like we thought previously.

- Clouds are hype. You can achieve the same thing with LVS ([linuxvirtualserver.org]("http://linuxvirtualserver.org/")),  Xen, and some REST-ful services. Cloud software just makes a similar process to this run a little smoother, but only sort of. Look at the command line stuff one has to do with UEC and you might think again. It's still not very polished yet.

- If you're wanting to host  like 1000 very active WordPress blogs and handle huge spike loads, then  LVS will get you there. If you're wanting to offer clients almost  dedicated-like hosting, then Xen will get you there. Xen and LVS can be  combined. WordPress is not a REST-ful kind of web app, so it doesn't fit  in a cloud model.

---

