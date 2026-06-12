---
title: "Panp7 locking up on return from standby/hibernate"
date: 2010-05-10
forum: System76 Support
---

### Post by magnumjones on 2010-05-10
Hey guys,

I have attached the log files from the system76 driver page (as per requested in a previous post).

Let me know what I can do, or if there is anything else you may need.

Thanks!!

-Dan

---

### Post by thomasaaron on 2010-05-10
This probably is because you didn't have the proprietary drivers enabled. (referencing your earlier post)

---

### Post by magnumjones on 2010-05-10
Thanks for the quick response!  I have installed the drivers and look forward to rolling in the pallid luxury of Lucid.

-Dan

---

### Post by magnumjones on 2010-05-20
Sadly, I am still getting lock-up/slow response from standby issues.

I came back from standby at 5:45pm EST and the computer stalled for about 1 minute, then came online and seemed like it was thrashing for about 5 minutes as I tried to close all the windows to see if I could get it back to functioning.

I attached the log file I made afterward.

Please help!

-Dan

---

### Post by thomasaaron on 2010-05-21
As best I can tell, these are the pertinent log entries...

> May 20 17:43:24 system76-pc kernel: [  136.647659] input: Mag-Tek USB Swipe Reader as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12
May 20 17:43:24 system76-pc kernel: [  136.647659] input: Mag-Tek USB Swipe Reader as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12
May 20 17:43:24 system76-pc kernel: [  136.647884] generic-usb 0003:0801:0001.0004: input,hidraw0: USB HID v1.00 Keyboard [Mag-Tek USB Swipe Reader] on usb-0000:00:1d.0-1.1/input0
May 20 17:43:41 system76-pc wpa_supplicant[1232]: WPA: Group rekeying completed with 00:23:69:fa:6a:06 [GTK=TKIP]
May 20 17:43:41 system76-pc wpa_supplicant[1232]: WPA: Group rekeying completed with 00:23:69:fa:6a:06 [GTK=TKIP]
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
May 20 17:48:20 system76-pc sudo: pam_sm_authenticate: Called
May 20 17:48:20 system76-pc sudo: pam_sm_authenticate: username = [magnum]
May 20 17:43:41 system76-pc wpa_supplicant[1232]: WPA: Group rekeying completed with 00:23:69:fa:6a:06 [GTK=TKIP]
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
May 20 17:43:41 system76-pc NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
May 20 17:48:20 system76-pc sudo: pam_sm_authenticate: Called
May 20 17:48:20 system76-pc sudo: pam_sm_authenticate: username = [magnum]

There's about a 20 second delay between...
> May 20 17:43:24 system76-pc kernel: [  136.647884] generic-usb 0003:0801:0001.0004: input,hidraw0: USB HID v1.00 Keyboard [Mag-Tek USB Swipe Reader] on usb-0000:00:1d.0-1.1/input0

...and...

> May 20 17:43:41 system76-pc wpa_supplicant[1232]: WPA: Group rekeying completed with 00:23:69:fa:6a:06 [GTK=TKIP]

What is "Mag-Tek USB Swipe Reader"? It looks like it's something on your keyboard? Does the problem occur with a different keyboard?

---

### Post by magnumjones on 2010-05-21
Actually, it is a USB credit card swiper, with Keyboard emulation.

Sadly, I don't think that is the only issue though.  

That would be the first time I used the cc swiper receiving it that day, but it has locked up twice since I upgraded the video driver, just forgot to write down time.

I'll keep an eye out, and post on the next occurrence, if that would help?

-Dan

---

### Post by magnumjones on 2011-02-13
Oh No!  The saga continues...

I haven't responded to this since I have been using my desktop almost exclusively in the last 9 months, but I went back to my mobile office and everything came back in full force.

The respond from hibernation seems to work like this,  if I am using anything Java programs (Eclipse, Open Office) the restart from hibernate is reeeeeeally slow (5 minutes).  If firefox is also opened with my standard 15-25 tabs, it can take up to 15 minutes to come back to life.

Without the Java program running, it takes loner than it should (about a minute), but is bearable, and firefox opened or closed has no impact.

The real kick in the groin happened today, when I got the flashing Caps Lock and Num Lock and a locked computer when I tried to unhibernate.  I did a forced restart and got  two rounds of triple beeps.

I went to my alternate internet connection, found out it was a kernel panic and have added the log below (as suggested in most forum posts dealing with that issue).

Don't know if this helps, but my sound also intermittently decides not to work (sometimes helps to turn off HDMI sound output, sometimes not).  Works fine after a reboot.

The wireless can be flakey, but works fine after a reboot.  Though my network is turned of by default

Additionally, my brightness goes dim after a return from hibernate (intermittent), but is fine after a reboot.

Since I usually hibernate, I'm guessing all those issue are related, but I really don't know.

I really appreciate all your help with this.  I mean does the computer work, absolutely.  It's fast and I can run it as a mobile server.  But it kind of grates when everytime I use it I'm getting a Windows experience.

Let me know if there is anything I can do to help,
-Dan

---

### Post by isantop on 2011-02-14
Do you get similar results if you try and resume from suspend? Also, what version of Ubuntu are you running?

---

### Post by magnumjones on 2011-02-15
Not locking up from suspend, but there is a pause(1-10 secs) and the screen has a display hiccup (a line of dots 2/3 of screen wide, 1 cm tall, 2 in from top left of screen).

I am running 10.04 - 2.6.32-28-generic (#55-Ubuntu SMP).

Does that help?

---

### Post by isantop on 2011-02-15
What happens if you try and hibernate while running on a LiveCD? Does it still lock up?

---

