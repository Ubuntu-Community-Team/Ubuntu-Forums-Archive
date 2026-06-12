---
title: "Use of a virtual image for banking"
date: 2014-10-23
forum: Security
---

### Post by aeronutt on 2014-10-23
I have a virtual image of Ubuntu (run on Oracle VirtualBox) that I use exclusively for banking and other critical access (a short list of  websites that are mutually exclusive with what I use on my normal boot). Is this any more or any less secure than a) using my normal boot to access those banking/critical sites, and b) booting and accessing those banking/critical sites from a USB?

---

### Post by TheFu on 2014-10-23
[http://krebsonsecurity.com/online-banking-best-practices-for-businesses/](http://krebsonsecurity.com/online-banking-best-practices-for-businesses/) says to use a liveCD.  For VM users like us, that translates into an ISO boot, without any connected storage inside the VM.  For that, I find TinyCorePlus the best solution. Small, efficient, fast, and not a general purpose OS to be hacked.

---

### Post by aeronutt on 2014-10-23
That site says use a dedicated system....which points to my fundamental question, does a VM image count as a dedicated system in this case (for security purposes)?   I would think it would....although I guess if a key logger were active on the normal system, it could get passwords typed in during the VM access.

Why do you say it's important to have no connected storage inside the VM?

---

### Post by mikodo on 2014-10-23
> **aeronutt said:**
> That site says use a dedicated system....which points to my fundamental question, does a VM image count as a dedicated system in this case (for security purposes)?   I would think it would....although I guess if a key logger were active on the normal system, it could get passwords typed in during the VM access.

Why do you say it's important to have no connected storage inside the VM?

I would like to use a similar set up and would like to hear answers, too.

I am guessing "no connect storage inside the VM", would mean shared/hosted folders, clipboard, drag and drop and maybe bridged network configurations like, allowing connection through usb hubs to the host's hardware.

I hope, we hear more about this.

---

### Post by kurt18947 on 2014-10-24
I don't find it that onerous to have a small partition (I use about 12 GB.) with its own independent O.S. installed. I use a utility that permits more than 4 primary partitions on a hard drive.  I'm pretty sure *buntu and other distros can be installed into and will boot from within an extended partition to work around the 4 partition/disk limitation without the use of a 3rd party utility. Disregard the preceding if you're using a newer machine with U.E.F.I. and GPT, there's no 4 partition limit with that.

Another option would be to create a 'real' install on a flash drive as opposed to a live USB. A benefit of a 'real' install vs. live USB is that a 'real' install can have security and other updates installed, a live USB cannot. If you're concerned about messing up your current hard drive and you're using a desktop machine, you could disconnect your current hard drive(s).  Then boot from a live DVD/USB, plug in a target USB drive and install. Once the install completes, change your BIOS boot sequence to check for a USB drive before booting from the reconnected hard drive or select the USB drive manually during the machine's P.O.S.T.

I'm not an expert in this stuff but by using one of the above procedures, I hope I'm no longer a 'low hanging fruit' for the bad guys.

---

### Post by TheFu on 2014-10-24
> **aeronutt said:**
> That site says use a dedicated system....which points to my fundamental question, does a VM image count as a dedicated system in this case (for security purposes)?   I would think it would....although I guess if a key logger were active on the normal system, it could get passwords typed in during the VM access.

Why do you say it's important to have no connected storage inside the VM?

No connected storage means there isn't anywhere for viruses, malware, spyware to be written between boots. No connected storage of any sort - we run a liveCD using the ISO file.  It is NOT an install. There is no place for anything bad to be written to storage when online. ISOs are read-only.

I would go further and say that if the hostOS is used on the internet, there is a risk too. Only you can decide how to mitigate those risks best. The real intent is to avoid anything that could compromise any part of the solution - applications, OS, hardware, networking.  If you are not confident that the hostOS is 100% clean, then perhaps virtualizing is not the correct solution?   I do not trust Windows as the hostOS, but only you can decide on that aspect of the security.

---

