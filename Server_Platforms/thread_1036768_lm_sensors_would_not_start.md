---
title: "lm_sensors would not start"
date: 2009-01-11
forum: Server Platforms
---

### Post by apkatt on 2009-01-11
**Sorry for tripple-post, I got an Proxy error**

Hi!

I'm trying to get the lm_sensors service to work. I have been following this guide: [http://24.97.150.195/nstwiki/index.php/PhpSysInfo](http://24.97.150.195/nstwiki/index.php/PhpSysInfo)

I read it carefully and tried both to add and not to add the extra text in the localrc and the modules.conf files.

When I try to start I recive this:

[I]service lm_sensors start
$lm_sensors: unrecognized service[/I]

The "sensors-detect" finds alot of chips/sensors. I use Ubuntu Server 8.10 and the motherboard is Intel Desktop Board D945GCLF2.

Anyone have any idea why I cant's start the service?

Thanks in advance.

---

### Post by apkatt on 2009-01-11
**Sorry for tripple-post, I got an Proxy error**

Hi!

I'm trying to get the lm_sensors service to work. I have been following this guide: [http://24.97.150.195/nstwiki/index.php/PhpSysInfo](http://24.97.150.195/nstwiki/index.php/PhpSysInfo)

I read it carefully and tried both to add and not to add the extra text in the localrc and the modules.conf files.

When I try to start I recive this:

[I]service lm_sensors start
$lm_sensors: unrecognized service[/I]

The "sensors-detect" finds alot of chips/sensors. I use Ubuntu Server 8.10 and the motherboard is Intel Desktop Board D945GCLF2.

Anyone have any idea why I cant's start the service?

Thanks in advance.

---

### Post by apkatt on 2009-01-11
**Sorry for tripple-post, I got an Proxy error**

Hi!

I'm trying to get the lm_sensors service to work. I have been following this guide: [http://24.97.150.195/nstwiki/index.php/PhpSysInfo](http://24.97.150.195/nstwiki/index.php/PhpSysInfo)

I read it carefully and tried both to add and not to add the extra text in the localrc and the modules.conf files.

When I try to start I recive this:

[I]service lm_sensors start
$lm_sensors: unrecognized service[/I]

The "sensors-detect" finds alot of chips/sensors. I use Ubuntu Server 8.10 and the motherboard is Intel Desktop Board D945GCLF2.

Anyone have any idea why I cant's start the service?

Thanks in advance.

---

### Post by kaibob on 2009-01-11
Post deleted by kaibob

---

### Post by cariboo on 2009-01-11
Do you have the following modules installed?

```
i2c-i801
smsc47m192
smsc47m1
```

To check in a terminal type:

```
lsmod | grep smsc
```

You sould get an output that looks something like this:

```
lsmod | grep smsc
smsc47m1               17160  0 
smsc47m192             20496  0 
hwmon_vid              11264  1 smsc47m192
i2c_core               31892  3 i2c_dev,smsc47m192,i2c_i801
```

The above output is from my D945GCLF.

Jim

---

