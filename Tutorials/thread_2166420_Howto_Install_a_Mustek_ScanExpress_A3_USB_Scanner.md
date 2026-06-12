---
title: "Howto: Install a Mustek ScanExpress A3 USB Scanner"
date: 2013-08-09
forum: Tutorials
---

### Post by dplmartin on 2013-08-09
First, check to make sure that the scanner has been detected on the usb bus. Look for a line like **Bus 005 Device 005: ID 055f:0210 Mustek Systems, Inc. ScanExpress A3 USB**

```
sudo lsusb -v >usb.txt
```
*Note: this outputs the contents to a file called usb.txt in the directory you run the command from.*

If you just plug in your Mustek scanner and run SimpleScan, you might be able to select the Mustek scanner and ask it to scan something but you'll get an error message telling you that SimpleScan is unable to connect to the scanner. The reason is that the scanner needs its firmware downloading into it before it will work and this isn't being done.

Here are the steps that I took (based on other helpful posts) to get my Mustek ScanExpress A3 scanner working.

First, ensure that SANE is installed.

```
sudo apt-get install sane
```

Then check to see if the gt68xx directory exists.

```
cd /user/share/sane/gt68xx
```

If it doesn't and only the sane directory exists, you'll need to create it.

```
sudo mkdir /user/share/sane/gt68xx
```

Make sure that you're in the directory and then download the scanner firmware. You can find the full list [at this site]("http://www.meier-geinitz.de/sane/gt68xx-backend/").

```
sudo wget http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/a32fw.usb
```

There are no manual edits required for this scanner, so you don't need to make any changes to */etc/sane.d/gt68xx.conf*

If you start up your scanning application like SimpleScan, you should find that it now works. The first time you do a scan after powering up the scanner may take a while. It will sit there thinking (looking like its hung) while it uploads the firmware. Subsequent scans will start quicker (until the scanner loses power again).

---

### Post by teapotrow on 2013-11-14
I needed to create the directory at 
sudo mkdir /usr/share/sane/gt68xx,   ie usr not user. Same for cd.
My Mustek A3 scanner is now working. Thanks very much for the how to.

---

