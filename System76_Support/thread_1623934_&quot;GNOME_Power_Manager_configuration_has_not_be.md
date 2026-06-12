---
title: "&quot;GNOME Power Manager configuration has not been installed correctly&quot; on Star3"
date: 2010-11-17
forum: System76 Support
---

### Post by 130s on 2010-11-17
I just bought star3 notebook and tried upgrading to 10.10 using Update Manager. Installation got stuck in the middle, so I restarted OS and then I found I can't log on. Details about phenomenon and what I did are below.
What do you recommend to work around? The only option I have in mind now is clean installation to either 10.04 LTS or 10.10. I prefer giving a try to 10.10, but since the reason why I prefer 10.10 is relatively trivial (i.e. a Japanese language engine called mozc is supported on 10.10 I heard), I can listen actively to your advises.

- Phenomenon
After boot, log-on window shows my user ID but it only turns to show "10.10" when I click there to log on as it used to be on 10.04. At the same moment, an error message also appears like "GNOME Power Manager configuration has not been installed correctly".

Actually I can log-on to CUI mode by ctrl + F2 (safe mode? I don't know how to call it), but no idea how to start full GUI mode. It has no ip address and I haven't tried to connect to the existing wireless network which it used to connect to on 10.04.

- What I did
1. Keep external battery off. This is because when I tried using Extra Battery Extra 6 Cell, GUI freezes at some random point.
2. Did everything up to task 8 in "Upgrade from 10.04 LTS to 10.10 Network Upgrade for Ubuntu Desktops (Recommended)" section in [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades) . This includes applying all available updates.
3. Reboot OS using GUI menu on right top, when progress bar halted at 31% for 7 hours or more at the installation process. I was unable to read what was the last process shown on console during installation since the console window was larger than the display area and it went lower than the boundary.

---

### Post by isantop on 2010-11-17
I'd say that's a botched installation. Go ahead and try a LiveUSB. You can use either 10.04 or 10.10, though we recommend 10.04 for the moment. If you'd like to test 10.10, you can, but be sure to click "Try Ubuntu" before installing, and give it a good test run to see if you like it or not. I say this because if you install it, then decide you don't like it, you will not be able to create a 10.04 LiveUSB from 10.10.

---

### Post by 130s on 2010-11-18
Thank you isantop. 
Now I've been trying to boot from LiveUSB but star3 seems not recognize LiveUSB as a boot device. Since the problem is different, I opened a new thread here: [http://ubuntuforums.org/showthread.php?p=10132812#post10132812](http://ubuntuforums.org/showthread.php?p=10132812#post10132812)

Isaac

---

