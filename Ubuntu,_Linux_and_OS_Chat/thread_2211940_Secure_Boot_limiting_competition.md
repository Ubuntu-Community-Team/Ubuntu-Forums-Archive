---
title: "Secure Boot limiting competition"
date: 2014-03-18
forum: Ubuntu, Linux and OS Chat
---

### Post by frank18 on 2014-03-18
[COLOR=#252525][FONT=Verdana][plot to lock other operating systems from Windows 8 devices]("http://www.zdnet.com/blog/bott/leading-pc-makers-confirm-no-windows-8-plot-to-lock-out-linux/4185"), but now we know Microsoft was not telling the whole truth.[/FONT][/COLOR]
[COLOR=#252525][FONT=Verdana][Journalist Glyn Moody]("http://blogs.computerworlduk.com/open-enterprise/2012/01/is-microsoft-blocking-linux-booting-on-arm-based-hardware/index.htm") dug around Microsoft's [Windows Hardware Certification Requirements]("http://msdn.microsoft.com/en-us/library/windows/hardware/hh748200.aspx") for Windows 8 client and server systems and found on page 116 that will Windows 8 Secure Boot can be disabled: on Intel systems, "Disabling Secure [Boot] must not be possible on ARM systems."[/FONT][/COLOR]
[COLOR=#252525][FONT=Verdana]What does that mean? According to Aaron Williamson, a lawyer with the [Software Freedom Law Center]("http://www.softwarefreedom.org/") an organization that provides pro-bono legal services to developers of Free and open-source software, Microsoft has wasted no time in [effectively banning most alternative operating systems on ARM-based devices that ship with Windows 8]("http://www.softwarefreedom.org/blog/2012/jan/12/microsoft-confirms-UEFI-fears-locks-down-ARM/").[/FONT][/COLOR]
[COLOR=#252525][FONT=Verdana]Microsoft will be doing this by using [Unified Extensible Firmware Interface (UEFI), ]("http://www.itworld.com/hardware/222791/goodbye-bios-hello-uefi")to block [block all other operating systems from Windows 8 systems.]("http://www.zdnet.com/blog/open-source/microsoft-to-stop-linux-older-windows-from-running-on-windows-8-pcs/9589") UEFI is the 21st century's replacement to PC and other devices' BIOS. It's used to set up your computer and make it ready to boot.[/FONT][/COLOR]
[COLOR=#252525][FONT=Verdana]Williamson explains, "The Certification Requirements define ... a 'custom' secure boot mode, in which a physically present user can add signatures for alternative operating systems to the system's signature database, allowing the system to boot those operating systems. But for ARM devices, Custom Mode is prohibited: 'On an ARM system, it is forbidden to enable Custom Mode. Only Standard Mode may be enable." [sic] Nor will users have the choice to simply disable secure boot, as they will on non-ARM systems: "Disabling Secure [Boot] MUST NOT be possible on ARM systems.' [sic] Between these two requirements, any ARM device that ships with Windows 8 will never run another operating system, unless it is signed with a preloaded key or a security exploit is found that enables users to circumvent secure boot."[/FONT][/COLOR]
[COLOR=#252525][FONT=Verdana]In short, Microsoft insists that any Windows 8 ARM-powered device can not be rebooted or rooted with the user's choice of operating system. And you thought rooting some Android phones was troublesome![/FONT][/COLOR]
[COLOR=#252525][FONT=Verdana]Williamson went on to say that while "While UEFI secure boot is ostensibly about protecting user security, these non-standard restrictions have nothing to do with security. For non-ARM systems, Microsoft requires that Custom Mode be enabled-a perverse demand if Custom Mode is a security threat. But the ARM market is different for Microsoft in three important respects"[/FONT][/COLOR]

---

### Post by oldos2er on 2014-03-18
Not an Ubuntu support request, moved to Ubuntu, Linux & OS Chat.

---

### Post by grahammechanical on 2014-03-18
I have not read all your post. Just enough to know that this is old news. It has been known about since the very early days of Secure Boot. It is why some Linux developers set about finding ways to legally boot Linux on machines with secure boot instead of recommending that secure boot simply be disabled.

Ubuntu 12.10 was the very first Linux distribution to have a Linux kernel that would legally install on a machine with secure boot enabled. It is thanks to the work of Ubuntu developers that it has been possible to install Ubuntu with secure boot enabled since the first Windows 8 machines were put on the market.

That is not to say that there are not problems. And those problems are often due to the non-standard way in which OEMs apply the protocols. And I know that I am referring to Intel X86 hardware and not ARM.

Are you aware that motherboards in machines running Windows 7 also had the facility for secure boot? It was not enabled by default. But that had to change with Windows 8.

Now if you really want to worry about security, read this:

[http://www.markshuttleworth.com/archives/1332](http://www.markshuttleworth.com/archives/1332)

Now that is something to worry about.

---

