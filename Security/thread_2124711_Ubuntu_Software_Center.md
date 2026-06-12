---
title: "Ubuntu Software Center"
date: 2013-03-11
forum: Security
---

### Post by galfly on 2013-03-11
Hi,

Ubuntu requires elevated privileges to install some software. In the pop-up where the root password is asked, if you click on details, you see "Action" and "Vendor". What's the purpose of Action? Nothing happens when I click on "Install or remove packages"

Thanks

---

### Post by cariboo on 2013-03-11
The action option in details, shows the command that will be used for the action ho have started. See the screenshot. To install a package it will use apt-get install, and to remove a package, it will use use apt-get remove.

---

### Post by galfly on 2013-03-11
Thanks for the screenshot, I don't see org.debian.apt.install, but only "Install or remove packages".

---

### Post by cariboo on 2013-03-11
> **m@ya said:**
> Thanks for the screenshot, I don't see org.debian.apt.install, but only "Install or remove packages".

I'm running Raring (13.04), so there may be a bit of difference in versions, I don't use the Software Centre, so I normally don't see any changes that are made to newer versions. I'm still a happy synaptic user. :)

---

