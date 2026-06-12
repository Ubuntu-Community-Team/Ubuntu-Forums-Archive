---
title: "Noob help with 8.04 Hyper v guest"
date: 2011-05-23
forum: Virtualisation
---

### Post by Noob_Lee on 2011-05-23
I've been a Ubuntu GUI user for some time, but have not really gotten into the cmd line OS like 8.04 server. I generally user Hyper-V with Microsoft boxes and VirtualBox for ubuntu guests. Now I am being forced to mix it up...

So I am running Server 2008 64bit R1 with Hyper V 6.1.7... I have been able to create the virtual disk and load Ubuntu 8.04 onto that disk. The place where I am dead in the water is the network interface. The guest is using the Local Area Connection 2 Virtual Network that the Win boxes are using.  ifconfig shows me a 127.0.0.1 loopback.  

when i check /etc/networkinterfaces, i show no ewth0, 1, 2 nothing. I also see no seth0, 1, 2, etc. It seems like it does not even recognize or acknowledge an interface exists. At this point, I am lost. In VirtualBox, I would install the Guest addins and be done with it, but I see nothing like this for this 8.04 guest.

Is there an ISO I need to dl for it? What do I use to extract iso's on 8.04? Like I said... total noob.

Any help w/b appreciated. :-({|=

---

### Post by Petrolea on 2011-05-23
Virtual Box has an option where you can choose which 'device' should be used for accessing internet in virtualized OS. There are quite a few options, I usually had to play around with them to make it work.

When that was set I had to manually insert the IP, gateway etc. in the configuration file.

Good guide: [http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/](http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/)

---

### Post by Noob_Lee on 2011-05-23
Thanks Petrolea, but I am using Hyper V, not VirtualBox. VB was only a reference point, but thanks anyway!

---

### Post by Noob_Lee on 2011-05-23
I've uploaded a screenshot for ease of interpretation. I've installed LIS on the Ubuntu server and still am not seeing eth or seth...

---

### Post by MustangNut on 2011-05-23
I would suggest using lspci -v to enumerate the known hardware.
On my vmware instance of Ubuntu 11.04 it shows the NIC as:

```
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
	Subsystem: Advanced Micro Devices [AMD] PCnet - Fast 79C971
	Physical Slot: 33
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at 2000 [size=128]
	[virtual] Expansion ROM at dc400000 [disabled] [size=64K]
	Kernel driver in use: vmxnet
	Kernel modules: vmxnet, pcnet32

```

from there you can try and figure out which module is required.

---

### Post by Petrolea on 2011-05-24
> **Noob_Lee said:**
> Thanks Petrolea, but I am using Hyper V, not VirtualBox. VB was only a reference point, but thanks anyway!

Oh, I forgot, I don't think it's a big difference there. 

And just because you can't see eth in conf file, doesn't mean it isn't there. 

Just to try answering your question, I ran Ubuntu in VirtualBox (I know it's not the same but that isn't the point). I had no connection too. Here's how I solved it:

- Use command 'ifconfig -a' to see all available connections.
- If ethn (n stands for some number) is disabled, enable it. ('ifconfig eth0 up' for example  - must be run as root)
- Then set IP and other stuff in conf file.

If it won't work the first time, try restarting ethn.

More info: [http://linux.die.net/man/8/ifconfig](http://linux.die.net/man/8/ifconfig)

Also check out the link in my previous post.

Hope this helps :)

---

### Post by Noob_Lee on 2011-05-24
In the instance of time, i had to "Pend" the Hyper-V and roll up a VBox install on a different server. I'll get back to the Hyper v install later this week as now I have to figure it out. It's now up and running and I can ping it from other hosts on the network. Now I just have to figure out why I cannot connect to it via putty.

It may just be a chipset issue since this server is new and quite heavy-duty. I'm willing to be 10 or 11 server would run just fine. 

I appreciate your help and will update this thread with hopefully good news and not more questions.  ;-)

---

### Post by Petrolea on 2011-05-25
> **Noob_Lee said:**
> In the instance of time, i had to "Pend" the Hyper-V and roll up a VBox install on a different server. I'll get back to the Hyper v install later this week as now I have to figure it out. It's now up and running and I can ping it from other hosts on the network. Now I just have to figure out why I cannot connect to it via putty.

It may just be a chipset issue since this server is new and quite heavy-duty. I'm willing to be 10 or 11 server would run just fine. 

I appreciate your help and will update this thread with hopefully good news and not more questions.  ;-)

I'm glad it works :) You can mark it as [SOLVED] now.

For SSH, make sure you run a SSH server there too, I don't think it's enough just for the main OS to run it. Google for more info, it is a common problem.

---

