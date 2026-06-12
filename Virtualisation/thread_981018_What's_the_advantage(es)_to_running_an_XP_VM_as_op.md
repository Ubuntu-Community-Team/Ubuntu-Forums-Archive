---
title: "What's the advantage(es) to running an XP VM as opposed to having a dual boot?"
date: 2008-11-13
forum: Virtualisation
---

### Post by Rubicon421 on 2008-11-13
Please include details on footprint size, ease of use, compatibility with installing/running windows programs, getting windows updates, USB and ports, drivers for devices that don't work in linux alone, and the best set up if choosing VM over dual boot w/ XP native.

Currently I have a dual boot on 3 machines; 2 w/ XP and 1 w/ Vista. All are running Ubuntu 8.10 and I am just trying to decide which one (if any) I will use only Linux on. I have used wine a little but had some issues. I would rather just keep some form of Windows and know that any windows programs I want will install without having to tweak wine to get it to run.

---

### Post by amauk on 2008-11-13
** Assuming Virtualbox here **

> **Kill Vista said:**
> footprint size
Less than real disk partitions
Virtualbox uses dynamically expanding disks
You set a disk size (think of this as a max size) and the disk size will expand on demand
> **Kill Vista said:**
> ease of use
Windows under a VM is exactly the same as native.
The Virtualbox front-end is easy as pie
> **Kill Vista said:**
> compatibility with installing/running windows programs, getting windows updates
Identical to running windows natively
(Windows will not even know it's running under another OS)

*edit*
Except of course 3D acceleration from your graphics card,
but that's fairly obvious
*edit*
> **Kill Vista said:**
> USB and ports
You will need the full version of Virtualbox for USB passthrough - this isn't in the Ubuntu repos, but you can download the debs from Sun
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
> **Kill Vista said:**
> drivers for devices that don't work in linux alone
Identical to native Windows
again, Windows will not even know it's running under another OS

*edit*
Drivers for the emulated hardware (including the VBox graphics card) are included within virtualbox itself (what's refered to as the "guest additions")
*edit*
> **Kill Vista said:**
> and the best set up if choosing VM over dual boot w/ XP native.
Ensure you have plenty of free space your Linux host machine

Something you haven't asked, performance.
bear in mind you are running 2 operating systems at the same time
it's best to be aware of the requirements
ensure your machines are beefy enough to do this

I'm running dual core @ 2.4Gz, 4Gb RAM and I can run Win XP under virtualbox very well
I give XP access to 512Mb RAM and 32Mb of Video memory and run XP @ 1280x1024 resolution

you've got to decide whether you can "lose" that RAM on your host OS without affecting performance.

---

### Post by Rubicon421 on 2008-11-13
I probably won't be doing much if anything on the host while using the VM so I'm not worried about loosing RAM. My machines are pretty beefy anyway.  If all my keyboards/mice are USB will they work with a fresh install of XP as a VM, or will I need the fix you mentioned? 

Also, One of the machines is a HP laptop with a restore disc instead of an OEM copy of windows. Can I use that to create the VM, and would that be the preferred method since it would include the drivers for the laptops hardware? I have an XP Home and XP Pro OEM &key for the other 2 machines (desktops, custom built) so I will probably stick with the same disc and OS that they have natively for them. It's the laptop I'm not sure about.

---

### Post by Calmor on 2008-11-13
> **amauk said:**
> ** Assuming Virtualbox here **

Identical to native Windows
again, Windows will not even know it's running under another OS

*edit*
Drivers for the emulated hardware (including the VBox graphics card) are included within virtualbox itself (what's refered to as the "guest additions")
*edit*


Since I haven't used the USB passthrough (I run Virtualbox OSE from the repos on 8.04LTS), I can't comment there.  However, my understanding is that other items, like your wireless card, sound card, and even your video card, are isolated from the virtual machine.  If you wireless card doesn't work in Linux, it won't work in Windows under a virtual machine.  Windows in a VM doesn't have direct access to the hardware, with the possible exception of USB passthrough.

Regarding the OP's question, some of the key benefits of using a VM are the ability to open the VM at any time (and not have to reboot), the ability to save snapshots of the machine, and the relative ease in which you can transfer the VM to another machine (just copy the hard disk file to another box).  Note that Virtualbox's hard disk format is somewhat unique and not compatible with VMWare or Microsoft Virtual Machine (or whatever they're calling it these days).  You can also share your files on a Linux file system with the Windows virtual machine easily through the shared folders feature.

The biggest drawback I can think of is having to give up your system resources to the virtual machine.  Typically this isn't much of an issue if you have a dual core processor and lots of RAM, but on an older system it may limit what you can do in Windows.  You need to assign a chunk of memory to Windows, which will then be unavailable to Linux, and the processor is shared depending on your system configuration.

---

### Post by Calmor on 2008-11-13
> **Kill Vista said:**
> I probably won't be doing much if anything on the host while using the VM so I'm not worried about loosing RAM. My machines are pretty beefy anyway.  If all my keyboards/mice are USB will they work with a fresh install of XP as a VM, or will I need the fix you mentioned? 

The keyboard/mouse will work even if you use the repository version.  Linux will send the keyboard and mouse events through Virtualbox to Windows, regardless of the keyboard and mouse types.  USB passthrough is only needed to access other devices, like flash drives (which could theoretically be accessed through shared folders instead) and devices such as cell phones, etc.  Without USB passthrough, don't expect to be able to sync a BlackBerry or use a Windows-only USB device.

> Also, One of the machines is a HP laptop with a restore disc instead of an OEM copy of windows. Can I use that to create the VM, and would that be the preferred method since it would include the drivers for the laptops hardware? I have an XP Home and XP Pro OEM &key for the other 2 machines (desktops, custom built) so I will probably stick with the same disc and OS that they have natively for them. It's the laptop I'm not sure about.

I don't know that the restore disc will work, as many of them look at the BIOS for signs that you're installing on an HP machine.  Virtualbox has its own BIOS, and the disc will not be able to detect the machine type.  The drivers for hardware, though, are not necessary as Virtualbox isolates the OS from the hardware.  As amauk posted, Virtualbox comes with guest additions, which contain video drivers and allow mouse integration.  Other drivers are not needed because Virtualbox emulates well-known hardware that Windows supports natively.

HTH

---

### Post by amauk on 2008-11-13
bear in mind Virtualbox emulates all the hardware - so the virtual machine will not be using any of the actual hardware in your machine, it'll be using software emulated hardware

All peripherals (keyboard, mouse, USB devices etc.) should work no problem
It's not really a fix, the guest additions is just an executable file you run that installs drivers for the virtualbox emulated hardware

But as I said, the open source version of virtualbox (the one in the ubuntu repos) doesn't do USB passthough (allowing USB devices to communicate with the VM)

For USB passthrough, you will need the restricted version of virtualbox (still free - cost wise, just not fully open source)

As for the restore disk,
it depends

some use a pre-configured image of Windows
if this is the case, you may have issues

some use a stock version of windows with a GUI front-end installer allowing you to install drivers post OS install
if this is the case, just don't install any of the drivers

Try it
there's zero chance of you mucking up your linux install
if it works, great
if not, delete the VM and uninstall virtualbox

---

### Post by Calmor on 2008-11-13
> **amauk said:**
> 
Try it
there's zero chance of you mucking up your linux install
if it works, great
if not, delete the VM and uninstall virtualbox

Agreed - virtualization is great for most uses, not so good for others - give it a shot and see if it fits your needs.

Personally, I dual boot Vista (preinstalled) and Ubuntu.  I rarely use Vista, though, because I have XP virtualized in Ubuntu, and have shared folders for XP to access documents on both partitions.  If I do need access to hardware (games, or programming for Windows Mobile devices, for example), I boot into Vista, otherwise I just use the Virtual XP.

---

### Post by Rubicon421 on 2008-11-13
If I do a VM on the laptop and use the OEM copy that is for my desktop instead of the restore disc that came with it, can I still use the cd key from the restore disc so that I don't have to use the same key twice? If I did (or had to) use the same key twice would this cause a problem with updates?

---

### Post by Calmor on 2008-11-13
As long as they're both XP keys, it should work, but there are sometimes some licensing issues.  For example, upgrade versions, full versions, and OEM versions have different keys, and are not interchangeable in my experience.  But, since your restore disc (most likely) contains an OEM license, it should have (and accept) any OEM key.  

I'd say give it a go.  As long as it passes the activation process, upgrades and everything will work as normal.  

I don't know how Microsoft's licensing of OEM software works in relation to installation on virtual machines, but I'd imagine that if it's not against the EULA, it's probably frowned upon.  That doesn't mean it can't (or shouldn't) be done.  To me, it's running on that hardware, which has the tag on the bottom, and it's paid for.  What more do they want?

---

### Post by Rubicon421 on 2008-11-13
So, should I try the restore disc first or go straight to the OEM copy that I know I am going to be using for a VM on another computer? I only have 1 key for the XP OEM.

---

### Post by Rubicon421 on 2008-11-13
What if I used a Wubi install and the 15GB of space for the virtual drive (Ubuntu folder on C: drive) is only 3.6GB from being full? Can I expand that before installing an XP VM?

---

### Post by Calmor on 2008-11-18
> **Kill Vista said:**
> So, should I try the restore disc first or go straight to the OEM copy that I know I am going to be using for a VM on another computer? I only have 1 key for the XP OEM.

I believe the keys are attached to hardware, not the disc, so if you have XP legally installed on your other machines, they use the key attached to the PC, leaving the key on the bottom of your laptop as a valid key for your VM.

If you haven't already, you can try the restore disc first if you like.  The worst it can tell you is that you're not restoring to an HP machine (since it will detect a generic PC) and won't let you do the install, then just use the OEM disc.

My views on the restore disc though are that they're often full of crap you don't need, and in this case, that includes drivers for hardware your VM won't have.  I'd personally just go with the OEM disc.

---

### Post by Calmor on 2008-11-18
> **Kill Vista said:**
> What if I used a Wubi install and the 15GB of space for the virtual drive (Ubuntu folder on C: drive) is only 3.6GB from being full? Can I expand that before installing an XP VM?

Just so I understand:

[LIST]
[*]You have Windows installed on the main partition of your drive
[*]You have Ubuntu installed in Windows through Wubi
[*]You've given Ubuntu 15GB of drive space
[*]You're using 11GB of that already with Ubuntu and other programs
[/LIST]

In that case, I would say you almost *need* to increase the Wubi virtual drive size, because while Windows XP will install in 3.6GB of space, you're squeezing both systems, and depending on how much RAM you give XP, it will want a decent-sized swapfile.

Unfortunately, I've never used Wubi and couldn't tell you how that's done.  I'd assume you need to boot into Windows and change the configuration?

After that, it should be the same as any other install.

---

