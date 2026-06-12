---
title: "Virtual Ubuntu Servers randomly crashing."
date: 2013-08-13
forum: Virtualisation
---

### Post by Donald_Langhorne on 2013-08-13
First, I'll describe the system I am using.  I am running 10 Dell PowerEdge R610 servers.  Installed in each is a software product called Proxmox.  It is a virtualization server, similar in concept to VMWare.  Each physical server runs the servers we use for our business.  This includes webservers, database servers etc.  All of our webservers are running Ubuntu 12.04 LTS.  Our live webservers are 64 Bit and our test/internal servers are 32-bit.  The Amount of Ram is between 8 and 12GB for our 64-Bit servers and usually 2-4 for our 32-Bit.

This system has been in place for 3 years now.  In that time I upgraded all the servers from 10.04 to 12.04 (This occured last summer with minimal issues).  Starting a few weeks ago, our servers started crashing.  Not all of them, and it is only our Ubuntu WebServers.  So far out of the 7 live and 3 internal web servers, 3 of the live and 1 of the test servers have crashed, all in the same fashion.  Our Proxmox servers have had minor OS updates applied in the last few months.  Proxmox BTW runs Debian.  I am using V2.3 of Proxmox still.  There is a 3.0 version available.  The main difference between the 2 is that 2.3 runs on top of Debian 6 and 3 runs on top of Debian 7.

The error code I am receiving is: error_code+0x67/0x6c.  What little I have found indicates it is a hardware problem, however since these are all virtual machines and the 4 machines in question are spread out over our physical machines I don't believe that to be the case here.  I have attached a screenshot for what was left on the screen after this event.  Any help would be greatly appreciated.  I am happy to provide more details, but figured I would start with this and wait for requests rather than do a complete dump all at once.

[IMG]http://www.langhorne.ws/wp-content/uploads/2013/08/Ubuntu_1204_error.png[/IMG]

---

### Post by TheFu on 2013-08-13
Looks like RAM going bad to me.  Check the hostOS logs for hints. Could be almost anything failing if that screen is inside a VM - failing HDD, failing disk controller, failing NAS, or failing RAM.  Is the error happening on multiple different physical machines or across the board on all of them?

x64 only or x32 too?  Start tracking all the differences between the working machines and the failures.

I'm not a fan of Proxmox, though I get that it seems easier to deploy and you can choose if you want paravirtual or HVM guests.  Are these all paravirtual? Is that a constant?

Anyway - start capturing data to figure out similarities and diffs between the working and failing servers.

---

### Post by Cheesemill on 2013-08-13
Is there anything in the VM logs on your Proxmox hosts?

I'm not near any of my networks at the minute but I think they live at /var/log/libvirt *somewhere*.

I'm interested in this as I run a few Proxmox hosts myself but I haven't had any issues.

---

### Post by Donald_Langhorne on 2013-08-13
Ok, first, I believe they are all paravirtualized.  I checked and the network drivers at least identify themselves as VirtIO (Paravirtualized) when I check in Proxmox.  If by HVM you are referring to the option in Proxmox for OpenVZ/CT container VMs then no, I have none of those.  One of the reasons I went with Proxmox was at the time I still had a number of Windows servers, some were running Windows 2000, but I also had 15-20 Linux servers, so I needed a system that would support both.  Proxmox fit the bill and overall has been running without a hitch for almost 3 years now.  It was my windows servers that kept me from considering Ubuntu's virtualization options.  

The 2nd question asked here was regarding to the logs.  I didn't really see anything in my /var/log folder that jumped out at me.  There is no libvirt* folder or files in /var/log/.  There are some log files that are obviously part of Proxmox but their logs seem to be regarding how the clusters stay in sync with each other.

Also, I might add that the virtual machines locked up, but I don't think Proxmox was even aware.  When I went into proxmox to restart them, they show as running and even show constant CPU utiization (the next time one crashes I will do screen grabs of all the proxmox activity charts for that VM).  So even if I found the logs, I wonder if anything would even show, since as I said Proxmox might not even be aware they crashed.  Other VMS (I have on average 5-6 per physical machine) run unaffected.

So, I'm rather dubious that it is a hardware issue because these 4 VMS are on 4 separate physical machines.  I don't know what the probability would be that 4 servers out of 10 would develop hardware problems nearly all at once after running for 2 years without a glitch, but it has to be infinitesimal.  I will also add that these servers have a number of redundancies built into them: RAID Array Drives that are hot swappable, dual power supplies and an IDRAC mini-computer to monitor various things like temperature etc and will email if there are any problems.  Again, I won't totally discount it, but I have my doubts.  The primary changes that have occurred with these systems in the last month or so, aside from code-changes to our website code would be system updates, both to Ubuntu 12.04 and to the Debian OS that runs Proxmox.

What I am going to try and do is move one of my problem live servers to another physical machine.  Proxmox can migrate the VM's and it makes that task a simple one. I Will see if the problem goes away.  These problem VM's seem to stay up anywhere from 24-72 hours at a time, so it won't take too long to see if this has an effect.  All my proxmox machines are running the exact same software and versions and all the VMs involved are on slave nodes, that is while I have machines on my primary proxmox cluster node, none of the VMs in question are on the primary, so I'll move from 2 machines that are as much alike as can be expected.  I do almost no direct work on these proxmox machines, save for periodic system updates, which I tend to do to all of them at once.

