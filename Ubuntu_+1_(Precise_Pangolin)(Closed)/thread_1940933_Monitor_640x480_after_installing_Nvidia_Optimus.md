---
title: "Monitor 640x480 after installing Nvidia Optimus"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jeggy94 on 2012-03-14
i followed the instructions on this page [http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04](http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04)
I have been trying to get dual-screen for a long long time now, so i just followed those instructions and where he says it should be 86 frames per seconds which i had but after restarting my monitor got 640x480 and i got over 300 frames per second. and when i open 'NVIDIA X Server Settings' and get this error 
```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
``` after that i restarted my computer and thats when this 640x480 thing started...

---

### Post by nbubis on 2012-04-10
Just had the same problem. After two hours of playing around I finally found this:

[http://askubuntu.com/questions/17892/failed-to-load-module-nvidia](http://askubuntu.com/questions/17892/failed-to-load-module-nvidia)

To the OP: did you ever get bumblebee installed properly on precise?

---

