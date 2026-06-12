---
title: "Broadband 2G connection"
date: 2021-11-02
forum: Ubuntu/Debian BASED
---

### Post by mike188 on 2021-11-02
In bodhi 5.1.0 there is no option for 2g connection, only 3g. In modemmanager there is no such option. I read manpage of mmcli, but still i dont understand what should i type in terminal to connect modem in 2g. Sakis3g does not have 2g option. I tried setting allowed mode in networkmanager mmcli, but i dont know the name of variable, it says couldnt match with MMModemMode value. Need detailed instructions how to do that in terminal. Is it possible to change that parameter in network manager gnome 1.8.10-2ubuntu3? Can i download earlier version of gnome with dependencies, where 2g option is present, remove the current one and replace it with that version?

---

### Post by coffeecat on 2021-11-02
*Thread moved to **Ubuntu/Debian BASED** sub-forum.*

---

### Post by mike188 on 2021-11-03
i started with reading about mmcli [http://manpages.ubuntu.com/manpages/bionic/man8/mmcli.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/mmcli.8.html) ; here when i try to set allowed mode as in the example, typing 2G or 3G it says 'Couldn't match '[3G]' with a valid MMModemMode value'; i dont know how to type that correctly.
Then i checked [https://ubuntu.com/core/docs/networkmanager/configure-cellular-connections](https://ubuntu.com/core/docs/networkmanager/configure-cellular-connections) ; it is about mmcli and nmcli; it worked;
Finally i read this [https://linuxhint.com/expertly-use-the-ubuntu-network-manager/](https://linuxhint.com/expertly-use-the-ubuntu-network-manager/) ; it is about nmcli and nmtui; it also worked. Two latter options connected modem in 2G; after this when i want to connect in 3G it connects only in 2G, even after i delete connection, disable networking and fill all fields again. I need to be able to connect 2G most of the time and sometimes 3G. What should i specifically  type in the <words> in the lines to set allowed mode in instruction 1, get values of MMModemMode, ect?

After another reboot it again connects to UMTS, HSPA only, using all mentioned methods; so maybe it is a random process. I need to be able force modem to connect to 2g or 3g in command line.

---

