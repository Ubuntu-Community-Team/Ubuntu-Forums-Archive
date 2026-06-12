---
title: "system-config-printer increases CPU work"
date: 2015-03-05
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-03-05
Hello,
i don't know if i have a corrupted installation of Ubuntu (15.04) but I'm encountering a lot of problems...

This time it seems that i've found a bug on system-config-printer.
When i open "Printers", and press on "ADD" the CPU work grows up to 30-32% and doesn't go down when i close the window. The only way to stop this abnormal CPU usage is to wait 3-4 mins, put the pc on Suspend (Stanby) or reboot.

I could report it with ubuntu-bug, but there is no "system-config-printer" to select, I can choose between 
system-config-printer-gnome
system-config-printer-common
system-config-printer-udev

which one should I choose?

The strange thing is that the LXTask doesn't report any abnormal CPU usage in any process, but the CPU usage bar grows to 30%

---

### Post by dino99 on 2015-03-05
i suppose you are using Lubuntu and your (unknown) printer is powered on. If it is an usb one, then unplug/plug it , then send the printing job. And watch /var/logs/*

---

### Post by enricobe on 2015-03-05
> **9d9 said:**
> i suppose you are using Lubuntu and your (unknown) printer is powered on. If it is an usb one, then unplug/plug it , then send the printing job. And watch /var/logs/*

No, I'm using UBuntu, the "original" :)

I have no printers connectend. I start Printer looking for a network printer but when I press  ADD the CPU usage grows up. I don't have any kind of freeze or bug using the program, just a high CPU usage

---

### Post by dino99 on 2015-03-05
> **enricobe said:**
> No, I'm using UBuntu, the "original" :)

I have no printers connectend. I start Printer looking for a network printer but when I press  ADD the CPU usage grows up. I don't have any kind of freeze or bug using the program, just a high CPU usage

Are you kidding ?
LXTask , as you wrote, is used by LXDE (aka Lubuntu) not by Ubuntu. So i suppose you have , at some time, used it, then switched to Ubuntu. (Hopes you have made then some cleanings)
Then you need a 'physical' hardware (printer connected and powered one) when you ask the system to find one; is that makes sense to you ?

---

### Post by enricobe on 2015-03-05
> **9d9 said:**
> Are you kidding ?
LXTask , as you wrote, is used by LXDE (aka Lubuntu) not by Ubuntu. So i suppose you have , at some time, used it, then switched to Ubuntu. (Hopes you have made then some cleanings)
Then you need a 'physical' hardware (printer connected and powered one) when you ask the system to find one; is that makes sense to you ?
No, I have installed LXTask to see the processes. I could not find the task manager so I've downloaded only LXTask from the software center. I couldn't find the "system monitor" because the italian translation of that software is unusual. Anyway, the information displayed on System Monitor and LXTasks are the same, aren't they?

Why should I need a physical printer if i'm trying to add a network printer? I think it's strange that pressing "Add" (with or without a printer connected) the CPU goes to 30% of usage

---

