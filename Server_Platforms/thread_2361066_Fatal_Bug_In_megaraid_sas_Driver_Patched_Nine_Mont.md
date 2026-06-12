---
title: "Fatal Bug In megaraid_sas Driver Patched Nine Months Ago, But...?"
date: 2017-05-11
forum: Server Platforms
---

### Post by JSeymour on 2017-05-11
Ran into this bug when trying to bring up a new 16.04 LTS server: [Exceptional levels of kernel spam about “MR_DCMD_PD_LIST_QUERY failed/not supported by firmware”]("https://askubuntu.com/questions/793815/exceptional-levels-of-kernel-spam-about-mr-dcmd-pd-list-query-failed-not-suppor")

It appears it was patched back in August, 2016: [[PATCH 4.7 068/186] megaraid_sas: Do not fire MR_DCMD_PD_LIST_QUERY to controllers which do not support it]("http://lkml.iu.edu/hypermail/linux/kernel/1608.2/02189.html")

According to [Upgrade 16.04.2 LTS to kernel version 4.8? [duplicate]]("https://askubuntu.com/questions/885054/upgrade-16-04-2-lts-to-kernel-version-4-8"), my new install *should* have gotten kernel 4.8, which, I presume, would have had the patch, but, the highest kernel level in /boot is 4.4.0-77.

So how do I get 4.8.x in my new install?

Thanks,
Jim

---

### Post by #&amp;thj^% on 2017-05-11
Have a look: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by JSeymour on 2017-05-12
> **1fallen said:**
> Have a look: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Ah!  Great, 1fallen.  Thank you very much!

---

### Post by #&amp;thj^% on 2017-05-12
Your Very Welcome..:)

---

