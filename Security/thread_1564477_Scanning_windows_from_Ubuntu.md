---
title: "Scanning windows from Ubuntu"
date: 2010-08-30
forum: Security
---

### Post by pivotraze on 2010-08-30
How do I scan a windows computer from my Ubuntu laptop via the network?

I have Ubuntu 10.04 on my laptop.

First Windows computer to scan has Windows XP Home Edition
Second Windows computer to scan has Windows Vista Home Basic

I have Avast 4 workstation and KlamAV insalled on it. What is the steps to make my computer scan those windows computers.

And how do I set up my firewall to work with firefox and empathy?

---

### Post by OpSecShellshock on 2010-08-30
AV scanning should really be done locally on the Windows machines. Avast has a client for Windows that can be installed, or I think they make a bootable CD that can be used (might be a better option). Either of those options would be much easier. The scan should be run while the computer is disconnected from the network (so long as the AV signature files are already up to date).

Web browsers and IM clients should not require any additional steps in order to function as long as the defaults have been maintained after installation.

---

### Post by pivotraze on 2010-08-30
I know, and I ran MalwareBytes' Anti-Malware from the windows computer in safe mode (24 viruses found btw) and want to make sure by using a 100% clean computer (so a virus can't hide itself) and scan with a powerful antivirus (avast).

Using Gufw and enabling the firewall to the "Deny" option for both incoming and outgoing makes firefox and empathy unable to connect to the internet.

---

### Post by howefield on 2010-08-30
> **pivotraze said:**
> want to make sure by using a 100% clean computer (so a virus can't hide itself) and scan with a powerful antivirus (avast).

AVG do a rescue CD

[http://www.avg.com/ie-en/avg-rescue-cd-download](http://www.avg.com/ie-en/avg-rescue-cd-download)

or you can make a bootable pen drive with Startup Disk Creator, and install anti virus on to it. Boot the computer with it and scan your windows disk.

---

### Post by OpSecShellshock on 2010-08-30
UFW can safely be set to allow out and deny in.

---

### Post by BigCityCat on 2010-08-30
Bit-defender for Linux can scan your windows drive from ubuntu.

[http://download.bitdefender.com/repos/](http://download.bitdefender.com/repos/)

add the deb repository, and then install it from synaptic. It's free.

---

