---
title: "Security on Linux"
date: 2013-02-06
forum: Security
---

### Post by Juniorr on 2013-02-06
Hello.

I came with a question today:

If I download and burn a Ubuntu (or any other Linux Distro) on an infected Windows system, what's the risk on having problems?

---

### Post by lisati on 2013-02-06
*Thread moved to **[Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338")**.*

---

### Post by sammiev on 2013-02-06
You will have no problems at all and you can install a AV program into linux to clean the window OS as well.

---

### Post by bodhi.zazen on 2013-02-06
Who knows the risk ?

What you do is check the hash

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You check the iso, burn the iso, check the burn.

It is not fool proof, but it is as close as you are going to get.

---

### Post by DuckHook on 2013-02-08
> **bodhi.zazen said:**
> Who knows the risk ?
What you do is check the hash...
...You check the iso, burn the iso, check the burn.
It is not fool proof, but it is as close as you are going to get.

+1
Clear-eyed, pithy and finds the heart of the matter. Lao Tzu would approve.

---

### Post by mike acker on 2013-02-10
.........um the disk probably needs a low-level format

the reason being: in Windows: you may have picked up a Master Boot Record virus.

the MBR Virus is the Master of Root Kits. The MBR Virus activates during boot up and cripples your system before the OS is running .

typically the MBR Virus alters your system so that its existance is not reported or accessible . hence A/V software running under the O/S may not be able to detect or remove the virus

the MBR Virus would probably be written for Windows and might not work on a 'Nix box

but as 'Nix is rapidly gaining in popularity I would not bet on that .

this is also a reason you do not want to run dual boot .  I would try WINE before I even thought about Dual Boot

---

### Post by mike acker on 2013-02-10
Adobe/Flash: two new hits 

> The first of them, CVE-2013-0633, works by tricking Windows users into opening a Word document containing malicious Flash content, while the bug, cataloged as CVE-2013-0634, can be exploited via Apple’s Safari or Mozilla’s Firefox browsers in both platform as well as Word documents booby-trapped with malicious Flash content on Windows.

Reference
[http://www.techspot.com/news/51586-adobe-issues-emergency-flash-update-warns-of-active-exploits-on-windows-and-os-x.html](http://www.techspot.com/news/51586-adobe-issues-emergency-flash-update-warns-of-active-exploits-on-windows-and-os-x.html)

why does flash get hit and hit and hit again and again ?

an application program -- and Flash is a component used in application  programs -- should not be able to modify the host o/s that it runs under

this should not happen in a Linux system: you have to use sudo (and be authorized to use sudo ) -- in order to update your o/s .

so why does it happen all the time in windows ? i suspect it has to do with these Remote Procedure Calls:   see:
[URL=http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/]("http://ubuntuforums.org/URL=http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/")

where does the executable code for flash run ?  in userland (as in Linux ) ? or in the kernel and activated by a "RPC" ?  if windows is running that in kernel mode and activating it via an RPC then that would explain why they have trouble with it twice a week .

---

### Post by aerokid240 on 2013-03-07
If you get hit with a virus, the best thing you can do is a fresh reinstall or restore the OS from an image. Once it system has been compromised it cannot be trusted, even if your AV thinks it got rid of it.

---

