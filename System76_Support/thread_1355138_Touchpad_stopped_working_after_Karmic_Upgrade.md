---
title: "Touchpad stopped working after Karmic Upgrade"
date: 2009-12-14
forum: System76 Support
---

### Post by Piggah on 2009-12-14
I upgraded to karmic today, and ive been having some issues. I've installed the system76 driver through system > administration > sys76 driver and rebooted and my touchpad is not responding at all. 

I tried to do a sys76 factory restore but that didnt seem to do anything. I'm quite unhappy with karmic right now and would like to go back to jaunty with all of my laptops components working properly, is there a way to restore? 

ive got a pangolin p5 driver version 2.4.0


thank you :)

---

### Post by gamerchick02 on 2009-12-14
Did you happen to hit Fn-F1 at any time?  That shuts off the touchpad.  Try hitting Fn-F1 and see if that brings the touchpad back.

Amy

---

### Post by Piggah on 2009-12-14
I tried that, its not Fn+F1. 

thank you :)

---

### Post by gamerchick02 on 2009-12-14
Hrm. That's strange.

I'm not having any issues with my touchpad.

Tom Aaron might be able to help you, especially if it's a hardware issue.

Amy

---

### Post by 5BallJuggler on 2009-12-14
Have a read of this, I had the same issue

[http://ubuntuforums.org/showthread.php?t=1306012](http://ubuntuforums.org/showthread.php?t=1306012)

Hope it helps
Phil

---

### Post by thomasaaron on 2009-12-15
Please try running the following command from a terminal...

sudo apt-get install grub-pc
sudo reboot -h now

---

### Post by akwala on 2009-12-16
I have a Serval Performance, which I upgraded to Karmic (64-bit) yesterday. Following this, the touchpad stopped working.

I'm attaching the output of "xinput list" -- it doesn't list Synaptics/Touchpad. Restoring the system76 drivers didn't help, nor did reinstalling xserver-xorg-input-synaptics.

I also created /etc/hal/policy/shmconfig.fdi with the following contents, which didn't help either:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">true</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
      <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```Does the solution in this thread apply to my situation? If not, any ideas?

---

### Post by thomasaaron on 2009-12-16
Yes, give my suggestion above a try.

---

### Post by akwala on 2009-12-16
> **thomasaaron said:**
> Please try running the following command from a terminal...

sudo apt-get install grub-pc
sudo reboot -h now

This worked. 

However, I got "error: command not found 'initrd'" at the first reboot attempt. I fixed it using the Karmic install CD: "Rescue a broken system" -> Reinstall GRUB. After this, I rebooted, and the touchpad is working again.
****

---

