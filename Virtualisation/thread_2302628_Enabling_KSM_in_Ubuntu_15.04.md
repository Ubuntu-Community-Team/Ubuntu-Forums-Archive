---
title: "Enabling KSM in Ubuntu 15.04"
date: 2015-11-11
forum: Virtualisation
---

### Post by imrazor on 2015-11-11
Right now I'm using Virtualbox for testing and educational purposes, and am running up against a resource issue, namely RAM. I'm hoping that Kernel Samepage Merge/Kernel Shared Memory would resolve my memory shortage, but I have some questions about configuring and using it.

1) Most of the documentation states that KSM will work any app, virtual machine or no. So even if VirtualBox does not explicitly support KSM, shouldn't KSM still work with Virtualbox?
2) It seems that I'll need to compile a custom kernel to use KSM. Is this true? I haven't compiled a kernel in a very long time.
3) If a custom kernel is a necessity, are there any PPAs or repos that include KSM and could be used to keep my kernel up to date?

I prefer VirtualBox to other solutions because I find it easy to configure and manage virtual networks with it, and Windows guests seem more responsive. But I'm willing to consider other solutions. Well, free ones, any way...

---

### Post by TheFu on 2015-11-12
On memory constrained systems (3G or less), look to LXC-type solutions. This doesn't work for Windows clients.

Do not over-commit RAM. Also, leave 512MB for the hostOS if Linux and 1G for Windows hosts.

BTW, support for 15.04 ends in Jan, so I wouldn't spend much time trying to make this work on that OS.
If you post some system details and planned VMs, we can provide some optimization ideas.

---

### Post by imrazor on 2015-11-12
Thanks for the reply. The idea is to have 3-4 Windows Server 2012 R2 servers running (some Core), along with 1 or 2 Win8.1 Enterprise 32-bit guests. Each server VM has ~1.5GB committed to it, and each client 1GB. The host OS has a dual-core i5-2520M, 8GB of RAM, 2x128GB SSDs and 500GB spinning hard drive. Workload will be very light - this a lab environment where I'm just learning about various aspects of Windows/AD networking. However I do want the VMs to boot pretty quickly, as I'll be making a lot of configuration changes to the VMs and rebooting frequently.

Wow, I thought non-LTS releases had two years of support before getting the axe....

UPDATE; Just upped it to 16GB of RAM, so I may not have to worry about KSM after all...

---

### Post by TheFu on 2015-11-13
Support periods:  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Stay LTS.

RAM is cheap.
Now the issue will be trying to run so many heavy OSes on a 2 core CPU. This is why Xeons were made.

---

### Post by imrazor on 2015-11-13
The i5-2520m does better than I thought it would, but trying to start 4 VMs at once causes the system to stutter pretty heavily. But they all do boot up after a short while and function normally. I'm barely putting any load on these VMs, and I doubt I will be in the future, except for updates and reconfiguration. I'd upgrade the CPU, but I already blew my "budget" on RAM.

Unfortunately, Xeons have not historically been available for notebooks. That has recently changed, but such a laptop is out of my reach.

What are the odds that "apt-get install dist-upgrade" would work without issues?

---

### Post by TheFu on 2015-11-13
A $400 desktop will blow away a $1500 laptop.

---

### Post by imrazor on 2015-11-13
Unfortunately, this has to be a mobile solution. I work 12 hours shifts Saturday and Sunday, and half my day is spent twiddling my thumbs. A mobile VM lab is the best way for me to study when I'm not working.

---

### Post by TheFu on 2015-11-13
> **imrazor said:**
> Unfortunately, this has to be a mobile solution. I work 12 hours shifts Saturday and Sunday, and half my day is spent twiddling my thumbs. A mobile VM lab is the best way for me to study when I'm not working.

Remote ... 

If you have internet, access is available from anywhere in the world over secure connections that works nearly as good as being on the same GigE LAN.  I do this whenever on travel.  Down the hall or halfway around the world, doesn't matter, provided there is ISDN or better internet.  Been traveling with a netbook or chromebook for years - they are remote-display-devices. The real processing power is back home on a $350 desktop running 12+ Linux VMs, easily.  A C2D can do that pretty easy. I know because I've done it, though I will admit that a Core i5 does make these servers *slightly* snappier.  Doubt any of the remote users can tell the difference.  We routinely have 3 remote desktop users on a single VM, but we could upscale it to 50 I'm certain with a little more bandwidth. It isn't like you need 1 VM per user login. That's just crazy talk.

