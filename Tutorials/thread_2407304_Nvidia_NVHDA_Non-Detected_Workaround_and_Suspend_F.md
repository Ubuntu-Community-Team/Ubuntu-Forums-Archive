---
title: "Nvidia NVHDA Non-Detected Workaround and Suspend Fix for NVHDA"
date: 2018-12-02
forum: Tutorials
---

### Post by markackerman8@gmail.com on 2018-12-02
NVHDA Still an ISSUE - Ubuntu may never become Newbie Friendly without solving this ...

... Until this seemingly simple fix is put into the mainline kernel, ... WORKAROUNDS BELOW;)

Nvidia HDA, is completely UNDETECTED through the HDMI port (which it is obviously designed for) with out the below fix (I am happy to put all these confusing necessary steps that MAY scare aware ANY Newbies) 

SO read this and put it into the kernel PLEASE UBUNTU!!!!

Note - this is on a bleeding edge Hp OmenX Laptop, with Nvidia's GTX1080M, Ubuntu 18.04 LTR and/or Ubuntu 18.10 does not solve the problem. Nor does any newer kernels using UKUU.

Also, After Sleep or Hibernation - WHICH IS Working (at least Suspend - Hibernation is still problematic requiring restarts after its' use - FIX THIS UBUNTU (I digress), ... 
... The aforementioned NVHDA Module (which SADLY needs to be manually installed), has to be ...

SADLY reloaded in TERMINAL OR the computer NEEDS TO RESTART TO SEE NVHDA and HDMI Audio, and obviously  WON'T WORK.:cry:

Here are the NON- USER FRIENDLY Workarounds !! :p

I hope this helps others ... :;)

TO install the module which is needed to even show my NVHDA, here is the work around
Solution - Install a Kernel module to toggle audio function.
&#8728; I can confirm that kernel module, posted by 
&#8227; Maik Freudenberg :guitar:

[HTML]https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27[/HTML]

• Kernel module to toggle audio function
&#8728; is working fine on my system. Thank you for the fix. The HDMI audio device now works as it should (now detected).

&#8728; The steps I did to enable HDMI audio device:
• 1. Download and extract the file nvhda.tar.xz. (from above link)
• 2. Run these commands in Terminal, in the location of the extracted folder 

Code:
```
make

sudo make install

echo nvhda | sudo tee -a /etc/initramfs-tools/modules

echo "options nvhda load_state=1" | sudo tee /etc/modprobe.d/nvhda.conf

sudo update-initramfs -u
```
&#8227; 3. Reboot.
Done .. Now it will be detected! :p

For Hibernate/Suspend Issue (NOT loading this module after waking up! :confused:)
• However, if I manually disable the audio output output "sudo tee /proc/acpi/nvhda <<< OFF" I'm then able to get it to sleep. I then have to turn it on again on resume with "sudo tee /proc/acpi/nvhda <<< ON


```
sudo tee /proc/acpi/nvhda <<< OFF
```
(before Hibernation/Suspend or Sleep)


```
sudo tee /proc/acpi/nvhda <<< ON
```
(After Resume)
• SOLVED! I

Plus some great news for newbies to end off on a good note!

My myriad of apci errors have magically vanished! with the new 4,19 Kernel (using UKUU)
MANY people are having Install problems and Boot problems on newer systems related to these acpi errors

GREAT news for them I HOPE! 

Always Trying to help, Mark

---

### Post by vidtek on 2018-12-02
Mark-
I can also report that all my boot errors have gone too:-
 > My myriad of apci errors have magically vanished! with the new 4,19 Kernel (using UKUU)

This is using Kubuntu 18.04 with a 4.19 kernel on my Asus Strix 270 i7 mobo.

I had a particularly annoying USB pci error string that caused a 3 minute boot delay.  As you say, very annoying, now fixed brilliant!

A big thank you to all who put their time and unpaid effort into this new kernel.
Tony

---

