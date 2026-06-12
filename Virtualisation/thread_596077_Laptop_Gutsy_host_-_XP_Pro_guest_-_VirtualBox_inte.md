---
title: "Laptop: Gutsy host - XP Pro guest - VirtualBox intermittent freezes both"
date: 2007-10-29
forum: Virtualisation
---

### Post by hungle0 on 2007-10-29
Hello -

The temporary freezes can cause my mouse and all programs in both OS's to stop responding. After about 10 - 15 seconds, I would have control of the system. Sometimes, if I don't move the mouse, then the programs in the XP guest would stop responding, but Ubuntu stays fine. If I move the mouse again, then the XP guest would continue to process and only continue if the mouse is active. Is this some sort of interrupt problem?

There are times when everything just works perfectly. Huh?

I have tried both Virtualbox 1.5.2 and 1.5.0 and still experiences the strange freeze of both Ubuntu host and the Windows XP guest. I am currently using 1.5.2. 

I have Ubuntu 7.10 i386 installed on a Gateway MX6960 laptop (intel gma 945/950 chipset). Specs: Core 2 Duo  T5600, 1.86 GHz, 2 GB RAM, 160 GB hd. I have disabled the Vanderpool option in the bios. Disabled the option in Virtualbox as well. The XP guest is on a VDI scalable to 10 GB, legit copy and updated with all patches. 

- Virtualbox USB support is currently on, but freezes occur with or without USB.
- XP Guest has 256 MB RAM, 8 MB Video RAM
- Enabled: ACPI, IO APIC, 1 shared folder
- Audio: ALSA (enabled) - freezes either way
- Guest Additions installed - freezes either way
- Intel VT (disabled) - freezes either way (including correct bios settings)
- Wired ethernet

Usually the idle CPU usage is around 6 - 11% or so for both Cores in Ubuntu while running the Guest OS in seamless mode or otherwise. All display modes seem prone to freezing. Ubuntu is controlling CPU speed as on demand, usually it is at 1 GHz even with Guest OS running.

I hope I am not forgetting anything. Well, I am only using the built-in touchpad mouse. Gutsy host is PERFECT when no guest is running. Compiz effects are off.

Help anyone?

---

### Post by Asgaard on 2007-10-29
I see the exact same behaviour on the same software versions, on a 1st gen Macbook (so nearly identical hardware too).

On a side note that doesn't contribute to solving the problem at all, I can say Virtualbox has always been flaky on me, with bizarre problems such as  these, or real guest freezes where I need to kill -9 all Virtualbox processes on sight to gain back control.

Such a pity, the other big freeware alternative is slow as a cow.

---

### Post by hungle0 on 2007-10-29
> **Asgaard said:**
> I see the exact same behaviour on the same software versions, on a 1st gen Macbook (so nearly identical hardware too).

Yeah, I have pretty much tried every possible software and bios configuration with no real solutions. The guest os seems stable RIGHT NOW, but the performance and freezes are so frequent and unpredictable. It is the unpredictable part worries me.

My laptop's hardware is like 98% identical to the older model Macbooks. Maybe it's the intel chipset ? This problem seems pretty isolated and rare. I have searched many forums and so far I think we are the only two that have reported such a problem. Maybe there are other people out there....

