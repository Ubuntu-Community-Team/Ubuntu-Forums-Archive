---
title: "Windows 10 VM Question"
date: 2017-04-17
forum: Virtualisation
---

### Post by jamie10001 on 2017-04-17
I currently run a dual boot setup with Windows 10 and Lubuntu on a fairly old Acer laptop. I was wondering if I could go full Lubuntu with Win 10 on a VM and still retain access to the things I need (Excel / Powerpoint) in windows and work round other stuff.


My current setup is below, and below that my thoughts on how to do it. 


**Current setup:**


Fairly old Acer Aspire laptop (Core i3)
8 GB Ram / 320 Gb hard disk


**Windows 10 - 200 GB**
        Documents: 24 Gb
        Music:  86 Gb
        Photos: 19 Gb
        Video: 38 Gb
Total: 167 Gb


**Disk Partitions:**
sda1- ntfs : 12 Gb (Laptop Windows recovery partition)
sda2- ntfs : boot
sda3- ntfs : 250 Gb (Windows 10 file system)
sda4- extended: 30 Gb (Lubuntu)
sda5- ext4: 23 Gb
sda6- linux swap: 7 Gb


**Uses: **
Windows 10 - Storage of photos / music / docs / videos
I use Google Photos / Google Music Manager to cloud store my music, photos, videos. 


Also use Google Drive. 


On the windows system I also use excel (fairly heavy VB user) and power point, but not much else. 


**Lubuntu: **
I use lubuntu for mostly everything except excel and powerpoint, I cant switch completely to Gnumeric / Impress as I need full compatibility for work related stuff. 


Must haves: 
Google Music Sync
Access to Excel / Powerpoint
Access to windows Documents. 
Google Photos sync. 


Everything else Lubuntu. 


**What I was wondering was the following setup:**


Lubuntu on full disk. 
Win 10 in a VM with office installed for Excel Access / Power Point. 


I think I can get Google Music Manager on Linux
Google photos I could maybe find a work around


How easy would this be to implement and will I lose any functionality ? 


Thanks.

---

### Post by howefield on 2017-04-17
Thread moved to the "*Virtualisation*" forum.

---

### Post by KillerKelvUK on 2017-04-17
Hi, welcome to the forum!

So this sounds easy but then I've been doing this for years now so easy is relative to your experience with linux and virtualisation, are you confident in the space i.e. know about virtual box or kvm/qemu or similar?

Functionality wise I'd just call your attention to video performance of a virtual machine...you say you use your current Win10 install for "video"...if this is watching videos then the out-of-box graphics capabilities of a vm isn't really up to it however you may find it acceptable.  That said you could just as easily switch to using your lubuntu host to watch videos so problem solved if it was even a problem to begin with.

Another gotcha could possibly be your Windows license.  If the Acer laptop came with Windows pre-installed its an OEM installation, I'm no legal expert but theory is you can't alter/move that license.  That said as you're simply moving Windows to be a virtual install on the exact same hardware then its a grey area, however if you've done the free upgrade to Windows 10 your license entitlement is now locked to the hardware spec used at the point of upgrade which means you cannot install a new clean Windows 10 into a VM and get it to activate using the OEM key.  If you have a full retail copy of Windows you intend to use then this is a non-issue.

Things to research and clarify here...
[LIST=1]
[*]What virtualisation technology are you going to use e.g. Oracle Virtualbox, kvm/qemu, xen, etc.  There are pros and cons to each, whilst I've limited direct experience with Virtualbox my take on your requirements is that this should give you what you want without getting too complex to setup.  I use kvm/qemu as technically its a better hypervisor and has a broader range of features and performance options but is probably a little more complex to setup and get to grips with than Virtualbox.  Xen is then similar to kvm/qemu but there are other hypervisor options you could look at also...so hence the research.
[*]Storage and partitioning.  People underestimate the impact of storage and disk layouts and then find themselves in difficult positions down the line when they want to make changes.  If your requirements are solely for this one laptop with only ever the one virtual machine for Windows the the simpler the better so you could just crunch everything together i.e. lubuntu root, home, vm storage, all your media.  If you know more about linux then of course separate home out into a different partition etc as you like.  However if you intend to run more virtual machines and you wand to look at serving data out to other devices in your home network and its likely data will grow then as well as appropriate partitions for home and vm images you might want to consider using logical volumes (LVM) for both virtual machine images and maybe your media storage.  This will give you options down the line for extending storage e.g. just adding an external disk and growing the logical volume or even moving it entirely onto new block.
[/LIST]

