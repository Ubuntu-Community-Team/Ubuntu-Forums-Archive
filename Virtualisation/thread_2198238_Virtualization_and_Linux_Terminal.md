---
title: "Virtualization and Linux Terminal"
date: 2014-01-07
forum: Virtualisation
---

### Post by FreeFog on 2014-01-07
[SIZE=3]Intro[/SIZE]
I'm new to virtualization, been reading about Xen, KMV, QEMU, VirtualBox, VMWare and others.  
I still don't know which to implement or how, thus the post.  
Thanks for your time.


[SIZE=3]What I want to do[/SIZE]
One physical PC running Kubuntu: in one terminal the KDE environment and in the other a virtual machine running Windows 7 64bits. By Linux terminal I mean the text interface you find when pressing CTRL + ALT + Fx, and lets you log-in in parallel.  

I'm trying to balance having two graphical environments against having everything on the same terminal being affected if a crash occurs in either the KDE environment or the virtual PC. This idea, I believe, would also allow me to run the virtual computer while having KDE shutdown.


[SIZE=3]Questions[/SIZE]
**Q1 **- Which virtual software do you recommend?.  
 **Q1a **- Source of reading material to achieve what I describe?.  

**Q2 **- How does the virtual machine will be rendered, what toll would have in the host computer?.  
 **Q2a **- Is there a way to reduce it, share a resource?.

**Q3 **- I been reading about Linux screen command, is managing screens the right way to do it?. <http://ss64.com/bash/screen.html>  

**Q4 **- Do you have a better approach?.  

**Q5 **- Recommendations?.


[SIZE=3]Added Requests[/SIZE]
**AR1** - Prevent the virtual machine from blocking keys that would allow switching between Linux terminals or assign new keys to the function.  
**AR2** - Automatically run the virtual machine in the extra terminal at start up.  
**AR3** - Set up key strokes, bootloader in such a way that the PC would start in one of the graphical environments, i.e. if I hold down Shif + F7 while booting KDE is not started and the focus changes to the terminal hosting the virtual Windows PC or vice versa.  
**AR4** - Have the the virtual images synced to a cloud. Any service in particular?.  
**AR5** - Attach an Android device to another terminal.  


**Again Thanks For Your Time.**

---

### Post by TheFu on 2014-01-07
When just starting out with VMs keeping it simple is important.

Pick the HostOS for which ever OS needs to most graphics capability. For most normal people, that would be MS-Windows.  Then load up Oracle's VirtualBox.  That will be where you install, start and control virtual machines. Since Windows is the host-OS, there isn't any need to have it inside any virtual machine.  If you select to install under Ubuntu as the HostOS, use the Oracle PPA, not the Ubuntu install repos.

Under virtualbox, setup the virtual machine hardware, then install whatever OS you like. There are many tutorials, youtube how-to videos and other helpful websites.  I'm partial to [this one]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox") with tips to get the best performance; I wrote it.  Don't just go with the defaults. It will turn out badly.

Forget the idea of terminals for now.  If you need a terminal, just use ssh.

Get some practical hands-on experience with virtualbox for now.  It is the easiest free way to get going for desktop users wanting to load another desktop OS ... like you.

I would never deploy a production server on virtualbox. NEVER.  However, for desktop-on-desktop needs like yours, it is perfect.  Sure, running a Linux server under Virtualbox is possible and good enough for developers, but NOT good enough for a 24/7/365 server.

KDE is just a GUI program.  There are 50 other similar GUI programs you can install on Ubuntu. Nothing special about it at all.  Just pick which one to be used at the login time. Of course, you'll need to install each that you want and you'll need to be careful about settings for 1 GUI trashing the settings for another.

AR1 - uh ... read the virtualbox manual for this. <cntl>-f is the normal key for this, but if you install the guest additions inside every clientOS, keyboard "capture" as it is called, doesn't happen.  The "capture" is a requirement if the guest additions are not installed.
AR2 - easily handled.
AR3 is more about dual booting.  Not relevant at all for virtualization needs.
AR4 - Virtual images are huge. Syncing to any cloud provider isn't a good idea for most people.  There are more efficient ways to save only the data necessary to recreate a Linux install - these methods will save 2G-6G under ubuntu.
AR5 - Android doesn't "attach" to any terminal. It needs an OS and will use either an MTP or USB-storage protocol to work. I suppose you could connect the android device to a BT keyboard and use the HDMI output to connect to a monitor ... It doesn't really work as well as people think. The touch part of android really is key and no mouse can replace that, IMHO.

Get going and have some fun!  You'll have many more questions - good news - the manuals for virtualbox are great!

With everything on Linux, there are 100+ ways to accomplish the same things. Above are what I think is the easiest way to get started.

---

