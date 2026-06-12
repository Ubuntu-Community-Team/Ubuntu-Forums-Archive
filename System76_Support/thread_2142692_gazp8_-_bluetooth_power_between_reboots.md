---
title: "gazp8 - bluetooth power between reboots"
date: 2013-05-06
forum: System76 Support
---

### Post by jeebustrain on 2013-05-06
I've had my Gazelle Pro for about a week now. So far I'm really liking it (although I kind of wish the battery was a bit bigger, but that's a minor gripe). Yesterday, I got around to pairing up my bluetooth Kensington Slimblade convertible trackball and it works fairly well. One problem though is that Ubuntu doesn't seem to want to keep Bluetooth turned on between reboots. I didn't have this problem with my old laptop that had a USB BT dongle. I found a setting in the BIOS to retain BT power settings, but it causes the laptop to go insane (gets stuck at a black screen with a blinking cursor and a mouse pointer). This occurs when I set the value in the BIOS, boot into Ubuntu, turn on BT and then reboot. It never comes back up. I have to hold in the power button and flip the BIOS setting back to Disabled in order for it to boot.

I'm still going through /var/log/dmesg but so far no smoking gun. 

Does this functionality work for anyone?

---

### Post by isantop on 2013-05-06
This is actually a BIOS option. By default, we have it disable the Bluetooth at each boot to save battery. You can change this by going into the BIOS configuration and going to Advanced > Advanced Chipset Control

---

### Post by jeebustrain on 2013-05-06
> **isantop said:**
> This is actually a BIOS option. By default, we have it disable the Bluetooth at each boot to save battery. You can change this by going into the BIOS configuration and going to Advanced > Advanced Chipset Control


Yes - I found it in my BIOS (as I mentioned in my post). But whenever I turn that on, boot into Ubuntu and then enable BT (fn+F12) and then power down, If I power it back on, the laptop goes insane and gets "stuck" at a black screen with a blinking cursor. 

I can get into tty1 to view dmesg. Nothing stuck out there.

SO I rebooted from console and it came right back up to the gui login. I shut it down and then try to power it back up. Same thing.

I rebooted again via tty and went into the bios, turned off the BT power setting and rebooted. 

This time I had a complete crash (kernel panic I believe). The system was totally unresponsive (couldn't hit any console, had to power down from power button). When I did that, and powered it back on, it came up to the gui login with no issues. 


From this, it seems that there is some interaction between the BT power setting and the BIOS. I can ONLY replicate this issue if I do the following:
1. enable the bios setting
2. Boot into ubuntu
3. hit fn+F12 to enable Bluetooth. 
4. Power down (reboot does not cause the issue)
5. Power back up.

I am able to reproduce this issue 100% of the time following these steps.

---

### Post by isantop on 2013-05-06
It sounds like you have a bad installation of Ubuntu. I woud reinstall it from a fresh copy of 13.04. The Bluetooth Power Setting won't have any effect on the OS, apart from the fact that the bluetooth module will be enabled on boot.

---

### Post by jeebustrain on 2013-05-12
OK - that's not it. I did a complete rebuild from scratch (twice actually - from 2 separate downloads of 13.04 x64). I even ran md5sums on each of the downloaded ISOs and they were correct.

I still have this problem. Whenever I enable that feature, the machine will not fully load the GUI from a cold boot. I have to drop to tty2 and reboot that way in order for the machine to reach the gui login.

---

### Post by isantop on 2013-05-13
Open a support ticket on our website. This is a hardware problem.

---

### Post by jeebustrain on 2013-05-13
OK - I think I managed to track down the root cause of this issue. My boot SSD is just too damn fast. I happened be looking at a couple other threads in this forum and noticed the one about lightdm not loading properly. I noticed the behavior was almost exactly the same. So I went in and tweaked /etc/init/lightdm.conf and added "sleep 1" right above "exec lightdm" and it seems to work fine now.

My guess is that the added speed of the boot SSD makes lightdm try to execute so fast that the added time overhead of loading the BT kernel module takes it just over whatever that threshold is. It doesn't exactly explain why it doesn't occur upon a soft reboot, but regardless, it now works. I've powered down the laptop and brought it back up at least 5 times with the Bluetooth Power setting enabled in the BIOS.

---

