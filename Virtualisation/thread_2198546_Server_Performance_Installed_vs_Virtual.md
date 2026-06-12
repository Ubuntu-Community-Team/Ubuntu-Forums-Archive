---
title: "Server Performance: Installed vs Virtual"
date: 2014-01-09
forum: Virtualisation
---

### Post by cweinhofer on 2014-01-09
I recently purchased an HP ProLiant G7 N54L (AMD Turion II 2.2 GHz Dual Core, 2 GB RAM) to use as a home server. The main function will be centralized storage for our home (mainly SMB shares, possibly some media streaming). The storage is all contained on a 2 TB drive which I sync with an external 2 TB drive for backup & traveling. I will also be running a virtualized Windows XP install to support a legacy printer.

My initial thought was to install Ubuntu Server directly on the machine, but then I was thinking about my travel. If I virtualized the file server as well, I could copy it to the external drive along with my files and then run it from my laptop through something like VirtualBox. This would allow my laptop to see the files as being in the same place as they are when I am home. (BTW, because it's likely to be suggested, the size of the files would make a cloud storage configuration untenable.)

My question is about the performance difference between various configurations. I am sure there will be some, but will it be significant given that there are only 2-3 users.

Option 1: Install the file server directly to the machine. Run Windows virtually.
Option 2: Install a basic linux OS to the machine and then run the file server and Windows virtually.
Option 3: Set up the server with some kind of bare metal hypervisor (Oracle VM Server or similar) to run the virtual file server and virtual Windows.

I have used VirtualBox quite a bit but have very little experience with servers and none with Type 1 hypervisors. I have no idea how easy it would be to copy the virtualized file server to the external drive each time and then run it from virtualbox under the Option 3 configuration.

Option 2 seems like the most straightforward given my desires and previous experience, but how much of a performance hit will I take? Also, if you would recommend that option, what should the base linux be?

---

### Post by Kirboosy on 2014-01-09
I would recommend that you do a bare metal install of whatever OS you want to use as your server and stick to it. 

The amount of RAM in your computer would most likely be your biggest issue. I would recommend installing Ubuntu Server 12.04 and learning the ins and outs of the server that way. Samba is really easy and simple to setup. 

As for your printer, have you ever use Linux with your printer? The support on Linux for your "legacy" printer might be better than you think. If you can setup the printer with Linux then you could have a CUPS share of the printer on the network so everyone could print to it

Hope that helps!
~Caboose

---

### Post by houstonbofh on 2014-01-11
Do a bare metal install.  Back the drive up the first time with DD, so you get the UUID information, and keep it synced with rsync.  When you take it with you, run can still boot it in a VM on your laptop...  You will simply have to adjust for the nic now being eth1.  You will also want to backport that udev and network information to the server to keep rsync from overwriting it...

---

### Post by TheFu on 2014-01-11
Turion systems are underpowered for virtualization.
2G of RAM is extremely minimal for a virtualization system too. These days, it is important to leave enough RAM for the hostOS. For Windows, that mean 1G, for Ubuntu 512MB is probably fine for non-desktops.
The only "bare metal" hypervisor I know is VMware ESX/i.  All the others require a hostOS.

If the printer is the only reason for Windows, see if it isn't supported by Linux. Older printers usually are now when Win7 dropped support for them. Had a client in a similar situation ... printer.  Ended up getting a $50 laser printer to replace the old one.  It was easier than buying $50 commercial printer drivers that would probably break every kernel. They've been happier ever since. Just be certain to get a printer that is natively supported by Linux and doesn't need any special drivers from the vendor. The support is extremely good these days. HP, Samsung, Brother seem to do a good job of support.

Perhaps a different option might work than copying files or VMs?  I travel about 6 weeks out of the country every year.  When on travel, I take a minimal netbook and use remote access with NX back to my desktop on a safe network that I trust. No need to copy any files and the netbook doesn't have any proprietary data to be lost or stolen. Plus if the netbook needs to be left at a border, it is only $200.  Too many other reasons why this is what I do to list here.  My normal, daily use, desktop runs under KVM in a "private cloud". NX performance is great for programming, email and web surfing from around the world or in the same building.  Not to great for video, but I don't use that much on travel.  The worst connections were actually nearby in the USA, but from Asia, Africa, Europe it has worked extremely well.

Assuming remote access is NOT an option, then ... 
If you plan to use vbox on the travel laptop, then you need to use virtualbox on the main system too.  VMs running under different VM tech isn't  switch-n-play.  Recommend staying with 32-bit or 64-bit matching tools on both the server and the laptop. If the laptop only runs 32-bit vbox, then only install a 32-bit OS on the server as well.

How good is the performance?  Well, that depends on the workload, RAM, CPU, networking and disk.  If you run 5 VMs and they are all busy, then expect performance to be much less than the physical host performance.  OTOH, if there is plenty of RAM, CPU, and only 1 VM running on a mostly quiet host then it is possible to get 90-95% native performance for non-graphics workloads ... provided the VM setup is smart.  Graphics applications are a poor choice for VMs.

External drives generally suck for running OSes, unless they are eSATA connected.  Major issues can be had running over any USB, including USB3. Lots of people in my LUG have tried and run in to queuing issues. When 1 or 2 processes read/write to a USB drive, everything is fine, but when an OS gets going ... there be issues.

---

### Post by houstonbofh on 2014-01-11
> **TheFu said:**
> The only "bare metal" hypervisor I know is VMware ESX/i.  All the others require a hostOS.

Xen is also available as a bare metal hypervisor.  [http://www.xenserver.org/](http://www.xenserver.org/)  And as you can manage it with openxenmanager, there are some significant advantages over VMware for the Linux desktop user. :)

That said, I still do not think he should be using and VM software.  A real hard drive can boot in a VM on his laptop on demand just fine.  (as long as it is not Windows... :) )

---

### Post by cweinhofer on 2014-01-12
Thanks for your thoughts. Given all of your advice I decided to stick with installing it straight to the hardware (I am assuming that's what you mean by a bare metal install). In my case, I realized it would work just as well to set up a VM on the laptop to read the files on the backup drive and make them available via SMB - there was no big reason I needed an exact copy of the server.

I have also done some of what TheFu recommends when I have internet available (which is not always). I have used TeamViewer and been generally pleased, but I'd be curious to know if you think NoMachine is better? (Sorry if that's a little off topic.)

---

### Post by cweinhofer on 2014-01-12
Also, I did give the printer another go and have still had no luck - but that's a topic for another thread. ;)

---

### Post by TheFu on 2014-01-12
> **cweinhofer said:**
> I have also done some of what TheFu recommends when I have internet available (which is not always). I have used TeamViewer and been generally pleased, but I'd be curious to know if you think NoMachine is better? (Sorry if that's a little off topic.)

TeamViewer requires a trusted 3rd party to work. That means they have access to your machines.  Think of all the times recently when 3rd parties have screwed up either by accident or through theft and caused issues - Target, Yahoo just last week.  I have NEVER used teamviewer, so I don't know how good or bad it may be. Just the idea of allowing a company that I have no paid contract access to my machines makes me nervous. Many folks do not have the same "issues" with unwanted middlemen that I do.

If they have the access or information, it will get out. Period. I expect it and believe it is just a matter of time.  BTW, HTTPS is broken, badly. Not to be trusted.

Why trust some other company when it isn't needed? To clarify, I don't think that NoMachine is "better".  I think that FreeNX is better because we run the server and we can control the ssh keys and we can control the firewall rules for which parts of the world are allowed to connect and we can control the number of failed attempts that are allowed before blocking completely.  NoMachine's client software v3.x has worked better for me than the qtnx and the other options, so I pointed that out. The other options should work with a freenx server.

---

