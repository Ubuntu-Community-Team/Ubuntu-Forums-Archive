---
title: "Guide: Powerware 5110 UPS monitoring/auto shutdown in Ubuntu 10.04 Lucid"
date: 2010-03-31
forum: Tutorials
---

### Post by Menthu_Rae on 2010-03-31
The information in this thread has been moved to [https://help.ubuntu.com/community/Powerware5110UPSin12.04](https://help.ubuntu.com/community/Powerware5110UPSin12.04)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062077#post12062077](http://ubuntuforums.org/showthread.php?p=12062077#post12062077)

Thread closed.


[SIZE="4"]Guide: Powerware 5110 UPS monitoring/auto shutdown in Ubuntu 12.04 Precise[/SIZE]

[SIZE=3]**NOTE:** I take no responsibility if you stuff something up doing this. So long as you have a moderate grasp of Ubuntu/Linux and editing configuration files - then this guide will be very straightforward. Make sure you read carefully and take things slowly.[/SIZE]

[INDENT]I'm going to skip the small talk - you can read over that here (where I stole the commands from):

[INDENT][http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)[/INDENT]

That out of the way - here's everything you need to do to get your Powerware 5110 UPS up and running/able to be monitored in Ubuntu 10.04 Lucid.

**Note:** Updated this guide to read for Ubuntu 12.04 as I just tested it and it works fine!

Also note that if you are dual booting with Windows7 or Windows Vista, I believe there is some kind of driver bug whereby your PC may shut down upon Windows startup with the 5110 plugged in via USB.

There is however a firmware update available from Eaton- or if you recently bought the UPS you should be OK (check the USB F/W version on the side of it, so long as it is higher than 0.5 you should be fine).

Now, onto the guide...[/INDENT]

**[SIZE="3"]The steps...[/SIZE]**

This looks like a lot of work - but it will take you a few minutes only!

```
$ sudo apt-get install nut
```

```
$ gksu gedit /etc/nut/ups.conf
```

[QUOTE=Insert this text]

[Powerware5110]
    driver = bcmxcp_usb
    port = auto[/QUOTE]

```
$ gksu gedit /etc/udev/rules.d/99_nut-serialups.rules
```
[QUOTE=Insert this text]

KERNEL=="ttyS0", GROUP="nut"[/QUOTE]

```
$ sudo udevadm control --reload-rules
$ sudo udevadm trigger
$ sudo upsdrvctl start
```

This should output...

[QUOTE=Output]

Network UPS Tools - UPS driver controller 2.4.3
Network UPS Tools - BCMXCP UPS driver 0.23 (2.4.3)
USB communication subdriver 0.18[/QUOTE]

```
$ gksu gedit /etc/nut/upsd.conf
```
[QUOTE=Insert this text]

ACL all 0.0.0.0/0
ACL localhost 127.0.0.1/32
ACCEPT localhost
REJECT all[/QUOTE]

```
$ gksu gedit /etc/nut/upsd.users
```
[QUOTE=Insert this text]

[local_mon]
    password = _YOUR_PASSWORD_HERE_
    allowfrom = localhost
    upsmon master[/quote]

```
$ gksu gedit /etc/nut/upsmon.conf
```

[QUOTE=Insert this text]

MONITOR Powerware5110@localhost 1 local_mon _YOUR_PASSWORD_HERE_ master
POWERDOWNFLAG /etc/killpower
SHUTDOWNCMD "/sbin/shutdown -h now"[/QUOTE]

```
$ sudo chown root:nut /etc/nut/*
$ sudo chmod 640 /etc/nut/*
```

```
$ gksu gedit /etc/default/nut
```
[QUOTE=Insert this text]

START_UPSD=yes
START_UPSMON=yes[/QUOTE]

```
$ gksu gedit /etc/nut/nut.conf
```
[QUOTE=Insert this text]

MODE=standalone[/QUOTE]

```
$ sudo /etc/init.d/nut start
```

```
$ sudo upsc Powerware5110
```

[QUOTE=Output]
ambient.temperature.high: 1
battery.charge.low: 22
battery.voltage:  26.9
device.mfr: Eaton
device.model: POWERWARE UPS    1500i
device.serial: 
device.type: ups
driver.name: bcmxcp_usb
driver.parameter.pollinterval: 2
driver.parameter.port: auto
driver.version: 2.4.3
driver.version.internal: 0.23
input.frequency:  49.9
input.frequency.high: 55
input.frequency.low: 45
input.frequency.nominal: 50
input.transfer.boost.high: 216
input.transfer.high: 280
input.transfer.low: 186
input.transfer.trim.low: 260
input.voltage: 238
input.voltage.nominal: 240
output.current:   0.7
output.current.nominal:   3.8
output.frequency:  49.9
output.phases: 1
output.voltage: 238
output.voltage.nominal: 240
ups.beeper.status: enabled
ups.firmware: Cont:00.50 Inve:01.50
ups.load:  18.4
ups.mfr: Eaton
ups.model: POWERWARE UPS    1500i
ups.power.nominal: 1500
ups.serial: 
ups.status: OL[/QUOTE]

**[SIZE=3]Monitoring your UPS from now on...[/SIZE]**

Simply run the last command:

```
$ sudo upsc Powerware5110
```

Which will net you the output with all your UPS information. Do with that what you will - feed it into some PHP page with SQL and run LAMP so you can have a live monitor/log of the UPS statistics, output it to a text file, feed it into conky, whatever! This is Linux - your skills are the limit limit :)

