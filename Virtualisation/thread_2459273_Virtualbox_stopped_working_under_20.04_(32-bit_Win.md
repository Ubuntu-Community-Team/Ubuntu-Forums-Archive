---
title: "Virtualbox stopped working under 20.04 (32-bit Windows guest)"
date: 2021-03-15
forum: Virtualisation
---

### Post by brendonwp on 2021-03-15
I have to run some Windows XP programs (don't ask why) and VirtualBox has stopped working with this client after upgrading from 18.04. Virtualbox 6.1 is the base version of VirtualBox supported on 20.04 and I suspect that 6.1 requires VT-X support even for a 32-bit OS like XP.   

I'm trying to roll back to 6.0.x with no success as it is not in the repositories for 20.04. Any suggestions?

---

### Post by mastablasta on 2021-03-15
> VirtualBox 6.1.0 -- support for hosts that don't have VT-x or AMD-v have been dropped.

kind of bad news. can you not enable it? most new machines have it as do old desktops. some laptops had it disabled but BIOS update enables it.

if you cant' enable it , i am not sure how much can be done other than getting older Ubuntu version installed and installing older vbox version in it

---

### Post by brendonwp on 2021-03-15
It's an old desktop that I've upgraded over the years. The motherboard was a cheapy because I spent my budget on cramming it full of RAM - one reason that it's still usable. Anyway, I can run VB when I boot Win8 on the same machine. 
I suspected that a rollback to 18.04 would be needed, but was hoping I was wrong.  Thanks anyway :)

---

### Post by ajgreeny on 2021-03-15
This may not be a very wise thing to do but if it is imperative that you continue with VBox 6.0 it is still available, even though no longer supported, from [https://www.virtualbox.org/wiki/Download_Old_Builds_6_0](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0), along with the Guest Additions extension pack.

Download and use at your own risk if you really must!

---

### Post by rsteinmetz70112 on 2021-03-16
I find it odd that Win 8 works but XP doesn't. Is your Win 8 64bit?

---

### Post by brendonwp on 2021-03-17
The Win8 is 64-bit - I have 8GB of RAM and can access it all. I run VB 6.0.10 on Win8 with no problems.
But if I go to Ubuntu VB and install the first version of 6.0.x that is listed against 20.04 it fails at module compilation. I've tried compiling the kernel from the command line with no luck. VB 6.1 installs but the XP VM will not run.     
My gut feel is that the underlying libraries used by VB changed between 18.x and  20.x, and now require hardware virtualisation. My primary machine is a recent laptop but I'm not happy with the my dual display setup.  I don't like the clutter on my desk

---

### Post by CelticWarrior on 2021-03-17
What errors are you experiencing exactly?

---

### Post by &amp;KyT$0P# on 2021-03-17
> **brendonwp said:**
> if I go to Ubuntu VB and install the first version of 6.0.x that is listed against 20.04 it fails at module compilation. 

Check your kernel version -
```
uname -a
```
To use VirtualBox 6.0.24 on Ubuntu 20.04, you need the deb from ajgreeny link above, and you must be running the stock 5.4.x kernel.  If you need the HWE kernel (currently kernel 5.8.something) then you are stuck with VirtualBox 6.1.x.

---

### Post by brendonwp on 2021-03-18
I downloaded VB 6.0.16 from Virtualbox.org. Then I installed this on my 20.04 box using gdebi. VB 6.0.16 is the first version listed as supporting 20.04. VB runs and opens up the list of my existing VMs. When I try to start my XP (32-bit) VM it halts with an error:

[SIZE=2][FONT=times new roman]"Kernel driver not installed (rc=-1908)[/FONT][/SIZE][SIZE=2][FONT=times new roman]
The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please try setting it up again by executing
[COLOR=#0000ff]'/sbin/vboxconfig'[/COLOR]
as root.
...
where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. "[/FONT][/SIZE]


When I run[FONT=times new roman] sudo 'sbin/vboxconfig"[/FONT] I get:

[FONT=times new roman]"vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: Look at /var/log/vbox-setup.log to find out what went wrong.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.
..."
[/FONT]

---

### Post by CelticWarrior on 2021-03-18
What were the errors when running 6.1?

For 6.0 [COLOR=#000000]you must be running the stock 5.4.x kernel.[/COLOR]

---

### Post by brendonwp on 2021-03-18
I'm no expert, but the download page specifies 6.0.16 as being compatible with Ubuntu 20.04. 
[https://www.virtualbox.org/wiki/Download_Old_Builds_6_0](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0)

Installed VB 6.1.14 and the corresponding Extension Pack. No errors reported. 

On running the XP VM reports: "Failed to open a session for the virtual machine"
Details:
[FONT=times new roman]VT-x is not available (VERR_VMX_NO_VMX).
[/FONT]
[FONT=times new roman] [/FONT][FONT=times new roman]
[/FONT]
[FONT=times new roman] [/FONT][TABLE]
 [TR]
 [TD][FONT=times new roman] [/FONT][FONT=times new roman]Result Code: [/FONT]
[/TD]
 [TD][FONT=times new roman] [/FONT][FONT=times new roman]NS_ERROR_FAILURE (0x80004005)[/FONT]
[/TD]
[/TR]
 [TR]
 [TD][FONT=times new roman] [/FONT][FONT=times new roman]Component: [/FONT]
[/TD]
 [TD][FONT=times new roman] [/FONT][FONT=times new roman]ConsoleWrap[/FONT]
[/TD]
[/TR]
 [TR]
 [TD][FONT=times new roman] [/FONT][FONT=times new roman]Interface: [/FONT]
[/TD]
 [TD][FONT=times new roman] [/FONT][FONT=times new roman]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}[/FONT]
[/TD]
[/TR]
[/TABLE]
[FONT=times new roman][/FONT]
The same VM ran under Ubuntu 18.04 on the same hardware. I would love to see it working again, but VT-X cannot be activated on this mobo.

---

### Post by CelticWarrior on 2021-03-18
> **brendonwp said:**
> I'm no expert, but the download page specifies 6.0.16 as being compatible with Ubuntu 20.04. 
[https://www.virtualbox.org/wiki/Download_Old_Builds_6_0](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0)



In that same page, in RED: > **[COLOR=#FF0000]VirtualBox 6.0.x is no longer supported![/COLOR]**
It's no longer supported for the reason stated above, twice.
If you must use the old version then you must remove the newer kernel and install the 5.4 branch.

Regarding the VT-x error this is what likely happened: The new version requires hardware virtualization support. This is mentioned at the Downloads page:
> [COLOR=#000000][FONT=Verdana]Please also use version 6.0 if you need to run VMs with software virtualization, as this has been discontinued in 6.1.[/FONT][/COLOR]
And again, use it at your own risk: > [COLOR=#000000][FONT=Verdana]Version 6.0 will remain supported until July 2020.[/FONT][/COLOR]
Almost a year out of support can be a problem for such sensitive software, vulnerabilities discovered after July 2020 weren't and won't ever be patched. Whether this is a problem you decide.

---

### Post by DuckHook on 2021-03-19
At the risk of muddying things further, it is possible to run XP in a pure QEMU environment without KVM (disable it). This means that your VM will be software only and will not rely on VT-x/AMD-v. It does mean moving away from VBox and familiarizing yourself with a new VM platform, but the security considerations alone to say nothing of the freedom to stay current would make this worth it.

---

