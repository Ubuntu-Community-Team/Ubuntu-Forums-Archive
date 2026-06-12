---
title: "best distro for vm"
date: 2011-02-26
forum: Virtualisation
---

### Post by chippanfat on 2011-02-26
Alright guys

I'm getting on with ubuntu server quite well but I'm looking to expand, and I've been looking into vmware server 2 for quite a bit. I use it happily on my windows box with ubuntu server installed inside that just so I can test things out

but now I'm looking at deploying it across my servers, I've had endless problems when trying to get vmware server 2 running on about server 10.04 and i'm just wondering if there are any better distro's or easier distros to use as a host for virtual machines, cheers :)

---

### Post by t3r0 on 2011-02-27
Hi,

You could try CentOS... But Those are production servers with anything important in them i'd suggest that go with vmware ESX.. The Essentials pack is reasonably priced and sooooo much better / more stable that vmware server.. 

t. Tero

---

### Post by HermanAB on 2011-02-27
Howdy,

Your problem is not with Linux, it is with VMware.

The VMware Server 2 is a POS and is deprecated and unsupported.  You should change to VMware Workstation or VMware Player.

---

### Post by chippanfat on 2011-02-28
cheers for the reply's guys :)

just something cheap and efficient I'm looking for :)

the setup i'd like to try is openSUSE and vmware server 2? just because of reading a tutorial on it, it seems quite lovely

and there any free alternatives available? i'm strapped for cash being a student and all :( products like VMware workstation would be out of my reach.

cheers

---

### Post by morr_rva on 2011-03-02
VMWare Player **is** free.  Do not install VMWare Server 2; it is End of Line and frankly, a waste of time.  I am running Player on my Ubuntu Maverick system and it works quite nicely.  I do not run OpenSUSE, so I don't know how it would perform there, but I do know it works very well under Ubuntu.

---

### Post by CharlesA on 2011-03-02
VirtualBox works, as does VMWare player. You can run both those ontop of an existing OS.

It's up to you to choose which one you want to use as both have similar features.

---

### Post by stlsaint on 2011-03-02
> but now I'm looking at deploying it across my servers, I've had endless problems when trying to get vmware server 2 running on about server 10.04 and i'm just wondering if there are any better distro's or easier distros to use as a host for virtual machines, cheers 

The real question here is "What is it you want to do?" Are you looking to host a webserver or just play around with distros? If you are looking to run a application on ubuntu server i would suggest you look into lxc as it is built into mainstream kernel. If you are installing on bare metal servers i would suggest [proxmox]("http://www.proxmox.com/products/proxmox-ve"). I am a strong supporter of proxmox for bare metal servers even though it uses openVZ! If you are looking to preserve resources then lxc or openvz is where you want to be. But if you are stuck on using a server to just do distro testing than that is a whole other ball game. Heck you can run vbox from cli on a server just fine. Also dont forget about KVM! :D 
As far as a certain OS....i say ubuntu, centOS or debian!!

---

