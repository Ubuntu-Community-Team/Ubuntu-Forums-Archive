---
title: "adb won't find my device when trying to install Ubuntu Touch"
date: 2015-10-10
forum: Ubuntu Phone and Tablet
---

### Post by enekoalfer on 2015-10-10
Hey!

I am an Ubuntu 14.04 User, and I was trying to install Ubuntu on my tablet following the official instructions ([https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)), but when I tried to use adb for the android backup with this command:  ```
$ adb backup -apk -shared -all
``` or for unlocking the tablet with this other one: ```
$ adb reboot bootloader
```I got this: "error: device not found".

When I write down this one: ```
adb devices
``` on the terminal, I get nothing. Nevertheless, the tablet appears as connected (in the tablet and the laptop).

I was wondering if anyone knows how to solve this. I am still pretty new with Ubuntu, and I haven't found any type of solution yet although I have been trying many different options.

By the way, the tablet is a BQ Maxwell 2 Plus (with Andorid 4.1.1), if it is important to know.

Thanks!

P.D.: Today I tried to connect my phone. This is also not found (BQ Aquaris E5 HD with Android 5.0).

---

### Post by handaxe on 2015-10-11
You might try moving the cable around the available usb ports on your desktop/laptop and even a different cable. I have read reports of that helping.

Oh, yes there were discussions of this on the[ Ubuntu-Phone]("https://launchpad.net/~ubuntu-phone") mailing list

---

### Post by enekoalfer on 2015-10-11
I have tried with all ports and 2 different cables :( Nevertheless, I will try with another one just in case.

Thanks handaxe!

---

### Post by enekoalfer on 2015-10-13
Nevermind, finally I was able to do it on my own. I had to edit the file HOME/.android/adb_usb.ini, and add "0x2207" there (in the last line). When I plugged the tablet I used *adb devices* and it was there, so problem solved. I copy the link here just in case it is useful for someone else.

[http://www.slatedroid.com/topic/41219-connecting-to-a-rk3066-based-board-via-adb-on-linux/](http://www.slatedroid.com/topic/41219-connecting-to-a-rk3066-based-board-via-adb-on-linux/)

Thanks!

---

