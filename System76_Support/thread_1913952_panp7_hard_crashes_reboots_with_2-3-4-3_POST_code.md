---
title: "panp7 hard crashes reboots with 2-3-4-3 POST code"
date: 2012-01-23
forum: System76 Support
---

### Post by arch_o_median on 2012-01-23
My panp7 has intermittently crashed since I got it, averaging perhaps a crash-a-week.  The frequency seems to be increasing approaching something like once-a-day.

  The crash has distinctive characteristics:

(1)    It doesn't appear to happen when I am not using the machine.  That is, I've never left the computer on for a long period of time without interacting with it, then returned to the machine to find it crashed.  

(2)   I have the impression there's a correlation with displaying movies, but it _certainly_ has occurred when I was _not_ watching movies.

(3)   When the crash occurs all input and output freezes.   That is, keyboard and mouse become completely non-responsive.   The screen ceases to show any variation.

(4)   The caps-lock LED and Scroll Lock LED indicators, on the front LED panel begin flashing on and off together with a period of about 1 second.

(5)   Upon hard rebooting the machine emits the Power-On Self Test (POST) beep code:  2-3-4-3

   I searched for this pattern and found this result:  "  2-3-4-3 Display non-disposable segments. "  at this url:  [www.computerhope.com/beep.htm]("http://www.computerhope.com/beep.htm") .   This result is for the Phoenix BIOS, which is consistent with this query:

$ sudo dmidecode | grep -A1 BIOS
SMBIOS 2.6 present.
35 structures occupying 1871 bytes.
--
BIOS Information
        Vendor: Phoenix Technologies LTD


(6)  After emitting this POST code the machine is unresponsive, and must be power cycled a second time.


  OK, that's all I can think of at the moment.   Thanks in advance for all your help!

--arch_o_median

Model: panp7

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:        10.04
Codename:       lucid

$ uname -a
Linux <HOSTNAME> 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:32:42 UTC 2011 x86_64 GNU/Linux

---

### Post by isantop on 2012-01-23
It sounds like you're having a kernel panic. Would it be possible for you to create a separate installation of Ubuntu on a smaller partition to test with? This would allow you to run a more recent kernel and ensure that the issue is software, and not hardware.

---

### Post by arch_o_median on 2012-01-23
I'm backing up my data now prior to partitioning with gnu-fdisk.  Once it's partitioned which version of Ubuntu should I install?

   Also I notice that the crashes correlate with playing movies and/or opening firefox on a flash containing web-page when I have flash installed.    I've seen mention of the video card being implicated in crashes that emit this kind of POST code.

---

### Post by isantop on 2012-01-24
That's a possibility.

I would recommend 11.10, since it's the latest version. We always recommend running the latest version of Ubuntu (except under very rare circumstances).

---

