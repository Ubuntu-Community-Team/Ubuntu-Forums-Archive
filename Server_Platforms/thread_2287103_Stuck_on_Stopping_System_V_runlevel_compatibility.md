---
title: "Stuck on Stopping System V runlevel compatibility"
date: 2015-07-16
forum: Server Platforms
---

### Post by david407 on 2015-07-16
Hi All,
I am newish to linux and I have across an annoying issues on my freshly installed ubuntu server.

The server is running as a VM (Gen 1) in Hyper-v, details are:

Ubuntu server 14.04
open ssh
samba
Plex media server

NOTE: I have run an ```
sudo apt-get update&&sudo apt-get upgrade 
```

When i issue an ```
sudo reboot
``` the server hangs on 'Stopping System V runlevel compatibility'

I am not sure how to get any logs to assist troubleshooting this issue, a quick search on google shows others have reported the issue however there does not appear to be a definitive solution nor does any of the suggestions work or apply. 

I have attached a screenshot for reference, can anyone help?

---

### Post by MAFoElffen on 2015-07-18
The missing info that might be useful is info on the hypervisor and what the VM is configured as. Also GPU info on your host (local or remote, even if VNC connected) client.

For example, for some reason the default VM Spice client's video graphics for KMS is Cirrus. I usually set mine to VGA and use an xorg.conf file up with how I want my graphics to be (resolution and such). If I leave a SPICE client as Cirrus, I alwys seem to have problems with Linux Guests.

Other hypervisors (Hyper-V, VirtualBox, VMWare), use the Host GPU's graphics capabilities, which if you have nVidia or AMD Radeon, tell me and I'll give you tips for that.

What I'm saying is that at the boot status messages, between checking battery status and System V Runlevel Compatibility... behind the scenes (on a desktop edition), it is trying to start xorg, load the graphics driver and display the desktop. So if it looks like it is hanging at one those messages, I suspect that the graphics layer is not loading properly.

---

### Post by david407 on 2015-07-19
HI MAFoEllffen,
I will try to answer the missing info part the best I can as i though i had already provided that information. The server and Hypervisor details are as follows:

Host: CPU: G3258, Motherboard: ASRock H97M, GPU: Onboard
Hypervisior: Microsoft Windows Server 2012 R2 Hyper-v Core (free)
VM: Gen 1, 1 x CPU, 2048 MB RAM, 10GB HDD, 
OS: Ubuntu Server, Release: 14.04, Codename: trusty, 3.16.0-43-generic GNU/Linux

I would like to re-clarify that the issue only happens when attempting to **shutdown** or **reboot**, i have no issues when starting the VM.

I have also notice the following prompts on the VM console session:

[  240.060173]     Not tainted 3.16.0-43-generic #58~14.04.1-Ubuntu
[  240.060212] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message
[  240.060431]  INFO: task systemd-udevd:1384 blocked for more than 120 seconds.

Could it be that there is a hung process causing the system to halt on reboot/shutdown?
Any idea how i could get more info as to what the hung_task is?

This is killing me because everything else is working; i just cant gracefully reboot or shutdown.

Thanks in advance.

---

