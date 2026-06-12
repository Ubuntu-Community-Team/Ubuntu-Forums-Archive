---
title: "HOWTO: Google Earth on Linux (Ubuntu) PC with GPS from Android smartphone/tablet"
date: 2013-05-15
forum: Tutorials
---

### Post by phamthanhnam on 2013-05-15
**Introduction**
In this tutorial, I will introduce to you how to use Google Earth on Linux (Ubuntu) PC with position/tracking feature by making use of the built-in GPS receiver from your Android smartphone/tablet.
There are many reasons to use it this way. First, why do you have to buy an expensive external GPS receiver when your Android device has already one? Secondly, there is no Google Earth Pro for Linux, Google Earth Free Edition lacks GPS feature, you can't use your GPS device **natively** within Google Earth for Linux, so you waste money :) Finally, your Android screen is too small and/or Google Earth doesn't support your Android device.
Let's start!

**Getting started**
Step 1: Install Google Earth for Linux (Ubuntu)
Google Earth for Linux installation is not so smooth as Google Earth for Windows or Mac, Google's support is quite bad for this problem. However, you will easily find instruction for this task somewhere on the Internet.

Step 2: Install a GPS sharing application on your Android using Google Play
There are many GPS sharing applications but generally, they use the same principle. There are 2 common methods for GPS sharing from an Android device: via Bluetooth and via ADB (USB cable or Wifi). I'll present both.
Here is a summary for some applications:
[table="width: 500"]
[tr]
	[td]Name[/td]
	[td]Via[/td]
	[td]TCP port[/td]
	[td]License[/td]
[/tr]
[tr]
	[td]ShareGPS[/td]
	[td]Bluetooth, USB[/td]
	[td]50000[/td]
	[td]Free[/td]
[/tr]
[tr]
	[td]BlueNMEA[/td]
	[td]Bluetooth, USB[/td]
	[td]4352[/td]
	[td]Free[/td]
[/tr]
[tr]
	[td]Solidsync Network/Bluetooth GPS[/td]
	[td]Bluetooth, Wifi[/td]
	[td]25010[/td]
	[td]2.99 USD[/td]
[/tr]
[tr]
	[td]Symarctic ExtGPS[/td]
	[td]Bluetooth[/td]
	[td][/td]
	[td]Free[/td]
[/tr]
[tr]
	[td]Bluetooth GPS Output[/td]
	[td]Bluetooth[/td]
	[td][/td]
	[td]10 minute trial or 0.92 USD[/td]
[/tr]
[tr]
	[td]GPS 2 Bluetooth v.4[/td]
	[td]Bluetooth[/td]
	[td][/td]
	[td]Free, just a widget[/td]
[/tr]
[/table]

**Please choose one of two methods: A or B**
Method A: GPS over Bluetooth
Step 3A: Install [Blueman]("https://launchpad.net/blueman") on Ubuntu. This tool will help you bypass all the command line hassle for bluetooth procedures.

Step 4A: Enable GPS in Android settings. Launch GPS sharing application, enable sharing via Bluetooth, and set your Android Bluetooth discoverable for a period of time.
Then, select 'Setup New Device...' in Blueman menu on your Ubuntu. Select your discovered Android device. Select 'Use Random Passkey' or 'Use Custom Passkey', whatever. Confirm paring on both Ubuntu and Android. Then select 'Serial Port' in 'Connect to'. If everything goes well, you will see the notification 'Serial port connected' about the new created device /dev/rfcommX (normally /dev/rfcomm0).
Make sure that the connected serial port is for GPS service, not for another service. Select 'Devices...' in Blueman menu, right-click on your paired Android device, select 'Refresh Services'. Disconnect the wrong service and connect the right service. You will see the status in GPS sharing application is 'Connected' if you connect to the right service.
Try this command (replace X by 0 or any number you are told above) to test:
```
sudo cat /dev/rfcommX
```
You will see NMEA strings on your terminal. Stop testing by pressing Ctrl-C.

