---
title: "ubuntu 10.x kvm guest"
date: 2010-10-10
forum: Virtualisation
---

### Post by sob04 on 2010-10-10
Hi everyone,

I have tried Ubuntu 10.04 and Ubuntu 10.10 (64 bits) kvm guests on a Debian host (64 bits, qemu-kvm 0.12.5) and responsiveness is horrible. I've had no problem in the past with Solaris/Windows/Debian guests. Is there any known limitation with Ubuntu as a kvm guest, or any tuning I got wrong?

Thanks

---

### Post by jaksun5 on 2010-10-15
I'm not speaking from experience, but since troweling the forums for my own kvm solutions I've noticed that a couple of people (albeit for XP Guests) advise to turn ACPI off if guest is stalling with no cpu activity

---

### Post by sob04 on 2010-10-15
The acpi is not running on the guest, and only acpi_cpufreq is running on the host.

So there must be something else... but thanks :)

---

### Post by naugtur on 2010-10-18
I am hesitating between KVM and Vbox for my little server and it'd be nice to know the answer to that too. 

First guest system would be winxp for my friends to use with a project, so thanks jaksun5 for your answer

---

