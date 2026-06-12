---
title: "Virtualizing windows to play games"
date: 2009-02-14
forum: Virtualisation
---

### Post by hatten on 2009-02-14
Hey, i thought of virtualizing my windows partition to not need to reboot when i wanna play games, and i wonder if my specs can handle it. The games I'm mainly gonna play is Heroes of might and magic 3 complete edition, Civilization 3 Play the world, EuropeMaplestory and maybe some more.
If that doesn't work is it very hard to get heroes/civilization working with wine? (i know maplestory doesn't work cause of gameguard)
My specs can be found in my signature. It's basically a Dell Dimension 4600 with 512 MB RAM. I'm thinking of upgrading my RAM to around 2 GB.

---

### Post by dcstar on 2009-02-15
> **hatten said:**
> Hey, i thought of virtualizing my windows partition to not need to reboot when i wanna play games, and i wonder if my specs can handle it. The games I'm mainly gonna play is Heroes of might and magic 3 complete edition, Civilization 3 Play the world, EuropeMaplestory and maybe some more.
If that doesn't work is it very hard to get heroes/civilization working with wine? (i know maplestory doesn't work cause of gameguard)
My specs can be found in my signature. It's basically a Dell Dimension 4600 with 512 MB RAM. I'm thinking of upgrading my RAM to around 2 GB.

If you want VM 3D video then you will need a VM that supports that sort of thing - I know VMware server doesn't (1.x, at least) but I believe VMWare Workstation does.

VMware has a free downloadable utility to convert an existing Windows installation into a VM, so you don't need to reinstall stuff (very handy...)

You will need more RAM, 2GB should be enough.

---

### Post by hatten on 2009-02-15
But you gotta pay for workstation, right?

---

### Post by MasterNetra on 2009-02-15
I agree 1.5-2 GB at least because remember ya still need to reserve 512 for Ubuntu. And you will probably want more then 256-512 of ram used for the windows + gaming.

---

### Post by Cybie257 on 2009-02-15
> **hatten said:**
> But you gotta pay for workstation, right?

If you're just going to virtualize your existing windows install, download Workstation (This has an IMPORT option to virtualize an existing machine, much like the converter utility tool spoken of in an earlier reply) and do so as it comes with a 15 or 30 day trial. Also, download the VMWare player for Linux. VMWare Player is free and works great running windows inside of Linux. Currently, I run 2 Windows 2003 server editions in VMWare Player on a Linux box with 2 Gigs of Ram at work. Since they do not require a lot of resources, they run fine setting them both up with 512MB ram.

My suggestion, since Workstation is a timed trial, be sure to set all your settings up just as you would want them (Virtual hardware). Not much that you can change with VMWare player. Also, be sure you just let it default to your current hard drive capacity. It will grow as needed and only take up the actual space used for data.

IE: if you have a 500GB drive that your XP is on and only 100GB is used, then only that 100GB will be needed, but there will be 400GB of space that can be used. Be sure to select the grow option, not the (can't think of the name, sorry) but the option that pre-formats the entire size. 

Also, when downloading the VMWare workstation, get the one for Windows, as the Linux version does NOT support the Live Virtualization method. Only the windows will let you virtualize a live computer, which works great.

MS Activation Note: You might get stuck with that annoying M$ activation crap, so as soon as you take care of that, and have it up and running in VMWare player to your liking, I suggest backing up the virtual machine (zipping it up) and storing it somewhere. That way, you don't need to go through all the painful mess if you ever need to start over if you blow up your windows with installing things. :)

It's late, and I hope I was able to give you some insight and help. I have a lot of experience playing with VMWare workstation, both on Linux and Windows (hosting and server modes). I will do my best to keep up with this thread if you need further help, but as a full time worker and almost full-time student, time is tough...

-Cybie257

EDITED this as I noticed earlier reply about the import utility tool. I have used that with success. Workstation just gives you the freedom to reconfigure hardware settings to get them exactly where you want them to be. (Ability to tweak the settings)

---

### Post by Cybie257 on 2009-02-15
I just thought I would add this as a separate note...

Virtualization is not the best method for anything that needs high-speed graphics. IE:Games, 3D modeling, etc.  Although, it does work fairly well, don't expect a lot of performance compared to a standalone computer. I've had success running full screen video and movies wih only slight noticeable reduction in quality, but no 3d-gaming experience as of yet to report on.

Some other things to note:

1. Be sure to save, or copy, the Virtual machine to an EXT2/EXT3 Native partition. This will run faster than if you installed it on an NTFS partition. 

2. Give the machine as much RAM as possible, but try not to exceed 50% of your physical system RAM. 

3. Install the VMWare tools (if they weren't installed at boot up. This installs virtual hardware drivers and will help overall speed and performance.

4. Make sure your network card (Virtual) is not set to NAT. Use the Host configuration. (I will edit this post for exact name). This way yourVM will acquire it own IP Address just like it was a different computer to avoid any network issues. 

Again, VMWare player doesn't allow you to change much of the settings. Only Workstation will allow that. That is why I am trying to cover as much as possible.

Hope this helps. 

-Cybie

---

### Post by binbash on 2009-02-16
Maplestory works with virtualbox but i didn't try the others

---

### Post by darco on 2009-02-16
> **Cybie257 said:**
> 

Some other things to note:

1. Be sure to save, or copy, the Virtual machine to an EXT2/EXT3 Native partition. This will run faster than if you installed it on an NTFS partition. 

-Cybie

Hmm, never heard of this tip. I have heard about moving the .vmx file to a separate hdd to lessen hdd activity on the main disc.

darco

---

