---
title: "System76 Serval screen resolution"
date: 2009-05-13
forum: System76 Support
---

### Post by oliverm on 2009-05-13
I've got the new System76 Serval with the 1920x1200 screen. When I present seminars I like to match the resolution of the projector, 1024x768. Using the latest Nvidia driver 180.44 and the nvidia-settings app, I'm only seeing 1280x1024 and 960x540, but no 1024x768 option.

Any ideas how I can set the resolution to 1024x768?

Thanks

---

### Post by thomasaaron on 2009-05-13
I see you posted a question in launchpad. Let's just go ahead and handle it in one forum... This is probably the best place.

Please provide more info on the brand and model number of your projector. Since we do not have the third-party hardware to test with, this could take some experimentation. Most likely, it will require manual editing of your xorg.conf file.

---

### Post by thomasaaron on 2009-05-13
Also, (and you have no idea how much I hate asking these questions), do you have the projector plugged into the dvi port and powered on?

If not, nvidia-settings will report resolutions available, but probably not the one you need.

---

