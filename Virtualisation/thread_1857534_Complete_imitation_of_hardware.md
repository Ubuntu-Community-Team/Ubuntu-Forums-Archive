---
title: "Complete imitation of hardware"
date: 2011-10-10
forum: Virtualisation
---

### Post by CrystalMV on 2011-10-10
Hello. I have been using Ubuntu for three months and I love this OS. However, I still have it installed into Windows file system via Wubi. Now I think it's time to make a full installation alongside Windows. However, I don't like messing so much with computer because that's risky, especially if for some reason I need to uninstall Ubuntu and keep Windows working properly. Because I'm a careful person, I decided to try doing all these actions in an emulator first. But I don't know what emulator to choose. It seems like many of them can only run specific operating systems. But if I understand correctly, emulator which completely imitates x86 hardware should be able to run any software designed for x86 with no problems and no need to adapt it to any OS. My question is, what emulator would you recommend me to test risky things and get accurate results?

---

### Post by LinuxFan999 on 2011-10-10
Try Oracle's Virtualbox, it's fast and has a lot of features. It is the closest to native speed out of all emulators and virtual machines.

Here's the website: [www.virtualbox.org](www.virtualbox.org)

---

### Post by bcbc on 2011-10-11
If Wubi runs on your machine, then a normal install will run the same - Wubi only virtualizes the disk, the hardware access is direct.

On the other hand, anything you do in a virtual machine does not show how Ubuntu will run on your machine as there is a layer of hardware abstraction there.

If your issue is installing/uninstalling - then the only thing you need to understand is that Windows requires the Windows bootloader. So after installing Ubuntu as a normal dual boot, when you want to uninstall it, you'll need to reinstall the windows bootloader first (and this is incredibly simple), before deleting/reformatting the Ubuntu partition. That's it.

---

