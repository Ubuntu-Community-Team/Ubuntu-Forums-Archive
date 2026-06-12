---
title: "Kernel 4.15.0-13 - HP Spectre x360 (13-ae005na) does not power off"
date: 2018-03-27
forum: Ubuntu Development Version
---

### Post by jblocke on 2018-03-27
Folks, anybody running Bionic on HP Spectre x360 13-ae005na? It looks like the recent kernel 4.15.0-13 does not allow to power off the machine and simply reboots instead. I see a launchpad bug #1756455 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1756455](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1756455) reported by an owner of similar machine (ae004). Anybody else affected?

---

### Post by dino99 on 2018-03-27
which is the exact kernel used ? Is the bios/uefi uptodated ? How is it set for booting ? (legacy/efi)
What warnings/errors journalctl  expose ?
 note that the coming 4.16 kernel has other PTI tweaks; maybe test  the latest 4.16 in case of some useful changes in your case.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by jblocke on 2018-03-27
Well, I seem to have exactly the same situation as the guy submitted #1756455: 4.15.0-13.14, latest (F.15A) BIOS, UEFI, secure boot is on but makes no difference because bug is reproducible with secure boot off. 4.15.0-10.11 "just works". Nothing suspicious or unusual  in the logs, because, well, what a successful shutdown is supposed to leave in the logs? But anyway, nothing **different** in the logs for 4.15.0-10.11 and 4.15.0-13.14

Not quite sure how PTI may affect that but I'm open to any troubleshooting suggestions. So will try 4.16 later today. Thanks a lot!

---

### Post by dino99 on 2018-03-27
so its time to send a linux report to explain that issue, and saying that 4.15.0-10 was ok; that will help to bisect the faulty commit

---

### Post by jblocke on 2018-03-27
Could you please advise, what would be the best way to bring ubuntu dev's attention to the bug? #1756455 has been sitting there since March 16th, and I do not have much to add besides simple "me too". If I just update [#176455]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1756455") I am afraid nobody is going to notice.

BTW, 4.16rc7 works just great and powers off device correctly.

---

### Post by dino99 on 2018-03-27
even if that look close to #176455 , its title pointing to 'reboot' is not the main cause of that hardware problem.

so open your bug via 'ubuntu-bug linux'  with the title 'Kernel 4.15.0-13 - HP Spectre x360 (13-ae005na) does not power off' and the details you have given here.
If later dev declare it as duplicate, that does not really matter, but at least you will grab a chance to get a fix more quickly (the initial report is out of radar at time)

---

### Post by jblocke on 2018-03-27
Great. Thanks a lot for clear instructions!

---

