---
title: "Which virtualbox or qemu"
date: 2014-06-13
forum: Virtualisation
---

### Post by turboruuvi on 2014-06-13
I've tried both virtualbox and qemu on my machine, but neither of them seems to work.

My machine is [HP pavilion a6622sc]("http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c01561538-16%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken") (Phenom 8550) running 32-bit Ubuntu 14.04 LTS.

Which is the defining thing: 32-bit Ubuntu or 64-bit HW?

Also, any pointers to tutorials about debugging a small RTOS using those (virtualbox, qemu)?
(How to get the debugger working.)
The RTOS is for x86 only.

---

### Post by TheFu on 2014-06-13
I'll ignore the RTOS. I haven't used one since the mid-1990s. Running an OS that is very sensitive to time fluxuations under any VM technology seems like a bad idea.

How much RAM does it really have?  The specs say 3GB - which should be plenty.  I'd be surprised if vbox doesn't run well on that machine. What do the log files say?  I can only guess that any issues are permissions-based.

---

### Post by turboruuvi on 2014-06-13
It complains about "triple fault".

On my pentium M based laptop (no HW acceleration, Linux Mint 13) it works from command line, but I don't seem to find
any way to use a debugger.

---

### Post by TheFu on 2014-06-13
Best to copy/paste the exact message and be certain to clarify exactly which machine and file it came from.

---

### Post by turboruuvi on 2014-06-13
> A critical error has occurred while running the virtual machine and the machine execution has been stopped.

 For help, please see the Community section on [[COLOR=#0000ff]_[http://www.virtualbox.org](http://www.virtualbox.org)_[/COLOR]]("http://www.virtualbox.org") or your support contract. Please provide the contents of the log file VBox.log and the image file VBox.png, which you can find in the /home/jaa/VirtualBox VMs/oxkernel/Logs directory, as well as a description of what you were doing when this error happened. Note that you can also access the above files by selecting Show Log from the Machine menu of the main VirtualBox window.
 Press OK if you want to power off the machine or press Ignore if you want to leave it as is for debugging. Please note that debugging requires special knowledge and tools, so it is recommended to press OK now.



from the logs:

00:00:03.503491 Guest Log: BIOS: Booting from Floppy...
00:00:03.705519 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
00:00:03.705524 !!
00:00:03.705524 !!                 Guru Meditation 1155 (VINF_EM_TRIPLE_FAULT)
00:00:03.705539 !!
00:00:03.705563 !! Skipping ring-0 registers and stack, rcErr=VINF_EM_TRIPLE_FAULT
00:00:03.705571 !!
00:00:03.705572 !! {mappings, <NULL>}
00:00:03.705574 !!
00:00:03.705583 
00:00:03.705584 The mappings are DISABLED.
00:00:03.705589 00000000ff800000 - 00000000ffbfffff  Hypervisor Memory Area
00:00:03.705598 !!
00:00:03.705599 !! {hma, <NULL>}
00:00:03.705601 !!
00:00:03.705606 Hypervisor Memory Area (HMA) Layout: Base 00000000ff800000, 0x00400000 bytes

---

### Post by TheFu on 2014-06-13
Impressive bug.
I'd open a ticket directly with Oracle on that: [https://www.virtualbox.org/wiki/Bugtracker](https://www.virtualbox.org/wiki/Bugtracker)

---

### Post by turboruuvi on 2014-06-13
Thanks.
I guess it's useless trying to wrestle with the virtualbox for now?
Maybe I should start frustrating with the qemu? ;-)

---

### Post by TheFu on 2014-06-13
If no VT-x/VMD-v support, I'd punt.
If you didn't open a bug with vbox, it will never be fixed.

---

### Post by turboruuvi on 2014-06-13
Virtualization was turned on in the BIOS if you mean that?
So you think it's not my own fault? What kind of bug you think it is?
I'll try to file a bug.

---

