---
title: "Podstudio UX1 in Ubuntu"
date: 2012-04-16
forum: Ubuntu Studio
---

### Post by Osecia on 2012-04-16
Hello.
I've got the Line 6 Pod Studio UX1, and want to use this as my recording device.
I've been able to get the sound working when I'm listening to music, movies etc. but I'm not able to get any input signals at all. 
I have tried to find a solution, but I just can't make it work. 
This is my last attempt before I return to Windows.
Anyone who knows what to do?

---

### Post by jejeman on 2012-04-16
Give us output from
```
arecord -l
```

---

### Post by Osecia on 2012-04-16
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
subdevices:1/1
Subdevice #0: subdevice #0
card 2: PODStudioUX1 [POD Studio UX1], device 0: POD Studio UX1 [POD Studio UX1]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by sgx on 2012-04-17
Hi, in qjackctl setup page

Input Device >
Output Device >

if it says default, or hw:0 hw:1,0etc
replace it with POD Studio UX1  without the brackets.
It may not work as an output device, so choose your
motherboard sound, or a soundcard, if you have one.

You can click the > widgets to see the list of
recognized cards in your computer.

But if all else fails, a Fender Mustang usb amp
works perfect in linux, and displays itself by name in

Input Device >

New ones start at $110, and all sound great. :guitar:

---

