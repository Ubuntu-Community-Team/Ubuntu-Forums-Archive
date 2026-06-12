---
title: "Win 8 Ubuntu 12 &quot;kernel requires an x86-64 CPU, but only detected an i686 CPU&quot;"
date: 2013-10-24
forum: Virtualisation
---

### Post by aztoby on 2013-10-24
I suspect this possibly could belong in either "virtualization" or "install & upgrade" but since I couldn't decide which was more apropos, I'm putting it here.

I have installed "VirtualBox 4.3 for Windows hosts x86/amd64." But when I attempt to install "ubuntu-12.04.3-desktop-amd64," either from CD/DVD or from ISO image, I get the following message.

"This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU."

I am posting this on both, VirtualBox and Ubuntu forums. I know mobo and proc support hardware virtualization because I was able to run MS Hyper-V. However, there is nothing in the mobo BIOS that 
allows turning hardware virtualization on or off... it's just automatically on. Any & all suggestions/thoughts are welcome!

Motherboard: Gigabyte GA-F2A85X-UP4(rev. 1.0)
Chipset: AMD A85X
BIOS: AMI EFI version F4
Processor: AMD A8 6600K (Socket FM2) 64-bit Quad Core
Memory: 16 GB DDR3
Operating System: Windows 8 Professional, 64-bit

---

### Post by JKyleOKC on 2013-10-24
You might have better luck with VirtualBox 4.2.18 instead of 4.3.0; as you can see from the vbox forums, 4.3 has quite a few problems still and is not at all what most would consider ready for prime time. For example, it disallows saved states on VMs created by 4.2 or earlier versions, and also snapshots.

---

### Post by 3rdalbum on 2013-10-25
In the VM settings there are special options you need to turn on to expose 64-bit mode to the guest OS. One is Nested Paging, the other is right above it but I can't remember its name.

Have a look and enable them and it will work. If you can't enable them, you are stuck with a 32-bit guest OS.

---

### Post by oldos2er on 2013-10-25
Moved to Virtualisation.

---

### Post by aztoby on 2013-10-25
[COLOR=#000000][FONT=Lucida Grande]The VirtualBox manual staes,
"[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]**Warning**[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]Do not run other hypervisors (open-source or commercial virtualization products) together with VirtualBox! While several hypervisors can normally be installed in parallel, do not attempt to run several virtual machines from competing hypervisors at the same time. VirtualBox cannot track what another hypervisor is currently attempting to do on the same host, and especially if several products attempt to use hardware virtualization features such as VT-x, this can crash the entire host. Also, within VirtualBox, you can mix software and hardware virtualization when running multiple VMs. In certain cases a small performance penalty will be unavoidable when mixing VT-x and software virtualization VMs. We recommend not mixing virtualization modes if maximum performance and low overhead are essential. [/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]**This does not apply to AMD-V**[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]."[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]I took this to mean that it is okay to have multiple hypervision apps simultaneously installed, but just don't run virtual machines in more than one app at at time. Additionally, the very last statement seems to imply that the entire warning [/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]*only*[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande] applies to Intel's VTx, and [/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]*not*[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande] AMD-V (which is what I have). That said, someone in the Virtualbox Forums suggested I was interpreting it incorrectly and so should try disabling Hyper-V.[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]Anyone reading this will be pleased to know that after disabling hyper-v (see note* below) and rebooting, I was able to easily install Ubuntu Desktop 64bit without issue (see note ** below).[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]*launched elevated command prompt (run as administrator) and entered the following script. "dism.exe /Online /Disable-Feature:Microsoft-Hyper-V" (without the quote marks, of course).[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]**when selecting OS type to install, I chose "Other/Other 64bit"

Thanks for all of your comments! ^_^[/FONT][/COLOR]

---

### Post by hari-menon on 2014-01-07
> **aztoby said:**
> 
...
[COLOR=#000000][FONT=Lucida Grande]**when selecting OS type to install, I chose "Other/Other 64bit"
[/FONT][/COLOR]...[COLOR=#000000][FONT=Lucida Grande]
[/FONT][/COLOR]
This helped. And it took almost two hours to figure this out.

Thanks!

---

### Post by Manuel_Sousa on 2014-01-30
Totally new to these matters, but checked a few answers in the forums ( >30 minutes ...)
Quad 6600 with Win8 - 64, Virtual Box, Ubuntu 13.10.
Kept getting that infernal message  "kernel requires an x86-64 CPU... bla bla"
checked Bios - virtualization was enabled

and in the end, just had to go to virtual machine settings, General, and in Operating System where I had Ubuntu, just had to set to the option Ubuntu ( 64 bit ), restarted the machine... voilá !!! Felt dumb for the time lost, but happy with the success

---

