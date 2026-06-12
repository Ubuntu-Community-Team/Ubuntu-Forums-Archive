---
title: "Running a &quot;virtual server&quot; within Ubuntu Server Base/Host machine."
date: 2014-10-27
forum: Server Platforms
---

### Post by john312 on 2014-10-27
Hi, i'm fairly new to ubuntu server and never really tried ubuntu desktop. Im actually not sure what im looking for specifically but do know the general idea. If by any chance this has been discussed or there's documentation please point me to it.

what i know is that in windows you can have vmware and run several OS with their own resources and in this case i've done several linux server distros where one would fail it only takes down the virtual machine but not the host computer - i'm wondering is there a way to do this under Ubuntu Server (headless) which is stored in my garage with only PSU and Ethernet cable plugged in.

My situation is i am running a core2duo machine with Ubuntu Server 14.04 which has 5 old IDE HDD for music, movies, documents, photos which acts as my home media server/data center i want to run a webpage (wordpress) securely where if it gets hacked my media server doesnt crash. The way i think of doing this is having a "virtualbox" run a linux server distro for web hosting and make it act like a separate computer on the network were if it crashes it doesn't take everything with it.

Any help or direction is highly appreciated. Thank you in advanced.

---

### Post by TheFu on 2014-10-28
Come join us in the Virtualization forums [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

Let me just say this ... the virtualization provided under Windows is a toy compared to the many options Linux provides.
* KVM - server on server
* Xen - server on server
* VirtualBox - desktop on desktop - good intro to Virtualization
* VMware Player - desktop on desktop
* LXC aka "Linux Containers" (docker and flockport sit over LXC)
and a few others are possible.  A C2D can run multiple VMs at near native performance ... security is completely up to you, your server management, configuration, and most importantly, network architecture.  Doing something stupid inside a VM will not protect the rest of your network or your hostOS.

It is possible to run a virtual desktop on a virtual machine. I've been doing this for my primary desktop for a few years now. It has gotten much easier and much more secure thanks to x2go. Avoid VNC or RDP with are not as quick and don't have any real security built-in.

At my blog, I've written a multitude of articles about and on [virtualization]("blog.jdpfu.com/tag/virtualization"). Feel free to browse.  Of course, there are thousands of other articles on these topics on the internet, since virtualization is required at most enterprises as a standard practice.  Most enterprises stopped deploying server OS installs directly on hardware in 2006. This is a well-worn path.

---

### Post by john312 on 2014-10-30
Thank you for the reply, and yes windows is simply a toy but i do like the power of linux and expansion. So far is been self tough through reading mostly but it is a field i could get into. Most companies i've been with seem to have a system not quit to its potential being most if not all are windows base. I have dealt with many windows visualizations but not really catching my eye.

As to security yes if one is not cautions everything can go down but of course i'll try to set it up for a small family type server/site nothing big - so far i haven't taken it out of my home network as im fairly new to it. I will defensively read through your blog and join you in the visualization forum to learn more.

Thanks again and i will defensively look into the options for the vm you have suggested.

---

