---
title: "Cannot get vfio-pci to grab nvidia 980ti"
date: 2018-03-27
forum: Virtualisation
---

### Post by relink2013 on 2018-03-27
I am running a clean install of Kubuntu 17.10 with the following hardware. 
I7-7700k 
16gb ram
ga-z270xp-sli Mobo
GTX 980ti (pcie slot1)
GTX 1050 (pcie slot2)

I am desperately trying to switch back to Linux, but I need a Windows VM running for gaming and CAD work. I have been trying all week to get the nouveau drivers to let go of my 980ti as I would like to pass that card through to a KVM running Windows10. While keeping the 1050 for Linux to use. 

I have followed numerous tutorials that walk through how to do this, but no matter what I do I end up with the same result. VFIO will grab the cards HDMI audio chip, but not the GPU. 

I have tried physically swapping the cards pcie slots, and it made no difference. 

My last ditch effort was to remove to the 1050, and install an old AMD HD5450 for Linux to use, so I could just black list the nouveau drivers completely, but sadly this just resulted in kubuntu not booting at all. &#128557;

I can use the HD5450 if I absolutely have to, but I would much much rather use the 1050. 

Please any help is appreciated. I have done this through unraid numerous times and it so easy. But now I’d like to actually do it on my desktop.

---

### Post by KillerKelvUK on 2018-03-27
Hey, would be useful to see your config to review?  Example of mine for this...

```
[FONT=monospace][COLOR=#000000]cat /etc/modprobe.d/virt-config-blackserver.conf  [/COLOR]
# Locate this file in /etc/modprobe.d/ and update-initramfs -u

#10de:1b81: nVidia GTX 1070 (video)
#10de:10f0: nVidia GTX 1070 (audio)
#1102:0012: Creative Labs SB Recon3D
#1106:3483: Aukey USB controller (VIA Technologies, Inc. VL805 USB 3.0 Host Controller)
#10de:1c03: nvidia GTX 1060 (video)
#10de:10f1: nvidia GTX 1060 (audio)

options kvm_intel nested=1
options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio_iommu_type1 allow_unsafe_interrupts=1
options vfio-pci ids=1102:0012,10de:1b81,10de:10f0,1106:3483,10de:1c03,10de:10f1 disable_vga=1
softdep nouveau pre: vfio-pci
[/FONT]
```

---

### Post by relink2013 on 2018-03-27
this is the only line in my config

 ```
options vfio-pci ids=10de:17c8,10de:0fb0
```

---

### Post by KillerKelvUK on 2018-03-28
Right from memory "disable_vga=1" removes the device from the VGA arbitration process on the host which assists with passthrough stability.  The bit you need to try is "softdep nouveau pre: vfio-pci" which basically advises the kernel to load the vfio-pci module ahead of the nouveau module so that you cards get caught in the right order.

---

### Post by droid2bsd88 on 2018-03-28
Oh my lord you need very similar GPUS in order to the sli subsystem to function correctly 
You are currently running a mismatched configuration So I'd suggest grabbing you're self another set of matched NVIDIA GeForce 150 or newer viriants.

---

### Post by KillerKelvUK on 2018-03-30
> **droid2bsd88 said:**
> [I] Oh my lord you need very similar GPUS in order to the sli subsystem to function correctly 
You are currently running a mismatched configuration So I'd suggest grabbing you're self another set of matched NVIDIA GeForce 150 or newer viriants.[/I]

Who mentioned anything about "sli"?

---

### Post by relink2013 on 2018-03-30
I tired adding "softdep nouveau pre: vfio-pci" to the top of the list in "/etc/modules" and the card is still loading with nouveau.

---

### Post by KillerKelvUK on 2018-03-31
> **relink2013 said:**
> I tired adding "softdep nouveau pre: vfio-pci" to the top of the list in "/etc/modules" and the card is still loading with nouveau.

So this is your problem... /etc/modules as a file gets called late in the boot process as such core kernel modules like nouveau are already started and have grabbed devices which qualify for their control.  You need to take a different approach as per my shared config and put a new file in /etc/modprob.d/ which includes your vfio module options as well as the softdep line.  And be careful also as the softdep line I believe needs to be ordered towards the end of the file (or at least after the line that actually loads vfio).  Once you have a file in this location with the right config you need to update your initramfs by issuing the following command...

```
sudo update-initramfs -u
```

As a result of the above the vfio module and its module options are loaded earlier in the boot process and therefore acquire the devices you specify.

---

### Post by relink2013 on 2018-04-02
Ok, I think I found the issue. I misread the output regarding IOMMU groups, my GPU is infact in a group with 4 other devices. So this means I need to install the ACS patch. I have successfully done this in Arch Linux, and it works! But I DO NOT want to use Arch, so how can I get the ACS patch going in ubuntu 17.10?

I found this ppa [here]("https://launchpad.net/~queuecumber/+archive/ubuntu/acso") is it as simple as just installing from this ppa and rebooting? or is there more that needs to be done?

---

