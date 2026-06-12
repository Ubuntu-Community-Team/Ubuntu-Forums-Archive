---
title: "upgrading to ubuntu 19.10 beta - chromium issue"
date: 2019-10-08
forum: Ubuntu Development Version
---

### Post by Claus7 on 2019-10-08
Hello,

the other day I tried to upgrade my system from 19.04 to 19.10 beta. Having already chromium in my system the upgrade was ok until chromium package was about to be installed. It required snap, since the new chromium is not installed as a pure deb package any more.

Knowing earlier, I would uninstall the aforementioned package first and then try the installation. Instead, I finished the installation using synaptic package manager since both command line (just the upgrade command) and software upgrader did not do the job.
In the meantime I tried to uninstall chromium in the middle of the upgrade process, yet having already downloaded chromium snap, still I had complaints from command line. Luckily synaptic got the job done.

Regards!

---

### Post by PaulW2U on 2019-10-10
[https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179](https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179) is the best place to report upgrade issues that affect the Chromium browser.

---

### Post by uRock on 2019-10-10
I upgraded a machine that has Chromium, though it did require the same removal of the deb and installation via snap, it didn't cause any issues with the upgrade.

---

### Post by Claus7 on 2019-10-10
Hello,

> **uRock said:**
> I upgraded a machine that has Chromium, though it did require the same removal of the deb and installation via snap, it didn't cause any issues with the upgrade.

I do not know if my issue has to do with the fact that I was using developers' kernel in the first place. Every time I was issuing the command: 
sudo do-release-upgrade -d

I was able to see that installation proceeded till chromium installation. The real problem was that instead of bypassing the installation of chromium, it stopped completely the installation without installing the rest of the packages, including the updated kernel. I do not remember the exact error I was getting, apart from the fact that the upgrade was interrupted.

While the upgrade was incomplete, I thought at that time that it was a bad idea to restart my computer, so I tried the software updater which caused packages to download anew and which, in the end, had the same result.

Since chromium seemed to be the issue, I opened synaptic and removed it. In between I had run sudo apt update, which seemed to be a bad idea since it downloaded more "updated" packages and at some point I had lost also the ability to open a terminal, because of the half-finished upgrade process. As a result I updated all packages from synaptic. In the end I saw that new kernel was installed and then I rebooted my system.

Which was working after the reboot.

Just to point that I did not use snap packages at that time, so during the upgrade it was trying to download these ones as well. It might be also a reason for the lengthy upgrade.

Regards!

---

### Post by uRock on 2019-10-10
Thanks for the info. I wouldn't have thought to give the software updater the chance to fix it.

---

