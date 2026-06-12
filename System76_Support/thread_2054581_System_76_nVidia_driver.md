---
title: "System 76 nVidia driver"
date: 2012-09-07
forum: System76 Support
---

### Post by kend650 on 2012-09-07
I am currently running Nvidia driver version 295.40 on my System 76 bonobo with 12.04.  The current release driver version for the 560M graphics card is 304.43.

I have three questions:

1)  Does System 76 provide updates to their GPU cards?

2)  Should I update the graphics card driver from the nVidia website? 

3)  What is System 76's recommendation on updating nVidia graphic cards?

Thanks

---

### Post by kend650 on 2012-09-15
Can System 76 please answer this question!!

---

### Post by Ubun2to on 2012-09-17
Installing drivers you find online is generally not a good idea, as the packages already in the repos are already tested, whereas online drivers can have no credibility yet still be listed. I forget the other reason why you do not install drivers you find online but are available in the repos-something about the installer process is different, and it does not install properly sometimes (if my memory serves correctly).
When updates are available, if the proprietary drivers are enabled, they will be pushed to you via the update manager.
All updates are made by nVidia, unless you are using the open source Nouveau drivers, and I do not know how those work (I mean the update process-I'm not sure if they have their own PPA, or if they are in the official repos).
You do not need to manually update the drivers unless you are working at nVidia and testing the drivers before releasing them, or just feel like taking a risk.

---

### Post by MoebusNet on 2012-09-17
+1

Unless you are attempting to solve a video driver problem, I would recommend waiting for Ubuntu to offer an update. Nvidia typically issues a driver update to fix a problem; for example xorg-server version has been updated to a newer version that the video driver does not support as happened to the nvidia-96 driver.

As long as your current video driver is meeting your needs (performance, stability etc.) I would just relax and leave it alone.

Just my opinion, YMMV.

---

### Post by kend650 on 2012-09-18
Thank you for the response.  This is the reply I expected.

The only problem I am seeing is the display blanks our occassionally for a few seconds, and then comes back to a normal display.  It doesn't happen frequently enough to warrant the hassel of a driver upgrade.  

I guess my real concern was who is responsible (System 76, Ubuntu, or nVidia) for making sure that the nVidia driver I have is the most latest stable version I should be running with the OS I'm currently using?  

Where will it show up in the System Settings (Additional Drivers, System 76 drivers, or the NVIDIA X Server Settings app???)

---

### Post by Ubun2to on 2012-09-19
> **kend650 said:**
> Thank you for the response.  This is the reply I expected.

The only problem I am seeing is the display blanks our occassionally for a few seconds, and then comes back to a normal display.  It doesn't happen frequently enough to warrant the hassel of a driver upgrade.  

I guess my real concern was who is responsible (System 76, Ubuntu, or nVidia) for making sure that the nVidia driver I have is the most latest stable version I should be running with the OS I'm currently using?  

Where will it show up in the System Settings (Additional Drivers, System 76 drivers, or the NVIDIA X Server Settings app???)

nVidia is the one responsible for the drivers, and the official Ubuntu repository developers are responsible for making sure the drivers and updates make their way down to the users.
If there are additional drivers that have been released after the computer was shipped, they should be available in the Additional Drivers (my ATI card has FGLRX drivers and FGLRX Post Release updates, neither is enabled (and the Post Release Updates always failed during install), as I installed the Catalyst Control Center so I could use multiple monitors, and I guess that disabled the drivers).
nVidia X Server Settings is for things like adjusting and configuring multi-monitor setups (which is quite nice to have in my experience) and modifying other video card settings like hardware acceleration (I have an AMD because of what came with my system, so I am not sure if all the AMD Catalyst Control Center options are the same on nVidia).
The System76 Drivers app is for easy updates for the hardware, to make sure that it is compatible with Ubuntu.
Basically, when there are updated drivers, they will come to you via the Update Manager.

---

