---
title: "Kernel issue - Linux 6.11.0-8-generic vs Linux 6.11.0-9-generic"
date: 2024-11-01
forum: Ubuntu, Linux and OS Chat
---

### Post by marcsonfire on 2024-11-01
Hi all, 

I'm relatively new to Ubuntu, so please bear with me as I explain my issue as best as I can.


I recently upgraded to Ubuntu 24.10 via the Software Updater, and everything went smoothly. However, after running the Software Updater again last week, the update process failed partway through. I submitted a report through the GUI and was told it’s the same issue as noted here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2068107](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2068107)


Since that failed update, my computer now hangs on the HP flash screen whenever I boot up (I’m on an HP z440 workstation with dual monitors, which becomes relevant soon). If I go into the boot menu and manually select "Linux 6.11.0-8-generic," the system starts fine and both monitors work. But if I let it boot normally or select "Linux 6.11.0-9-generic," it either hangs at the HP logo or shows a blank screen.


Interestingly, if I boot into Linux 6.11.0-9-generic in Recovery Mode, the system does boot up, but only one monitor is active, and it doesn’t seem to recognize the Nvidia graphics card. In the System Details, under "Graphics," it just lists "Onboard Graphics" instead of showing "NVF1" as it does when using Linux 6.11.0-8-generic.


Does anyone have any ideas on how I can fix this, so I don’t need to go into the boot menu every time I turn on my computer?


Thank you in advance for any help! Please let me know if there’s any other information I can provide.

Marc

---

### Post by grahammechanical on 2024-11-01
I do not have the solution but I can explain something. When we load Ubuntu using Advanced Options>recovery mode>Resume we load to a desktop using an open source video driver Nouveau) and not the proprietary video driver (Nvidia). A reboot will load the proprietary video driver.

May I suggest that you open Software and Updates>Additional Drivers tab. If the system is connected to the internet some proprietary video drivers will be found. Disable the one that is presently being used an choose another one. It may be that the Nvidia driver in use does not Linux kernel.

Regards

---

