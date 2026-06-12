---
title: "Virtualbox vs WINE vs Dual Boot"
date: 2008-10-07
forum: Virtualisation
---

### Post by jbuczek on 2008-10-07
I've read a bunch of help, man, blog and forum opinions about the problem of dealing with the last few Win apps after finding the light..... er.... penguin... and converting to ubuntu.  I'd like to summarize my findings for "peer review in case I've gotten off track.  I'll add that as much fun as it can be to play with your system all day long, I have work to do and I can't spend my life tweaking a bunch of system software to work properly.

Programs I still need to use under WinXP: Quicken 2006, TurboCAD V15, TreePad Biz, ABC Amber text format converters.  Apparently TreePad and ABC will work under WINE.  Quicken and TurboCAD will not.  I've looked at all the (free) native linux replacements for Quicken that I can find but I have decades of data using multiple currencies and none of them will import the data correctly at this time.

My computer is a dual core 2.6 Mhz Pentium with 1 GB RAM and a total of 380 GB HDD.

My conclusions are:

Dual boot gives me the best performance but every other usability factor is negative and getting out of the MS lockup is the reason for linux in the first place.

WINE eliminates the need for a MS license, requires less overhead generally and takes only the resources it actually needs.  If I use it for the things that work and use VB for the things that don't it increases the overhead if I need to have both going at the same time for another app.  I suppose I could run the same app under the VM if it's on or under WINE if not but..........jeez.

VirtualBox takes half my RAM and CPU resources even if it's doing nothing but as far a I know neither these apps nor anything I'm likely to use under Ubuntu are multi-threaded so the loss may not be all that great. 

So...... it looks like VirtualBox is the obvious choice.  Any disagreement?

Given that, anybody know a site where I can get guidelines for stripping WinXP down to the minimal RAM/CPU footprint?  I"m even thinking about trying Win2K in the VM to completely bypass MS's licensing checks.

Thanx

---

### Post by rzrgenesys187 on 2008-10-07
Maybe something is wrong with your Virtualbox installation, but when I have it idling it only uses about 1.5~2% of my cpu and 512mb of RAM (it does take a little inactivity to get to this point, however), but that is set by the system.  I was using Office last night while tarring about 5GB of files and didn't notice any significant lag.  My computer is a mid-range laptop so nothing really powerful.  Overall it works much better for me than dual booting since I don't have to reboot to use one application.  Wine works for the majority of what I use but sadly MS Office is something I can't get around using for school.

---

### Post by iansane on 2008-10-08
Another stick of ram would definately help the vbox. I have similar processor and 2 gigs ram and it runs window vm's ok. One thing I found is that XP sp1 with no av and no updates runs great. Then as I need to install programs if they require sp2 or a newer version of .net framework I install it and it gets slower and slower cause all these updates cause more background services to connect to the internet.

Try running wireshark on the host and watch as the XP virtual machine boots up. There's more there than just getting an IP from the router.

---

### Post by bpalone on 2008-10-08
I use Win2K for the very reason you recite.  I have not ever really cared for XP, I just tolerated it on my laptop.  Now, I have a dual boot laptop and desktop, and one linux only desktop.  All have VirtualBox installed with Win2K as the guest.  I find that most of my apps work at about normal speeds within the Virtual machine.  I store my files on the Native Windows Disk, and that slows things just a bit but is tolerable.

Here is a suggestion. Might want to set up your printer(s) as network printer(s), that way it is easy to get your full Windows print functionality from your VM.  That way, either system can access the printer(s) while both are running.

I did have an issue with QuickBooks not liking my files being outside of the Virtual Disk.  So, I placed them there and make a point to copy a backup out to the native disk before quitting. 

If you have the disk space, I would keep a dualboot system along with the VirtualBox.  That way, if you have some heavy duty work that the program just seems to work better in a native environment, you have the option to go that route.

All of this is worth just exactly what you paid for it.

---

### Post by tjwoosta on 2008-10-08
if you are not planning on running any graphics intensive applications ,like video games, then the virtualbox should do the job 

i set my virtualbox to use only 256mb ram and it runs windows xp fine