VMware has too much overhead in terms of background processes and bloat of installed packages... :(

---

### Post by Shazaam on 2007-10-29
Have you tried this yet? It's for kvm but might work for you.

[http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround](http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround)

---

### Post by hungle0 on 2007-10-29
> **Shazaam said:**
> Have you tried this yet? It's for kvm but might work for you.

[http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround](http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround)

I have just changed the ACPI setting just as the wiki suggested. I originally had "ACPI Uniprocessor" or something similar under the computer setting. I have changed it now to "Standard PC". 

The first reboot didn't work - but then I just disabled the ACPI option in the Virtualbox settings. The second boot worked fine and the guest xp redetected all of the hardware.

I will test out this configuration for a bit and then report the results. Thanks for your suggestion. :D

---

### Post by hungle0 on 2007-10-30
Bad news. "Standard PC" method doesn't work. I have switched it back to the regular ACPI Uniprocessor.

I find that whenever I change ANY settings in the VirtualBox main GUI such as VM settings or deleting another machine, this will start in motion the hiccups. Temporary solution - Reboot and don't touch any settings of VirtualBox. Well, this seems to work most of the time.

I am astonished that so few people are experiencing this problem given the use of Ubuntu, Intel GMA 945/950 chipsets, core 2 duos, and VirtualBox.

---

### Post by mkrisch on 2007-10-31
just thought i'd mention i'm seeing it as well.  running virtualbox 1.5.2 on a thinkpad x60s under ubuntu 7.10.  it runs really nicely, but the occaisional lock ups are troublesome.  i find that after the first few, moving the mouse doesn't free it.  i've found that if i press the power button that wakes things up--and brings up the logout windows, but i just close it.

i'm trying out vmware player and workstation 6 to see if i get the freezes there as well.

---

### Post by hungle0 on 2007-10-31
> **mkrisch said:**
> just thought i'd mention i'm seeing it as well.  running virtualbox 1.5.2 on a thinkpad x60s under ubuntu 7.10.  it runs really nicely, but the occaisional lock ups are troublesome.  i find that after the first few, moving the mouse doesn't free it.  i've found that if i press the power button that wakes things up--and brings up the logout windows, but i just close it.

i'm trying out vmware player and workstation 6 to see if i get the freezes there as well.

I am going to continue with VirtualBox even with the hiccups. I have the virtual machine setup and working with everything I need - just the freezes.

I have found a somewhat working solution: 
 1. Open up VirtualBox gui from a fresh Ubuntu boot
 2. Start up the XP guest and let it completely boot up.
 3. Shutdown the XP guest by normally shutting down XP. - SHUTDOWN, don't restart.
 4. Exit (close) the VirtualBox gui.
 5. Open VirtualBox gui and without doing ANYTHING else, start the XP guest again.

Normally, I would just let the mouse and keyboard still for about 30 seconds to see if a freeze occurs. If it does, then I just repeat step 4 and 5. Most of the time, it works after two tries.
Maybe I am just paranoid, but don't open Ubuntu's System Monitor when the vm is running.

Yeah, it is a bit of an inconvenience,  but I will put up with it until a better solution is discovered or an official VirtualBox update/fix.

---

### Post by dyrer on 2007-11-04
I have a similar problem but with cd
If I will insert any cd in tray linux freezes and only reset is possible
(Is a desktop pc)

---

### Post by Kristopher on 2007-12-27
Yip both Ubuntu(Host) and XP (Guest) freeze when using Virtualbox. Installed with the Add remove not a .deb

HP Pavilion dv6238ea Notebook PC | Ubuntu 7.10
2 Gb RAM | 120Gb HD | Nvidia Go 7400 256MB | Intel® Core™ Duo CPU T2250 @ 1.73GHz

---

### Post by algoe on 2008-02-12
I also have this problem. It also seems do disconnect my wireless network connection when it freezes. The guest is generally slow, and freezes every 5-10 seconds if i don't move the mouse constantly.
I have a thinkpad z60p. The intel chipset seems to be a common factor here :(
Perhaps this one should be registered on launchpad?

---

### Post by UMDGaara on 2008-02-14
Same problem here...sorry I don't have a solution.

This problem comes and goes at random for me. Sometimes it freezes up every few minutes, other times I will use VirtualBox for days with no issues. I have no clue what causes it.

---

### Post by trycage on 2008-03-17
Dear All

keywords: Virtualbox Ubuntu gutsy Wireless hangs

I have the same problem of frequent disconnections (with guest os hangs) of my Wireless in UBUNTU gutsy using VBOX 1.5.x. with guest os WINXP.

I tried the following workaround

Checking from WinXp guest OS, VBox assign an DHCP IP
in the domain 10.0.2.x
with gateway 10.0.2.2
and
DNS 10.0.2.3


Hence I forced my virtual network interface to the static address (in winXP)
IP 10.0.2.200
Mask 255.255.255.0
Gateway 10.0.0.2
DNS 10.0.0.3

And until now it is working fine (I completed the total windows update process
from the scratch)

I seems to be something related to the DHCP service of the NAT

I hope it can Help

Trycage

---

