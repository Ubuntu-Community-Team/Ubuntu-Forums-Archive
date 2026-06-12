---
title: "Serp1 webcam under Ubuntu 9.04"
date: 2009-08-31
forum: System76 Support
---

### Post by 982000971 on 2009-08-31
I haven't had a consistently working webcam since the day I bought my Serp1. I just want it to work so I can use Skype. I once followed the instructions of [http://ubuntuforums.org/showthread.php?p=4918932#post4918932](http://ubuntuforums.org/showthread.php?p=4918932#post4918932) and it worked for a while, but never for very long.

I need help.

---

### Post by brijohn on 2009-08-31
The instructions you linked to are quite outdated. Currently the code to support the microdia sn9c20x based webcams has been merged into the mainline kernel and will appear in karmic. 

If you don't wish to wait for karmic to be released you can install the latest version of the v4l-dvb tree which also has the code in it with the following instructions.

Install the necessary build tools
# sudo apt-get install build-essential mercurial linux-headers-`uname -r`

Checkout the most recent version of v4l-dvb
# hg clone [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)

Build drivers
# cd v4l-dvb
# make

and finally install the updated v4l subsystem
# sudo make install

You should now be able to load the driver with
# sudo modprobe gspca_sn9c20x

And next time you reboot the driver should load automatically when you connect your camera.

Brian Johnson

---

### Post by 982000971 on 2009-08-31
Thank you very much for the response. Everything ran pretty smoothly until:

# sudo modprobe gspca_sn9c20x

which returned:

```
FATAL: Error inserting gspca_sn9c20x (/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/gspca/gspca_sn9c20x.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by brijohn on 2009-08-31
It may be an issue with some parts of the previous version of teh v4l subsystem being loaded. The following commands will print out exactly what its complaining about.

# sudo dmesg -c
# sudo modprobe gspca_sn9c20x
# dmesg

I'd try rebooting first however its likely parts of the old version ofthe v4l subsystem are still loaded. Rebooting will fix that.

---

### Post by thomasaaron on 2009-09-01
Here is how we got it working on the SerP2. It may work on the SerP1 as well...

add the following to your list of apt sources...

deb [http://ppa.launchpad.net/nickel62metal/ubuntu](http://ppa.launchpad.net/nickel62metal/ubuntu) jaunty main

(To do this, run...
sudo gedit /etc/apt/sources.list
...and paste that line into the bottom of the file and save it.)

Then run...
sudo apt-get update
...followed by...
apt-get install microdia-dkms 

Then reboot your computer. Check to see if your cam works in cheese, Ekiga and Skype.

---

### Post by 982000971 on 2010-01-18
I need an update on this for 9.10

---

