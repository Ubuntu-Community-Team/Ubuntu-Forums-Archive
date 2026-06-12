---
title: "Run Vista under ubuntu with VirtualBox from hard disk"
date: 2012-08-25
forum: Virtualisation
---

### Post by harun3d on 2012-08-25
Running vista with an existing vista .iso image file or dvd is possible and explained clearly on many internet sites.

But I don't have a vista .iso image file.  I have a dual boot of vista and ubuntu on my hard disk.  I can run both separately.  I want to run vista without waiting to shut down ubuntu and starting up vista.  Can't I run vista with virtualbox at the same time in ubuntu?

---

### Post by TheFu on 2012-08-25
The answer is "perhaps", but it won't be easy.  Lots of people have wanted to use a physical machine OS installation and run that inside a virtual machine.  Because the physical hardware on a PC and the virtual hardware _presented_ inside a virtual machine are different this isn't usually feasible.

However, there is an option to convert a "physical" install in to a "virtual" install using **p2v** tools. [https://duckduckgo.com/html/?q=p2v+virtualbox](https://duckduckgo.com/html/?q=p2v+virtualbox) will show a few, but the trick is to find a tool that creates a virtual image compatible with your virtualization hypervisor, virtualbox.

I hope these leads are useful.

---

### Post by jim_deadlock on 2012-08-25
This link might be useful, although complicated:

[How to migrate existing Windows installations to VirtualBox]("https://www.virtualbox.org/wiki/Migrate_Windows")

With that said, if you have an original Vista installation DVD (not recovery) with the product code then it's a straightforward process to install it in Virtualbox, I've done it several times.

---

### Post by harun3d on 2012-08-26
It is really difficult.Or it asks too much time.  I think that is the most important thing that ubuntu can do: an automatic parallel boot of windows.  For accessing windows files, this is already done.  It can be accessed directly.  But it would be nice to run windows virtually in ubuntu with one click.  I need windows for office documents.  libre office (or open office also) is  not fully compatible with windows office.

My computer is so much slow when I use windows comparing with ubuntu.  I used computers of 4 cores and 8 threads 3ghz (core i7) in windows.  They copy 100MB in 50sec.  They are so slow in windows.  they are slower than my 2core 2thread  1.7ghz in ubuntu.

---

### Post by TheFu on 2012-08-26
> **harun3d said:**
> It is really difficult.Or it asks too much time.  I think that is the most important thing that ubuntu can do: an automatic parallel boot of windows.  For accessing windows files, this is already done.  It can be accessed directly.  But it would be nice to run windows virtually in ubuntu with one click.  I need windows for office documents.  libre office (or open office also) is  not fully compatible with windows office.

My computer is so much slow when I use windows comparing with ubuntu.  I used computers of 4 cores and 8 threads 3ghz (core i7) in windows.  They copy 100MB in 50sec.  They are so slow in windows.  they are slower than my 2core 2thread  1.7ghz in ubuntu.

VirtualBox shouldn't be that slow inside a VM. Have you followed the best practices for network and storage setup?  
* Preallocation of storage is mandatory. NEVER use sparse files.
* Always use virtIO drivers when possible.
* If you can't use the virtIO network drivers, use an Intel PRO/1000 virtual NIC regardless of your physical NIC.

Automating the startup of a virtualbox VM is trivial too. Just put **vboxmanage** with the correct arguments to startup the specific VM into a script. Drop that script into the auto-startup folder for your distro.

---

### Post by Cheesemill on 2012-08-27
> **harun3d said:**
> I think that is the most important thing that ubuntu can do: an automatic parallel boot of windows
This isn't a Ubuntu problem, it's a Windows problem.

It's because Windows is so tightly linked to the actual hardware that it's installed on  that attempting to boot it inside a VM causes all sorts of problems.

Perhaps if you ask Microsoft nicely enough they will come up with a solution for you :)

---

