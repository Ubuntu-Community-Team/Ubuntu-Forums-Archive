---
title: "How can a Bluetooth keyboard that requires a code entry be paired in Ubuntu Touch?"
date: 2015-11-24
forum: Ubuntu Phone and Tablet
---

### Post by ZICODIAN on 2015-11-24
I have a Bluetooth ThinkPad 2 Tablet keyboard ([http://www.amazon.com/Lenovo-Thinkpad-Tablet-Bluetooth-Keyboard/dp/B009ZN8TEM](http://www.amazon.com/Lenovo-Thinkpad-Tablet-Bluetooth-Keyboard/dp/B009ZN8TEM)) and I want to pair it with my Ubuntu Touch Aquaris E4.5. Due to GUI limitations, I want to try to do this in the terminal. I'm hoping that the process'll be similar to that on Ubuntu Desktop.


On Ubuntu Desktop 15.10, when pairing the keyboard, the following message is presented in a GUI dialog:


> Please enter the following PIN on "ThinkPad keyboard" and press "Enter" on the keyboard:
<6-digit number>


Entering the 6-digit PIN on the Bluetooth keyboard and pressing Enter completes the pairing of the keyboard and it works fine. When I try to pair the keyboard on Ubuntu Touch, no GUI dialog is presented displaying the code that is to be entered on the Bluetooth keyboard. So, I want to try to pair the keyboard in the terminal.


I have tried the following:


```
phablet@ubuntu-phablet:~$ hcitool scan
Scanning ...
        AB:CD:EF:GH:IJ:KL       ThinkPad Keyboard
phablet@ubuntu-phablet:~$ bluez-simple-agent AB:CD:EF:GH:IJ:KL
RequestPinCode (/org/bluez/863/hci0/dev_AB_CD_EF_GH_IJ_KL)
Enter PIN Code: 0000
Release
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout
phablet@ubuntu-phablet:~$

```

What should I try next?

---

