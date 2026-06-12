---
title: "Enterprise Grade Server Hardware Suggestions"
date: 2010-01-21
forum: Server Platforms
---

### Post by robmhood on 2010-01-21
Hi All. I've been running multiple Ubuntu Servers in a non production environment and am now ready to make the switch from Windows Servers to Ubuntu on a couple of my production servers.

I'm looking to acquire (purchase or build) a couple of servers with the following specs:
Dual Quad Core Xeon Procs
32GB RAM
a minimum of 200GB RAID 5 storage (true hardware controller)with SAS drives. I need 10k rpm or better

Any suggestions on a vendor for purchasing a server?
I've looked at System76 but it looks like they only offer SATA drives
Dell?  Doesn't look like they even offer the Ubuntu Server OS as an option any more


If I were to build my own . . . 
My main stumbling point here is true hardware RAID compatibility 
I would be using an Intel SR2500ALLXRNA 2U Barebone Server (can find them at Newegg).  Intel has a raid activation key (AXXRAK18E) that turns their software RAID into a true hardware RAID module.  I've use it on a VMWare server for virtualization (and VMWare is based on a Linux Kernal), but I haven't found anyone who has gone this route with a stand alone Ubuntu install or any listing of hardware compatibility.  Anybody with any experience with Intel Server Motherboards with Intel Hardware Raid and Ubuntu?

I would prefer to go the all Intel Inside route, but my alternate plan would be a 3ware card as that appears to be very popular in the forums

Any advice would be greatly appreciated!

Rob

---

### Post by Xianath on 2010-01-21
I stumbled upon this vendor while working on a storage project: [http://eracks.com/](http://eracks.com/) . They are very OSS oriented and will pre-install the OS for you if you wish. If they find hardware incompatibilities, they'll suggest alternative parts but given the component vendors (Tyan, LSI, Adaptec, 3Ware) I don't expect issues. However, apart from being impressed with the choices they are giving, I have no experience with them so I can't comment on build quality, support etc. Might be worth checking out anyway.

I have significant experience with Dell servers and think that for production servers, they are a smart choice. A few years ago the company I worked for had to choose between Dell, HP and IBM for our Linux-based appliances and they went for the Dells. Well build, run SLES well so I can't imagine why they shouldn't run Ubuntu, and of course you got worldwide on-site support if you can afford it. I imagine price also played a part but I wasn't involved in that process so I can't comment.

As of hardware RAID -- well, 3ware, LSI and Adaptec are all very viable choices. I respect Intel but have zero experience with their RAID controllers (fakeraid doesn't count) so no idea there. However, I would seriously consider staying away from any on-board RAID controller even it if is a true RAID and not fakeraid. Three or five years from now when your motherboard suddenly dies for you, it will be out of stock, out of production, and you have no guarantee that this chip will be in use on then-popular server boards. At least with add-on boards you have significant reasons to believe you'll be supported if/when the controller dies. Of course this is not an issue at all with software RAID but it seems you've made up your mind there already.

Finally, the barebone you're pointing at has a single PSU. Bad idea for a RAID even with battery-backed cache, and even with write barriers enabled (also, who knows if the RAID controller driver will support them?). Get a chassis with redundant PSUs and hook them into separate UPS'es. Better be safe than sorry, and the price tag of redundant PSUs is not so bad.

HTH,
Peter

---

### Post by steven.jones on 2010-01-21
Dell is a good choice for quality hardware. 

As a get around for hardware support, you can get VMware's ESXi software (installs on a USB key or sdcard for free). So instead of buying two servers, buy one of a slightly higher CPU and memory spec, which is cheaper....and run both Ubuntus' in/on that, that is fully supported by Vmware (in terms of support, which you would have to buy if you want to ring them)...dodges the hardware bullet neatly. The Dell R710s we run are  2x3Ghz quad core and 72Gb of ram, we use usb or sdcards and keep the disks for vmware storage 4 or 8 x 146gb 10k sas disks (for our bigger sites we have a SAN)....costs us $20,000NZ but we can run 20 servers on each, so thats $1000 a server.......

For home I do something similar, I have the free ESXi setup on a desktop but get a linux NAS

---

### Post by steven.jones on 2010-01-21
Linux NAS was Openfiler....it will be Ubuntu once I get iSCSi going....

---

### Post by robmhood on 2010-01-26
Thank you Peter for your suggestions!!!  eracks.com is interesting and worth a closer look and I'll going place a call to Dell to see what they have to say.  Your advice on the card makes plenty sense to me too, but the way this server will be functioning I would be looking at a replacement cycle in the 3-5 year timespan.  Good Catch on the barebones single PSU!  I'm a firm believer in redunancy - it lets me sleep at night.  Thank you again!!

Rob

---

### Post by robmhood on 2010-01-26
Many Thanks to you too Steven.  I had the big "duh" moment when you said ESXi.  I'm in the middle of planning virtualization on some other servers, but for some reason I was stuck in the "traditional" server mode of thinking.  I can get the Intel whitebox server configured to VMWare's hardware compatiblity specs which gets me past the Ubuntu hardware compatibility and ESXi doesn't take a lot of resources so it shouldn't drag down the performance.  Thanks Again!

Rob

---

### Post by Xianath on 2010-01-26
If you go down the virtualization path, make sure your CPU has both virtualization extensions (AMD-V or Intel VT-x) as well as IOMMU (AMD-Vi or Intel VT-d). This shouldn't be an issue in the enterprise class processors but still make sure you double-check anyway since model numbers of either vendor are not always intuitive, and a higher model number doesn't necessarily indicate more features.

My personal preference would be the [six-core AMD Opteron CPU]("http://www.amd.com/us/products/server/processors/six-core-opteron/Pages/six-core-opteron-key-architectural-features.aspx") which Dell does offer, as do Sun (a company I have the deepest respect for). Your mileage may vary (and probably does).

Cheers,
Peter

---

