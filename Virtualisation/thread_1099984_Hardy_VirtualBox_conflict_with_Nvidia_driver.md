---
title: "Hardy VirtualBox conflict with Nvidia driver?"
date: 2009-03-18
forum: Virtualisation
---

### Post by JerryI on 2009-03-18
I am very new to linux and Ubuntu (about 10 days experience).  I have installed VirtualBox inside Hardy (64 bit) and have put XP in VirtualBox.  

1) I cannot get the VirtualBox window to be more than approx. half the height and half the width of my 22 inch monitor. Am I missing something, or is that as good as it gets?

2) Before I installed VirtualBox and XP my Nvidia driver was working fine with Twinview for an effective 40-inch wide screen.  I have two Acer 22 inch monitors. Now only the primary monitor works.  
If I type sudo nvidia-settings I get the response 'command not found'
If I type sudo apt-get install nvidia settings the response is 'couldn't find package nvidia'
If I type sudo /etc/init.d/gdm restart
The computer restarts and hangs within a few seconds.  I then have to turn it off and on via the mechanical switch to get a good reboot back into Hardy.

After my latest boot, System > Administration > Hardware Drivers shows NVIDIA accelerated graphics driver (latest cards) enabled - in use.  Now I can type sudo nvidia-settings to pull up the application that allows me to reconfigure to twin view.  Can someone help me understand why my configurations don't seem to stick and help me fix the problem?  Spending an extra hour fixing stuff every time I reboot isn't very rewarding.

Thanks.

---

