---
title: "Bluetooth troubleshooting help requested"
date: 2012-05-06
forum: System76 Support
---

### Post by jcllings on 2012-05-06
Serial number: 8C05SC943529
Model: panp9

Intel Centrino 1030 - 802.11 b/g/n Wireless LAN + Bluetooth Combo Module

I had to re-partition this for LVM and that means that I'm not sure I have all the right stuff installed.  What packages should I have installed to get Bluetooth to work? This is a brand new machine that arrived yesterday. An Ivy Bridge CPU (3rd gen Core i7 quad).  It's an absolutely beautiful machine that is ridiculously fast. The Bluetooth is the one fly in my ointment.

Seems like I have the latest driver:

####@####:/home/****# md5sum /home/***/Downloads/iwlwifi-6000g2b-ucode-18.168.6.1/iwlwifi-6000g2b-6.ucode /lib/firmware/iwlwifi-6000g2b-6.ucode 
1f1763dfd472a487c3d61eac0a12b766  /home/***/Downloads/iwlwifi-6000g2b-ucode-18.168.6.1/iwlwifi-6000g2b-6.ucode
1f1763dfd472a487c3d61eac0a12b766  /lib/firmware/iwlwifi-6000g2b-6.ucode
####@####:/home/****# 

Jim C.

---

### Post by jcllings on 2012-05-06
> **jcllings said:**
> Serial number: 8C05SC943529
Model: panp9

Intel Centrino 1030 - 802.11 b/g/n Wireless LAN + Bluetooth Combo Module

...

Jim C.


Some progress to report. I figured out that you have to use the Fn key (its right next to the ctrl key) on the keyboard coupled with the Bluetooth function key on the keyboard. The Bluetooth key is blue ( surprise! ;-) ) and the icon on it looks like an antenna sending signal. When you hit this, watch for the Bluetooth symbol (the funny looking blue "B") to show up in your tray. 

This got me as far as getting a connection to my headset but I still don't have any audio devices showing up for the headset.

---

### Post by jcllings on 2012-05-06
> **jcllings said:**
> Some progress to report. I figured out ...

Still more progress to report. I've got the RFMAB2 RocketFish bluetooth headset to connect but it still doesn't do anything. If I press the various control keys on the headset, I get the O with a line through it in the center of my screen.  I notice that no sound device shows up in the sound settings.

---

### Post by jcllings on 2012-05-07
Woohoo!! 
I got this working!!

The bluetooth laptop hardware is:

Intel Centrino 1030 - 802.11 b/g/n Wireless LAN + Bluetooth Combo Module

The headset hardware is: RocketFish Headset model RFMAB2

To recap, this is a from-scratch re-partition and re-install of Ubuntu 12.04 Server ( but as a Desktop, so Desktop kernel, Gnome, etc. ) on a model panp9 machine from System76. You have to use CTRL-F12 to fire up bluetooth. Then you need to set up a connection as per usual. Once, you have a connection, there's a couple of pactl commands, and that's it.

Don't know if you have to do this every time. Hope not. Could also try modifying the commands below so that it has appropriate info in the Sound Settings dialog. Don't know if this is possible yet though. 


user@host:~$ pactl load-module module-alsa-sink device=bluetooth
user@host:~$ pactl load-module module-alsa-source device=bluetooth

This makes a new sound sync and source show up in the PulseAudio Sound Settings. Then all you have to do is select it. 

Still doesn't map the headset's keys to media player controls but this is hardly required since you are almost surely sitting at the keyboard anyway. The volume keys actually do work, though. Maybe I'll figure out the Next/Previous and Play/Pause keys later. :-)

If you have any trouble with this, try adding your user to the following groups:

bluetooth
pulse
pulse-access


Jim C.

---

### Post by jcllings on 2012-05-08
Procedure:

1. Log in.
2. Fn+F12 (After these keys, the bluetooth icon should appear in your tray)
3. Connect your RFMAB2 by shutting it down and then starting it again. Make sure you continue to hold the play button on the headset long enough for it to make one series of tones, followed by another series. Then right click on the bluetooth icon in your tray and select "Set Up New Device" and then select Continue. When your RFMAB2 appears in the dialog, select it and move through the rest of the dialog as appropriate.
4. Execute this script:

#!/bin/bash

echo load-module module-alsa-sink device=bluetooth | pacmd | grep -v Welcome | sed 's/>>>.//g' | tr '\n' '\000'
sleep 5
echo load-module module-alsa-source device=bluetooth | pacmd | grep -v Welcome | sed 's/>>>.//g' | tr '\n' '\000'
echo update-sink-proplist alsa_output.bluetooth device.description=\"RocketFish RFMAB2 Headset\" | pacmd | grep -v Welcome | sed 's/>>>.//g' | tr '\n' '\000'   
echo update-source-proplist alsa_input.bluetooth device.description=\"RocketFish RFMAB2 Headset\" | pacmd | grep -v Welcome | sed 's/>>>.//g' | tr '\n' '\000'

---

