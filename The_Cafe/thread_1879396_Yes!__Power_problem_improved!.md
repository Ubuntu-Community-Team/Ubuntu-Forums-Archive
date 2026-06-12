---
title: "Yes!  Power problem improved!"
date: 2011-11-11
forum: The Cafe
---

### Post by nrundy on 2011-11-11
Here's a Phoronix report
[http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1)

Preying that Ubuntu incorporates this fix in 12.04LTS

---

### Post by ikt on 2011-11-11
> **nrundy said:**
> Preying that Ubuntu incorporates this fix in 12.04LTS

Don't prey on ubuntu =o

Just speak to the relevant developers and you'll get an answer. (most are on IRC or contactable via email)

---

### Post by JDShu on 2011-11-11
Technical question: when the issue with ASPM first arose, I had wondered if the Linux kernel could pretend to be the Windows kernel in order to work with hardware, and that seems to have been the right answer. What kind of uncertainties were there that made kernel developers unsure if they could take this approach? Just a matter of needing more reverse engineering?

---

### Post by Cardamominal on 2011-11-12
I had always gotten better performance in terms of power usage with Arch Linux on my Netbook as opposed to Windows, but I'm glad this problem was fixed. I've always wanted a battery that lasts for 6+ hours.

---

### Post by 3rdalbum on 2011-11-12
> **JDShu said:**
> Technical question: when the issue with ASPM first arose, I had wondered if the Linux kernel could pretend to be the Windows kernel in order to work with hardware, and that seems to have been the right answer. What kind of uncertainties were there that made kernel developers unsure if they could take this approach? Just a matter of needing more reverse engineering?

Pretty much. It wasn't enough to say to the BIOS "I'm a Windows OS", it had to actually behave in a Windows-specific way to get the hardware to relinquish control. It seems to have required some detective work and reverse-engineering to figure out how Windows convinces the hardware to give over control.

Unfortunately, the correct way of engineering these devices would be to tell the truth to the BIOS and get the BIOS to handle this; but the devices didn't do it, therefore there was a problem. It goes to show you that hardware manufacturers don't really care about doing things the right way; for them, if it works on whatever versions of Windows they currently support, then it's "good" even if it is a dirty hack that might break in the future.

---

### Post by JDShu on 2011-11-12
> **3rdalbum said:**
> Pretty much. It wasn't enough to say to the BIOS "I'm a Windows OS", it had to actually behave in a Windows-specific way to get the hardware to relinquish control. It seems to have required some detective work and reverse-engineering to figure out how Windows convinces the hardware to give over control.

Unfortunately, the correct way of engineering these devices would be to tell the truth to the BIOS and get the BIOS to handle this; but the devices didn't do it, therefore there was a problem. It goes to show you that hardware manufacturers don't really care about doing things the right way; for them, if it works on whatever versions of Windows they currently support, then it's "good" even if it is a dirty hack that might break in the future.

That is unfortunate... does this also mean that as new Windows versions come out, all that old hardware is going to stop working on modern OS's? And how would Linux deal with supporting both new and old hardware?

---

### Post by mafi127 on 2011-11-12
how can I instal it to ubuntu 11.10?

---

### Post by LowSky on 2011-11-12
> **mafi127 said:**
> how can I instal it to ubuntu 11.10?

Compile the new kernel yourself. Hopefully it doesn't screw things up.

---

