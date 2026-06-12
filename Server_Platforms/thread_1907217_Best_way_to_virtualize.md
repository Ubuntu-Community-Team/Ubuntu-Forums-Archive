---
title: "Best way to virtualize?"
date: 2012-01-10
forum: Server Platforms
---

### Post by JoeGoalie on 2012-01-10
Right now I have Ubuntu Server 10.04 installed with OpenVPN, Samba, SABnzbd, Sickbeard, Couchpotato, Headphones, and Plex Media Server. It all works except SABnzbd gives me issues. I can't figure out why, but it keeps crashing. When it crashes, it does it hard. It can only be solved by a hard reboot. So, I got to thinking... If I create a virtualmachine for SABnzbd to live in, it might be more stable as it will be the only thing installed on that VM. Also, if it crashes, it shouldn't take down the entire system. Also, my wife is in school and the server is at a desk. I'd like to have Windows 7 installed on a VM so she has a workstation she can use with the benefits of snapshots and what not. I normally would use Virtualbox, but I noticed there is an option for KVM during the install of Ubuntu Server. Which is better for my use?

On a side note, any recommendations on getting a GUI to run it all in? I was thinking lubuntu-desktop because it looks nice and is lightweight. However I wonder if I should just go all out and get the ubuntu-desktop (likely with no install recommends option). 

System specs:
Core 2 Quad 2.4GHz
8GB DDR 800
ATI HD4850 (was a make shift htpc in a previous life)

---

### Post by rubylaser on 2012-01-11
Personally, I love [Proxmox]("http://pve.proxmox.com/wiki/Main_Page").  It's Debian based (so it Ubuntu), supports KVM and OpenVZ and comes with a very nice, simple web interface to manage the whole setup.  I run this clustered in our work environment and standalone at home.  I've run hundreds of Linux and Windows boxes on it, and it works very well.

Sorry to hear you're still having problems with SAB.  It runs like a tank for me, and I use all of those other services except Plex Media Server, because I use Openelec XBMC HTPCs.

---

### Post by JoeGoalie on 2012-01-11
I use Plex because I'm often remote. I'm USAF and even now I'm away from home TDY at a class. I love the server side transcoding it does.

I have no idea why SABnzbd keeps crashing. It's extremelly frustrating because I can't pin point the cause. I'll look into Proxmox, and it sounds great for a completly headless server. Unfortunately I'm going to have to add some desktop environment in order to run a VM locally as a workatation for my wife's school work. Is KVM a more effecient software, or should I stick with Vbox? I've never heard of OpenVZ before, I'll have to look into that as well.

---

### Post by JoeGoalie on 2012-01-11
Actually I do have one idea why SABnzbd might be crashing.  It seems to crash after movie downloads.  I think it might be related to the sorting of movies.  You said you have SAB and Couchpotato, how do you have it setup to sort?

---

### Post by rubylaser on 2012-01-11
I have it setup per those [Ainer guides]("http://www.ainer.org/") that I posted before.  SABnzbd+ doesn't do any post processing for my files other than running the SABtoSickbeard script for TV shows.  I have Sickbeard and Couchpotato doing all of the renaming and sorting for me.

[OpenVZ]("http://wiki.openvz.org/Main_Page") is container based virtualization, so if you have a linux host, your vm's would use the same kernel as the host.  Also, you don't need a virtualization enabled processor to run an OpenVZ instance.

For a quick, single vm, virtualbox is easier to setup. But, I'm wondering what apps your wife is using for school.  If it's just the Office Suite, those apps will all run fine in Wine without the need for virtualization.

---

### Post by JoeGoalie on 2012-01-11
> **rubylaser said:**
> I have it setup per those [Ainer guides]("http://www.ainer.org/") that I posted before.  SABnzbd+ doesn't do any post processing for my files other than running the SABtoSickbeard script for TV shows.  I have Sickbeard and Couchpotato doing all of the renaming and sorting for me.

[OpenVZ]("http://wiki.openvz.org/Main_Page") is container based virtualization, so if you have a linux host, your vm's would use the same kernel as the host.  Also, you don't need a virtualization enabled processor to run an OpenVZ instance.

For a quick, single vm, virtualbox is easier to setup. But, I'm wondering what apps your wife is using for school.  If it's just the Office Suite, those apps will all run fine in Wine without the need for virtualization.

I dont know why I didn't consider his guides for post processing...

OpenVZ sounds pretty awesome. I've used Solaris Zones at works, so I understand the concept. In Solaris you have to run a command to export the display and launch stuff from terminal to open in X on the global zone though. Can OpenVZ act like a more traditional VM and run on the machine? I guess I need to look up installing Ubuntu in OpenVZ. The only thing that would really tie her to Windows (if wine works with Office well) would be our printer. We have a Kodak printer and I've only ever found x86 drivers for it. It just occured to me though, that I can probably just install an x86 Ubuntu VM...

