---
title: "Optimizing Ubuntu server for virtualization under VMWare Server 2.0"
date: 2009-04-24
forum: Virtualisation
---

### Post by samosamo on 2009-04-24
I am seeking an official list of modifications to improve performance on Ubuntu server hosts running VMWare Server 2.0, as well as Ubuntu server guests that run on them.

I have an Ubuntu 8.04 Server host running VMware Server 2.0.  It hosts eight Ubuntu 8.04 Server guests.  My most major issue is the performance is unbearable.  My second issue is the time is constantly way into the future on the guest machines.  Something is definitely wrong.

You may think 8 guests is too much, but the guests have *very* light duty and I am absolutely sure that with the proper settings it will run perfectly fine on this Intel Core2Quad Q9400 with 8GB of DDR2 1066 RAM.

I have not yet made ANY modifications to the host or the virtual servers with the intention of enhancing performance.  I have come across a few articles listing tips and tricks to make, like kernel options at boot time, /etc/vmware/config file, and guest vmx files.  None of them are from trust worthy sources.  I am not sure whether or not to mess around.

Following the text book, vmware-tools is installed on each machine.  In addition to this a crontab script runs once every 2 hours on the host to snapshot each guest for emergency recovery.

---

### Post by samosamo on 2009-04-26
ttt, this is kind of important.  An clean install of 8.04 LTS Server on a Core2Quad machine has 100% utilization with 8 guests idling.  Something is way off.

---

### Post by HermanAB on 2009-04-26
My tuppence worth:
[LIST]
[*]Don't use VMware Server 2.x.  The 1.x series is way better.  Otherwise use Vmware Workstation.
[*]In the guests, turn off background snapshots.
[*]On the host, change to runlevel 3.
[/LIST]

---

### Post by Cheesemill on 2009-04-27
Have you tried using Ubuntu JeOS 8.04 as the guest OS, it's a version of Ubuntu Server that's specifically optimised for use in a VM.

Cheesemill

---

### Post by samosamo on 2009-04-27
I guess there is no official way of doing this ?  I don't want to play guessing games.  Is VMWare Server 2.0 not considered a production solution?  I don't really understand.  They are a reputable company and brand name.

Since making this post, I was forced to try some of those tips and tricks I find scattered around the internets.  Turns out they made things better but that is not the point.  I don't think I should have to work so hard for this.  The installer should take care of the extra settings, or at the very least there should be a how-to.

And yes, on the host I am using Ubuntu Server x64.  I failed to mention the x64 part in the first post.  On the guests I am using x64 servers built from "ubuntu-vm-builder" (which is JeOS's tool on hardy, vmbuilder didn't come until intrepid).  They are all 8.04, except one which is 8.10.

The host and each guest were apt-get update'd and then vmware-tools were manually built on each machine with no errors.  The network drivers have been replaced by e1000 (ubuntu-vm-builder defaults to Flexible) and vmxnet module is loaded.  Everything is up to date as it should be.

If I have done something wrong, will someone please let me know?

---

### Post by Cheesemill on 2009-04-27
I've found the WebUI slower on VMware 2.0 than running the old VMware 1.0 console, but my VM performance has been better with 2.0, although I know that some people have had problems with it.

I run 6 JeOS 8.04 VM's + tools all with 256MB on a Core 2 Duo with 2GB at work (all CLI installs with one or two functions each).

What hardware are you running your host on ???

If your hardware supports it you should run the free VMware ESXi hypervisor instead of VMware Server, it will give you far better performance.

Just my 2 cents,

Cheesemill :KS

---

### Post by samosamo on 2009-04-27
I considered ESXi but with all the things I hear about how finicky it is with hardware requirements, I thought I'd would get my feet wet with VMWare Server until I could acquire an approved machine at work for testing.  So I built my own quad core machine.  With all the trouble I'm having with VMware Server I still probably made the right decision.

I have made some tweaks and honestly performance has improved about 1000% but that still doesn't satisfy me.  That's not what this thread is about.  It hasn't improved to where I want it to be anyway.  I implemented every single tweak I could find but I'm still not happy with the performance under load, specifically iowait.

I'm not willing to roll back to 1.0.  It is not an option.  Besides, all the tweaks I found for 2.0 were written for 1.0 anyway.  So I'd probably be experiencing the same problems.

What is your server's load average with 6 JeOS's?

edit: By the way, I enjoy using the Web UI.  It's pretty solid.  I've used it for hours and hours so I say that with confidence.

---

