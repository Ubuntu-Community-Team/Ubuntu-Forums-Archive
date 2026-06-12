---
title: "Random Terrible Performance in Galago Ultrapro"
date: 2014-07-11
forum: System76 Support
---

### Post by Lemmywinks29 on 2014-07-11
I received my Galago about a week ago and have been having a very strange issue.

Roughly half the time that I boot my computer, things work fine. The other half of the time I get terrible performance in games and extremely low fps. This is usually fixed by rebooting the computer, but I can't figure out what the issue is.

Anyone have any thoughts?

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep VGA -A2

---

### Post by tgalati4 on 2014-07-12
It could be overheating and safety-throttling.  Seems there are a few posts on these forums for overheating and/or shutdowns on these machines.  Rebooting allows the CPU to cool down enough to function again.  Try displaying some temperatures and post what you find:

```
sensors
```

Make sure the fans are spinning.

---

### Post by Lemmywinks29 on 2014-07-12
I can't imagine it being a cooling issue, since the applications will run terribly after the computer has only been on 1 minute. I've installed sensors though

---

### Post by Lemmywinks29 on 2014-07-12
I ran lspci -knn | grep VGA -A2 				and got:

00:02.0 VGA compatible controller [0300]: Intel Corporation Crystal Well Integrated Graphics Controller [8086:0d26] (rev 08)
    Subsystem: CLEVO/KAPOK Computer Device [1558:7410]
    Kernel driver in use: i915

---

### Post by damianoj on 2014-07-13
Does the issue occur both on battery and plugged in? If it is only on battery a BiOS update may be helpful

---

### Post by KSmooth on 2014-07-14
Same issue here, try to plug in, then it should be faster :)

---

### Post by a-emma on 2014-07-15
> **Lemmywinks29 said:**
> I can't imagine it being a cooling issue, since the applications will run terribly after the computer has only been on 1 minute. I've installed sensors though

Hello Lemmywinks29. Can you please login to your System76 Account and open a support ticket in the 'my account' section? Our staff may have a different solution for you on top of the advice you've been provided in the forums. We'd love to help!

Kind Regards,
[email]Emma@system76.com[/email]

---

