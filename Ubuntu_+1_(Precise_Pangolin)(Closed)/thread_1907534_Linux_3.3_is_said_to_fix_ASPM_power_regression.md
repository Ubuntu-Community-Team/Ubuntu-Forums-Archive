---
title: "Linux 3.3 is said to fix ASPM power regression"
date: 2012-01-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-11
The irritating ASPM power regression is said to be finally fixed in the next linux kernel 3.3.

Here is the Phoronix article on this issue:
[http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM](http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM)

---

### Post by JMB74 on 2012-01-11
***"Canonical, however, has already pulled this into their Linux 3.2 kernel for the forthcoming Ubuntu 12.04 LTS release." ***

---

### Post by cariboo on 2012-01-11
> **JMB74 said:**
> ***"Canonical, however, has already pulled this into their Linux 3.2 kernel for the forthcoming Ubuntu 12.04 LTS release." ***

Citation please.

---

### Post by JMB74 on 2012-01-11
Here: [http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM](http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM)

The commit into the precise kernel I believe.

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commit;h=77bcc2b0626a8bcb9e76b030a159a32e2e075b53](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commit;h=77bcc2b0626a8bcb9e76b030a159a32e2e075b53)

Which is the patch discussed here:

[http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=2)

that didn't make it into 3.2 mainline.

---

### Post by xyzzyman on 2012-01-11
Unfortunately launchpad's already been cleared of earlier releases, but the ASPM patch was added back in Ubuntu's build of RC3 or RC4.

---

### Post by phibxr on 2012-01-18
> **cariboo907 said:**
> Citation please.

It seems like this was supposed to have been included, but that it has been dropped again.

"Unfortunately the i915 RC6 patch was dropped with commit 371de6e4e0042adf4f9b54c414154f57414ddd37 because the RC6 fix still seems to make some systems freeze and as yet we've not got a reliable list of hardware that fails with rc6. The current recommended solution is to enable rc6 using i915.i915_enable_rc6=1 for hardware that doesn't lock up."

[[Source]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/913886")]

---

### Post by JMB74 on 2012-01-18
> **phibxr said:**
> It seems like this was supposed to have been included, but that it has been dropped again.

"Unfortunately the i915 RC6 patch was dropped with commit 371de6e4e0042adf4f9b54c414154f57414ddd37 because the RC6 fix still seems to make some systems freeze and as yet we've not got a reliable list of hardware that fails with rc6. The current recommended solution is to enable rc6 using i915.i915_enable_rc6=1 for hardware that doesn't lock up."

[[Source]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/913886")]

No. That is an entirely different intel graphics specific power saving patch set they are trying to bring in for their new chipsets.

Nothing to do with the long standing ASPM regression.

---

### Post by xyzzyman on 2012-01-18
If you download the source of ubuntu's 3.2 kernel you'll see the ASPM patch [https://lkml.org/lkml/2011/11/10/467](https://lkml.org/lkml/2011/11/10/467) has been backported into the corresponding files.

---

### Post by dino99 on 2012-01-18
And some good investigations:

[http://smackerelofopinion.blogspot.com/2011/12/improving-battery-life-in-ubuntu.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ASmackerelOfOpinion+%28A+Smackerel+of+Opinion%29](http://smackerelofopinion.blogspot.com/2011/12/improving-battery-life-in-ubuntu.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ASmackerelOfOpinion+%28A+Smackerel+of+Opinion%29)

[https://wiki.ubuntu.com/Kernel/PowerManagement](https://wiki.ubuntu.com/Kernel/PowerManagement)

on my side i'm already following these ideas and ready to report to get best results. Hopes you do too :)

---

