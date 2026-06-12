---
title: "Install problem?"
date: 2010-03-02
forum: Virtualisation
---

### Post by Whisp3r on 2010-03-02
I had VirtualBox 2 running on my machine, and my little dropdown menu for upgrade was greyed out. So I went ahead and uninstalled VB, and downloaded and installed a fresh new 3.1.4.

When I try to install it, I get the following error:

Code: Select all   Expand viewCollapse view
    Unpacking virtualbox-3.1 (from .../virtualbox-3.1_3.1.4-57640%5fUbuntu%5fjaunty_i386.deb) ...
    Setting up virtualbox-3.1 (3.1.4-57640_Ubuntu_jaunty) ...
    addgroup: The group `vboxusers' already exists as a system group. Exiting.
    Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
    Success!
    * Starting VirtualBox kernel module                                           
    * modprobe vboxnetflt failed. Please use 'dmesg' to find out why

    dmesg:
    [160455.680697] vboxdrv: Successfully loaded version 3.1.4 (interface 0x00100001).
    [160455.887939] vboxadd: exports duplicate symbol AssertMsg2 (owned by vboxdrv)




Help please? :)

---