If nothing else, I'll follow up here next week after I move one of the VM's and let it run for a 5-6 days

---

### Post by TheFu on 2013-08-13
Seems like a HW issue is extremely unlikely, I agree completely.
Is it possible to **not** update all the machines at the same time?  Did the problem begin across all the machines after the same client update or was it after the hostOS update?  I can understand not doing those separately.  I don't.

3 yrs ago, the Ubuntu virtualization wasn't all that great, so Proxmox was the least of the evil choices. Things have changed. KVM under Ubuntu is rock solid.

VirtIO usually means HVM - Windows requires HVM virtualization. BTW, this is what KVM provides by default too.

Paravitual run different kernels that are hostOS aware.  There are also "containers" ... like LXC and openvz. These are more like BSD jails, since they share the same kernel.

Well, if there isn't anything in the hostOS or clientOS logs, I think we're screwed ... you can only hope that someone else will see the issues and report them, get a patch, and magically, they are fixed for you too.  Do you have a central rsyslog server that gets the logs from each client? That can be helpful when clients lockup and the logs (with the last errors) are wiped at reboot.

You didn't mention - 32-bit or 64-bit OS lockups? Both or just 1 type? It would be useful if these happened only on x32 or only on x64 VMs. That would reduce the issues some.  Then you might try running the processes on the failing machine arch on the non-failing arch.  Those errors look like ATA or BIOS setting problems, but the fact that things have been working so long .... where their any defaul BIOS changes in the most recent proxmox for debian release?

I wouldn't know anymore than you do either at this point. Just asking questions ...

---

### Post by Donald_Langhorne on 2013-08-13
I did some more looking around and in the syslogs on the proxmox machines, I found these entries:

Aug 13 07:31:45 node6 pvestatd[928151]: WARNING: unable to connect to VM 130 socket - timeout after 31 retries
Aug 13 07:31:52 node6 kernel: usb 2-3: reset high speed USB device number 5 using ehci_hcd

I see this getting logged periodically throught the day.  They are almost always paired up with the problem VM.  I googled for the 2nd line and it seemed to indicate that it was a problem USB drive.  I don't have any USB devices hooked up to these machines, and even if I did, I have no idea why these 2 errors would "pair" up together.  I think I will post this issue to Proxmox support as well, since these errors would seem to indicate something going on with Proxmox possibly.  These machines live at a hosting facility locked in cages so no one would have plugged anything into them.

---

### Post by TheFu on 2013-08-14
> **Donald_Langhorne said:**
> I did some more looking around and in the syslogs on the proxmox machines, I found these entries:

Aug 13 07:31:45 node6 pvestatd[928151]: WARNING: unable to connect to VM 130 socket - timeout after 31 retries
Aug 13 07:31:52 node6 kernel: usb 2-3: reset high speed USB device number 5 using ehci_hcd

I see this getting logged periodically throught the day.  They are almost always paired up with the problem VM.  I googled for the 2nd line and it seemed to indicate that it was a problem USB drive.  I don't have any USB devices hooked up to these machines, and even if I did, I have no idea why these 2 errors would "pair" up together.  I think I will post this issue to Proxmox support as well, since these errors would seem to indicate something going on with Proxmox possibly.  These machines live at a hosting facility locked in cages so no one would have plugged anything into them.

Forget the USB message. Not important.
I found lots and lots about the **pvetatd** problem. [http://pve.proxmox.com/pipermail/pve-devel/2012-October/004203.html](http://pve.proxmox.com/pipermail/pve-devel/2012-October/004203.html) is just 1.

---

### Post by Donald_Langhorne on 2013-08-14
thanks for the link to that.  I don't restart my proxmox boxes very often and they have all been up for 150+ days at this point.  I will restart them tonight.  If that fixes it I may start to schedule reboots for them every 60 days as a way to mitigate this.

---

### Post by TheFu on 2013-08-14
> **Donald_Langhorne said:**
> thanks for the link to that.  I don't restart my proxmox boxes very often and they have all been up for 150+ days at this point.  I will restart them tonight.  If that fixes it I may start to schedule reboots for them every 60 days as a way to mitigate this.

If there is a new kernel installed, you **must** reboot.  Nobody will force that - you must do it.  On my systems, a file is created ... 
**/var/run/reboot-required** - if that file exists, then a reboot is necessary.  Clearly, if the hostOS has a new kernel, you'll want to reboot it.

---

### Post by Donald_Langhorne on 2013-08-19
Re: reboot, I think you misunderstood.  I was referring to rebooting the proxmox nodes.  They were not where the problem was exhibiting, it was in the VM machines.  In saying that I had not updated in that long, I did update the last time I updated the OS, but at this point with it being debian 6.0 and Proxmox 2.3 (version 3 is the latest) there just are not that many updates anymore.

Having rebooted the proxmox machines with the trouble VMS I am no longer experiencing these issues, so I believe a restart was the fix, not a restart of the VM specifically but the physical host the VMS were on.  As someone else posted to this forum who pointed to a possible memory leak in Proxmox, I think that is likely the problem, and a reboot would obviously address that.

So hopefully someone else running a VM will see this thread in the future and consider the problem being "upstream" from the machine that is throwing the error.

---

### Post by TheFu on 2013-08-20
If this is solved, could you please mark it as [SOLVED] in the thread tools?

---

