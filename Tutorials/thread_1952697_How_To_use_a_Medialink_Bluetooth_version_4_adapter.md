---
title: "How To: use a Medialink Bluetooth version 4 adapter with an Apple Magic Trackpad"
date: 2012-04-04
forum: Tutorials
---

### Post by mgmiller on 2012-04-04
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/MedialinkBluetoothAdapterWithAppleMagicTrackpad](https://help.ubuntu.com/community/MedialinkBluetoothAdapterWithAppleMagicTrackpad)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2038020](http://ubuntuforums.org/showthread.php?t=2038020)


Support threads regarding the wiki and it's content should be created in a suitable forum.


I recently got a Medialink USB bluetooth adapter.  This is their latest Bluetooth V 4.0 class 2 device.  It's very small and barely sticks out of the USB port.

Here is how I got it working with my Apple Magic Trackpad in Ubuntu 11.10.

On first install the system does not detect it as a bluetooth device.
lsusb shows the device ID as:  0a5c 21e8

I found a review of the device by Yuri Wiitala on amazon.com 03/24/2012.

To paraphrase:

Detailed explanation: This device is handled just fine by the stock btusb kernel module. The issue is that the driver does not recognize the exact USB vendor/product ID. However, the driver was fixed just a few weeks ago. It'll just take a little time for your favorite Linux distro update to pick up the fix. Yuri Wiitala

Here is the fix for now:
First, create the .conf file...
```
gksu gedit /etc/modprobe.d/medialink-btusb.conf
```Next, Paste in the following line of code...
```
install usb:v0A5Cp21E8d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe btusb; echo 0a5c 21e8 > /sys/bus/usb/drivers/btusb/new_id
```Click to save the file.

Finally, reboot and the adapter will show up as a bluetooth device in the top panel.

Next, click on the bluetooth indicator in the top panel and select Preferences.
Make sure both the Bluetooth and Visibility sliders are set to "ON".

The last thing I had to do to make my Apple Magic Trackpad work with this adapter was to briefly push and release the power button on the side of the trackpad to start the green light blinking.  If the light is not blinking, the Apple Magic Trackpad is not in discoverable mode.

While the light on the trackpad is blinking, click the + in the bottom left corner of the Bluetooth window, then click continue and while it's searching,  change the PIN options to '0000' (most headsets, mice & GPS devices), then click close.

It should quickly find the trackpad, first as a string of numbers that then changes in a few seconds to Apple Wireless Trackpad.  Click on it to select the Apple Wireless Trackpad and then click Continue.

The next dialog that opens should tell you that the pairing was successful.

The last thing I did was go to the mouse preferences and under touchpad, clicked to enable 2 finger scrolling, horizontal scrolling and Enable Mouse clicks with touchpad.
You can adjust the Acceleration and Sensitivity sliders to your preference.

The Apple Magic Trackpad now does the following:
1 finger is simple pointer motion and 1 finger tap is the same as a left click
2 finger tap is the same as a right click. (handy for easy back and forward in web browser)
2 finger vertical and horizontal scrolling works in dialog boxes and web pages
ctrl and 2 finger vertical scroll will zoom in and out (same as ctrl scroll wheel)
3 finger tap brings up the "Unity Handles" that let you easily grab a corner or edge or center of a window to move or resize it.
4 finger tap brings up the main Unity Menu (same as the super key)

That's all I could discover.  There is no "pinch zoom" that I can find although I think the ctrl 2 finger trick will work to zoom pictures is Shotwell.

If anybody finds other tricks, please let us know by posting here.

:popcorn:

---

### Post by Plaguester on 2012-05-02
[SOLVED]
I hadn't noticed that some kernel updates were being held back by apt. Upgraded from 3.0.0-17 to 3.0.0-19 and bluetooth works fine on boot. I am still having problems on resume from suspend (dmesg complains about no reset_resume for btusb and then nothing I do seems to allow me to get it back other than rebooting), but will update here if I find a solution.

[OLD POST]
I tried the conf file above and it works fine if I boot up and then plug in the device. If I try to boot with the device plugged in, it does not work and then prevents the rest of the USB devices from being detected (wireless keyboard and webcam). There weren't any useful messages in dmesg. Is there another log I can try?

---

### Post by domsom on 2012-05-06
mgmiller: Great post, thanks!

I stumbled upon this solution only after desperately googling for the ID of my BT adapter. For the search engines & everyone else with this adapter: The patch also works with a Delock 61889.

---

### Post by dougmessenger on 2012-07-17
Thanks for the help in getting my system to recognize the Medialink Bluetooth device.  It was hard to find this posting, but the perfect and simple solution.  The trackpad info was extraneous.

---

### Post by _UsUrPeR_ on 2012-12-17
Just FYI: This worked for me in Ubutu 10.04.

For search functionality purposes:

IOgear PN: GBU521
Bluetooth 4.0 USB Micro Adapter
lsusb id: 0a5c:21e8 Broadcom Corp

The two coded instructions above worked without a hitch. Prior to that, the adapter was unrecognized. Thank you so much! :D

Edit:

I got some crap iomega mouse + keyboard working. Everything's great. Apparently I also accidentally found my phone. Looks like the adapter has full functionality.

---

### Post by GUZZLR on 2013-09-07
Good Stuff...I'm definitely sold on Media Bridge products. I've got the MediaBridge router, and this by far is the best, and definitely the most stable router I've ever had...I really like it.

---

### Post by coffeecat on 2013-09-07
A reminder - from the OP:

> **mgmiller said:**
> This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/MedialinkBluetoothAdapterWithAppleMagicTrackpad](https://help.ubuntu.com/community/MedialinkBluetoothAdapterWithAppleMagicTrackpad)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2038020](http://ubuntuforums.org/showthread.php?t=2038020)


Support threads regarding the wiki and it's content should be created in a suitable forum.

Thread closed to further posting.

---

