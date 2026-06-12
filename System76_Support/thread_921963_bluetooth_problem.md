---
title: "bluetooth problem"
date: 2008-09-16
forum: System76 Support
---

### Post by hvacr on 2008-09-16
I have the Pangolin Performance laptop with a bluetooth mouse I use with it. Is there anyway to have the bluetooth module power up when I start up the computer. I have to hit the FN + F12 keys when I  boot up.

---

### Post by thomasaaron on 2008-09-17
Not that I'm aware of. I just tried the instructions here...
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

...which contain information for manually connecting to the device. If we could do that, we could create a start-up script for you.

However, I keep getting a "no route to device" error. I think this is because there may actually be a bios-level switch that makes the device available via the Fn-F12 button.

There are also some configuration files I tried with no luck for this same reason.

---

### Post by hvacr on 2008-09-17
> **thomasaaron said:**
> Not that I'm aware of. I just tried the instructions here...
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

...which contain information for manually connecting to the device. If we could do that, we could create a start-up script for you.

However, I keep getting a "no route to device" error. I think this is because there may actually be a bios-level switch that makes the device available via the Fn-F12 button.

There are also some configuration files I tried with no luck for this same reason.

Interesting, I will give it a try tonight, seems like it will not work though. I will do some more searching myself. I do believe it is bios level though, as I can hit the FN + F12 keys before ubuntu boots up, and the bluetooth will be enabled.

---

### Post by tssgery on 2008-09-17
I can hit Fn+F12 at any time after I log in and bluetooth becomes available. In fact, Fn+F12 toggles the availability of bluetooth so there no need to do it at boot time.

---

### Post by hvacr on 2008-09-17
> **tssgery said:**
> I can hit Fn+F12 at any time after I log in and bluetooth becomes available. In fact, Fn+F12 toggles the availability of bluetooth so there no need to do it at boot time.

On mine I have to do it after each reboot. I will be looking into it more this weekend.

I just installed vista 64 bit, and have the same thing. Each reboot I have to enable bluetooth. This seems to be at the bios level. Could this be something the manufacturer change with a bios revision. 

I have to dual boot because of certain programs I need, no yelling at me.  :)

---

### Post by thomasaaron on 2008-09-18
> This seems to be at the bios level. Could this be something the manufacturer change with a bios revision.


I'm sure it is. But I kind of doubt they will.

---

### Post by hvacr on 2008-09-19
> **thomasaaron said:**
> I'm sure it is. But I kind of doubt they will.

I checked with Sager about this and this was there reply


"By default the Blue tooth is turn off when the system's power is turn off, you will have to activate the module every time you need to use it, for this model, the Bios do not have any thing to do with the Blue tooth device".

Well, that kind of sucks.

---

