---
title: "Starting Over with VMware"
date: 2007-10-29
forum: Virtualisation
---

### Post by twoseids on 2007-10-29
[FONT="Trebuchet MS"]Okay, I've got these big dreams of running Windows within Ubuntu using VMware. I've done it in with Dapper in the past. This time, I'd like to try [**this method**]("http://venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop") of having the Windows Start menu come up right inside GNOME. Even better if I can [**use my physical Windows partition as the virtual machine**]("http://www.howtoforge.com/vmware_converter_windows_linux")!

But here's my problem. When I was installing (again) VMware Server, it told me that while I should have 8GB free for the "partition", I actually only had 4.25GB free. So I told it to use 4GB. Then my install hung up because of my lack of disk space. This is odd, because my /home directory still has 57GB free and that's where I thought most of the VMware files went.

My / directory, oddly, is full to the brim. And it's a 10GB directory, which I thought would be sufficient for this average user.

So here are my questions:
[LIST=1]
[*]Is my VMware problem related to my / directory being full?
[*]What could fill up the / directory so quickly?
[*]Are there files I can clean up (I've already cleared out an older kernel)?
[*]How can I wipe VMware from my system so I can do a clean install? I tried re-installing and it failed.
[/LIST]
Thank you one and all for your help.
[/FONT]

---

### Post by twoseids on 2007-10-29
Bueller? Bueller?

---

### Post by bodhi.zazen on 2007-10-29
VMWare stores machines in : /var/lib/vmware/Virtual Machines

by default. 

You can either move the default or save the machines in say ~/VM

---

### Post by twoseids on 2007-10-29
> **bodhi.zazen said:**
> VMWare stores machines in : /var/lib/vmware/Virtual Machines

by default. 

You can either move the default or save the machines in say ~/VM
So would you recommend I just delete the /var/lib/vmware/Virtual Machines/Windows XP Home Edition directory? The contents are 4.3 GB. Ah hah.

---

### Post by Shazaam on 2007-10-29
What I have done is make a folder on my desktop (which is in the /home folder) for storing my vm's. So far it has worked ok.
Depending on the type of vm you can either have it set up with a static virtual hard drive size or a dynamic size. Static is the way to go if you are cramped for space.

Not a thread hijack but thank you bodhi.zazen for the /var/lib hint. I have been getting errors with Synaptic (gzip) so I poked around in /var/lib/apt/lists/partial to fix it.

---

