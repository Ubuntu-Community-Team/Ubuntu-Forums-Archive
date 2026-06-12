---
title: "Ubuntu LTSP extemely slow"
date: 2015-03-10
forum: Virtualisation
---

### Post by sspence on 2015-03-10
Hello,

I hope this is the right forum, if not I apologize in advance.  I have Ubuntu 14.04 (both server and desktop) as a virtual machine on VMware ESXi and have added LTSP.  The server is set for 2 sockets with 4 cores each and has 16Gb of memory.  Using the vmware client to access a console session from a remote host Ubuntu runs awesome, just like it is a local session.  When I boot the thin client the performance goes down the drain.  It literally can take 3-5 minutes just to boot to the desktop (on the thinclient) and trying to launch firefox can take just as long if not longer.  I have been playing with this for at least a week and have reloaded everything multiple times.  I cannot seem to get this lag out of the sytem.  One more thing, I am using PFsense for routing and firewall, and watching traffic graphs within PFsense show the maximum momentary speed for the server/ thin client to be about 2Mbps but it is not a consistent speed, they will spike momentarily and then sit idle for a period of time.   

I have reconfigured the network with no luck, I have run a network speed test on the network and get excellent result (86Mbps).  

I am trying to setup my network to allow my 4 kids to each have a thin client, but if one is this sluggish I could only imagine what 4 would look like.

Any help or suggestions would be great,

Thanks in advance!

---

### Post by TheFu on 2015-03-11
Too many cores and too much RAM assigned to the VMs. Go with 1 core and 2G of RAM, max for a desktop.  BTW, I wouldn't use LTSP and don't really see why ESXi is used. It isn't needed.

So ... I would do it like this if I were trying to support 20 users on a single Ubuntu server with remote desktops.
* setup a pure server - no GPU. Text only interface.
* install x2go server (this is a free NX implementation)
* no virtual machines needed (and I use VMs for everything!)
* create X number of logins on the server (depends on the power of the server) - 20 users shouldn't be any issue
* setup disk quotas and some shared storage for everyone. Put the users into the same secondary group - keep their primary groups individual.
* create ssh keys for each user, install the public key on the server in the individual ~/.ssh/authorized_keys files (by userid)
* load up an x2go client on each client workstation with the ssh keys. These can be Windows, Linux or OSX machines

Be aware that no remote desktop solution handles video well regardless of the network bandwidth. None.  For audio and productivity applications, x2go is the best of these solutions.

I suppose if you need the machine to do other things, you could deploy this "shared server" into a VM - I'd use KVM. I've run ESXi, Xen, VirtualBox, VMware Player, Server, and Workstation - for server-based VMs, give me KVM every time. It really is **that good**.  It takes about 5 min to setup KVM on an existing Linux box.  Search "jdpfu kvm ale-nw" for a presentation with how-to steps.

And for some general virtual machine tuning ideas: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) those apply to every hypervisor.  The main idea is NOT to over allocate RAM or CPUs to a VM.  In Linux, too much of a good thing can be a bad thing.

How well does all this work?  My daily use desktop for the last 2-3 yrs has been an NX remote desktop running inside a KVM VM in a private cloud. I've accessed it from 5 continents with only a minor difference in performance.  NX uses ssh tunnels.  The VM I'm on currently has 2 other users working too. We have shared storage areas and private areas.   That's handy for shared documents ... er ... or audio media. 

We forget we are working through a remote desktop. It really is THAT good.

---

