---
title: "What's the best way to install multiple softwares on one server?"
date: 2022-08-28
forum: Server Platforms
---

### Post by simon0100 on 2022-08-28
Hello,
I have a small server PC lying around (Intel N5105/16GB/Ubuntu Server 22.04.1) and want to use it for multiple purposes.

I would like to install Home Assistant, a NAS Software (for example TrueNAS), a Router Software (to use the PC as a managed access point for my Smart-Home devices), and maybe a VPN Server Software.

My question now is: What's the best way to do it? I already figured out "apt install" won't help me, since most of the software I want to install is only available as a full operating system (.iso). Should I create four virtual machines, or is there any better way to do this? If so, does the VM slow down the installed software? Is there anything I should be aware of when configuring the VM? Is Ubuntu Server even the best choice for this project?

Thank you in advance.

---

### Post by ActionParsnip on 2022-08-28
Which software will you install using the ISO?

---

### Post by simon0100 on 2022-08-28
I was thinking about KVM or VMware for virtualization. Home Assistant provides the virtualization files directly to download, and TrueNAS is only available as an ISO.

I just found out that TrueNAS requires all my 16GB RAM, but supports virtualization. So, would it be better to install TrueNAS as my main operating system and install the other software inside virtual machines?

---

### Post by howefield on 2022-08-28
Thread moved to the "*Server Platforms*" forum.

---

### Post by ActionParsnip on 2022-08-28
Why not just configure Ubuntu as a NAS? Why mess around with virtualisation and such when Ubuntu can give you a storage on the LAN that you can use...? Why bother?

---

### Post by simon0100 on 2022-08-28
I wanted to use the web interface / dashboard for configuration, but you are right, this will probably be the simplest solution. As for Home Assistant, I'll try installing it in a Docker container. Thanks!

---

### Post by LHammonds on 2022-08-29
If you have hardware with 16 GB of RAM and you want it to perform 4 different services but one of those services requires all 16 GB of RAM, you might not have enough hardware to run everything...especially not as 4 different operating systems + virtualization.

Some services should be run separately from everything else...such as VPN because that service typically has a direct line to the outside world and would be an attack surface.  If successfully attacked and that is the same system running all your other services, then the attacker would have direct, immediate access to them.  Think of an attack package that breaks down your front door and throws in an encryption bomb locking down everything on the server. That scenario wouldn't be too hard to imagine if your services were maxing out the RAM and the attacker caused a service to work too hard and fail because it ran out of resources.

I would have internet-facing machines as isolated as possible from everything else and imagine what an attacker could do if that service and operating system were taken over.  What could an attacker do with that service once compromised (was the VPN service isolated from the OS such as being run with its own limited credentials and not the "root" account)....what could the attacker do if the OS running that service was compromised...etc.

If you do not know how to manually install the service and just use somebody else's ISO image, at least make sure you are familiar enough with it to know how it was built with the above scenarios in mind...such as being able to isolate it if compromised by a hacker.

If you have any important data / configurations on that machine, make sure you back it up locally and a separate/remote machine grab the backup files.  Make sure it is in a way that the backup machine does the collecting one way....make sure the machine being backed has zero access to the backup machine.  The less your data servers know about your remote backup machine, the better.

I'm not trying to scare you out of doing it....just make sure each service has the needed RAM/CPU/HD to operating and make sure you are aware of potential risks and are ready for them.

LHammonds

---

### Post by simon0100 on 2022-08-30
I know, a VPN connection to a local network is always a security risk. I just wanted to access a folder/file on the NAS from outside. But I think I'll forget TrueNAS and share storage over Ubuntu, as @ActionParsnip suggested. Home Assistant is installed via Docker, I'll try the same for RaspAP (an access point software I recently found). For backup, I just use a 3TB HDD connected over USB. Anyway, VPN is the least important feature for me, so I will let it go for now, and think about it later.

Thank you!

---

### Post by TheFu on 2022-08-30
> **simon0100 said:**
> I know, a VPN connection to a local network is always a security risk. I just wanted to access a folder/file on the NAS from outside. But I think I'll forget TrueNAS and share storage over Ubuntu, as @ActionParsnip suggested. Home Assistant is installed via Docker, I'll try the same for RaspAP (an access point software I recently found). For backup, I just use a 3TB HDD connected over USB. Anyway, VPN is the least important feature for me, so I will let it go for now, and think about it later.

Thank you!

