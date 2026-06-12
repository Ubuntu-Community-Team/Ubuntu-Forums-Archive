---
title: "New here, need help installing windows 10"
date: 2018-08-20
forum: Windows
---

### Post by vvitch2 on 2018-08-20
So basically its a long story and to skip 10 paragraphs of my life, my computer was busted, i installed ubuntu onto a stick and installed it, it fixed it. And basically ive realised that i actually want windows 10 back, but i basically destroyed the usb stick. And i dont have any dvds. Long story short: Is it possible to download windows 10 with just the iso and a laptop running ubuntu?

---

### Post by cclothier on 2018-08-20
If you have access to a Windows machine, go to [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10) and use the tool to create the Win10 installation media.

---

### Post by oldfred on 2018-08-21
UEFI or BIOS hardware & install of Ubuntu?
You will need to install Windows in same boot mode UEFI or BIOS. 
And Windows only installs in UEFI mode to gpt partitioned drives or only to MBR partitioned drives with BIOS.
If you install in the wrong mode, it will convert drive's partitioning and in effect erase Ubuntu.
Just be sure to boot in same  boot mode as Ubuntu and drive partitioning must also match.

---

