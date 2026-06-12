---
title: "Kern.log is filling up with i2c errors"
date: 2021-04-26
forum: Server Platforms
---

### Post by rmelkert on 2021-04-26
I've been installing a new Ubuntu Server 20.04 system and all is going fine, except there is a (apparently non fatal) i2c error flooding the kern.log

```

Apr 27 05:17:37 srv01 kernel: [31398.980494] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:17:57 srv01 kernel: [31419.460807] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:20:11 srv01 kernel: [31552.579808] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:20:31 srv01 kernel: [31573.059753] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:21:33 srv01 kernel: [31634.499618] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:22:03 srv01 kernel: [31665.219176] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:22:34 srv01 kernel: [31695.939112] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:23:05 srv01 kernel: [31726.659046] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:23:35 srv01 kernel: [31757.378968] i2c i2c-3: sendbytes: NAK bailout.
Apr 27 05:24:57 srv01 kernel: [31839.298770] i2c i2c-3: sendbytes: NAK bailout.

```

i2cdetect says it's a radeon thing
```

i2c-3   i2c             Radeon i2c bit bus 0x90                 I2C adapter

```

I believe its a sensor, might be the fan? Thing is this is a fanless card (only really needed during installation as the system is headless most of the time).

It doesn't seem to do any harm but I hate it filling the log this way, so:

Can I disable this sensor somehow?


Any help/pointers would be appreciated.

---

### Post by slickymaster on 2021-04-27
Thread moved to **Server Platforms** for a better fit

---

### Post by ameinild on 2021-04-27
I gave an answer to this on AskUbuntu.com

[https://askubuntu.com/questions/1324364/how-to-stop-kern-log-and-syslog-from-growing-too-much/1324384](https://askubuntu.com/questions/1324364/how-to-stop-kern-log-and-syslog-from-growing-too-much/1324384)

Just replace the "contain" string with something else, for instance: 

```
if $msg contains "i2c-3: sendbytes" then { stop }
```

---

### Post by rmelkert on 2021-04-29
> **ameinild said:**
> I gave an answer to this on AskUbuntu.com
Thanks.

That is certainty a last resort option, but I was hoping on a more elegant solution.

Also I read the i2c-3 label can change between boots.

Anyone knows of a (kernel parameter) setting to exclude the 0x90 radeon sensor. 

Or a way to determine what is pulling that sensor and make it stop doing that.

I'm not running lm-sensors but I did notice the /etc/sensors3.conf. It, however, does not contain an obvious reference to the problem sensor.

---

### Post by rmelkert on 2021-05-19
Just an update, for people having similar issues.

I still don't know what the core cause of this issue is, but it went away when I disconnected the monitor.

So it seems it has nothing to do with sensors at all, maybe it doesn't like the monitor switch or the card has some problems with the old 'vga' port.

Anyhow, as this is a headless system anyway it solves the issue for me.

---

### Post by coolspot18 on 2022-01-07
> **rmelkert said:**
> Just an update, for people having similar issues.

I still don't know what the core cause of this issue is, but it went away when I disconnected the monitor.

So it seems it has nothing to do with sensors at all, maybe it doesn't like the monitor switch or the card has some problems with the old 'vga' port.

Anyhow, as this is a headless system anyway it solves the issue for me.

I built a new Ryzen server but used an old Radeon HD 2400 card for video. The server worked well with a VGA monitor but tonight I racked the server and connected it to my old VGA KVM switcher. It was after I hooked up my KVM that I noticed the NAK error in dmesg ... so I think you're right, it's something to do with the VGA port and the connected device.

---