---

### Post by rubylaser on 2012-01-11
Also, if your drivers are deb packages, you could --force-architecture to get them to install, or compile from source too.

---

### Post by JoeGoalie on 2012-01-11
> **rubylaser said:**
> Also, if your drivers are deb packages, you could --force-architecture to get them to install, or compile from source too.

I just ran through the guides for the post processing and rebooted.  Didn't really change a whole lot.  Did setup the sabtosickbeard stuff though.  I wasn't using that before.

The drivers were a .deb package, I never knew about the --force-architecture option though...  How would I use that command?  I've only ever installed a .deb from the repository or from the gui.  I wouldn't even know where to begin when it comes to compiling.

Info on OpenVZ is surprisingly hard to find.  All the install guides are somewhat convoluted.  A lot of them mention using the Proxmox though.  That solution does look good, but I haven't found anything on the ability to run the container graphically.  I want to use the container as if it was the actual OS and have the GUI and everything.  Is it even possible?

---

### Post by a2j on 2012-01-12
Proxmox does not support software raid :(
did anybody try OpenNode?

---

### Post by JoeGoalie on 2012-01-12
> **a2j said:**
> Proxmox does not support software raid :(
did anybody try OpenNode?

Well that kills Proxmox for me.

---

### Post by rubylaser on 2012-01-12
> **a2j said:**
> Proxmox does not support software raid :(
did anybody try OpenNode?

Not, true.  They say it doesn't support it, because they don't want to have to troubleshoot mdadm for users that have never used it before.  It's built on Debian, so mdadm is available and works just fine. I run an mdadm RAID1 array on a couple of my cluster nodes.

---

### Post by JoeGoalie on 2012-01-12
> **rubylaser said:**
> Not, true.  They say it doesn't support it, because they don't want to have to troubleshoot mdadm for users that have never used it before.  It's built on Debian, so mdadm is available and works just fine. I run an mdadm RAID1 array on a couple of my cluster nodes.

Where can I find the .deb or the ppa?

---

### Post by rubylaser on 2012-01-12
> **JoeGoalie said:**
> Where can I find the .deb or the ppa?

In light of what you're trying to do with your wife's software, I'd not suggest Proxmox in your situation.  It's really designed for headless virtualization servers.  And to install the package for your printer, you'd download the .deb file via the command line.

```
wget url_here
```

Then, install it...
```
dpkg --force-architecture -i deb_package_name.deb
```

---

### Post by JoeGoalie on 2012-01-12
Even after I configured everything according to the guide, SABnzbd still took a dump on me.  This is incredibly annoying.  It just doesn't want to get along with Couchpotato.

---

### Post by a2j on 2012-01-12
> **rubylaser said:**
> I run an mdadm RAID1 array on a couple of my cluster nodes.

is it possible to make it work on 4 drive raid10? I like that software but no software raid kills it.

---

### Post by rubylaser on 2012-01-12
But it does.  I works fine for me on Ubuntu 10.04.  I've had all of those services running for over a year flawlessly.  The only difference in packages between yours and mine is I don't use Plex Media Server.  I can't really provide more info other than to say those guides have been proven to work for hundreds of users on the XBMC forums, so they're very proven at this point.  There has to be something causing a conflict (misconfiguration, software conflict, permissions, etc).

---

### Post by rubylaser on 2012-01-12
> **a2j said:**
> is it possible to make it work on 4 drive raid10? I like that software but no software raid kills it.

Why wouldn't it?  It's the same mdadm in Debian that Ubuntu uses.  You'd have to set it up via the command line, but that's certainly not a hard task.

```
mdadm --create /dev/md0 -l 10 -n 4 /dev/sd[abcd]1
```

---

### Post by JoeGoalie on 2012-01-12
> **rubylaser said:**
> But it does.  I works fine for me on Ubuntu 10.04.  I've had all of those services running for over a year flawlessly.  The only difference in packages between yours and mine is I don't use Plex Media Server.  I can't really provide more info other than to say those guides have been proven to work for hundreds of users on the XBMC forums, so they're very proven at this point.  There has to be something causing a conflict (misconfiguration, software conflict, permissions, etc).

I don't doubt that it does work. I followed the guide and it didn't work for me. I'm going to rebuild the system anyway as now I'm confident to do it. I was keeping the rest of my drives with Windows Server still loaded. I have to set it up the way I really want it with my RAIDs this time. Hopefully I will do whatever I missed...

---

### Post by rubylaser on 2012-01-12
I'm glad to hear it :)  Please let me know if you have any issues or need any help.  Good Luck.

---

### Post by a2j on 2012-01-16
still unable to get any kid of software raid to work properly with proxmox. some updates usually brake it. I guess there is a reason why they don't support it.

but what about Ubuntu Enterprise Cloud?

---

