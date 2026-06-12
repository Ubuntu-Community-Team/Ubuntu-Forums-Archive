---
title: "NUT configuration with USB UPS MGE Ellipse 750"
date: 2008-10-06
forum: Server Platforms
---

### Post by mansonthomas on 2008-10-06
Hi,

I'm trying to configure NUT to work with my MGE Ellipse 750 UPS on my hardy heron install.

So far I've done this : 

sudo apt-get install nut

vi /etc/nut/ups.conf

[ellipse750]
driver = usbhid-ups
port = auto
desc = "Ellipse 750 UPS"

But the UPS doesn't seems to be recognised : 

```
thomas@home:/etc/nut$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.2.1-
Network UPS Tools: 0.29 USB communication driver - core 0.32 (2.2.1-)

Using subdriver: MGE HID 1.01

```



whereas it's connected : 

```
thomas@home:/etc/nut$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c012 Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0463:ffff MGE UPS Systems UPS
Bus 001 Device 001: ID 0000:0000


```


Any idea of what's wrong ? 

thomas.

---

### Post by mansonthomas on 2008-10-06
well, after some tries, and restart, it finally works ;)

---

### Post by mansonthomas on 2008-10-08
Hi,

I've blogged about setting up an UPS on USB here : 

[http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html](http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html)

with configuration file and scripts available for download.

Hope this will be useful to someone.

Thomas.

---

### Post by cariboo on 2008-10-08
I've got a Belkin UPS 950 that I finally gave up on. I have connected it to my home pc and it works well enough to give me time to shut it down during a prolonged power outage. For my server I purchased an APC Back-UP XS 900, after a 2 minute search I used apcupsd from the repositories and it took me another 2 minutes to set it up.

I would recommend APC for ease of setup and so far (only had it for since the first of September) reliability.

Jim

---