if you are planning on running games then your best bet would be a dual-boot

---

### Post by bumanie on 2008-10-08
Virtualbox is a good choice. By the way, I believe that GNU cash is compatible with quicken - may be worth looking into.

---

### Post by Znupi on 2008-10-27
I use VirtualBox to run a WinXP vm from time to time. I do this mainly because I have to use Paint.NET which wine can't run and mono-paint doesn't really work. Also, I'm a web designer so I need to test websites in IE7, and using VirtualBox it's a breeze.
I have a dual core 2.8Ghz Pentium with 512MB of RAM. The virtual machine works relatively decent with only 512RAM (I give it 128 ram and 128 video), but Ubuntu is quite slow while the machine is running. But, I have a suspicion this is mostly because of HDD access (I'm not sure what kind of hard disk I have, but I think it's pretty slow - when moving files around I only get 3-4MB/s). Try getting a separate hard disk (a really small one, like 20GB) and put the virtual hard disk on that (it has been recommended to me, but I can't buy another hard disk right now), it should significantly increase the quality of the virtual experience :)
Personally, I find VirtualBox great, it's really easy to setup and use. You can get it installed (from the repos) and get a virtual machine running in under 5 minutes (most of which is download time of the packages :P)
Have fun :)

---

### Post by bodhi.zazen on 2008-10-27
Wine / Virtualbox / VMWare / KVM ~ Each has advantages and disadvantages, choose the tool that works best for you. Other then that, opinions may vary.

---

### Post by Tichondrius on 2008-10-27
> **jbuczek said:**
> I've read a bunch of help, man, blog and forum opinions about the problem of dealing with the last few Win apps after finding the light..... er.... penguin... and converting to ubuntu.  I'd like to summarize my findings for "peer review in case I've gotten off track.  I'll add that as much fun as it can be to play with your system all day long, I have work to do and I can't spend my life tweaking a bunch of system software to work properly.

Programs I still need to use under WinXP: Quicken 2006, TurboCAD V15, TreePad Biz, ABC Amber text format converters.  Apparently TreePad and ABC will work under WINE.  Quicken and TurboCAD will not.  I've looked at all the (free) native linux replacements for Quicken that I can find but I have decades of data using multiple currencies and none of them will import the data correctly at this time.

My computer is a dual core 2.6 Mhz Pentium with 1 GB RAM and a total of 380 GB HDD.

My conclusions are:

Dual boot gives me the best performance but every other usability factor is negative and getting out of the MS lockup is the reason for linux in the first place.

WINE eliminates the need for a MS license, requires less overhead generally and takes only the resources it actually needs.  If I use it for the things that work and use VB for the things that don't it increases the overhead if I need to have both going at the same time for another app.  I suppose I could run the same app under the VM if it's on or under WINE if not but..........jeez.

VirtualBox takes half my RAM and CPU resources even if it's doing nothing but as far a I know neither these apps nor anything I'm likely to use under Ubuntu are multi-threaded so the loss may not be all that great. 

So...... it looks like VirtualBox is the obvious choice.  Any disagreement?

Given that, anybody know a site where I can get guidelines for stripping WinXP down to the minimal RAM/CPU footprint?  I"m even thinking about trying Win2K in the VM to completely bypass MS's licensing checks.

Thanx

hahahaha, good one

VirtualBox does not take any more ram than the what the guest OS needs). This means it doesn't even necessarily take all the memory allocated to it, unless the guest is actually using that memory. Also it doesn't use any CPU cycles if the guest is idling. Also you can actually pause the virtual machine if you're not using it, so then it takes zero resources.

BTW, You still need a windows license to run inside a virtualbox.

BTW (2), windows still has more applications support and hardware compatibility than Linux. And it has a huge advantage as a gaming platform. So that's why the best way is to run Vista host (for DirectX 10 games, google Chrome, windows apps) and Linux guest for everything else. That works great and the guests (I'm actually running two Linux VMs under Vista) don't take any resources while idling or suspended.

BTW (3), dual boot is gone, it's totally passe, as it doesn't give the same functionality as running different OSes simultaneously.

So put that in your research.

---

