---
title: "Video Out Switcn Pangolin Value (panv2) laptop"
date: 2007-08-04
forum: System76 Support
---

### Post by jvslice on 2007-08-04
My computer is a Pangolin Value (panv2) laptop and have tried to follow the instruction on a previous post which dealt with a Seval Performance laptop, which has a Nvidia graphic driver,. My laptop uses Intel for its graphics driver.

I have had no luck on getting an external monitor to work.  

I hooked up a monitor - ATI MicroScan F720 to the laptop as a test bed with no luck.  Any help would be appreciated, I will not be able to try anything after this weekend since I will be on the road, and in two weeks will be teaching a course using PowerPoints (Impress) and would love to get this working on my System76 laptop.

---

### Post by jvslice on 2007-08-04
Additional Information
While rebooting, during grub startup, I tried using the Fn-F3 keys and was able to transfer the screen between the laptop and the external CRT.  But once logged in still unable to transfer between the two.  Well at lease this indicates that thr hardware is OK.

---

### Post by thomasaaron on 2007-08-06
Open a text editor: gedit
Paste the following code in (without the code tags).
Save it to your Desktop as video-switch.sh
Make it executable: sudo chmod a+x ~/Desktop/video-switch.sh

Now you can double click the text file's icon, and then click run, to cycle through the vga out options ( LCD only, LCD + External Projector/Monitor, Ext. Monitor Only).

You could also create a launcher on your upper panel to run it.

Code:

> #!/bin/sh
#filename: video-switch.sh

switch=`cat /proc/acpi/asus/disp`

switchChange=`expr $switch + 1`

if [ $switchChange -gt 3 ]; then
switchChange=1
fi

echo $switchChange > /proc/acpi/asus/disp

exit 0



---

### Post by jvslice on 2007-08-07
I have followed all of the above instructions, but I am unable to shift to an external monitor while in linux, only during reboot before the kernel loads.  While on the road this week I have access to an external LCD monitor.

Please let me know, what additional data is needed to find a solution.

thanks

---

