---
title: "Getting Brave and Monero into the Ubuntu Software Repository"
date: 2019-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by thumbult on 2019-11-22
I got Ubuntu 19.10 on my HP Compaq Elite 8300 with a Nvidia GeForce 1660 Ti and I really love the system. I really thought that the ZFS filesystem is an amazing thing and the graphics driver works so well I can watch High Definition movies practically without even using the processor with VLC.

I would really love to be able to use the system more but am having trouble with obtaining access to outside software using the apt command.

Who would I need to talk to in order to get Brave Web Browser, and Monero Wallet into the official Ubuntu software repository so I could install it without needing to add anything?

---

### Post by Frogs Hair on 2019-11-26
You would  have to contact the developers of both applications . Brave is in the snap store , but is community maintained and not the latest version. They update when they have time.

---

### Post by SeijiSensei on 2019-11-27
You can add the Brave repository to apt so it will be updated along with everything else on your system.

Run this command:
```
sudo echo 'deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ [version] main' > /etc/apt/sources.list.d/brave.list
```
replacing [version] with the code name for your version of Ubuntu, "eoan" for 19.10.

Then run "sudo apt update; sudo apt upgrade" and the most recent version of Brave will be installed if it is newer than the one you have. The current version is 1.0.1.

---