To remotely access storage, use sftp or ssh. No need for a VPN.  Linux file managers all support sftp://, so you can drag-n-drop if the default group and umask are acceptable. IF not, drag-n-drop, then ssh in and chmod/chgrp as you like.  Don't forget about the setgid flag for directories.

I can't imaging any Linux home needing a VM with more than 4G of RAM. Most of mine use 512MB+ 1vCPU or less with a few using 2G and 2 cores.  16G of RAM can easily support 10+ VMs. I've had 20 on a Core 2Duo system years ago.

I would be worried about the Celeron N5105 CPU, but not too much.  I had a G3258 running Plex, NFS, Calibre, Nextcloud, Wallabag and a few other things for years. It was dual core and about 50% fewer passmarks.  The Celeron N5105 should be fine, assuming you can enable VT-x support in the BIOS.  For VMs, that is very important.  For containers, it is not. [https://www.intel.com/content/www/us/en/products/sku/212328/intel-celeron-processor-n5105-4m-cache-up-to-2-90-ghz/specifications.html](https://www.intel.com/content/www/us/en/products/sku/212328/intel-celeron-processor-n5105-4m-cache-up-to-2-90-ghz/specifications.html) seems fine to me.

VMs are about 10x heavier than a Linux container like LXC or docker. Even with that overhead, they are pretty fast, unless you want to run games.  For for server stuff, you'll likely never notice.  

Putting too many things inside the same OS install is bad. Software stacks often overlap, but diverge quickly so you'll have trouble getting them to play nice when it is time to upgrade in 3-6 months to newer, fixed, software.  That's where containers or VMs really help.  The different software stack dependencies are contained for just the programs/servers that need it.

The risk of allowing ssh (with keys, never passwords) or a real, solid, VPN server, are minimal.  Having 2 ports open to 10% of the world - never the entire world - which along allow authenticated connections using 4K keys is pretty minimal.  We know how to secure ssh. Lots of how-tos online.  With about 10 non-default changes, you'll not need to worry about remote attacks, much, if at all.  Of course, you'll want real-time warnings about the attacks - tools like logwatch and fail2ban will aid in that.

As long as you don't intend to use the router setup for your WAN security, just LAN stuff, I don't see an issue.  I keep my IoT junk upstream and have the ISP's router split the traffic - my public IPs go to a dedicated device with a 64-bit AMD CPU running OPNsense which manages 3 physical LANs.  WiFi is on the IoT junk, untrusted, network outside my protected LAN.   All wifi devices, IoT, video streaming crap, game consoles sit there. Can't trust any of those.  I'd never allow wifi devices on the protected LAN. Too many wifi security failures over the decades. There are more yet to be announced.

---

### Post by kevdog on 2022-08-31
TrueNAS (whether CORE or scale) uses ZFS and hence requires a lot more RAM.  You can virtualize this installation however I'd just recommend it's own separate machine.  Huge learning curve here but its really really fun.  Been using TrueNas Core for about 3 years and its really fun to play with.  For your other needs -- router, VPN, Home assistant needs, you really don't need all the much power but will need at least two networking jacks if planning router -- WAN and LAN which would hopefully fit to a switch.  I could forsee you needing minimum 8GB of RAM however likely need at least 16GB.  My opinion here might be different however I'd look at using a Hypervisor for the base install and then virtualizing pfSense/OpnSense and Home Assistant.  I'm in the minority but I use xcp-ng as my hypervisor since I find it really easy to use, however proxmox and ESXi are the more popular choices.  With the recent acquisition of ESXi by Broadcom, I'm not sure what that means for the future of home users in terms of free-use.  I'm not trying to spread FUD about ESXi its just that it's future as a free hobbyist option may change, no one knows.  ESXi is hugely popular and likely the most used hypervisor in the business world.  pfSense/OpnSense can provide either OpenVPN or Wireguard (really happy with using Wireguard to connect to home with computers and phones as clients).  Introducing a business level router into your home system is really really nice for capabilities.  Home Assistant also has a virtualized option which I did install on xcp-ng and I think I dedicated it 2 Gb of RAM.  It doesn't take much.  

Hopefully that gives you some ideas to think about.  There is no one great or correct way to implement your goals.  Have fun with whatever you come up with.  Tom Lawrence from Lawrence Systems Forums puts together a lot of videos on xcp-ng and TrueNAS and FreeNAS and I found it to be a really useful learning resource.

---

