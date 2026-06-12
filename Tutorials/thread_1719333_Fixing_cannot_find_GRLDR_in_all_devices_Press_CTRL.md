---
title: "Fixing cannot find GRLDR in all devices Press CTRL ALT DELETE to Restart issues"
date: 2011-04-01
forum: Tutorials
---

### Post by s_olsen on 2011-04-01
I had an issue with ubuntu no longer booting up and giving me the error message

"cannot find GRLDR in all devices. Press CTRL+ALT+DELETE to restart"

I did some searching but still couldn't get it to work.

I am using Windows Vista with Ubuntu installed (not on a separate partition, but "within" windows)

I solved the problem by using Shadow Explorer (to access Vista's shadow copies, for windows 7, see note below)

I copied the most recent versions of 'wubildr' and 'wubildr.mbr' to my flash drive and rebooted (leaving the flash drive plugged in)

It booted up just fine, not sure why it works :confused:, my best guess is the 'wubildr' and 'wubildr.mbr' files were corrupted on my hard drive.

Not a permanent solution, but if it works, I am not going to complain.:D

Note: If you are using windows 7, simply right click on 'wubildr' and 'wubildr.mbr' (separately) and select properties. Under the 'Previous Versions' tab select a previous version and click 'open', then copy the files to a flash drive.

---

### Post by oap108 on 2011-07-26
I had this problem as well: 
Error.cannot find GRLDR in all devices. Press ctrl+alt+del to restart

I solved it quite easily after checking some blogs. 
I searched the WUBILDR.* files on my Windows 7. They were located on the ubuntu folder. I copied -not moved- the 3 files directly to c:/
and it worked!!
:)

---

### Post by ArlieS on 2013-01-28
I've got the same problem, Ubuntu 12.04.1 LTS, also a windows installer (wubi) installation . I've booted in windows, and see that the files wubildr and wubildr.mbr are still present in C: They are also present in c:\ubuntu\winboot.   

For what it's worth, the _second_ time I booted windows after the first ubuntu boot failure, it insisted on running CHKDSK and found and corrected all kinds of stuff. 

The maddening thing though, is that AFAIK there had not been a recent crash of either Ubuntu or windows. How do I get FS corruption without a crash? :confused: 

I copied the files and rebooted - no luck. 

Opening a new thread for this, since my version is not yet solved.

---

### Post by hoffiusp on 2013-02-06
Hello,

I've got the same error.  I did a windows install of Jolicloud (ubuntu) on D: partition. I'm using Vista. 
I've looked for the files wubildr' and 'wubildr.mbr but instead I only found jolibildr en jolibildr.mbr.  I've copied it to my C: but didn't work.
How can I get tot shadow explorer? Any suggestions?

---

### Post by kundu92 on 2013-06-03
Hi there,

I am running Win 7, with Ubuntu 12.04 LTS installed within Windows (installed using WUBI).
I encounted the same problem.

I just copied the <WUBILDR.*> files from under **C:\ubuntu\winboot** to **C:\** and it worked like a charm upon reboot. :D

Cheers!

---

