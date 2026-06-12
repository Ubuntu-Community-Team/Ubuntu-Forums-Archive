---
title: "Can only install downloaded packages from command line"
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by Psychobudgie on 2014-04-03
Hi,

Bit of an odd one this. Since an update last week I have only been able to install third party packages via dpkg using the command line. If I attempt to install anything other than from the repos via software centre or app grid the install fails but offers no error. Just simply informs me that it failed. No errors or warnings via apt-get or dpkg. Does anyone have any ideas what the issue could be?

---

### Post by ajgreeny on 2014-04-03
Install synaptic with ```
sudo apt-get install synaptic
``` and then see if you can use that to install packages you want.

If you already have the packages downloaded try installing and using gdebi, which you may find tells you more than USC.

Either way, I would suggest that **synaptic** and **gdebi** are both worth adding to any new install of the *ubuntu family of OSs.
I have no idea what you mean by **app grid**.

---

### Post by Mateusz Stachowski on 2014-04-03
Synaptic isn't good for installing external packages but I agree that it is worth adding to any new install. Gdebi is what you need for installing external packages in GUI. Install it and then right click on any .deb package and go to properties to set gdebi as default for opening this type of files.

Also this is a bug which is reported and you could check "affects me too": [(14.04) Unable to install external deb packages "Package operation Failed"]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228")

App Grid is a light-weight alternative to Ubuntu Software Center but it is closed sourced.

[http://discourse.ubuntu.com/t/app-grid-discover-and-install-apps-for-your-computer/960](http://discourse.ubuntu.com/t/app-grid-discover-and-install-apps-for-your-computer/960)

---

### Post by Psychobudgie on 2014-04-04
> **Mateusz Stachowski said:**
> Synaptic isn't good for installing external packages but I agree that it is worth adding to any new install. Gdebi is what you need for installing external packages in GUI. Install it and then right click on any .deb package and go to properties to set gdebi as default for opening this type of files.

Also this is a bug which is reported and you could check "affects me too": [(14.04) Unable to install external deb packages "Package operation Failed"]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1290228")

App Grid is a light-weight alternative to Ubuntu Software Center but it is closed sourced.

[http://discourse.ubuntu.com/t/app-grid-discover-and-install-apps-for-your-computer/960](http://discourse.ubuntu.com/t/app-grid-discover-and-install-apps-for-your-computer/960)

I searched high and low for that bug, so thank you very much for pointing me to it. I atleast realise I am not going mad. I've added my self to the affected and will persevere with dpkg until it is patched.

Thanks again

---

