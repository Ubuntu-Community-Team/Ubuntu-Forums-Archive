---
title: "Ubuntu Unity Oracular is no go since August 31"
date: 2024-09-03
forum: Ubuntu Development Version
---

### Post by Yahoé on 2024-09-03
For the past three days, Ubuntu Unity Oracular doesn't load the GUI after a dist-upgrade. I first thought of an issue with nvidia-driver, but desinstalling it did not help. A full resinstall experiences the same issue. Where the greeter should be, I get a dark screen with the mouse point, that alternates with a black screen with a dash blinking in the upper left corner.  Anybody else had the same problem?

---

### Post by zebra2 on 2024-09-04
If your post is correct is looks like you are updating with "apt-get dist-upgrade".  You may want to switch to "apt update" and then "apt upgrade" with you updates since that command will not install the proposed repos and other not yet fully integrated updates.  If you want a full update with "apt" you would use "apt full-upgrade".  
I admit that I know nothing about the Unity desktop as it exists today but I logged into Unity Discourse and for the few posts available there is appears they are using the "apt" updater. 

Using proposed for a development version is risky.  I admit I have used Proposed with the dev version myself over the years but it is a "at your own risk" venture. In today's Ubuntu apt-get is also risky but old habits are not easy to break. I do admit I'm not sure if this applies to Unity.

---

### Post by chrismine on 2024-09-10
Since 2 days ago Ubuntu boot to splash screen showing 20 years and logo, some screen artifacts after that. I've tried reinstall ubuntu deskstop and lightdm from command line.
Also did a fresh install with the daily ISO of 6 Septmber with the same results.

Running LInux Mint currently. Will wait a few days and use a later ISO to see if problem fixed.

---

### Post by Yahoé on 2024-09-26
The dev team fixed the issue that is no longer present in the current daily. It may have been related to the greeter.

---

### Post by chrismine on 2024-09-28
I tried a fresh install on a different PC with a Nvidia graphics card and 240GB SSD drive.
Could do it because the installer gave an error.
I thus installed 24.04.1 which worked fine.
Proceed to da a distribution upgreade with sudo dp-release-upgrade -d
Rebooting and Ubuntu boot to screen with higher reolution graphics showing logo and Ubuntu 20 years. - After that just a black screen with mouse cursor.
I noticed the HDD light steady ...

---

