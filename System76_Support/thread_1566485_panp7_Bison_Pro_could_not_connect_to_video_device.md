---
title: "panp7 Bison Pro could not connect to video device"
date: 2010-09-02
forum: System76 Support
---

### Post by kms3 on 2010-09-02
Hello,

When I launch camorama, I get a 'could not connect to video device' error message. 

When I received my laptop, there were no books or CDs. All I got was some Ubuntu stickers. Is this normal?

Thanks,
kms3

---

### Post by isantop on 2010-09-02
In an effort to be a greener company y using less paper, we no longer ship welcome manuals with our systems. They are still available online, in pdf format, by locating your system here: [http://knowledge76.com/index.php/Category:Systems](http://knowledge76.com/index.php/Category:Systems).

There is a hotkey to turn on the webcam. Press Fn+F10 to toggle it on and off. Turn the camera on, then restart the program you want to use. This'll get it working.

---

### Post by kms3 on 2010-09-05
I have tried the Fn + F10 combo, still no camera. I am looking for the pdf right now. 

I am hoping the pdf will cover BlueTooth and sound, as I do not have either working right now.

Thanks,
Kyle

---

### Post by kms3 on 2010-09-08
Ok Fn + F10 does not work for the camera. 

Fn + F12 works for BlueTooth and I am able to pair with my blackberry. I am going to start troubleshooting the connection to see what I can uncover. Any guidance would be appreciated.

Thanks,
Kyle

---

### Post by isantop on 2010-09-08
Let start with the camera. Open a Terminal (Applications > Accessories > Terminal) and run:
```
lsusb
```
Then press Fn+F10 again and repeat the command. Send me the output from both runs.

---

### Post by kms3 on 2010-11-01
Sorry for the late response, I did not receive notification about your response.

Something to note, I use a 4 port KVM switch with my laptop. 

When I push the key combination, Fn+F10 I use the laptop's keyboard.

Before pressing Fn+F10:

kms@drank:~$ lsusb
Bus 002 Device 011: ID 10d5:55a4 Uni Class Technology Co., Ltd 
Bus 002 Device 010: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 009: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 008: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 004: ID 147e:1000 Upek 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

After pressing Fn+F10:
kms@drank:~$ lsusb
Bus 002 Device 012: ID 5986:0343 Acer, Inc 
Bus 002 Device 011: ID 10d5:55a4 Uni Class Technology Co., Ltd 
Bus 002 Device 010: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 009: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 008: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 004: ID 147e:1000 Upek 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The camera does not work with camorama, but it does work with Skype. Skype is much more important. 

Thanks,
Kyle

---

### Post by isantop on 2010-11-01
Well, the hardware is functional, so we know it's not a hardware issue. Does the camera work with Cheese?

---

### Post by kms3 on 2010-11-01
When I launch Cheese in the terminal, I get a segmentation fault.

I get the following from dmesg:

[19335.114590] cheese[13004]: segfault at 0 ip 00007fceda3ab0b2 sp 00007fcecd860cb0 error 4 in libcheese-gtk.so.18.0.0[7fceda39b000+17000]
[19340.644557] uvcvideo: Failed to query (135) UVC control 2 (unit 5) : -71 (exp. 2).
[19340.648686] uvcvideo: Failed to query (135) UVC control 2 (unit 5) : -71 (exp. 2).
[19341.301289] cheese[13009]: segfault at 0 ip 00007f6c266980b2 sp 00007f6c19b4dcb0 error 4 in libcheese-gtk.so.18.0.0[7f6c26688000+17000]

~kyle

---

