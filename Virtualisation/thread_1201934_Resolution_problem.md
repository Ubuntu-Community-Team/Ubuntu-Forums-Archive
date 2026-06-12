---
title: "Resolution problem"
date: 2009-07-01
forum: Virtualisation
---

### Post by cardpogi on 2009-07-01
Hi to all, well what's happening to me is that im runing ubuntu netbook remix on my accer aspire one and  have a virtualbox with windows Xp black edtion, I get the 800x600 1024x768, etc but i want to get the 1024x600 resolution so when i set it to full screen i get a fullscren windows xp? anyone can help out with this?

---

### Post by nemodot on 2009-07-01
Did you installed the guest additions?

Devices->install guest additions

---

### Post by cardpogi on 2009-07-02
Uhm... think it made it kinda worst, now i only get 600x480 and 800x600.. XD any other ideas?

---

### Post by Perryg on 2009-07-02
Once you have the guest additions installed (if they installed properly) You use the mouse drag or host key combination to change the Windows screen size  (Host + F) = Full screen, (Host + L) = seamless.  These are toggle keys so use them to return to normal as well.  The color depth can still be changed in the Windows VM.  One other thing that you must have set in the settings of the VM must have at least 10 meg of Video Memory to achieve full screen.

---

### Post by cardpogi on 2009-07-02
I can use full screen but i cant fill the screen it leaves a blank space, and when i go to 1024x768 its too big for the screen and i can't see some things like the start up button etc...

---

### Post by Perryg on 2009-07-02
If you have black areas around the window in full screen mode then the guest additions did not install properly.  I would try it again.  If you click on install guest additions from within the guest and under the device tab of the VirtualBox window and nothing happens then click devices again and then unmount the CD/DVD and click on install guest additions again. You should see that they are installing and be told to reboot the VM. Manually setting the screen size in Windows will always give you improper results.

---

### Post by cardpogi on 2009-07-02
Ok so thanks for the help, lots of thanks. :) I didnt notice after installing guest additions the auto-resize button was on, so what i did Is host+f to go to full screen, and thne host+g to autoresize to the full res.. thanks!

---

### Post by Perryg on 2009-07-02
You're welcome.  Enjoy.

---

### Post by bmullan on 2009-10-17
> **cardpogi said:**
> Hi to all, well what's happening to me is that im runing ubuntu netbook remix on my accer aspire one and  have a virtualbox with windows Xp black edtion, I get the 800x600 1024x768, etc but i want to get the 1024x600 resolution so when i set it to full screen i get a fullscren windows xp? anyone can help out with this?

are you sure your _netbook_ supports higher resolutions. 1280x800 is about the highest I've seen.

---

