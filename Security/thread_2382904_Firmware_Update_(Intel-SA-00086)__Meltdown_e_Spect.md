---
title: "Firmware Update (Intel-SA-00086)  Meltdown e Spectre"
date: 2018-01-18
forum: Security
---

### Post by espectro2 on 2018-01-18
About update  Bios in ubuntu 16.04 after the episode Meltdown and Specter everyone is  recommending update bios this INTEL-SA-00086 tool replaces the firmware  update via page of the official site of the motherboard?
this update replaces the bios update through the official website?
Thanks for listening

What exactly do they mean in this Intel-SA-00086 Detection Tool User Guide
It is not just to extract tar.gz and execute the command followed by sudo or root python ./intel_sa00086.py
I need to do something else before I do not understand what to do with this filespsInfoLinux64
Thank you for your attention.

[https://www.intel.com/content/www/us/en/support/articles/000025619/software.html](https://www.intel.com/content/www/us/en/support/articles/000025619/software.html)
[URL="https://usn.ubuntu.com/usn/usn-3531-1/"]
https://usn.ubuntu.com/usn/usn-3531-1/[/URL]
[URL="https://www.intel.com/content/www/us/en/support/articles/000025619/software.html"]
[/URL]

---

### Post by DuckHook on 2018-01-19
The detection tool that you have linked to has nothing to do with Meltdown and Spectre. Instead, it refers to a different problem with Intel CPUs that is explained [here]("https://arstechnica.com/information-technology/2017/11/intel-warns-of-widespread-vulnerability-in-pc-server-device-firmware/"). I also posted on this issue [here]("https://ubuntuforums.org/showthread.php?t=2382017").

To use the tool, both the python script *intel_sa00086.py* and the library *spsInfoLinux64* (the latter can be found inside the "common" subdirectory) must be executable. On my copy, once extracted, the executable bit for both files was already set. You should be good to just go ahead and run it.

Note that the ME vulnerability is, in some ways, even worse than Meltdown/Spectre. It just hasn't received as much press coverage. You should also approach these issues realistically. If no one will ever have physical access to your computer except you, then for the next while at least, ME vulnerabilities are unlikely to be risks for you. If they are, then you will have to rely on your HW OEM to issue the right patches. There is nothing that Ubuntu or OS distributors can do about this one.

---

### Post by DuckHook on 2018-01-19
> **espectro2 said:**
> …this INTEL-SA-00086 tool replaces the firmware…
BTW, the tool does not replace your firmware. It just detects whether you are vulnerable. Very few manufacturers have rolled out firmware patches for this one yet. You have to wait for yours to issue such a patch (maybe contact them?). This tool just detects.

---

