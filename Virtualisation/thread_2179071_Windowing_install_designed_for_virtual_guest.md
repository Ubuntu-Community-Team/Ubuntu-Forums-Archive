---
title: "Windowing install designed for virtual guest?"
date: 2013-10-06
forum: Virtualisation
---

### Post by 1clue on 2013-10-06
Hi,

I'm looking for a lightweight windowing variant (preferably 12.04 LTS) that has an option to set it up as a VM guest.

Ubuntu Server has an option to set up as a VM guest, and it cuts out a lot of the tools that assume you're on real hardware.  I'm looking for this same sort of thing in a lightweight ubuntu variant.

I have some Mac users who need to have Ubuntu as a virtual guest on their laptops.  They don't do the command line thing too well.

This basic VM will be copied over and over on the same machines and used as a base to do other things, so I don't want a heavy VM.

If nothing shows up, I'll just try to install xubuntu-desktop from the Ubuntu Server install.

---

### Post by TheFu on 2013-10-06
I've never tried this, but setup the initial install using JeOS, then add the GUI you want (LXDE/XFCE) on top.  

I do something similar using Ubuntu Server with just ssh-server loaded.  I'm much happier.

The great thing about Ubuntu - clone as much as you like!  Just change the MAC as seen by the VM host to prevent network confusion if they are on the same LAN.

I would be concerned over using JeOS for some installs - didn't think it supported a full network stack ... like iptables-based firewalls.

Also, JeOS only works on Linux hosts, but  I'm definitely ** not** certain of this.

---

### Post by 1clue on 2013-10-06
The application is for software development.  We need a build system for each customer, once we set it up it will be isolated on NAT, and will only be used to build and test software using the source and development tools which were used when we built their system.

We get this situation occasionally when some customer makes a support call 2 or 3 years after we built.  Our development workstations don't even have the correct version of the tools anymore, so we can't even build the app again.  We want to be able to build with just a minor change, test it and redeploy without a fuss.

This is definitely a clean room type of build.  It won't be exposed to the real Internet, so I'm not worried about firewall rules.

I think I have a JeOS install on one of my hosts somewhere.  I'll go see what it's got.

Last time I tried Server and installing xubuntu-desktop I ran into some sort of issue.  I don't remember what it was, but it made me actually download xubuntu rather than using server, it was too much of a PITA.  Don't remember what it was.  It's not the "can't find a reason to install ..." message, that's just a minor irritation and not really a roadblock.

Thanks.

---

### Post by TheFu on 2013-10-06
This is a perfect use for virtualization.

If your software isn't doing image processing or videos, then you could setup a KVM box with a few TB of storage and remote desktop into to do the builds. Each active VM could use qcow2 as the file system with compression - highly storage efficient, if just a little slower.  With server hardware, you could put in a RAID1 SSD solution to easily overcome disk performance when a client needs work and leave the other "frozen" VMs on cheaper spinning disks (or a shelf) until the time they are needed again.  Just move the active and inactive VMs between SSD and cheaper storage as needed.

I have a friend who runs all his Windows VMs on RAID1 SSDs for this reason.  They use sparse allocations and qcow2 file systems - performance is blazing for their VM servers - including MS-exchange.

I've run "Server" with both xfce and lxde, but still use a pure-WM-only environment often enough.  A JeOS install shouldn't take more than 10-15 minutes.  I need to check it out too ... just my reverse proxy needs fancy firewall rules after all. Thanks for the idea.

---

### Post by 1clue on 2013-10-06
Ya I think so too.

One server is an ESXi box, real server hardware and RAID and SSDs.  That's at the office.

I have an i7 with ssd and software RAID with Xubuntu on it, that doubles as a workstation and as my KVM box.  It beats the crap out of my Mac.

All the developers have Mac laptops.  They all use virtualization via Parallels.  They're limited to 8g so they're a bit old, but we still use them because Apple doesn't make a 17" laptop anymore.

Frankly I question how valuable a laptop is to me, they're neat but I hardly ever take it out of the office.  I'm more interested in a multimonitor luggable setup.  It would be interesting to have a supersized iMac and an extra 27" thunderbolt monitor as my "laptop."  I'd try for a Linux solution but I'm not sure my employer would go for it.

Anyway, as far as I'm concerned I can use pure Ubuntu Server on the VMs.  I need every bit of speed I can get IMO, and every bit of RAM.  But I have this i7 over here and if I can offload the virtualization tasks to that then I'd be better off.

OK well I have a start anyway.

Thanks.

---

### Post by TheFu on 2013-10-07
I'm a netbook/tablet and powerful desktop user.  No laptop can match that for coding.  Remote access is good enough these days that a lite tablet/netbook with a good remote connection is a viable way to work.  I do that for my desktop and know [others who do it too.]("http://yieldthought.com/post/31857050698/ipad-linode-1-year-later")  I've been doing this for about 2 years.  My main desktop is actually running on a remote "private cloud" server as a KVM instance.  It isn't perfect, but it isn't bad at all.  Plus I don't have to worry about security when I'm traveling or sensitive data being lost or stolen on my netbook.  It doesn't have anything sensitive and it has an encrypted HDD.

I do software development too, but it is web server stuff, not anything compiled (like I did for 10 yrs - cross-platform C/C++).  Ruby is the heaviest stuff I write, but most of my real work is with Perl+Dancer. Tight, fast, amazing. Easily runs on 384M servers, unlike RoR stuff.

My Core i5 15" 1080p laptop has lots of CPU, but the disk I/O just can't keep up.  I've performed testing and it is scary how much slower laptops are due to disk IO.  I should probably swap in a 500G SSD to be happy.   I like the laptop for all sorts of things ... provided I don't have to carry it.  Car - sure. Airplane - NO WAY!

The netbook display sucks. I always feel like I'm missing 400+ px, which is true.  I tried to do it with an android tablet, but got burned while in Europe. Wasn't prepared for most ports to be blocked by companies and hotels, so my VPN couldn't connect.  Then I was stuck with an OS incapable of troubleshooting the issues ... sometimes only nmap will help.  Being burned that one time made my tablet into a home-only device. Basically it is for reading and next to the TV to look things up now. Nothing else.

Anyway, good luck with your solution.

---

### Post by 1clue on 2013-10-07
I need the monitor space.  A netbook won't cut it for me.  I'm contemplating a 3- or 4-monitor solution right now, the 1920x1080+1200x1080 combination I have now isn't enough.

I also really need the horses right at the workstation.  RDP would be prohibitively expensive, I can do most of my work offline but with remoting a GUI environment across the wire would mean I would need to be on and passing bits constantly.

My ideal solution would be something like a Mac Mini only with extra monitor and usb3 ports.  And then a truck load of monitors.

---

