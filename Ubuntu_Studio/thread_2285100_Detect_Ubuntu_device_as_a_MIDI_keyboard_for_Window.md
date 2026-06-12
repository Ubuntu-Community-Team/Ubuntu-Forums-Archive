---
title: "Detect Ubuntu device as a MIDI keyboard for Windows"
date: 2015-07-03
forum: Ubuntu Studio
---

### Post by blackmamba2 on 2015-07-03
Hello, 
I am creating a little experimentation application on my Odroid XU3 with Ubuntu 15.04 Lite.
The device (Odroid) receives midi as input via a keyboard (this part is OK) and sents some other midi instructions to the computer to create harmony (this part is not ok).
The use case  is :
you play on your midi keyboard some notes, the odroid received them, the embedded application code analyses them, find new notes (midi instructions) and send them to VST instruments on your Windows PC.
TO achieve that, I need the Odroid device to appear as a MIDI keyboard in Windows that  people can add the device in their DAW.
Do you guys have any idea how to achieve that? I tried with g_midi but it's not working.
Thanks a lot

---

### Post by jejeman on 2015-07-03
This is Ubuntu forum, not for windows.
What is this Odriod device? Is it USB device?

---

### Post by blackmamba2 on 2015-07-03
Hello,
Sorry I forgot to mention this is USB everywhere.
Here is the Odroid, it's like a raspberry pi with some differences.
[http://dn.odroid.com/homebackup/201407071058089142.jpg](http://dn.odroid.com/homebackup/201407071058089142.jpg)
It is to connect to windows but the part to expose the MIDI device is on the Ubuntu side I believe.

---

### Post by jejeman on 2015-07-03
Okay, I get it know. You have Ubuntu installed on this Odroid. It receives MIDI data, and now you need this device (actually a computer) to send MIDI data via USB. Or even more, to act as USB MIDI device which is then recognized on Windows OS.
So, the question is how to make Ubuntu to be a MIDI device.
Maybe it is easier to send MIDI data via USB?

---

### Post by blackmamba2 on 2015-07-03
This is exactly what you described. 
Actually, the MIDI data will be sent by USB, the problem is to make the device exposed as a MIDI controller for windows that when I plug it via the USB OTG port, windows recognizes it as a midi controller.

---

