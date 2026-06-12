---
title: "Webcam on the new Darters"
date: 2007-07-30
forum: System76 Support
---

### Post by shingalated on 2007-07-30
How can we get the supported webcam working on the new Darter ultras?  It doesn't seem to be showing up in lspci...do I need to install some kind of kernel module?

---

### Post by thomasaaron on 2007-07-31
The web cam works in the new Darter.

Open Ekiga. If I remember correctly, you have to go to Edit > Preferences and then select Video devices.

Make sure it is set on USB2 video device and Auto.

Then, on the phone itself, select the little icon for the web cam.

Also, the P2 button above the keybaoard will turn it on and off.

---

### Post by shingalated on 2007-07-31
Ekiga crashes for me on start up, I have tried the webcam in "Cheese" a program similar to Photobooth in OS X, I still have to try it on openwengo. I will try the P2 button though.  What does P1 do?
Thanks!

---

### Post by YannickDefais on 2007-07-31
> **shingalated said:**
> Ekiga crashes for me on start up

Can you copy and paste here what "ekiga -d 4" says in a terminal ?

Regards,
Yannick

---

### Post by thomasaaron on 2007-07-31
The P2 button might be causing the crash.
It can cause Ekiga to do a core dump if the camera is turned off.

---

### Post by shingalated on 2007-07-31
I am at work right now, and will test it when I get home.
Thanks!

---

### Post by ackey on 2007-07-31
When I run ekiga, it seg faults.  The printout is:

whobuntu:~> ekiga -d 4
2007/07/31 14:50:00.719   0:00.423                        ekiga Detected audio plugins: ALSA
2007/07/31 14:50:00.720   0:00.423                        ekiga Detected video plugins: Picture,V4L2,V4L
2007/07/31 14:50:00.720   0:00.423                        ekiga Detected audio plugins: ALSA
2007/07/31 14:50:00.720   0:00.423                        ekiga Detected video plugins: Picture,V4L2,V4L
2007/07/31 14:50:00.882   0:00.585                        ekiga Detected the following audio input devices: HDA Intel,Default with plugin ALSA
2007/07/31 14:50:00.882   0:00.585                        ekiga Detected the following audio output devices: HDA Intel,Default with plugin ALSA
2007/07/31 14:50:00.882   0:00.585                        ekiga Detected the following video input devices: USB 2.0 Camera with plugin V4L
2007/07/31 14:50:00.882   0:00.585                        ekiga Detected the following audio input devices: HDA Intel,Default with plugin ALSA
2007/07/31 14:50:00.882   0:00.585                        ekiga Detected the following audio output devices: HDA Intel,Default with plugin ALSA
2007/07/31 14:50:00.882   0:00.585                        ekiga Detected the following video input devices: USB 2.0 Camera with plugin V4L
2007/07/31 14:50:01.242   0:00.945                        ekiga Ekiga version 2.0.3
2007/07/31 14:50:01.243   0:00.946                        ekiga OPAL version 2.2.3
2007/07/31 14:50:01.243   0:00.946                        ekiga PWLIB version 1.10.3
2007/07/31 14:50:01.243   0:00.946                        ekiga GNOME support enabled
2007/07/31 14:50:01.243   0:00.946                        ekiga Fullscreen support enabled
2007/07/31 14:50:01.243   0:00.946                        ekiga DBUS support disabled
2007/07/31 14:50:01.246   0:00.949                        ekiga Set TCP port range to 30000:30010
2007/07/31 14:50:01.246   0:00.949                        ekiga Set RTP port range to 5000:5059
2007/07/31 14:50:01.246   0:00.949                        ekiga Set UDP port range to 5060:5100
2007/07/31 14:50:01.246   0:00.949                        ekiga OpalEP  Created endpoint: h323
2007/07/31 14:50:01.246   0:00.949                        ekiga H323    Created endpoint.
2007/07/31 14:50:01.247   0:00.950                        ekiga OpalMan Added route "pc:.*=h323:<da>"
2007/07/31 14:50:01.247   0:00.950                        ekiga OpalEP  Created endpoint: sip
2007/07/31 14:50:01.247   0:00.950                        ekiga SIP     Created endpoint.
2007/07/31 14:50:01.248   0:00.952                        ekiga OpalMan Added route "pc:.*=sip:<da>"
2007/07/31 14:50:01.249   0:00.952                        ekiga OpalEP  Created endpoint: pc
2007/07/31 14:50:01.249   0:00.952                        ekiga PCSS    Created PC sound system endpoint.
2007/07/31 14:50:01.249   0:00.952                        ekiga OpalMan Added route "h323:.*=pc:<da>"
2007/07/31 14:50:01.249   0:00.952                        ekiga OpalMan Added route "sip:.*=pc:<da>"
2007/07/31 14:50:01.251   0:00.954        Opal Listener:84b5338 Listen  Started listening thread on tcp$198.129.216.246:1720
2007/07/31 14:50:01.251   0:00.954        Opal Listener:84b5338 Listen  Waiting on socket accept on tcp$198.129.216.246:1720
2007/07/31 14:50:01.252   0:00.957       Opal Listener:b24054c0 Listen  Started listening thread on udp$198.129.216.246:5060
2007/07/31 14:50:01.254   0:00.957       Opal Listener:b24054c0 Listen  Waiting on UDP packet on udp$198.129.216.246:5060
2007/07/31 14:50:01.257   0:00.960                        ekiga AVAHI   Adding service Nicole Ackerman
Segmentation fault (core dumped)

---

### Post by hardyn on 2007-07-31
> **shingalated said:**
> Ekiga crashes for me on start up, I have tried the webcam in "Cheese" a program similar to Photobooth in OS X, I still have to try it on openwengo. I will try the P2 button though.  What does P1 do?
Thanks!

what is the name of that program, i have been looking for something better than what i have currently been using.

---

### Post by YannickDefais on 2007-07-31
@ackey,

Hopefully this has been fixed, could you try last stable?
[https://help.ubuntu.com/community/Ekiga?highlight=%28ekiga%29#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c](https://help.ubuntu.com/community/Ekiga?highlight=%28ekiga%29#head-57385c7cf79361cbb4d7195b9f43c1bb33c1e94c)

Regards,
Yannick

---

