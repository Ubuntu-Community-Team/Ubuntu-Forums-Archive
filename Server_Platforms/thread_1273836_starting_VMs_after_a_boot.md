---
title: "starting VMs after a boot"
date: 2009-09-23
forum: Server Platforms
---

### Post by ikman on 2009-09-23
I am using Ubuntu 9.04 x64 and KVM to configure some VMs for the first time during initial installation they would work intermittently (I'm sure there was a pattern :-).  When I installed them for the hopefully production run, with correct usernames, RAM, etc., They would not connect to the network (intra- nor internet) with ssh or ping.  

I ran "/etc/init.d/networking restart"  and checked the /etc/network/interfaces file and the numbers are the same as when it was working. 

virsh commands worked and the virt-manager brought up the GUI from where I could shell into the VMs...but no Network connections. So I rebooted my server. The server connects to the network and has full functionality again. I can bring up the virt-manager GUI but the three VMs show a status of "shutoff" and when I attempt to open one of them I get the new window says "guest not running. When I try to "connect" or "start" one of them I get errors and fails. 

virsh # connect vm0
error: Failed to connect to the hypervisor
error: could not connect to vm0

virsh # start vm0
error: no valid connection


There must be some small thing I have overlooked this time. But I can't find it. Any suggestions.

Thanks,

---

