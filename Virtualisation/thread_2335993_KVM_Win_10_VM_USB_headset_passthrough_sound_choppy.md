---
title: "KVM Win 10 VM USB headset passthrough: sound choppy, glitches"
date: 2016-09-03
forum: Virtualisation
---

### Post by firepol2 on 2016-09-03
Hi there,

I'm a newbie with libvirt, kvm etc., I followed several guide to setup a Windows 10 Pro (64 bit) gaming virtual machine with with GPU pass through and it works quite well except that the sound is interrupted from time to time, it skips or glitches. Not sure how to say properly in English (not my mother tongue): in a game (The Division) **some audio is skipped from time to time** which gets on my nerves and I'd like to fix this issue. The same happens e.g. if I watch a YouTube video with Chrome, it starts ok and after a while some music is skipped, which makes watching videos quite annoying.

Please help me to fix it, I will be eternally grateful.

**My system:**
[LIST]
[*]Motherboard: [Asus Z170 Pro Gaming]("https://www.asus.com/Motherboards/Z170-PRO-GAMING/")
[*]CPU: [Intel I7 6700]("http://ark.intel.com/products/88196/Intel-Core-i7-6700-Processor-8M-Cache-up-to-4_00-GHz")
[*]Ram: 32 GB
[*]HD: Samsung SM951 NVMe, bulk (512GB, M.2 2280)
[*]USB Headset: [Plantronics Rig 500 HD]("http://www.plantronics.com/us/product/rig-500hd")
[*]OS: Ubuntu 16.04
[*]Kernel: 4.4.0-34-generic #53-Ubuntu
[/LIST]

I followed [this guide]("http://www.se7ensins.com/forums/threads/how-to-setup-a-gaming-virtual-machine-with-gpu-passthrough-qemu-kvm-libvirt-and-vfio.1371980/") (**guide 1**) to setup my first VM definition (xml) and make the GPU passthrough work.
Then I inserted in the XML also the part to attach my USB headset and tried to google around for solutions to fix the choppy sound, sound glitches (those the keywords that lead me to some people having similar problems) and found [this question]("http://askubuntu.com/questions/719819/libvirt-configure-guest-to-share-host-audio") (**askubuntu 1**). I tried to copy the pulse folder and use the settings as the guy suggested but didn't see any improvement in my case.

I've read in some places that it's recommended to set in the guest (Windows 10) the sound sample rate to be the same as the one of the host.

In Windows 10, the default sound quality is: 16bit, 48khz
So I tried to set it in Windows to 44khz, but the sound was totally bad. So I tried also to set it to 16bit (48khz). No change.

I tried to set the sample rate to 48 khz in ubuntu, if I run this command I can see my sound devices and their details:
```
pacmd list-sinks
```
[pacmd list-sinks result (pastebin]("http://pastebin.com/0KG9A9re"))

As you can see I have several sound devices:
[LIST]
[*]mother board integrated sound card
[*]another external sound card
[*]HDMI sound
[/LIST]

The I found [this guide]("https://ubuntuforums.org/showthread.php?t=2266916") in this forum (**guide 2**). Guide is huge and I'm not really sure what I could use to solve my audio problem, but it helped me to check these interesting files:
[LIST]
[*]/etc/libvirt/**qemu.conf**
[*]/etc/apparmor.d/abstractions/**libvirt-qemu**
[/LIST]

Inspired from guide 2 I tried to enable hugepages, hoping it would improve something, but it didn't.
I added my user to these groups: pulse, pulse-access, libvirtd.
I run the vm like this (I gamingvm is the name of my vm, but also the xml file is called the same, to make it easier):
```
virsh create gamingvm
```

**Here some more details about my VM and relevant config files** (I pasted on **pastebin** so this thread won't be 1km to scroll...)

[LIST]
[*][My VM definition]("http://pastebin.com/pUSexYh4") guest vm Windows 10 64 bit, see I commented the last qemu command line parameters since they seem to have no effect
[*][My qemu.conf]("http://pastebin.com/e3dTptTs") relevant I guess these 2 settings: **cgroup_device_acl** and I'm not sure about **nographics_allow_host_audio = 1**
[*][My apparmor libvirt-qemu]("http://pastebin.com/KkSexdMM") this file looks quite complex to me and I have no clue how to configure it, so maybe here I forgot something
[/LIST]

Again I define myself a **newbie** in virtualization (I still don't get many things) and the sound is quite important to me, because of gaming of course, but also because I don't like stuff to be almost ok but one thing not ok, like the sound in this case.

Thank you for helping to figure it out. If you need more information let me know and I'll paste everything in pastebin and update this post (if I can update this post of course) or reply in a comment. Cheers.

---

### Post by firepol2 on 2016-09-08
Quick update. I tested a different usb external soundcard, an aureon one. And that one works perfectly. So I believe my Plantronics USB headset is bad for passthrough somehow (in my Linux host it works perfectly, just passing it through causes bad results)... I tried to plug it in a USB 2 port, same problem.

Or maybe the problem is that it's an headset with microphone? I'll do more tests but at least I know that if I use external sound it works. Now I have to figure out how to make this headset work, since I wanna use it for gaming...

---

