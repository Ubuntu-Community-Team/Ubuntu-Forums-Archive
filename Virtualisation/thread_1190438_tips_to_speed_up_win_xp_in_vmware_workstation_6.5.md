---
title: "tips to speed up win xp in vmware workstation 6.5"
date: 2009-06-17
forum: Virtualisation
---

### Post by pythonscript on 2009-06-17
I'm running ubuntu jaunty with a copy of win xp pro sp3 x86 running in vmware workstation 6.5. For some reason, as soon as I start running the virtual machine, my entire machine slows to a *dead crawl. *My processor activity seems relatively high (about 60% on both heads of my intel core2duo 2.4 ghz) but that still doesn't seem like it should be overtaxed yet. The win xp machine is barely useable, and I've given it 1.5 GB of ram out of my 4 gb system (which is x86, so I guess it's really only 3 GB, but still...) Any ideas? I'd like to know if anyone else has had this same problem, and if so, how can I speed up both?

I tried turning virtualization on in the bios, but, according to other sources I found and my own experience after trying it, it causes vmware workstation 6.5 to crash... so that's kind of out of the question. I've set the win xp machine to use only one cpu, then both cpu, and neither seems to make any difference. Any ideas? I'd LOVE to be able to run my win xp apps without booting into xp (installing xp on my extremely xp-unfriendly laptop is a whole other story of my life...) Thanks in advance!

EDIT:  I also disabled visual effects in both systems, and that didn't really seem to make much of a difference.

---

### Post by nfox on 2009-06-17
You're right about the 3GB of RAM and you are giving 1/2 to your VM. Likely to be the issue. You also don't want VMWare to try to use both cores as it really will only use one but having both can [insert explanation] and cause it to lag. You can configure it to stick to one CPU. That should dramatically boost speed. How's the guest anyways? What about the basics like did you fail and install limewire/antivirus 2009? Do you know it's not just the guest at fault? I use VBox and have no issues. I have 2GB of RAM and give my XP and 7 installs a meager 1/2 - 1 GB RAM and have no issues. But I also maintain the installs by defragging, not installing crapware, etc.

Long story short, you won't get a simple answer for this.

---

### Post by pythonscript on 2009-06-17
> **nfox said:**
> What about the basics like did you fail and install limewire/antivirus 2009?

Thanks for the tip, but no, I didn't do that. I have no idea if it's only the guest, or both, but I've never had speed problems running xp on bare systems or in other virtual environments with much less resources. I felt I had to allot a lot of ram, since the only apps I *need* to run natively on windows are tunebite and visual studio. Visual studio, not so much, but to run effectively, tunebite needs a good portion of ram, and I assumed that overkill was better than not enough ram. 

I've tried only one cpu, and that didn't improve the usage at all. Thanks for the help!

---

### Post by mindgrep on 2009-06-24
Install VMWare tools. This installs updated drivers for video, mouse and other devices, and just doing this *dramatically* speeded up my windoze xp vm (running in redhat5 on my dell laptop).

---

### Post by pythonscript on 2009-09-06
I had already installed vmware tools, and that didn't make much of a difference. Two things I did do, though, that really helped. 

[LIST=1]
[*]Installed a server kernel on my laptop instead of the generic one. This way, I could use all 4 GB of my ram and simply allot more ram to the vm.
[*]Completely remove vmware workstation and use the proprietary version of virtualbox. It runs better for what I need it to do.
[/LIST]
Thanks for the help!

---

### Post by Dedoimedo on 2009-09-07
I've written about this - tips to improve VM performance. Check the site if you're interested.

The two most important ones:

- Place the VMs on NON-system disk. This will speed things considerably. Second internal disk or even external one. This allows you to run VMs with good speed even on laptops with just 5400rpm disks.

- Install VMware Tools.


Cheers,
Dedoimedo

---

### Post by pythonscript on 2009-09-07
> **Dedoimedo said:**
> 

- Place the VMs on NON-system disk. This will speed things considerably. Second internal disk or even external one. This allows you to run VMs with good speed even on laptops with just 5400rpm disks.

- Install VMware Tools.


Cheers,
Dedoimedo

As I said, I've already installed Vmware tools, and that didn't make any difference. I installed those immediately after installing windows xp, and the performance issue was there right from the start. I tried placing the virtual disks on my external hard drives, one ext3 and another ntfs, but I didn't notice any speed difference. VirtualBox is working great for me now, though, so I don't see myself going back to vmware workstation any time soon.

---