### Post by FreeFog on 2014-01-07
Excuse me thought my needs aren't developed in the thread, I tried to keep it as compact as possible and for that I expressed it in "What I want to do".
I have some translation software suits that can only run on Windows, by experience installing more than one version of it in a machine results in problems, my idea was to create some non-modifiable images containing Windows 7 and the translation suit, one Windows image per Suit. I have no problem and love Linux.
I will check your tutorial but still your answer is out of scope, thanks for your reply.

---

### Post by TheFu on 2014-01-07
Sorry.  I saw 2 posts for your forum id and made some assumptions.
Then I saw 
> Q4 - Do you have a better approach?.
Q5 - Recommendations?.
and took my lead to provide "a better approach" followed by "recommendations."

I'm sorry.

If the windows translation software uses a microphone, it is much easier if that interface happens through Windows, IHMO.  I say this as someone with 20+ Linux installs at home and 2 MS-Windows.  I run Windows under a KVM VM, but that is non-trivial and doesn't provide very good performance or extra interfaces beyond keyboard, video, mouse.

I was NOT just recommending what works, rather, I was recommending what I thought would work best for most users new to virtualization.  If you don't want to run Windows as the hostOS - fine.  The link still has the settings needed to get Linux working well under **any** VM with the most important performance issues that are hard to fix later spelled out. 

I am sorry if you were/are offended by my answers.  I love Linux too. ;)

---

### Post by 1clue on 2014-01-07
> **FreeFog said:**
> [SIZE=3]Intro[/SIZE]
I'm new to virtualization, been reading about Xen, KMV, QEMU, VirtualBox, VMWare and others.  
I still don't know which to implement or how, thus the post.  
Thanks for your time.


We don't have enough information.  Do you intend the VMs to start when the computer boots, or only on demand?

VirtualBox is like VMware Player, you run it on demand.  It's the easiest thing to set up out of your list, but kvm/qemu lets your VMs start during your host system boot, and shut down when your host shuts down.

> 
[SIZE=3]What I want to do[/SIZE]
One physical PC running Kubuntu: in one terminal the KDE environment and in the other a virtual machine running Windows 7 64bits. By Linux terminal I mean the text interface you find when pressing CTRL + ALT + Fx, and lets you log-in in parallel.  

I'm trying to balance having two graphical environments against having everything on the same terminal being affected if a crash occurs in either the KDE environment or the virtual PC. This idea, I believe, would also allow me to run the virtual computer while having KDE shutdown.


You are confusing Virtual Terminals with Virtual Machines.  You need to get this straight:
A real terminal was a keyboard and monitor (VT100, VT220, 5250, 3270, etc) which was hooked to multi-user computers back when I was younger, and most of the folks on this forum probably weren't born yet.

A virtual terminal is a software application which acts like a real terminal.  That's what you have on your Ubuntu box, and pretty much any Linux box.  Linux/Ubuntu is a multiuser, multitasking operating system.  Each of your virtual terminals (ctrl-alt-Fx) is hooked to your host operating system.  Each Linux-based guest VM will ALSO have those.

Your guests will be accessed as though they were separate machines on the network.  That's the point to virtual machines.  Usually, the only way you get to them is on the network in my environment, the VM host is headless -- has no keyboard, mouse or monitor attached -- and has no GUI on it at all.  The host only needs enough to make the system work, and the virtualization software.  Most KVM/QEMU tutorials for Ubuntu seem to use Ubuntu Server as the host.

To access a Windows guest, you'd probably use remote desktop software.  To access a Linux guest, you'd use any number of things, I use ssh -X <vm-guest-ip-address>.  You can also use X across the network directly, although that's not as secure.

You can also use a GUI client in KVM/qemu such as virt-manager, and that gives you a VNC-style 'console'.  You can do this on your desktop system or laptop too, although most examples aren't really clear on that.

> 
[SIZE=3]Questions[/SIZE]
**Q1 **- Which virtual software do you recommend?.  
 **Q1a **- Source of reading material to achieve what I describe?.  


This depends completely on your answer to the question about when they boot and how they run.  I use KVM/Qemu because my VMs start when the system boots, and my VMs aren't all on hardware that has a screen. I would start at [http://qemu.org](http://qemu.org) and plan on using virt-manager with it so you have a GUI tool to manage your VMs.  

> 
**Q2 **- How does the virtual machine will be rendered, what toll would have in the host computer?.  
 **Q2a **- Is there a way to reduce it, share a resource?.


Most of the consoles built into virtualization software use VNC for gui systems as far as I can tell.  If you just need a command line, then use ssh.

VMs are not the best at graphically intensive software, even if you're running with your workstation as a host.  Whatever you're using to run games, that should be the host.  If you're using Windows as a host, then KVM/QEMU are out of the question.

