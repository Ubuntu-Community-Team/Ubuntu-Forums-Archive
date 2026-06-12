---
title: "Install Windows 7 as guest OS"
date: 2016-04-17
forum: Virtualisation
---

### Post by pfeiffep on 2016-04-17
I currently have a multiple boot scenario that I'm thinking about switching to virtualisation. I've not found answers to my questions on line.
Existing configuration:
[LIST]
[*]SSD hosting Windows 7 and programs -  I boot by selecting in BIOS 
[/LIST]
[INDENT=2]12 GB memory, Intel core i7 CPU
[/INDENT]
[INDENT=2]recovery partition on SSD [no Win7 physical media]
[/INDENT]
[INDENT=2]internal HDD for shared data storage [NTFS]  
[/INDENT]

[LIST]
[*]internal HDD for Ubuntu [separate partition from data], test partition for other OSes - GRUB controlled 
[/LIST]
[INDENT=2]Ubuntu 14.04 LTS will replaced with 16.04 LTS after release
test partition deleted plan on installing guest OSes
[/INDENT]

[LIST]
[*]ESATA 1TB drive for backups and additional storage 
[/LIST]

My idea is install Ubuntu on SSD and run Win 7 and test linux as a guest OSes. The prime motivation is to simplify.

So here are my questions:[INDENT]1) Is it possible to install Windows into a virtual environment from a self created iso image [no serial # available]?
2) If possible can Windows be maintained?
3) Can software installed be properly maintained and upgraded?
4) Will installing multiple guest OSes drastically decrease the life of SSD?
5) most appropriate virtualisation software for my situation?
[/INDENT]

And of course any advice on how to proceed will be considered!

---

### Post by TheFu on 2016-04-18
You can get the S/N for Win7 using tools. You will need this.
There are physical-to-virtual tools.  VMware has one, but I haven't used it since 2008-ish.
Maintenance of any Windows OS is an issue, always. Don't think a VM or not matters.

Pre-installed Win7 is probably licensed only for physical installation, not virtual.  The migration effort may never work if that is the case for your Win7 install.  Retail copies of Win7 did not have that limitation.  I've run a retail Win7 inside VMs using both virtual box and KVM.  Migration of a pre-installed Win7 never worked for me.

SSD lifetimes are still just theory, IMHO.  I hope to get 1 yr, with anything more being pure luck.  Having excellent backups is rule number 1 for this stuff.  Be completely positive you can get back to where you started before beginning. This stuff is risky. It is all on you if there are any issues.

In short, you can move to a virtual machine with the proper Win7 license. If you don't have that, the OS checks for specific hardware that is NOT available when running inside a VM will make that impossible.

---

### Post by pfeiffep on 2016-04-18
> **TheFu said:**
> You can get the S/N for Win7 using tools. You will need this. I found the S/N on the about computer page in control panel

> Maintenance of any Windows OS is an issue, always. Don't think a VM or not matters..Yes Win maintenance is a pain - is the pain level increased if running a guest?

> Pre-installed Win7 is probably licensed only for physical installation, not virtual.  The migration effort may never work if that is the case for your Win7 install.  Retail copies of Win7 did not have that limitation.  I've run a retail Win7 inside VMs using both virtual box and KVM.  Migration of a pre-installed Win7 never worked for me.Thanks, I'll try it and if it doesn't work install Windows 10 as guest

> SSD lifetimes are still just theory, IMHO.  I hope to get 1 yr, with anything more being pure luck.  Having excellent backups is rule number 1 for this stuff.  Be completely positive you can get back to where you started before beginning. This stuff is risky. It is all on you if there are any issues.My HP desktop was purchased in 2011 with the SSD installed - guess I'm super lucky.

> In short, you can move to a virtual machine with the proper Win7 license. If you don't have that, the OS checks for specific hardware that is NOT available when running inside a VM will make that impossible.So an iso image of my current Win 7 install won't boot as a guest OS?

---

### Post by TheFu on 2016-04-18
> **pfeiffep said:**
> I found the S/N on the about computer page in control panel

Yes Win maintenance is a pain - is the pain level increased if running a guest?

Thanks, I'll try it and if it doesn't work install Windows 10 as guest

My HP desktop was purchased in 2011 with the SSD installed - guess I'm super lucky.

So an iso image of my current Win 7 install won't boot as a guest OS?

Win maintenance is always a pain. Don't think a VM has any relevance, except that GPU and other HW drivers aren't a pain, because they don't matter.

Whenever moving partitions and OSes around, excellent backups are mandatory.

It is unlikely to run is the short answer.
Don't think any ISO of Windows will boot - I've never seen that (but I'm hardly a microsoft expert). Where would it write temp files?  Whether it will boot or not depends on the license. You never said which license you have, but almost always a pre-installed Win7 will be locked to the vendors physical hardware, which virtual machines cannot completely spoof.  SOL, dude.

Opinion:
Win10 is worse than dumping Windows completely IMHO. Whatever. It is your machine and life. Seems that privacy isn't a right, but must be demanded.  I suppose that running Win10 without any network stack would be ok.

---

### Post by Habitual on 2016-04-18
> **pfeiffep said:**
> I found the S/N on the about computer page in control panel.
That's not it.
What you see is the decoded COA code.
It is NOT your installation serial as you see it.

Try the magic jelly-bean keyfinder, I may find your COA code.

---

### Post by SeijiSensei on 2016-04-19
If you using Windows for gaming, you may be unhappy with this solution.  The VM only has access to a virtualized graphics adapter and cannot directly address the video hardware.  Modern games will often not install in a VirtualBox VM, so if you do play games in Windows, consider a dual-boot arrangement.  You can still configure the Linux side to support VMs and reboot only to play games.  I have a dual-boot with Windows and Linux and VirtualBox VMs on both sides with the opposite flavor OS installed in them.

---

### Post by MAFoElffen on 2016-04-19
+1 = Agreed!

I did the dual boot, then pass-through experimentation with type-1 hypervisors ... and went back to dual boot. If I hadn't done gaming on native metal first, it might have been different. But running something in Virtual, and having it be reactive ... I got lag, that I just didn't want to accept. In virtualization, you just accect that there is going to be lag. But for gaming, that was not a good mix for me.

It can be done, with a passthrough using some type 1 hypervisors... but let's just say that my own experience with that was not fruitful.

IMHO-- I'm all for putting as much into virtualization as possible. But if the goal is "gaming," my priorities, standards and points of measure are just "different."

---

