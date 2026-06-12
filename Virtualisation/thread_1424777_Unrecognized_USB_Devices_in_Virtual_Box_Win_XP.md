---
title: "Unrecognized USB Devices in Virtual Box Win XP"
date: 2010-03-08
forum: Virtualisation
---

### Post by qprfact on 2010-03-08
Hi, I am running Win XP Pro in Virtual Box 3.1.4 in Ubuntu.

The reason is two fold - 

1. To get MSN Messenger with webcam working (Pidgin in Ubuntu is fine for everything else) - although I have just seen about emesene and so will give that a go!

2. To run iTunes and allow syncing with an iPod Touch

iTunes is installed and runs fine, but the big problem I have is that some USB devices are not being recognized (the webcam and the iPod).

They appear in the "Settings" section of Virtual Box, but in the Win XP session they do not even appear in the section at the foot of the screen (it says no USBs). 

But the USB mouse and keyboard *DO* work. So there is clearly some USB functionality.

I am probably doing something really daft, but having spent the best (or worst) part of 6 hours on this yesterday, I need to put a general plea out.

Thanks in advance

---

### Post by pirlo89 on 2010-03-08
I don't think that you can use your usb devices that are connected to your host (ubuntu) in your guest (win xp) using virtualbox. You need to use vmware for that. What virtualbox does to your mouse and keyboard is capture the movement of a mouse and the keystrokes of a keyboard.

---

### Post by qprfact on 2010-03-09
I finally got the iPod working last night - I had to follow the procedure here - [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB) - and then reboot a couple of times for it to work

---

