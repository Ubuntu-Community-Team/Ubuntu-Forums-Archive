---
title: "Installing onto Asus Q87T Motherboard"
date: 2015-08-21
forum: Server Platforms
---

### Post by fizgig on 2015-08-21
Been ripping my hair out to get any recent version of Ubuntu server running on this motherboard with an SSD hard drive.  I've tried it with UEFI enabled and 14.04 64bit server.  I've tried it with the CSM activated and everything set to legacy and installed Ubuntu server without UEFI.  No matter whay I do, I get an unstable system - Many times I can get it to boot just fine with no issues.  Most of the time though, I get a BIOS error screen that says the following:

"The current BIOS setting do not fully support the boot device.  Click OK to enter the BIOS Setup.
Go to Advanced > Boot > CSM Parameters, and adjust the CSM settings to enable the boot device."

I do that and have tried everything.  I've disable the security mode (deleted the keys and set OS to "other").  Does anyone have any tips on anything else I can try?

---

### Post by oldfred on 2015-08-21
I installed to an Asus Z97-AR and had to change a lot of UEFI settings. And I only could get it to boot flash drive in UEFI mode with UEFI only. Not even UEFI & CSM mode.
There was a Setting for Windows or Other, I think that is the Secure boot UEFI setting. I changed to Other, but Ubuntu should boot with Secure Boot on.
I always partition in advance and used gpt and created my ESP & 25GB / (root) partition on SSD with large data partition on hard drive. 

I did not adjust any timings as I want reliability not speed. 
I turned fast boot off orginally and then changed to fast boot off on cold boot and 3 sec delay on fast boot if a warm reboot, so I could get into UEFI settings. Otherwise too fast to hit key. And fast boot can be too fast to see USB drive as bootable device.
It seemed very strange that many UEFI settings were under the CSM setting.
Set USB boot to UEFI only. I think this was under CSM settings?
Boot from Storage devices with UEFI.
Boot from network ignore, so not trying to check Internet while booting.

If you removed keys, you will  not be able to boot with Secure boot which is probably the Windows setting.

---

### Post by fizgig on 2015-08-21
Thanks for the reply.  My latest settings appear to match yours and no dice.  Going to send this machine back.

---