---

### Post by DonkyBoY on 2010-04-22
ive just tested under 9.10 x64 and works just fine Thankyou for your help :)

---

### Post by wzup on 2010-05-25
Nice guide. Thanks!
Works on Ubuntu Server 10.04 x86_64, with my Powerware 5110 1000i :).

---

### Post by chrisbay90 on 2010-10-04
Thanks Menthu_Rae youre an absolute legend.

This guide worked for me on Ubuntu 10.04 x64 headless server using Eaton Powerware 5110 UPS 500Va

---

### Post by SundaY82 on 2010-12-17
I used this guide to get status on my Eaton 5110 700VA, running Ubuntu x64 10.10 server.

One thing though, the info displayed... what should you look for, what info is worth keeping track on both during power and when you loose power. 

Some info I would like to check is current power usage(watt), battery status if its fully charged or not. Estimated time it will last if power goes. And when power goes out keep track of battery status.
Is this info possible to get from upsc?

---

### Post by SundaY82 on 2010-12-17
This is what my ups show by the way:
> # upsc Powerware5110
ambient.temperature.high: 1
battery.charge.low: 11
battery.voltage:  13.5
device.mfr: Eaton
device.model: POWERWARE UPS    700i
device.serial: `Ô>
device.type: ups
driver.name: bcmxcp_usb
driver.parameter.pollinterval: 2
driver.parameter.port: auto
driver.version: 2.4.3
driver.version.internal: 0.23
input.frequency:  49.9
input.frequency.high: 55
input.frequency.low: 45
input.frequency.nominal: 50
input.transfer.boost.high: 207
input.transfer.high: 275
input.transfer.low: 178
input.transfer.trim.low: 250
input.voltage: 234
input.voltage.nominal: 230
output.current:   0.4
output.current.nominal:   1.8
output.frequency:  49.9
output.phases: 1
output.voltage: 234
output.voltage.nominal: 230
ups.beeper.status: enabled
ups.firmware: Cont:00.50 Inve:01.50
ups.load:  22.2
ups.mfr: Eaton
ups.model: POWERWARE UPS    700i
ups.power.nominal: 700
ups.serial: `Ô>
ups.status: OL

---

### Post by Jeinhor on 2011-01-09
Thanks for this excellent guide, works like a charm! :D

However, does anyone know what the numbers actually tell me? I want to write a small program that monitors the UPS minutely, and when the battery level goes below a threshold runs a custom script. But... what number tells me the battery level? Or if the UPS is running from battery?

Thanks in advance!

---

### Post by TwistedTripper on 2011-04-30
This worked for me on 11.04. Thanks.

---

### Post by neptune on 2011-05-03
This stopped working on Natty.

I get the following errors:

```

$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.6.0
Network UPS Tools - Generic HID driver 0.35 (2.6.0)
USB communication driver 0.31
Using subdriver: CyberPower HID 0.3
libusb_get_report: error sending control message: Operation not permitted
Can't initialize data from HID UPS
Driver failed to start (exit status=1)
```

```

$ sudo /etc/init.d/nut start
 * Starting Network UPS Tools                                            [ OK ] 
                                                                               
Broadcast Message from nutmon@forester                                         
        (somewhere) at 13:30 ...                                               
                                                                               
Communications with UPS GS-UPS@localhost lost                                  
                                                                               
                                                                               
Broadcast Message from nutmon@forester                                         
        (somewhere) at 13:30 ...                                               
                                                                               
UPS GS-UPS@localhost is unavailable                                            
```


My config files are as follows:

ups.conf
```

[GS-UPS]
driver = usbhid-ups
port = auto
desc = "Geek Squad UPS"
```

upsd.conf
```

LISTEN 127.0.0.1
LISTEN 192.168.1.20
```

upsd.users
```

[ups-master]
password = pass
actions = SET
instcmds = ALL
upsmon master 

[ups-user]
password = pass
upsmon slave 
```

upsmon.conf
```

MONITOR GS-UPS@localhost 1 ups-master pass master
SHUTDOWNCMD "/sbin/shutdown -h +0"
RUN_AS_USER nutmon
```

nut.conf
```

MODE=netserver
```

/etc/default/nut
```

START_UPSD=yes
START_UPSMON=yes
```

---

### Post by neptune on 2011-05-30
anyone able to help out with this issue?

---

### Post by Menthu_Rae on 2012-05-26
> **neptune said:**
> anyone able to help out with this issue?

Necro reply: I just followed my first post but using Ubuntu 12.04 and it works perfectly :p

---

### Post by jimbo123 on 2012-06-11
Hi Menthu_Rae,

I've also got an Eaton Powerware 5110,.. and followed bit'n'pieces of guides from several places before stumbling onto this one.

I was looking to see whether others have managed to make the 5110 shutdown as part of their shutdown sequence ?

Thought 'nut' could do that, but am not having much luck.

Running 12.04,.. installed with apt-get and very similarly to the guide in post #1.

Any experiences are welcomed.

Thanks,

Jim.....

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/Powerware5110UPSin12.04](https://help.ubuntu.com/community/Powerware5110UPSin12.04)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012411](http://ubuntuforums.org/showthread.php?t=2012411)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