Hope this doesn't put you off in any way, what you want to do is most certainly achievable but does require a little bit of technical finesse so if this is new to you then I'd say persevere and just keep posting here for any help you need.

---

### Post by smd3 on 2017-04-17
I use Windows 10 on VirtualBox, mostly for school and work. (I need to use MS Excel/Word, and access some government sites with a card-reader)  Before I switched to LInux, I ran WIndows 10 in Parallels on my Macbook Pro.

Virtualbox is pretty good, although not quite as solid as parallels. I get an unexplained hang every now and then when I use windows, it seems to occur more frequently when I've just booted up my Linux (host).

The installation of VirtualBox was very easy, I used the repositories for Ubuntu.  Once started up I booted the iso I downloaded from Microsoft.  (I had to purchase a WIndows Key)

If you have your old key you might be able to get them to re-authorize it.  I did this a couple times on my Mac when I switched from dual-boot to running in Parallels. Then, again when I changed my Parallels hardware configuration.

That leads me to the next point.  Setup your virtual machine the best you can the first time, making changes can trigger the Windows activation. (For example, allowing VirtualBox to use one processor, then going back and adding the second)

Parallels made printing pretty easy on the Windows virtual machine. I still haven't sorted this out on VirtualBOx.  Right now the network is configured like the host machine is the router. (This is the easiest to setup).  I think I need to set it up so that the Windows virtual machine accesses my network more natively, and get my router to assign it an address like it's a separate computer.

No issues that I can think of, other than that, it works really well!

---

### Post by Bucky Ball on 2017-04-18
I've run WinXP on Virtualbox. Win7, Win8.1. All fine. Recently made a Win10 virtual machine and it is total rubbish. Works, but so slow and sluggish just not worth the effort. Back to Win7 or XP. 

I am using an i3 machine with half your RAM, 4Gb, but maybe you're experience will be better with Win10 in Virtualbox.

---

### Post by sp40140 on 2017-04-18
When you say "fairly old" how old? you have i3 (which generation), which is already low end dual core cpu. Windows is already resource hungry as it is. So, your VM will run very slow. And if you use VB heavy excel sheets, you will need lots of resources. Also, acer makes consumer class laptops, which don't play nice with power use (specially issues related to heat management).
So, I suggest that you only use VM set-up if you use excel and powerporint very rarely or you will be frustrated with vm performance.
Your RAM and HDD are adequate.

---

### Post by smd3 on 2017-04-18
> **Bucky Ball said:**
> I've run WinXP on Virtualbox. Win7, Win8.1. All fine. Recently made a Win10 virtual machine and it is total rubbish. Works, but so slow and sluggish just not worth the effort. Back to Win7 or XP. 

I am using an i3 machine with half your RAM, 4Gb, but maybe you're experience will be better with Win10 in Virtualbox.

I'm using a new i7 with one "core" (so one virtual core) allocated to the VM, and 3gb ram.  It runs windows 10 fine.  I wish I'd set it to two cores, so it would use one physical core.  Changing it now means dealing with Windows activation, I'm sure.

---

### Post by Bucky Ball on 2017-04-19
> **smd3 said:**
> I wish I'd set it to two cores, so it would use one physical core.  Changing it now means dealing with Windows activation, I'm sure.

Why not close the virtual machine and change the amount of cores in 'Settings' and find out? Can't see how that has anything to do with Win activation. :-k

---

### Post by &amp;KyT$0P# on 2017-04-19
Make sure you shut down the VM and create a snapshot of it **before** experimenting.  Then you can just restore the snapshot if it doesn't work out.

---

