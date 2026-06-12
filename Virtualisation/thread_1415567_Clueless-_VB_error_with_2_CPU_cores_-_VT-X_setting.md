---
title: "Clueless- VB error with 2 CPU cores - VT-X settings"
date: 2010-02-25
forum: Virtualisation
---

### Post by janthonywj on 2010-02-25
Hi all, 

I'm not so experienced with this sort of thing, but I'm trying to install a VM in VirtualBox with Windows XP 64-bit. I have had VT-X enabled with other machines but if I enable two cores under the setting I get an error message:
-----
Failed to start the virtual machine <NAME>.
Unknown error creating VM (VERR_VMX_MSR_LOCKED_OR_DISABLED).
-Details-
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {6375231a-c17c-464b-92cb-ae9e128d71c3}
-----
From what I understand from other forums, this is probably caused by VT-X being disabled in my BIOS. However, I have almost no options to choose from when accessing my BIOS at startup, much less any VT-X information. 

Does anyone have any insight or know how I can change my BIOS information from Ubuntu 9.10 64-Bit, or even seeing if the settings are currently set right... BTW I'm running on a Sony Vaio VGN-FZ140E laptop, with 4GB ram, and the processor is Core 2 Duo T7100 off the top of my head.

---

### Post by janthonywj on 2010-02-25
Just to add to this post as I have done some more research on this very troubling issue, in case someone finds this in a search... 

Apparently there has been a huge issue with Sony computers across the board with this over the past couple of years. Sony has "locked down" the VT technology in the CPU for some unknown reason... basically just to do it. While I'm still very upset about them disabling a feature that is NO WHERE advertised as a limitation to this laptop, I'm even more shocked to read that newer Sony laptops like the impressive Z series, also is on lock down. There has to be some sort of false advertising legality to this with Sony. 

I started chatting with some Sony tech support rep, that couldn't say much useful information other than point me to vague websites about the issue. The guy was more interested in telling me that my computer wasn't compatible with Linux than even talking about my issue, even after I stated that Ubuntu is running on my computer better than Windows ever could hope to. 

Anyway, unless you are good enough to know how to manually patch the BIOS, there isn't much you can do about this. I'm just screwed trying to run a 64 bit OS in a virtual machine for now, but I'll keep looking for a solution.

---

### Post by janthonywj on 2010-02-26
Since I know so many people are interested, I found some solutions. For my FZ series Sony laptop, with a Pheonix made BIOS, a rather lengthy and tedious solution is laid out here, 

[http://www.linuxformat.gr/?q=content/how-unlock-and-enable-hardware-accelerated-virtualization-technology-vt-sony-vaio-laptop-and]("http://www.linuxformat.gr/?q=content/how-unlock-and-enable-hardware-accelerated-virtualization-technology-vt-sony-vaio-laptop-and")

A man named named Igor Livicki, has made a much easier to use BIOS patch for a differnt type of BIOS that is included in some Z series laptops and FW series. You can find that thread at:

[http://software.intel.com/en-us/forums/showthread.php?t=63409]("http://software.intel.com/en-us/forums/showthread.php?t=63409")

It also points out that Sony has wised up and started changing the BIOS in their newer laptops, but still some are disabled. However, that doesn't help me as my laptop is like a year and a half old and they won't help me anymore. 

Done and done.

---

### Post by untanne on 2011-02-21
Hi [janthonywj]("http://ubuntuforums.org/member.php?u=765264")

many thx for your posts. It helps me. Well, I did a BIOS update for my HP DV8-1050eg laptop and after that the VT-Option was disabled. Enable this option and the error was gone.

Thanks and best regards Untanne

--
HP DV8-1050eg, ubuntu 10.10, VBox 3.2.8 OSE

---

