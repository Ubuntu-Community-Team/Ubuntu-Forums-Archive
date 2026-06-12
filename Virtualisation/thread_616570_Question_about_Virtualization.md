---
title: "Question about Virtualization"
date: 2007-11-18
forum: Virtualisation
---

### Post by jonberling on 2007-11-18
Hello Everyone,

It's time to replace my old PC. I was thinking about buying an ubuntu system from dell. The only problem is that I need to run windows applications from time to time. The program that I need to run on windows the most is MS Visual Studio 2005. (And probably VS2008 when it comes out.)

My question is how much ram would you recommend? And would you recommend virtualizing WinXP SP2, or Win2000 SP4? I think Win2000 would be lighter in the system requirements, but does it have any trouble running newer software? (IE Photoshop CS3 needs at least WinXP SP2).

Is there any problems with WGA if it's running virtualized? I'm pretty sure that the license I have allow me to run either OS in a virtual machine. (but not vista :( )

Also, I gather from reading the forums that playing Civ4 on a virtualized OS is a no go.

---

### Post by climatewarrior on 2007-11-18
The reason you cant play civ 4 in your virtual machine is because virtual machines dont support 3d acceleration. But as far as I know Vmware is working on this ans they already released a product for the macs that makes it possible to run some 3d acceleraated studd in virtual machines. I guess that will eventually come to linux. As for know you might want to try to runt it with wine or cedega. As for the memory I would say that 1GB sould be enough but the more the better. 2GB would be really nice specially if you run a heavy ubuntu ( compiz fusion, awn, etc) . It also makes a very big difference what you use for virtualization. I think that Xen is probably the fastest but I might be harder to setup than vmware or virtual box. Im not really into virtualization so please wait for some one else's opinion. Also I think that you wint have any problems with running winxp sp2. I have a laptop with 512mb of ram and isued to have it with virtualbox and it ran just fine.

---

### Post by nutter78 on 2007-11-18
Use your VM for the office type stuff, but set up a dual boot for your games!

---

### Post by Asobi on 2007-11-19
as i could have given my topic the same name i just post here.

i want to create a virtual machine to run some adobe applications and solidworks. but if possible i want to virtualize and existing windows xp installation and still keep it bootable (for games) ..is this possible?!

ive googled a bit and vmware player and virualbox can both create virtual machines to install windows on. but from what i understood vmware workstation can virtualize an existing windows installation and still keep it bootable outside the virtual machine.

any knows more about this or the possiblity to virtualing and existing windows installation and keep it bootable.

---

### Post by VorDesigns on 2007-11-25
ibid, above although I'm planning on starting out with Server iron to run multiple development OS' with less equipment; it is kind of rediculous in my small space now with too much equipment and a painful electric bill.
My plan is for using a Dell PowerEdge server with 8GB of RAM and a three to five 250GB RAID5 drive configuration.
I have licensing for VMWare Server in the Win32 environment but I don't want to shell out for or lose resources to a WinX host OS.

---

### Post by gb64 on 2007-11-25
My Sony has 1.5GB Ram, and I have run many times a VMware VM  XPsp2 with assigned 768MB using full VS Studio 2005 Pro along with DDK and SDK. Do not notice any problems with compiling speed.

---