### Post by harun3d on 2012-08-27
> **TheFu said:**
> VirtualBox **shouldn't be that slow **.
I had to precise it maybe.  It is not in virtual box that I tested it.   It was normal run of windows 8 on a core i7 and I was surprised that fastest processor (intel core i7=latest technology I think) which runs windows is much slower than a slow processor running ubuntu.  

I mentioned this because this is the reason why I don't want to use windows in normal boot.  I only want to use it in virtual boot with virtualbox to use it as less as possible due to its turtle speed.

---

### Post by TheFu on 2012-08-27
To make any OS desktop faster, 
* turn down the graphics "cheese." 
* Turn off 3D-effects, Aero, and all those fancy animations.  

**This applies to Linux and MS-Windows equally.  **Windows-Vista and later basically doubled the hardware requirements for a similar level of performance as WinXP.  Linux-based OSes have always been lighter than MS-Windows, though Unity-Ubuntu is pushing more and more feature-bloat into their Unity desktop.  

If you want the quickest Ubuntu desktop, don't use Unity. Use a raw window-manager like FVWM or a light-weight DE like LXDE instead. FVWM was the first WM that supported virtual desktops.  I still use it from time to time. It is hard to explain how fast it actually is.

I run Windows7-Ultimate inside a KVM virtual machine to record TV shows. The KVM server doesn't even have a graphics card installed. It has power and a network cable, that's it. The GUI access into MS-Windows is only through RDP. Win7 will not show any TV videos.  However, the HDD and network performance are at almost native levels.  Moving 10-20GB TV recording files from that VM routinely gets 70-80MB/sec (560 Mbps).  That proves that both HDD and networking for Windows7 can be pretty excellent.  BTW, that's on a Core i5 CPU with 1.5GB RAM allocated to the Windows7 VM.  I use virtio drivers.

None of this solves your issue. We need more facts about the problem to help.  
**Complete physical machine Specs**
* RAM
* HDD - how much, how it is allocated, how it is connected
* Network - connection, cabling, card
* Video Adapter
**Complete VM Specs**
* RAM
* HDD - how much, how it is allocated, how it is connected, which controller chips
* Network - connection, cabling, virtual card

Do not allocate more RAM or CPUs to a VM than is necessary. If the hostOS is starving for either, every VM will be slow too. For a Windows desktop, no more than 2 vCPUs should be allocated.  Always leave as least 1GB of RAM for the hostOS. These are rules of thumb.

