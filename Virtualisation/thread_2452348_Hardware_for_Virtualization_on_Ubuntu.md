---
title: "Hardware for Virtualization on Ubuntu"
date: 2020-10-20
forum: Virtualisation
---

### Post by rsteinmetz70112 on 2020-10-20
I have been looking into virtualization on Ubuntu. I want to try it out on one of my Windows computers but I'm not sure whether my somewhat dated hardware will work. I have a Asrock N68C-GS4 FX motherboard with an AMD FX8320E Processor. As far as I can tell AMD says the processor is capable of virtualization but the AMD Windows HYPER-V utility says virtualization ( AMD-V ) is not enabled in the BIOS. The only setting I can find is "Secure Virtual Machine" and it is [ENABLED]

---

### Post by SeijiSensei on 2020-10-20
Rather than asking here, why not just give it a try? Either it will install and work properly, or it will not. You won't damage anything by trying.

I've run VirtualBox on a wide variety of hardware over the past few years.  I'd be more concerned about memory size than any of the things you listed. 4 GB is probably the absolute minimum for the Windows host, so you can give the Ubuntu VM 1.5 GB and leave 2.5 GB for the Windows host.  Anything less than 4 GB will likely give you pretty abysmal performance with lots of disk swapping.  I upped my memory to 16 GB a couple months back so I can give both my Kubuntu host and my Windows VM 8 GB each.

You can install VB from the repositories, but I recommend using Oracle's own repository by following the instructions here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  VirtualBox will then always be current and updated by apt like any other package.  Just a word of warning to avoid confusion.  If you specify 
```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib
```
in sources.list, you may notice that you get a binary named [FONT=Courier New][SIZE=1]virtualbox-6.1_6.1.16-140961~Ubuntu~**eoan**_amd64.deb[/SIZE][/FONT]. Oracle doesn't release a new version for every new release of Ubuntu.  The eoan (19.10) version works just fine on my 20.04 focal machine.

---

### Post by rsteinmetz70112 on 2020-10-20
The reason I asked here is I I'd like to avoid any unnecessary detours. If necessary I have other hardware I can use.

---

### Post by SeijiSensei on 2020-10-20
Waiting for answers here is going to take longer than just trying to install it on your machine.

I'm an empiricist by nature especially when it comes to computing.

---

### Post by rsteinmetz70112 on 2020-10-21
> **SeijiSensei said:**
> Waiting for answers here is going to take longer than just trying to install it on your machine.

I'm an empiricist by nature especially when it comes to computing.

I believe in doing some investigation before diving into the deep end of the pool.

---

### Post by Tadaen_Sylvermane on 2020-10-21
Don't use Hyper V. Use VirtualBox. HyperV is likely complaining about lack of VT-D, something needed for passthrough and not a common requirement for most home users.

---

### Post by sh1ba on 2020-10-22
I wouldn't suggest even using Hyper V, I would use either Virtual-Box or even VM-Ware as I believe they have their own Guest add-ons? correct me if I am wrong. -

---

### Post by lammert-nijhof on 2020-10-22
I would use Virtualbox too, it is reliable and used very frequently by desktop users. In the BIOS try looking for AMD-V. Try [https://www.youtube.com/watch?v=JULTTn3TPnw](https://www.youtube.com/watch?v=JULTTn3TPnw) 
Otherwise try to find the manual for your motherboard on Google.

---

### Post by rsteinmetz70112 on 2020-10-23
I have the manual and as far as I can tell there is no setting for AMD-V only  "Secure Virtual Machine" and it is [ENABLED]
I tried installing Virtual Box on one of my 64 bit Ubuntu 20.04 desktops and all I get are 32-bit options.

---

### Post by rsteinmetz70112 on 2020-11-02
I now have virtual box up and running with Windows 7 in a VM.

Thanks for your input.

---

