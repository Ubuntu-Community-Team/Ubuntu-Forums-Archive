---
title: "installing via vmplayer"
date: 2018-04-23
forum: Virtualisation
---

### Post by matt18 on 2018-04-23
Ello all. I want to try 16.04 on my win 10 laptop. I have vmware player 6.0.7. Here are my laptops specs

Processor    AMD A10-5750M APU with Radeon(tm) HD Graphics, 2500 Mhz, 4 Core(s), 4 Logical Processor(s)
Installed Physical Memory (RAM)    12.0 GB
Total Physical Memory    11.2 GB
Available Physical Memory    6.66 GB
Total Virtual Memory    13.5 GB
Available Virtual Memory    8.76 GB
Page File Space    2.27 GB

will this be enough for wanting to run 16.04 in vmware player as a second os, if i run nothing else in the back ground of win 10?

thanks. i hope this works. last ubuntu version i tired, youtube, prime video, and netflix did not work. now i hope they do haha. mainly switching to ubuntu for the file manager because windows 10's sucks. i love the fact that gnome allows sftp in the location bar and you can save it in your locations sidebar. windows 10, i have to use a sftp client...... its a hasle. i just want my youtube, selectTV,prime video, hulu, and any other video to work including netflix, vudo, tubi and whatever else there is out there haha

---

### Post by TheFu on 2018-04-24
Any computer with 4G of RAM and a 1st generation Core2Duo CPU should be able to have a nice Linux experience.
You'll probably find more help here if you use virtualbox instead of VMware Player.  More people use virtualbox for a number of reasons.

Video inside a virtual machine will almost always be noticably slower until you are advanced enough to use GPU passthrough. I don't think the point-n-click hypervisors like vmware-player support that.

When it comes to DRM protected video sites, Linux is often a 2nd-class citizen as far as those commercial providers are concerned.  I used to fight with keeping them working on my general use Linux systems until it just became too much hassle and I bought a cheap roku.  Since then, I've been much happier. No real hassles. Roku is well supported by all of the DRM'd video providers.  A roku costs less than 30 minutes of my time at work, so the ROI happens fairly quickly.

---

### Post by wildmanne39 on 2018-04-24
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by matt18 on 2018-04-29
thank you much for the replies. 

Ok, for VB, its been about 10 years since i have used it. I HATED it when i first used it. I liked vmware better for the mere fact that i could run my linux full screen as in i couldnt tell i was using windwos at all. VB, at that time, lacked the ability to do that.

With that said. i am willing to give it another go. I have also found that out of the box, youtube and netflix work on chrome, im not sure about prime. 

I am aware of roku express, me parents have one. I have used a roku for about 8 years now(at my parents house haha) but for me i created this instead because as a full time mechanical and areospace engineering student, money can be scarce haha

[https://lt728843.wixsite.com/roku](https://lt728843.wixsite.com/roku)

anyway, i want to try the new linux in VB and see what it is like. Can i run it full screen in VB without doing all this crazy crap, or is it going to require me to do some major configurationing (thats a new word) of stuff?

thanks. Hope you all have a great weekend.

---

### Post by TheFu on 2018-04-29
I think you misunderstand.

The roku comment was there just to make your life easier.  That's all.

The VB comment was more about these forums than any lack in capability for VMware Workstation.  VMware Player is a different thing.  Folks here just have much more experience with VB.  Actually, I stopped using VB around 2014 and have been using KVM+libvirt, but that isn't an option for systems that have Windows as the host.  The only suggestion is to only have 1 hypervisor installed on a system at a time.

All of these will have similar issues with good playback.  Video playback is getting better, but not exactly what virtual machines are created for.  For the best video performance in side a virtual machine, setting up 2 GPUs, 1 for the hostOS and the other for the guest in exclusive-access mode is required.  Normally, this is done with Linux as the hostOS and Windows as a guest.  Gamers do this.  They normally use KVM or Xen as the hypervisor.   There are a few guides in these forums for the required hardware and manual config changes that people use.

Intel has been working on shared GPU VM passthru for a few years. It is getting close, but not quite ready.  And it only works with intel CPU/GPUs.  It has been a few months since I checked into it. Maybe it is ready now? [https://01.org/igvt-g/blogs/wangbo85/2018/sharing-guest-framebuffer-host](https://01.org/igvt-g/blogs/wangbo85/2018/sharing-guest-framebuffer-host) - link is for lurkers. Not for AMD users.

[https://community.spiceworks.com/topic/1985036-vmware-workstation-gpu-passthrough](https://community.spiceworks.com/topic/1985036-vmware-workstation-gpu-passthrough) has info on VMware's options. Looks like ESXi supports GPU passthru, but that is like getting a dumptruck when you just want a Fiat.

BTW, I'm a fellow ASE, though I haven't done any directly related work in that field since the mid-1990s.

---

### Post by matt18 on 2018-04-30
> **TheFu said:**
> I think you misunderstand.

The roku comment was there just to make your life easier.  That's all.

The VB comment was more about these forums than any lack in capability for VMware Workstation.  VMware Player is a different thing.  Folks here just have much more experience with VB.  Actually, I stopped using VB around 2014 and have been using KVM+libvirt, but that isn't an option for systems that have Windows as the host.  The only suggestion is to only have 1 hypervisor installed on a system at a time.

All of these will have similar issues with good playback.  Video playback is getting better, but not exactly what virtual machines are created for.  For the best video performance in side a virtual machine, setting up 2 GPUs, 1 for the hostOS and the other for the guest in exclusive-access mode is required.  Normally, this is done with Linux as the hostOS and Windows as a guest.  Gamers do this.  They normally use KVM or Xen as the hypervisor.   There are a few guides in these forums for the required hardware and manual config changes that people use.

Intel has been working on shared GPU VM passthru for a few years. It is getting close, but not quite ready.  And it only works with intel CPU/GPUs.  It has been a few months since I checked into it. Maybe it is ready now? [https://01.org/igvt-g/blogs/wangbo85/2018/sharing-guest-framebuffer-host](https://01.org/igvt-g/blogs/wangbo85/2018/sharing-guest-framebuffer-host) - link is for lurkers. Not for AMD users.

[https://community.spiceworks.com/topic/1985036-vmware-workstation-gpu-passthrough](https://community.spiceworks.com/topic/1985036-vmware-workstation-gpu-passthrough) has info on VMware's options. Looks like ESXi supports GPU passthru, but that is like getting a dumptruck when you just want a Fiat.

BTW, I'm a fellow ASE, though I haven't done any directly related work in that field since the mid-1990s.

LOL, yeah i missunderstood. I had been working on about 2 hours of sleep. I have been training in solidworks and i have never used the software so my brain is hammered.

What work did you do as an ASE? I have no idea where i am going to go with my degree. I just know that i like what i am doing. 

I might give VB a go again. at least i know i will get alot of support on here for it.

---

