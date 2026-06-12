---
title: "VT -x is disabled?"
date: 2018-06-20
forum: Virtualisation
---

### Post by kara.p3 on 2018-06-20
Although I read the error message, I don't understand it. I installed VMware Workstation 14 Player and downloaded Ubuntu 18.04 desktop AMD64. I'm using a Windows 7 64-bit OS on my non-virtual desktop -although I'm not sure that matters since I'm installing Ubuntu on a vm.[ATTACH=CONFIG]280163[/ATTACH]

---

### Post by deadflowr on 2018-06-20
*Thread moved to **Virtualization** *

Basically you need to access your machine's BIOS menu
and look for setting for vt -x (might just say something about virtualizing) and enable it.
and also it's says to disable something that says trusted execution.
Then save those settings (Most BIOS will allow to save settings when closing/exiting)

After that you can boot back into Windows and try loading the vm again.


*The BIOS is usually accessible at the first screen that the machine shows, it might be the machine vendor name like Dell or Lenovo, or even the cpu brand like AMD or Intel.
(There is usually a shortcut listing on that screen that will say either system menu or BIOS menu, usually something like F2, but yours may vary)

Hope it helps

---

### Post by kara.p3 on 2018-06-20
Thanks for the help! The message made sense after you broke it down for me, and I now have Ubuntu running on my VM.

For anyone else who reads this, here's the solution. The BIOS menu options and navigation keys may differ on your system; however, it's pretty self-explanatory when I searched around for specific tabs.

**Part I**
Find out if your system supports Virtualization Technology (VTx/VTd)


[LIST=1]
[*]Download and install the **Intel Processor Identification Utility** from Intel's website [http://www.intel.com/support/processors/tools/piu/](http://www.intel.com/support/processors/tools/piu/)
[*]Open the processor identification utility window
[*]Select** CPU Technologies**
[*]Check the** Intel Technologies** tab: Is VTx/VTd is supported by your system?
[LIST]
[*]If YES, then you can enable this feature
[*]If NO, then your system doesn't support virtualization. Sorry..
[/LIST]

[*]Check **BIOS Utility** tab: Is VTx/VTd is supported by your system?
[/LIST]

[LIST]
[*=1]If YES, then move on to Part II
[*=1]If NO, you may need to update your BIOS firmware
[/LIST]
[INDENT]

[/INDENT]
**Part II**
Access your BIOS firmware to enable Intel(R) Virtualization Technology


[LIST=1]
[*]Restart your pc
[*]Select **Access BIOS**
[LIST]
[*]Before Windows loads, a black screen appears with some white text giving you menu options
[LIST]
[*]If Windows 7, press **F10 **key
[*]If not Windows 7, quickly read which Fn key to press
[/LIST]
[/LIST]

[*]Select **Setup Utility**
[*]Right arrow to **Advanced Tab **(might be a different tab on your system)
[*]Down arrow to** Intel(R) Virtualization Technology**
[*]Down arrow to **Enable**
[*]Right arrow to **Exit**
[*]Down arrow to** Exit Setup**
[*]Prompt: **Save and Reset Screen?** [YES]
[*]PC automatically restarts
[/LIST]

Viola! Enjoy your VM!

---

### Post by TheFu on 2018-06-20
> **kara.p3 said:**
> Although I read the error message, I don't understand it. I installed VMware Workstation 14 Player and downloaded Ubuntu 18.04 desktop AMD64. I'm using a Windows 7 64-bit OS on my non-virtual desktop -although I'm not sure that matters since I'm installing Ubuntu on a vm.

64-bit OSes must have vt-x enabled to work inside a VM.
Not all BIOSes provide access to enable VT-x (sometimes called "Virtualization Extensions") in the BIOS.   Usually it is the lower-end laptops that block access.

---

