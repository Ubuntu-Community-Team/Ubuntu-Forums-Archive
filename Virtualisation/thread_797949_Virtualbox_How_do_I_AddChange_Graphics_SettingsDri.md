---
title: "Virtualbox: How do I Add/Change Graphics Settings/Drivers for Kubuntu?"
date: 2008-05-17
forum: Virtualisation
---

### Post by OzzyFrank on 2008-05-17
OK, I know how to change screen resolutions, and I've had my fair share of fun with display drivers, but this question has to do with the display of Kubuntu running under Virtualbox. It installed with what I assume are just some basic drivers, and the max/default screen res is 800x600, which I can't change to a higher one, obviously. How do I go about giving Kubuntu better drivers so I up the screen size?

In the virtual Windows XP I installed a day earlier the default size was 800x600, but I was able to go into Display Properties and increase that (though there were no resolutions for widescreen, which I can live with). What can I do about Kubuntu? Can I copy over my **xorg.conf** from my *physical* Ubuntu/Kubuntu system to the virtual one? I tried looking in Virtualbox settings for something that could help, but didn't see anything. How do I proceed? Cheers

---

### Post by gareth_005 on 2008-05-17
You may need to install the virtual box guest additions drivers.
I only use xp in VirtualBox, not linux. Check if there is an option to mount/install the guest additions cd in the guest.

Copying your xorg-config won't work as the guest has a virtual video driver, not the real one.

---