We really would like to help.  A few yrs ago I wrote an article about making WinXP 50% faster under virtualbox - [http://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved](http://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved). There are other tips there too.  

Since that time, I've switched away from Virtualbox for Linux-hosted VMs to improve system stability. It wasn't stable on my hardware back then, whereas KVM has been rock solid on the identical hardware over a year. I mostly do server virtualization. For running a desktop within a desktop, I'd choose virtualbox. It is the better choice for graphical needs.

I look forward to seeing your setup in detail.

---

### Post by harun3d on 2012-08-29
**Complete physical ma**[IMG]http://ubuntuforums.org/images/editor/color.gif[/IMG]**chine Specs**
* RAM:[COLOR=Red] 2GB SO-DIMM DDR2-667                                    [/COLOR]
* HDD - how much, how it is allocated, how it is connected: s[COLOR=Red]ee picture below, not e-sata, 5400rpm[/COLOR]
* Network - connection, cabling, card:[COLOR=Red]  cable connection[/COLOR]
* Video Adapter:  I[COLOR=Red]ntel GMA X3100 (shared video memory)                                     [/COLOR]
**Complete VM Specs**
* RAM:[COLOR=Red] I gave 1gb for windows and 1 for ubuntu[/COLOR]
* HDD - how much, how it is allocated, how it is connected, which controller chips: [COLOR=Red]I gave 25 GB for vista in virtual box (in real hard disk it was 60GB for vista).  I tried all possibilities in virtual box concerning type of install: install as virtual disk, virtual machine, parallel disk,... None of them were able to start my windows from hard disk or from windows installation cd[/COLOR]
* Network - connection, cabling, virtual card: there was no option for network connection in virtual box I think

Running vista or xp from cd in virtualbox in ubuntu is also good for me, if running from hard disk would be difficult or impossible.

---

### Post by Elfy on 2012-08-29
*Thread moved to **Virtualization**.*

---

### Post by TheFu on 2012-08-29
[COLOR=Black]> **harun3d said:**
> **Complete physical ma**[IMG]http://ubuntuforums.org/images/editor/color.gif[/IMG]**chine Specs**
* RAM:[/COLOR]> **harun3d said:**
> [COLOR=Black] 2GB SO-DIMM DDR2-667                                    
* HDD - how much, how it is allocated, how it is connected: s[/COLOR][COLOR=Black]ee picture below, not e-sata, 5400rpm
* Network - connection, cabling, card:[/COLOR][COLOR=Black]  cable connection
* Video Adapter:  I[/COLOR][COLOR=Black]ntel GMA X3100 (shared video memory)                                     
**Complete VM Specs**[/COLOR] [COLOR=Black]
* RAM:[/COLOR][COLOR=Black] I gave 1gb for windows and 1 for ubuntu
* HDD - how much, how it is allocated, how it is connected, which controller chips: [/COLOR][COLOR=Black]I gave 25 GB for vista in virtual box (in real hard disk it was 60GB for vista).  I tried all possibilities in virtual box concerning type of install: install as virtual disk, virtual machine, parallel disk,... None of them were able to start my windows from hard disk or from windows installation cd
* Network - connection, cabling, virtual card: there was no option for network connection in virtual box I think

Running vista or xp from cd in virtualbox in ubuntu is also good for me, if running from hard disk would be difficult or impossible.[/COLOR] [COLOR=Black]

This is a laptop?  That means it has a slower, lower powered, CPU.

It has a slow physical disk. That doesn't help.  You didn't really say how the HDD was connected.  Is is IDE, SATA, USB, something else?  What disk controller chips are used?  ICH6 or something else?

Vista likes RAM, over 1G.  If I recall, 1G was the "minimal" config for Vista. It will be slow. You are stuck since you only have 2G total.  I ran vista for a few yrs, it was a hog.

The shared RAM for video memory is stealing more RAM that you need too, plus inside the VM, you are probably taking another 128MB of RAM, so your 1G for Ubuntu is more likely leaving only 512MB for Ubuntu. Not good, especially if you run Unity.

Be certain that you install the **Guest Additions** and that you turn down all the GUI "cheese" inside Vista. I haven't run Vista in a few yrs, but I think it is in the "*Adjust the Appearance and Performance*" settings.

You didn't say what the virtual hardware you selected for emulation is. That is important.  NIC, HDD, Controllers. Those settings **are definitely** inside Virtualbox. I use them all the time.  Your real hardware - the actual chips used - is important too when you are trying to get the best performance.

Windows doesn't run from a read-only device except in a recovery text mode. Take that up with Microsoft.

Basically, I think you'd be happier running WinXP inside a VM on this machine. XP doesn't demand as much RAM.

This isn't really the place, but might I make a suggestion?  Perhaps you would be better off running Linux inside VirtualBox with Vista as the hostOS?  You can run Linux full screen and forget that it is inside a VM.  I did that with Vista for over a year.
[/COLOR]

---

### Post by harun3d on 2012-08-30
[[COLOR=Black]full specs[/COLOR]]("http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&com.broadvision.session.new=Yes&PRODUCT_ID=150406")[COLOR=Black]
Is is IDE, SATA, USB, something else? [COLOR=Red]IDE[/COLOR] 
  What disk controller chips are used?  ICH6 or something else? [COLOR=Red]????[/COLOR]
 1G was the "minimal" config for Vista. [COLOR=Red]I'll take 1.3gb for vista and I have already disabled many processes in msconfig and services in services.msc file.  I will do it if it will be a new install.[/COLOR] 
You didn't say what the virtual hardware you selected for emulation is. [COLOR=Red]I don't know which one I have to choose.  I have tried all of them.  Can you say me which option I have to choose.  It is enough for me that vista and ubuntu runs at the same time no matter how they do.  [/COLOR]
  NIC, HDD, Controllers. [COLOR=Red]???[/COLOR]
Basically, I think you'd be happier running WinXP inside a VM on this machine. XP doesn't demand as much RAM.  [COLOR=Red]I have a xp cd also.  If you give the instructions I can run xp together IN ubuntu.[/COLOR]
This isn't really the place, but might I make a suggestion?  Perhaps you would be better off running Linux inside VirtualBox with Vista as the hostOS?  You can run Linux full screen and forget that it is inside a VM.  I did that with Vista for over a year.[/COLOR]
[COLOR=Red]Yes I think I will do it like that since I see that it is not so easy to run windows in linux.  [/COLOR]

---

### Post by TheFu on 2012-08-30
> **harun3d said:**
> [COLOR=Red]Yes I think I will do it like that since I see that it is not so easy to run windows in linux.  [/COLOR]

Actually, running Windows "inside" Linux is really easy, provided you have the appropriate hardware.  It seems that you do not.

For example, I'm surprised that a Core i7 machine has an IDE HDD and 2G of RAM. That just doesn't sound correct.

The instructions for WinXP are the same.

---

### Post by harun3d on 2012-09-03
> **TheFu said:**
> For example, I'm surprised that a Core i7 machine has an IDE HDD and 2G of RAM. That just doesn't sound correct.

the core i7 machine was not mine.  I don t know the HDD of it.  It would have 8GB of ram I think.

---

### Post by harun3d on 2012-09-14
> **TheFu said:**
> For example, I'm surprised that a Core i7 machine has an IDE HDD and 2G of RAM.
I **guessed** that it would have a IDE HDD since I thought that it was the latest technology but maybe I am wrong.  anyway a portable computer of 1000 euro bought in 2012, core i7, at least 4 cores, 8gb ram.  This was not mine computer configuration.  I gave it to compare.

but my 2X1,7ghz 2gb ram should also be able to do that I think. ubuntu only asks 250mb of ram in idle situation (ubuntu 12). windows vista requires 1.2gb ram in idle situation.

---

### Post by TheFu on 2012-09-14
> **harun3d said:**
> I **guessed** that it would have a IDE HDD since I thought that it was the latest technology but maybe I am wrong.  anyway a portable computer of 1000 euro bought in 2012, core i7, at least 4 cores, 8gb ram.  This was not mine computer configuration.  I gave it to compare.

but my 2X1,7ghz 2gb ram should also be able to do that I think. ubuntu only asks 250mb of ram in idle situation (ubuntu 12). windows vista requires 1.2gb ram in idle situation.
[SIZE=4]
[/SIZE] [CENTER][SIZE=4]**I owe you an apology!**[/SIZE]
[/CENTER]
 
BTW, IDE is  15+ yr old tech.  SATA is newer, but still 5 yrs old.

Last night at an installFest, I helped someone with a Core i7, 6GB of RAM and 300GB free install Ubuntu 12.04 with Unity into a virtual machine.  **After the install, it was painfully slow.**  That is an understatement.  Every character that I typed didn't get displayed until about 30 seconds later.  To the other person, it seemed that Ubuntu had locked up.  He wanted to delete the Ubuntu install and leave. Clearly, something was broken.  This was with 12.04.1 32-bit desktop.

If I hadn't seen this myself, I wouldn't believe it either.

I'm working on more detailed instructions now to be published soon.
[http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) - is a draft, but it should be nearly ready.

So, with all that said, I apologize for not believing that performance for a fast machine running virtualbox with Ubuntu inside could suck.

---

