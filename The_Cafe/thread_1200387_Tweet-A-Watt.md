---
title: "Tweet-A-Watt"
date: 2009-06-30
forum: The Cafe
---

### Post by greenrubberducky on 2009-06-30
So...not sure how many makers are out there...

Has anyone tried building a Tweet-A-Watt yet? I have successfully completed one sender/receiver pair. Got it working on Windows, and have been toying around with it a bit. I've now moved the receiver to the workshop in the basement, and want to run it on Ubuntu. Running the Python script is fine and easy. My current issue is figuring out what port it is on or even what drivers I may or may not need. 

Just started into it, I'll post my progress. Wondering if anyone else has their tweet-a-watt running on a linux box?

---

### Post by Blood//Stain//Child on 2009-06-30
?

---

### Post by greenrubberducky on 2009-06-30
Quite...

[http://ladyada.net/make/tweetawatt/]("http://ladyada.net/make/tweetawatt/")

Takes a Kill-A-Watt power meter, adds an xbee-based 900MHz radio, and transmits the power usage data to a PC every couple seconds.

---

### Post by greenrubberducky on 2009-06-30
Okay...finding the device was quite easy...

1) unplug it, then plug it back in. The USB cable that is.
2) run ```
tail /var/log/messages
```. This will output the most recent system messages. Find one that starts with "Detected: FT232RL". The next line will tell you what device it is. Mine was ttyUSB0.
3) in the wattcher.py script, change the "COM4" setting to the proper device name. Mine is now "/dev/ttyUSB0".

---

### Post by greenrubberducky on 2009-06-30
The message log output, tail end:
```
speedracer@workshop-wonder:/dev$ tail /var/log/messages
Jun 29 23:54:05 workshop-wonder -- MARK --
Jun 29 23:58:09 workshop-wonder syslogd 1.5.0#5ubuntu3: restart.
Jun 30 00:01:22 workshop-wonder kernel: [ 1651.106244] usb 2-1: USB disconnect, address 2
Jun 30 00:01:22 workshop-wonder kernel: [ 1651.107123] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
Jun 30 00:01:22 workshop-wonder kernel: [ 1651.107144] ftdi_sio 2-1:1.0: device disconnected
Jun 30 00:01:47 workshop-wonder kernel: [ 1676.344038] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jun 30 00:01:48 workshop-wonder kernel: [ 1676.544524] usb 4-1: configuration #1 chosen from 1 choice
Jun 30 00:01:48 workshop-wonder kernel: [ 1676.547149] ftdi_sio 4-1:1.0: FTDI USB Serial Device converter detected
Jun 30 00:01:48 workshop-wonder kernel: [ 1676.547182] usb 4-1: Detected FT232RL
Jun 30 00:01:48 workshop-wonder kernel: [ 1676.547246] usb 4-1: FTDI USB Serial Device converter now attached to ttyUSB0

```

---

### Post by greenrubberducky on 2009-06-30
Well...it's up and running. Had to install about 10 new python packages (fresh 9.04 install), but it's up and tweeting. For some reason it won't write to the powerdatalog.csv file, so no history is being captured. It's 1am, so I'll work on that tomorrow.

---

### Post by Johnny B on 2009-07-25
which packages did you have to install? so far i have installed python-simplejson.
did you find any good tutorials?
how did you deal with the md5 deprecation warning?
i tried installing python-subvertpy, with no luck.

---

