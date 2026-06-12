---
title: "XenServer Vs VMware"
date: 2009-05-07
forum: The Cafe
---

### Post by wcpon on 2009-05-07
Hi all, wish to get more comments from all of you guys, the virtualization software that available in the market now.
XenServer Vs VMware....
Let's make a discussion here to see which is more reliable. :P

---

### Post by thisllub on 2009-05-07
There are plenty of detailed discussions on this.
Basically Xen needs a special kernel i.e. no Windows VMs. but it is good for Linux VMs. I find it almost impossible to get a satisfactory X server working with it so I call it server only.

VMWare does it all but can be slow and memory hungry. I have no hesitation recommending it in a production environment. Just give it 2 GB of ram + the allocated ram per VM and you should be fine. It has great management tools too.

I think VirtualBox is the best for one off VMs e.g. a Windows VM on a Linux desktop machine. Networking is a downside though. You have to set up bridging to get in to it from outside and there are known problems with this on wireless networks.

---

### Post by rickyjones on 2009-05-07
For personal use on my laptop I like VirtualBox. For production use in an enterprise server environment... VMWare ESX without a doubt.

Thanks,
Richard

---

### Post by wcpon on 2009-05-11
> **thisllub said:**
> There are plenty of detailed discussions on this.
Basically Xen needs a special kernel i.e. no Windows VMs. but it is good for Linux VMs. I find it almost impossible to get a satisfactory X server working with it so I call it server only.

VMWare does it all but can be slow and memory hungry. I have no hesitation recommending it in a production environment. Just give it 2 GB of ram + the allocated ram per VM and you should be fine. It has great management tools too.

I think VirtualBox is the best for one off VMs e.g. a Windows VM on a Linux desktop machine. Networking is a downside though. You have to set up bridging to get in to it from outside and there are known problems with this on wireless networks.

With the XenServer 5.0 latest version...
Is it able to challenge with VMware?
Because I thinking of using XenServer for my company environment...
Hope to get more information from you all...

---

### Post by thisllub on 2009-05-11
> **wcpon said:**
> With the XenServer 5.0 latest version...
Is it able to challenge with VMware?
Because I thinking of using XenServer for my company environment...
Hope to get more information from you all...

Download them all and try them.
It appears that Windows VMs might work with Xen now.
That would be an improvement.

---