If your hardware supports virtualization directly you can donate hardware to a VM, at which point it would run at very close to native speed.  You need support in your CPU (almost all CPUs support it now) and in your motherboard (some don't) and possibly in your devices, but probably your desktop setup doesn't have those devices.  Hardware support for virtualization in the device means the device knows about virtualization and has some way of partitioning parts of that hardware for a different VM.

> 
**Q3 **- I been reading about Linux screen command, is managing screens the right way to do it?. <http://ss64.com/bash/screen.html>  


Screen is a really good command to know, but it has pretty much nothing to do with virtualization.  What it's good for is when you ssh to some other box, and want a bunch of command lines to different places doing different things, and you want your entire session to stay there when you disconnect.  I use it all the time.

You could (I do) use screen on your VMs.

> 
**Q4 **- Do you have a better approach?.  

**Q5 **- Recommendations?.


You're over-thinking this.  The first thing you should do is use VirtualBox to install a VM, and play with it.  You might keep it, but expect that you might have to throw it away and start over.  It's not a big deal to do this.

KVM/Qemu isn't much more complicated than VirtualBox.  It's all pretty easy.  You're confused right now because you haven't tried it yet.  Once you do, it will become much more clear.

> 
[SIZE=3]Added Requests[/SIZE]
**AR1** - Prevent the virtual machine from blocking keys that would allow switching between Linux terminals or assign new keys to the function.  
**AR2** - Automatically run the virtual machine in the extra terminal at start up.  
**AR3** - Set up key strokes, bootloader in such a way that the PC would start in one of the graphical environments, i.e. if I hold down Shif + F7 while booting KDE is not started and the focus changes to the terminal hosting the virtual Windows PC or vice versa.  
**AR4** - Have the the virtual images synced to a cloud. Any service in particular?.  
**AR5** - Attach an Android device to another terminal.  


**Again Thanks For Your Time.**

Your added requests need to wait until you've made a couple VMs.  You're WAY over-thinking this for a beginner.  The good thing about VMs is you can delete them and start over without a second thought.  Well, you have to have second thoughts about your Windows bits because that's a license and you have to pay for it.

Start with something, create a Linux VM which is NOT the same exact thing your host uses, and play with it.  Just create it and follow the instructions on the screen, and if you mess up royally nobody cares.  It takes me 5 minutes to set up Ubuntu Server.

---

### Post by CharlesA on 2014-01-07
> **1clue said:**
> Your added requests need to wait until you've made a couple VMs.  You're WAY over-thinking this for a beginner.  The good thing about VMs is you can delete them and start over without a second thought.  Well, you have to have second thoughts about your Windows bits because that's a license and you have to pay for it.

Agreed. It's not really a bad thing, but it will just lead to more questions than answers at this point.

> Start with something, create a Linux VM which is NOT the same exact thing your host uses, and play with it.  Just create it and follow the instructions on the screen, and if you mess up royally nobody cares.  It takes me 5 minutes to set up Ubuntu Server.

I used (and still use) VirtualBox on both Windows and Linux. I've moved over to KVM/OpenVZ (Proxmox) for my main server, but I have stuck to using VirtualBox on the Windows and Linux desktop machines because it's mostly GUI based.

Note: The VMs I have running in VBox are "on demand" - anything that I want running 24/7 is created in either KVM or OpenVZ, depending on what it will be used for.

---

### Post by Bucky Ball on 2014-01-07
I'd say install VirtualBox and start exploring. You will probably answer some of your questions as to what's possible by experimenting to see if it is. ;)

VirtualBox is in the repos (install from Software Centre or Synaptics).

---

### Post by FreeFog on 2014-01-07
Not offended shoot ahead.

---