### Post by KillerKelvUK on 2018-04-02
Okay so qemu wouldn't complain about IOMMU separation until you actually started your guest so your latest post is now something different as IOMMU separation has little to so with the vfio module loading and grabbing the right devices.  Did you resolve the VFIO problem, can you share what your solution was for others to benefit from?

Regards ACS patching, I'd recommend you start a new thread appropriately titled so you solicit the best advice possible on that topic.  As a more direct answer to your question, typically when deploying the ACS patch you need also use a kernel boot-time parameter to activate it but my experience with this is limited as I've not had to do it for years and when I did I was building my own kernel.

---

### Post by relink2013 on 2018-04-02
I have still not solved the VFIO problem, no. I followed what was suggested in the previous replay, and it still doesn't work.

I created a file called vfio and in it is:

vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
softdep nouveau pre: vfio-pci
vfio-pci.ids=10de:17c8,10de:0fb0

I then updated the initramfs

Ok, so I made a mistake and forgot to add ".conf" at the end of my file. I corrected it, and Now when I try to update initramfs I get the following errors.
```
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 1: ignoring bad line starting with 'vfio'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 2: ignoring bad line starting with 'vfio_iommu_type1'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 3: ignoring bad line starting with 'vfio_pci'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 4: ignoring bad line starting with 'vfio_virqfd'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 6: ignoring bad line starting with 'vfio-pci.ids=10de:17c8,10de:0fb0'


```

---

### Post by relink2013 on 2018-04-03
I GOT IT! Thank you all so much for your help. I just simply removed the other lines from my vfio.conf file leaving only "softdep nouveau pre: vfio-pci", and everything seems to be working just fine, I can pass-through my GPU now!

Quick question though, my primary (Linux host) GPU is a GTX 1050 and I would like to install the proprietary drivers for it, do I need to change that "softdep nouveau pre: vfio-pci" line to something else since I wouldn't be using nouveau?

I still have other issues and questions related to the ACSO patch, and physical disks, but I'll open another thread for that.

---

### Post by KillerKelvUK on 2018-04-03
> **relink2013 said:**
> I have still not solved the VFIO problem, no. I followed what was suggested in the previous replay, and it still doesn't work.

I created a file called vfio and in it is:

vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
softdep nouveau pre: vfio-pci
vfio-pci.ids=10de:17c8,10de:0fb0

I then updated the initramfs

Ok, so I made a mistake and forgot to add ".conf" at the end of my file. I corrected it, and Now when I try to update initramfs I get the following errors.
```
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 1: ignoring bad line starting with 'vfio'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 2: ignoring bad line starting with 'vfio_iommu_type1'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 3: ignoring bad line starting with 'vfio_pci'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 4: ignoring bad line starting with 'vfio_virqfd'
libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/vfio.conf line 6: ignoring bad line starting with 'vfio-pci.ids=10de:17c8,10de:0fb0'


```

I know from your latest post you have managed to get this working but for the sake of completeness the reason you got these errors is because your syntax in the file was wrong.  The config I shared in my earlier post showed that you need to prefix the module lines with the word "options" as the below...

```
[FONT=monospace][COLOR=#000000]cat /etc/modprobe.d/virt-config-blackserver.conf  [/COLOR]
# Locate this file in /etc/modprobe.d/ and update-initramfs -u

options kvm_intel nested=1
options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio_iommu_type1 allow_unsafe_interrupts=1
options vfio-pci ids=xxxx disable_vga=1
softdep nouveau pre: vfio-pci

[/FONT]
```

Regards switching to the nvidia propriety driver:  You'll need to blacklist the nouveau driver (the nvidia install attempts to do this for you), you'd then need to alter the softdep line to change nouveau to nvidia.  However depending on how/where you are telling vfio which pci ids to sequester you may find the nvidia driver more troublesome than nouveau, as such you'd need to follow my recommendations more faithfully.

---

### Post by relink2013 on 2018-04-03
Will do, I’ll make the corrections when I get home today. I can’t believe I forgot to put “options” before the lines, I knew that too, it just slipped my mind.

---

### Post by relink2013 on 2018-04-08
Ok so, final report. It is all working perfectly. 

I ended up only needing the "softdep nouveau pre: vfio-pci" line, when any of the other lines were present, I would boot to a black screen. But without adding that one line, my 980ti would boot up using nouveau. So thank you very much for your help.

---

### Post by KillerKelvUK on 2018-04-09
Glad you have it sorted.

Please remember to mark this thread as 'solved' using the "thread tools" menu on your original posting.

Cheers

---

### Post by relink2013 on 2018-04-09
OH I should also add, for anyone else who might be having the same problem. You MUST swap your GPUS. The GPU that your trying to pass-through cannot be the GPU that your system boots from. SO I had to move my 980ti into pcie slot 2, and put the 1050 into slot one. 

I read that there is a way to pass through the boot GPU, but it doesn't seem worth it, when you can just swap the cards and call it a day. and I suppose if your using your Integrated graphics, then you can disregard this, just make sure your BIOS is set to boot from IGPU.

---