Step 5A: Download gegpsbluetooth.py in the attachment. I got the idea from [gegpsd for direct GPS devices]("http://www2.warwick.ac.uk/fac/sci/csc/people/computingstaff/jaroslaw_zachwieja/gegpsd") and reprogram to use GPS over Bluetooth with some bug fixes/improvements. This program gets GPS data from /dev/rfcommX and writes it into /tmp/nmea.kml for Google Earth. Feel free to reprogram it if you are good at Python :P
Run the following command:
```
sudo python gegpsbluetooth.py
```
or if you are not using /dev/rfcomm0:
```
sudo python gegpsbluetooth.py -p /dev/rfcommX
```
If you don't want to sudo, you can sudo chmod 666 /dev/rfcomm* or add yourself in group 'dialout'.

Method B: GPS over ADB (USB or Wifi)
Step 3B: Install adb, enable 'USB debugging' on your Android
You just need the executable 'adb'. You don't need to download the entire ADT bundle or Android SDK. Fortunately, adb is already in Ubuntu repository.
```
sudo apt-get install android-tools-adb
```
Enable 'USB debugging' on your Android device in Settings. The way to enable it may vary, it depends on your device model and/or Android version. However, every Android version has this option. It is usually under 'Development' category in Settings. Try Google if you can't find out.
Connect your Android to PC by USB cable and check to ensure that adb is able to see your device in working state (not offline):
```
adb devices
```
It will list the series number of your Android device, like this:
*0123456789abcdef   device*
Sometimes 'adb' in Ubuntu repository is not updated (the latest version at this time is 1.0.31) and it doesn't work with your Android (adb shows your device with 'offline' status). You may have to download Android SDK to extract the lastest version of 'adb'. With Android 4.2.2, you have to confirm RSA fingerprint pop-up dialog on your Android to allow adb to connect.

Step 4B: Run adb to forward port
If you are using ShareGPS, run:
```
adb forward tcp:50000 tcp:50000
```
Replace 50000 by 4352 if you are using BlueNMEA, by 25010 if you are using Solidsync Network/Bluetooth GPS (see step 2).
Now test to ensure you are receiving NMEA strings via ADB:
For ShareGPS:
```
telnet localhost 50000
```
For BlueNMEA:
```
telnet localhost 4352
```
For Solidsync Network/Bluetooth GPS:
```
telnet xxx.xxx.xxx.xxx 25010
```
xxx.xxx.xxx.xxx is Android's IP address on Wifi network. It is showed in listening status when you start sharing GPS over network in Solidsync Network/Bluetooth GPS. Your Android device and PC should be in the same Wifi network.
You will see NMEA strings received. Stop testing by opening another terminal and type:
```
skill telnet
```

Step 5B: Download gegpsadb.py in the attachment. I made this program to use the new method (GPS over ADB). This program gets GPS data from TCP socket after 'adb forward' and writes it into /tmp/nmea.kml for Google Earth. Feel free to reprogram it if you are good at Python :P
Run the following command if you are using ShareGPS. This is default supported application.
```
python gegpsadb.py
```
For BlueNMEA:
```
python gegpsadb.py -p 4352
```
For Solidsync Network/Bluetooth GPS (replace xxx.xxx.xxx.xxx by Android's IP address, see step 4B):
```
python gegpsadb.py -a xxx.xxx.xxx.xxx -p 25010
```

**You are now close to the goal**
Step 6: Download gps.kml in the attachment. Give your Android device a sky view and wait until it can locate your position (latitude/longitude). Right-click on gps.kml, and select Open with Google Earth. Voila, the earth will turn to fly you to your position. You can also see a yellow pin on a nearby airport in Google Earth!

Step 7: When you are finished with Google Earth, kill gegpsbluetooth or gegpsadb by Ctrl-C to stop receiving data. Stop sharing and quit Android application. Turn off Bluetooth/WIfi/GPS to save battery if you want.

---

