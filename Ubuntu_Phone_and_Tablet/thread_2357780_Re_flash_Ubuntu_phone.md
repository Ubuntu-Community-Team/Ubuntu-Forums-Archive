---
title: "Re flash Ubuntu phone"
date: 2017-04-06
forum: Ubuntu Phone and Tablet
---

### Post by woody2707-3 on 2017-04-06
As Ubuntu phone is now officially dead&#128580; can someone please point me in the right direction for flashing my mx4, Bq 5hd and m10 tablet to android if I need to. I don't want to do this but might need too as I cant afford to have this amount of non useable stuff. Also how stright forward is it to do comparedvto say putting Linux onto a laptop.
Thanks for any help.

---

### Post by dumazdamaz on 2017-04-09
I don't know about any other devices except for MX4. This is quite easy. It is not similar to installing to a laptop. However, it is not complicated either. Phones have a separate mini OS called a recovery. You can flash this with a linux tool called fastboot. You can either use Meizu's own one (See link) or you can use one of the fancy ones that gives you much freedom (like twrp). Then after that you can use the recovery miniOS/bootloader to install either Flymes Os, which is Meizu's own OS, but it is essentially their tuned version of Android, or you can install Cyanogen mod, wich is known to work with MX4. You can use adb tools to send the img to the phone. After that you just reboot into the bootloader/recover and select install. The Meizu OS is Android 5, but they also have a Android 6 beta image, that you can install if you so wish (after you get the stable OS working).

See this thread:
[https://forum.xda-developers.com/meizu-mx/general/ubuntu-to-flyme-t3143297](https://forum.xda-developers.com/meizu-mx/general/ubuntu-to-flyme-t3143297)

---

### Post by woody2707-3 on 2017-04-15
Thanks for the info. Will have a look into it soon. As said don't want to change but might be forced too in the future.

---

### Post by Gone fishing on 2017-04-16
I'm very sorry Ubuntu phone is being killed, I liked my MX4 and thought it had real potential, however I've flashed mine to flyme 5.1.12.0G using instructions I found here [https://forum.xda-developers.com/general/rooting-roms/disccusion-developing-meizu-mx4-custom-t3120673/page14](https://forum.xda-developers.com/general/rooting-roms/disccusion-developing-meizu-mx4-custom-t3120673/page14) the instructions were a pdf see attached. I also then added Google Play Store, to make this easier Flyme has an app called Google Apps Installer, it can be found in flyme's own store called "Hot Apps" you'll find it in Featured > more.

Not been on the forums for a while[-(

PS I rooted mine which is very easy in Flyme there is a button you click and its done!

---

### Post by woody2707-3 on 2017-04-16
Thanks very much.Will have a look at getting it done. Can't be doing with this state of limbo now, and can't think of anything to do but put android on one of them.

---

### Post by RobGoss on 2017-04-16
You might want to head over to **XDA** forum they have all the knowledge that's needed about flashing phones

best of luck

---

### Post by paeschli on 2017-04-17
Here is the guide to flashing Android Lollipop: [http://www.mibqyyo.com/comunidad/discussion/75471/is-there-any-guidance-i-can-replace-the-ubuntu-with-android-for-m10-fhd/p1](http://www.mibqyyo.com/comunidad/discussion/75471/is-there-any-guidance-i-can-replace-the-ubuntu-with-android-for-m10-fhd/p1)

It's really sad that the people who invested in this project now have to choose between unusable and unsupported Ubuntu software or an outdated version of Android. I would absolutely love to be able to flash the latest version of LineageOS on my M10 tablet.

---

### Post by woody2707-3 on 2017-04-19
Thanks for your help looks straight forward enough. Still annoyed about the whole situation, but best make the most of it. Might even try and sell the MX 4 just incase someone has a use for it&#128514;&#128514;&#128521;

---

### Post by woody2707-3 on 2017-04-20
One last question on this. What does the fastboot screen on the phone look like. After holding down start and volume up button, I get a blank screen with the Ubuntu symbol in the middle of it. Is this correct? Just wanted to check before carrying on, haven't done this before so just taking my time to check everything.

---

### Post by woody2707-3 on 2017-04-20
sorry about that all done and working thanks for the help

---

### Post by wlbi on 2017-05-03
Probably the MagicDeviceTool is a very good solution for changing the os on a device.
I tried that already on my BQ M10 FHD tablet and it works great.
[https://github.com/MariusQuabeck/magic-device-tool](https://github.com/MariusQuabeck/magic-device-tool)

**Functions and supported operating systems**

[LIST]
[*]Ubuntu
[LIST]
[*]Install Ubuntu Touch
[*]Switch Channels
[*]Install OpenStore
[*]Screencast
[/LIST]

[*]Android
[LIST]
[*]Install CyanogenMod (with or without GApps)
[*]Install LineageOS (with or without GApps)
[*]Install Maru OS
[*]Install Sailfish OS
[*]Install Phoenix OS
[*]Install Factory Android Image
[*]Backup / Restore
[*]Lock / Unlock bootloader
[*]Install TWRP recovery
[/LIST]
[/LIST]
 [B]
Supported devices[/B]

[LIST]
[*]BQ Aquaris E4.5 (krillin)
[*]BQ Aquaris E5 HD (vegetahd)
[*]BQ Aquaris M10 HD (cooler)
[*]BQ Aquaris M10 FHD (frieza)
[*]Meizu MX 4 (arale)
[*]Meizu Pro 5 (turbo) removed until Marius can get his hands on this device
[*]LG Nexus 4 (mako)
[*]LG Nexus 5 (hammerhead)
[*]Asus Nexus 7 2013 WiFi (flo)
[*]Asus Nexus 7 2013 LTE (deb)
[*]Samsung Nexus 10 (manta)
[*]OnePlus One (bacon)
[*]Fairphone 2 (FP2)
[/LIST]

---

### Post by Wadim_Korneev on 2017-08-22
Good information [COLOR=#000000] about flashing Android Lollipop [/COLOR]http://www.mibqyyo.com/comunidad/discussion/75471/is-there-any-guidance-i-can-replace-the-ubuntu-with-android-for-m10-fhd/p1

---

