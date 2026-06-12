---
title: "Firefox update automatically"
date: 2024-01-30
forum: The Cafe
---

### Post by VMC on 2024-01-30
Title is the question.

The answer is:
```
**sudo chown -R <user>:<user> /opt/firefox**
```

My "**Settings **> **General **> **Firefox Updates"** is set for auto install updates, but has never worked.

I got tired of downloading firefox, unzipping, then copying firefox folder to "/opt".
The answer is easy peasy.

I'm answering my own question so I don't forget where to look. :)

PS: If your using Snap Firefox. No idea :(

---

### Post by oldfred on 2024-01-30
I use the ppa and have had no issues.

You also have to reset priorities as shown or it will reinstall the Firefox snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)

---

### Post by ajgreeny on 2024-01-31
You're obviously using the .tar.bz (or is it .tat.gz, I'm not on my Xubuntu OS at the moment) which is what I use having removed the total snap infrastructure from my machines.
As I'm the sole user I just leave the firefox archive in its own folder in Downloads and it works faultlessly. I do however create a symbolic link from that Downloads executable to /usr/bin/firefox to allow cli command **firefox** to work as usual.

---

### Post by Frogs Hair on 2024-02-01
A .deb is available per the FF 122 release notes , but you need to add the repository as outlined in the instructions. I have used the instructions on two installations.   

[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions)

---

### Post by #&amp;thj^% on 2024-02-01
i have no issues with mine as well...
The links by oldfred an Frogs Hair lay it out nicely.
I've added a extra step:
```
echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
```
That command disables automatic Firefox updates from the Snap repository.

---

