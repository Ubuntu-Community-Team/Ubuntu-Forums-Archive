---
title: "Desktop Virtualization for CAD/Science/Engineering Applications"
date: 2009-03-31
forum: Virtualisation
---

### Post by azredwing on 2009-03-31
Hi all,

**The rationale for this post**: I've looked everywhere for performance data pertaining to various virtualization packages but I haven't found any. I figured I'd post this so someone out there who has the same questions I do can find some empirical data/testimonial and waste more than a few hours creating, running, and testing on virtual machines. I hope this helps somebody, and I hope people will contribute to this effort.

**Background**: I am a student in aerospace and computer engineering, as as such I run quite a bit of CAD and other scientific software packages. I am running Linux as my only operating system, but there's a lot of software out there I use that is Windows only. In an attempt to not have a dedicated partition on my desktop for Windows (and to get the same design tools on my laptop), I turned to virtualization. 

I originally started with VMWare Workstation on the advice of my dad, who routinely uses this software for his work. I switched to VirtualBox for a very short time after switching to Jaunty. For the past few weeks I wondered if there was a performance gain or loss by using VBox, and all the data I could find was biased or non-existent. VBox vs VMware almost looks to me like emacs vs vi.

To that end, I have successfully installed SolidWorks 2008 on both, and I would like to share my experiences with any other engineers out there who require Windows software for their work. I plan on testing other design programs for computer engineers as well, and as applicable compare them to a native Linux installation.

