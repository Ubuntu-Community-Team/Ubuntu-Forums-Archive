---
title: "Why is nvidia so unstable against the ubuntu-server edition kernel?"
date: 2019-09-03
forum: Server Platforms
---

### Post by lukeeee2 on 2019-09-03
have set up nvidia driver / cuda using deb and runfile installation  methods on more than a dozen different computers all running ubuntu  16.04 - the desktop installs typically very stable but the server  editions have about a 50/50 chance of the driver failing to build against a  kernel upgrade - I've tried mixing up which version of the driver I  install but it doesn't seem to make a difference. Why is it so unstable  on the server edition and is there anything I can do to improve  stability?
I find it particularly confusing as I thought that the server  and desktop kernels were the same?

---

### Post by TheFu on 2019-09-03
Take up the issue with the driver maker.  Directly installing packages using the .deb file is an anti-pattern.

---

### Post by Frogs Hair on 2019-09-03
Hello and Welcome!
 
Proprietary drivers can't be improved by Ubuntu developers or the community. Does the open source driver perform well enough ?

---

### Post by oldfred on 2019-09-03
I believe even nVidia says not to use the .run if your distributor has the driver available.

Your Ubuntu install has nVidia drivers available and newer or newest drivers are available via the ppa.

       Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[URL="http://ubuntuforums.org/showthread.php?t=2261714"]http://ubuntuforums.org/showthread.php?t=2261714

      [/URL]
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
    [URL="http://ubuntuforums.org/showthread.php?t=2261714"]
[/URL]

---