### Post by FreeFog on 2014-01-07
Most statements are answered in my main post if read as whole, specially the demand remark.
I could have not made such plan with out experimenting, I have used VMWare for many years, on its basics functions.
I understand virtualization is a vast galaxy of solutions, and on the contrary I aim for a simple one, but more importantly to a solution that has low upkeep.
So I make the following inquire:
**Q6** - Can I start KDE in one of Linux Terminals (I try not to use virtual wording to avoid confusion but yes I don't refer to an actual machine affix to a host or to a terminal emulator app like konsole) and a headless VirtualBox in another, so the order of events would be:
Automatically log in to terminal 1 and 2.
Start KDE in tty1.
Start VirtualBox in tty2.
Then access VirtualBox PC from KDE.

The previous answer I could most possibly obtain it by testing but it's carried by the next:
This time I would avoid rendering anything in the terminal running the Virtual Machine and since it's run separately:
**Q6a **- Could I use an Hypervisor or should I rely on VNC?.
**Q6b - **The translation software is not a heavy weight on graphics but having a decent render helps tremendously since specially reduces tiredness; as I noted before I'm only interested in this approach to avoid a crash from affecting the other slice (terminal) but if this will impair my vision I would just simply run it from within KDE, What do you assert best?, the translation software has a bad performance because I believe it over uses many resources, it has no complex UI and mutch of the CPU power is lost in the licensing verification; I have 6Gb of RAM at my disposal is using something like Xen, KVM / QEMU far more better?.

Thanks for your time.

---

### Post by CharlesA on 2014-01-07
> **FreeFog said:**
> Most statements are answered in my main post if read as whole, specially the demand remark.
I could have not made such plan with out experimenting, I have used VMWare for many years, on its basics functions.
I understand virtualization is a vast galaxy of solutions, and on the contrary I aim for a simple one, but more importantly to a solution that has low upkeep.
So I make the following inquire:
**Q6** - Can I start KDE in one of Linux Terminals (I try not to use virtual wording to avoid confusion but yes I don't refer to an actual machine affix to a host or to a terminal emulator app like konsole) and a headless VirtualBox in another, so the order of events would be:
Automatically log in to terminal 1 and 2.
Start KDE in tty1.
Start VirtualBox in tty2.
Then access VirtualBox PC from KDE.

Not possible as far as I know. You always have to access the VM from the desktop of whatever machine you are running it on. This includes if you are running it headless.

> The previous answer I could most possibly obtain it by testing but it's carried by the next:
This time I would avoid rendering anything in the terminal running the Virtual Machine and since it's run separately:
**Q6a **- Could I use an Hypervisor or should I rely on VNC?.
**Q6b - **The translation software is not a heavy weight on graphics but having a decent render helps tremendously since specially reduces tiredness; as I noted before I'm only interested in this approach to avoid a crash from affecting the other slice (terminal) but if this will impair my vision I would just simply run it from within KDE, What do you assert best?, the translation software has a bad performance because I believe it over uses many resources, it has no complex UI and mutch of the CPU power is lost in the licensing verification; I have 6Gb of RAM at my disposal is using something like Xen, KVM / QEMU far more better?

Are you asking if using the VM software's "console" verses using VNC to access the guest is a good idea or not? I try not to use VNC, so if I need GUI access to a VM, I use NX or SSH. You would still need to access them from within the desktop environment, so no using tty1 or tty2 for each VM.

KVM is built into the Linux kernel, so that might be worth considering but if you want ease of use, go with VirtualBox. Virt-manager for KVM is easy to use, but VirtualBox might be even easier.

---

### Post by 1clue on 2014-01-08
If you're fixated on a console-like session, then you can start your VM and then start a second X session :1 and attach it to a console.  That X session would need to attach itself to your VM.  It would be a  TCP-based console same as if you had a remote X-enabled system and a local headless X server to connect to it.  I really can't think what that would get you, you could do the same thing with Xnest and have it be a window in your existing local session.

I don't particularly care for VNC, so I don't use it.  For most of my Linux installs, it's command-line only.  For the ones that aren't I usually ssh -X and run my app.  For Windows VMs I use rdesktop.

---

### Post by TheFu on 2014-01-08
It is possible to automatically start virtualbox VMs on either Windows or Linux or other hosts. These can be with or without an active window being displayed. There is a CLI setting and using the normal Linux init methods for startup works.  It is most common to point-n-click to start a VM, however.

Using the term "terminal" is confusing to us here and inaccurate to what will be the end result. Perhaps "window" is a better description? I dunno.

It is possible to access any VM over the network using any normal network access method (vnc, ssh, nx, whatever), assuming you setup the networking and run the service "INSIDE the client VM" correctly for that.  Go with **bridged** networking and all is easy. The VMs appear just like any other install on the LAN.  Until you play with the networking choices yourself, it won't be clear how they work.

I think something like this is what you intend:
```
hostOS (Linux)
    |____KDE-VM
    |____Win7-A
    |____Win7-B
    |____Win7-Z
```

---

### Post by jdeca57 on 2014-01-09
> **TheFu said:**
> 
Under virtualbox, setup the virtual machine hardware, then install whatever OS you like. There are many tutorials, youtube how-to videos and other helpful websites.  I'm partial to [this one]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox") with tips to get the best performance; I wrote it.  Don't just go with the defaults. It will turn out badly.

Thanks for your blog info. It's amazing what difference in speed these changes from default Virtualbox settings make. Especially when they warn that Enable IO APIC will actually slow down the system... I thought AMD-v was the only critical thing. But then I was wrong. :-)

---

### Post by TheFu on 2014-01-09
> **jdeca57 said:**
> Thanks for your blog info. It's amazing what difference in speed these changes from default Virtualbox settings make. Especially when they warn that Enable IO APIC will actually slow down the system... I thought AMD-v was the only critical thing. But then I was wrong. :-)

You are welcome. Glad it was helpful.  IO APIC will slow down a system, but NOT having it seems to be worse when multiple VMs are running. Win-XP seems to be the most sensitive to this setting.

---