Oh ... that's right - you're trying to do stuff with Windows. That blows most of this away.  For remote access under Windows, you need a full VPN - like openVPN.  The security for RDP connections is pretty weak. VNC is worse, so definitely use openvpn with that, or at least an ssh-tunnel.  If you do ssh, just go with x2go for a remote desktop. More efficient than VNC/RDP AND more secure since ssh is built-in. Be certain to use ssh-keys for authentication.

---

### Post by imrazor on 2015-11-13
> **TheFu said:**
> Remote ... 

If you have internet, access is available from anywhere in the world over secure connections that works nearly as good as being on the same GigE LAN.  I do this whenever on travel.  Down the hall or halfway around the world, doesn't matter, provided there is ISDN or better internet.  Been traveling with a netbook or chromebook for years - they are remote-display-devices. 
I considered that option, but the problem is the only internet access I have at work is a tethered, metered personal cell phone. Running all those remote desktops would blow through my data cap in no time. Can't use my work desktop either due to IT Security policies at my workplace.

---

### Post by TheFu on 2015-11-13
Yep.  Seems like you are stuck. 

Hope the big drive is eSATA connected, not USB. Many USB storage connections, including USB3, get into lockups when more than 3-4 task get into the queue. Hope yours doesn't. eSATA performs exactly like an internal SATA connection.

Seem odd to me to be at work and do non-work things on their time. I would have been fired at every job I've had for that.   Are they hiring?

My old vbox tuning article: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

---

### Post by imrazor on 2015-11-13
> **TheFu said:**
> Yep.  Seems like you are stuck. 

Hope the big drive is eSATA connected, not USB. Many USB storage connections, including USB3, get into lockups when more than 3-4 task get into the queue. Hope yours doesn't. eSATA performs exactly like an internal SATA connection.

Seem odd to me to be at work and do non-work things on their time. I would have been fired at every job I've had for that.   Are they hiring?

My old vbox tuning article: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)
It's a help desk job. If the phone's not ringing, I'm not working. I'm sure my employer would prefer I educate myself in IT, rather than surfing or watching movies, like most of my co-workers do at night or on the weekends.

The 500gb drive is actually internal. My laptop has 2 drive bays, an mSATA slot, and a convertible optical bay. It weighs a ton.

Now to take a look at your tuning article. I've also been experimenting with KVM/Proxmox on another machine and may take that route if there's not an upgrade path for me. Besides, Ubuntu keeps locking up one me when it comes out of sleep. I blame the buggy AMD drivers rather than Ubuntu itself, but I do need something more stable. Are LTS releases more stable than regular releases?

---

### Post by TheFu on 2015-11-13
Do not just put the hostOS to sleep without doing the same for each of the VMs first.

Yes, the purpose of an LTS is stability.  IMHO, the purpose of the 3 other releases between each LTS is updated HW support and technology demonstration. I would never deploy a server on a non-LTS release unless very new hardware requires it. Sometimes the non-LTS stuff is really amazing.  Other times it is terrible.

Ubuntu distro upgrades usually work, but always make a backup first. Sometimes there are hicups.  "apt-get dist-upgrade" doesn't upgrade from 1 release to another. There is a different process for that.

---

### Post by imrazor on 2015-11-14
The machine isn't locking up when it wakes from sleep. It's locking up when the *display* wakes up. Still trying to find the right setting to disable that.

Thanks for the tuning article. Switching from PIIX3 to ICH9 does seem to help a good bit. Not sure why an IDE controller is the default. Unfortunately, even with a 500GB drive I'm a little constrained for space, so I went with dynamic disk sizes. I noticed in your article you eventually decided on KVM. Was this strictly based on performance? Virtualbox seems easier to manage at least.

Funny, I thought the last time I did an in-place upgrade of Ubuntu I changed the release name on each line in /etc/apt/sources.list then did "apt-get install dist-upgrade." Has the process changed, or am I remembering it wrong?

---

### Post by TheFu on 2015-11-14
I've **never** done any ubuntu release upgrade that way.  Didn't switch to Ubuntu until 8.04.   Whenever I open a terminal, if an upgrade is available, it tells me the command.

Vbox is the easiest free solution for desktop-on=desktop VMs.  
KVM is 
* more stable
* faster
* more flexible
* clearly better for server-on-server VMs
* handles enterprise storage 
* KVM is what openstack builds on
* plus   uh   Oracle - that's enough reason to dump virtualbox - ever seen an oracle bill? I have.
* and with virt-manager just as easy to create/manage VMs...except it can do it from anywhere in the world, securely.

I can't think of any business that uses virtualbox inside their data center, but pretty much every non-100% Microsoft shop uses KVM or Xen inside theirs. But Microsoft-centric companies seem to like to give MSFT money, for some reason that completely eludes me.

But I'm biased.

---