**What this thread is NOT:** I realize that VMWare Workstation is neither  _[gratis o libre]("http://en.wikipedia.org/wiki/Gratis_versus_Libre")_ (for the monolinguists out there, I mean it's neither free-speech-free nor free-beer-free.) This is NOT the place to debate the merits of the use of a non-free/proprietary license. My personal belief is that people should be able to do what they want, and if that means locking themselves into a proprietary license, so be it, it's his choice. I will not respond to any post about using a non-free license, and I request that mods please help keep this thread clean and squelch any talk about this debate. Engineers and scientists, I'm sure, will mostly care about the performance of their software and not of their software license when doing their work. Thus, take it somewhere else. Thanks.

**CALLING ALL SCIENTISTS, MATHEMATICIANS, AND ENGINEERS**: There is a clear lack of data for the various virtualization packages out there that can directly apply to us. Most users only need something like iTunes and games, and maybe MS Office for those who aren't fans of OO.org. We need way more performance than that out of our machines. I'm sure you've felt as frustrated as I was trying to see if you could squeeze more juice out of your virtual installation, or maybe you're sick and tired of dual-booting to use a single CAD tool. Please contribute anything you've learned when it comes to your software tools, from benchmarks to testimonials. I realize that there's general data out there about the speed of various virtualization packages, but this data isn't comprehensive or specific enough to tell us what is good and what isn't.

**My specs**:
Intel Core2Quad 2.4GHz (x64)
4GB RAM (not sure of speed)
nVidia GeForce 8600GS, dual-headed
eVGA 122-CK-NF68

**My WinXP virtualization environment**:

I always do the following things, first thing after installing a new VM. You can take to the bank that these optimizations are constant throughout each VM I use. I suggest checking out Jeff Atwood's post at [Coding Horror]("http://www.codinghorror.com/blog/archives/000639.html") for more details. I base all my optimizations on this post.
[LIST]
[*]Install guest additions/VMWare Tools/guest helper
[*]Update OS
[*]Disable Windows Firewall, antivirus warnings
[*]Disable system restore
[*]Disable page file
[*]Use XPlite to remove unnecessary software
[*]Defrag, zero, shrink hard drive
[/LIST]

Aside from these optimizations, the only things I keep installed on each VM is CAD/design tools. I will assume each software package is independent from another (i.e., installations not conflicting for some reason) unless I suspect otherwise. I also defrag/zero/shrink the HD after a major installation, e.g., I add a new package.

**Future plans**: I plan on testing AutoCAD 2009, ANSYS, and maybe some computer-aided logic design tools as my education continues. I have no idea what software packages I will be running on my own computers vs. the labs at school, so I need your help in making this thread successful.

**On to the results!**: The data below will become more exhaustive in time, and of course I need your help to aggregate data. There isn't much here now, but as my schooling goes on and I learn how to use more design software, I will continue updating this thread.

**_Solidworks 2008_**:

_VMWare Workstation_: [COLOR="SeaGreen"]**RECOMMENDED**[/COLOR] (WinXP+SP3, 1GB RAM allotted).

I have had very good experiences with VMWare for Solidworks. Solidworks uses OpenGL for 3D rendering, and my graphics card is fully taken advantage of. The rendering is excellent, and I see no difference between my virtual environment and a native Windows environment. Moving in the SW environment, mating, sketching, etc are all fast and with no artifacts. Some may see a performance hit with doing a finite-element analysis (e.g., CosmosXpress or Cosmos Full). I have not done complex finite-element analysis on any parts or assemblies yet, so I cannot comment as to the speed of that vs. native.

Note that my laptop can also run SW08 no problem, but it does not have an OpenGL-capable card, and so 3D visualization must be rendered by the VM itself. My laptop has no issues running SW, and again performance is akin to native.

_VirtualBox_: [COLOR="Red"]**NOT RECOMMENDED**[/COLOR] (WinXP+SP3, 1GB RAM, 64MB Video RAM)
I tried this out for the first time today, and I was very excited to see it install and get to the main environment okay. Sadly, that's where it ended. With 3D acceleration enabled, I can look at a rendered part, but that's about as far as it goes. Trying to move or rotate the part (actually, the mouse) immediately causes a rendering failure. The user is treated to the Welcome-To-Solidworks background if he moves the mouse; the part completely disappears, save for the single plane which the mouse is currently hovering on.

Turning off 3D acceleration makes it a little better. Now you can at least move the mouse. However, rotating a part or assembly causes the entire part to get "blocky"; e.g., cylinders are rendered as rectangular solids, circles are rendered as squares, texturing disappears, etc. I'll take a screen shot when I get a chance.

Also, SW was hopeless to even get into - usually (but not always!) it would crash the first time I go to run it, and it would crash upon exit of the program. I didn't even try to run a finite-element analysis. I could never see/move the part to find the point of loading I wanted.

**_Xilinx ISE/WebISE_**

_Native Linux:_ [B][color="seagreen"] RECOMMENDED (with caveats)[/color]
[/B]
Installing the ISE is an [_absolute pain in the ***_]("http://ubuntuforums.org/showthread.php?t=559245&page=2"), but once installed runs nicely - sometimes. I never got ISE 9.2i to work; after finally installing it, I could never run waveform simulations due to a C++ compilation error. Apparently ISE 9.2i expects an obsolete C++ package to run the simulator, but these packages were outdated by the time Gutsy came around. I had no luck getting 9.2i working as anything more than a glorified Verilog IDE.

10.1i is better. Still a pain in the *** to install, but simulations are run much faster than in Windows, thanks to the gcc compiler (as opposed to Borland on Windows). HOWEVER, suppliers like Digilent sell Windows-only dongles and interface software to their FPGA/CPLD boards for design synthesis. This software fits really well with ISE in Windows, but I have yet to see anyone on a consistent basis make their Linux ISE actually implement a design onto an FPGA.

So, run Linux ISE for simulation and synthesis, but use Windows ISE to actually get that synthesis onto an FPGA/CPLD.
           
_VMware Workstation_: [COLOR="Magenta"]**Okay/Not really tested**[/COLOR]

Installing ISE into a Windows environment is WAY EASIER than into a Linux environment. Way too much configuration in Linux that you have to deal with after installation that just doesn't exist in Windows, and the end result of all that configuration is the same design environment as you'd get in Windows. Eh, take the good with the bad I suppose. Nothing is perfect.

As I stated above, the compiler is slower when synthesizing/simulating. To be honest, I've really either run ISE in either native Linux or in native Windows in the lab; I've never had to run this in a virtual machine. 

I have not tested connectivity issues using a Digilent board. Again, never had to with a native Windows box at school.

---

### Post by freakalad on 2009-04-04
Well put together, thanks

Looking along similar lines.
My server spec very closely matches yours'.

Gone through the whole rigmarole of deciding on a VM environment: VMWare is good but not FOSS (insert own rationale here...), VirtualBox is a bit lightweight, ProxMox won't install (deb+KVM), XenSource is paravirt, so would require custom kernels which may not have 3D support

KVM is the VM platform of choice of Ubuntu & RedHat, so future growth & support should be good. Also able to make use of physical partitions for clients, similar to VMWare Workstation.
Since it's a visualization environment, I can run standard clients OS's, but this comes at a performance sacrifice.

The VMGL project, which provided OpenGL capabilities to VM environments, seems to have tapered out, so that looks like a dead-end.

Interested in high-end gaming, media center & video editing from VM clients (dual-booting is not far from ideal), but without 3D Hardware Acceleration (OpenGL), this is going to be EXTREMELY hard.

To address the performance issue:
* multi-core 64-bit Intel CPU's with VT support
* LOTS of RAM. The more the merrier
* consider placing VM clients on LVM partitions on separate physical disk from OS, to reduce read/write latency. Possibly RAID.

Please post more info on High-Performance 3D in VM's as you make progress. 
At the moment I'm pretty stumped....

thanks

- J

---

