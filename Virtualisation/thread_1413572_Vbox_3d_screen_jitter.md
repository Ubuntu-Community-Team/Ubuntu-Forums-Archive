---
title: "Vbox 3d screen jitter"
date: 2010-02-22
forum: Virtualisation
---

### Post by vickelly on 2010-02-22
windows 7 using VirtualBox 3.1.4 to host Ubuntu 9.10 with guest additions installed.

this one has had me stumped for more than a month. the basic issue is that when I'm running ubuntu in windowed mode I have a full set of resolutions to choose from and am able to use rotate cube without issue. once I switch to full screen all hell breaks loose. it will manage to resize to 1920 by 1080 but no longer will rotate cube work properly. the screen strobes and jitters. if I change my resolution I loose the ability to switch back to the first. slowly making my screen size smaller and smaller. what's going on? what can I do to fix this? 

please let me know If I can provide any additional information.

---

### Post by yogesh.girikumar on 2010-02-23
Hi,


       To fix this issue, you can try enabling 3D acceleration feature of VirtualBox. Open VirtualBox, Click the VM and Click Settings.


       Under Display settings window, check the checkbox that says "Enable 3D Acceleration". Also please make sure if Video Memory is set to **at least** 12 MiB.

---

### Post by vickelly on 2010-02-23
yogesh,

thank you for the reply. currently my vbox has 3d acc enabled and is set the the max 128mb of video memory. 

I'm fairly sure this isn't a speed issue... I let vbox access all 4 of my processor cores and 4gb of ram. :confused:

I've tried tweaking every setting I can think of.

I just noticed that as of the vbox update I no longer loose my resolution option. I can switch back form say 1024x786 to 1920x1080
I only experience the issue when at my full 1920x1080 res. if I bump it down all of my visual effects work fine....:confused:

this is also regardless of whether I have vbox set to boot into full screen or not.

---

### Post by vickelly on 2010-02-23
I guess it has been awhile since I updated my ati drivers. now with the most current revision for my card hd4890 everything works fine.

---

