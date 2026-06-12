---
title: "Anyone downloaded 16.10 and tried Unity8?"
date: 2016-10-14
forum: Ubuntu Development Version
---

### Post by Chanath on 2016-10-14
Anyone downloaded 16.10? It was out yesterday. 
I'm trying Unity 8. Nothing much there yet. Does anyone have more on Unity 8?
Zooming, pinching etc doesn't work in a touch screen environment. Can push from the right edge to look at all open windows, though not much. 
Left edge pull would bring the launcher, but no dash. Icons are not pretty.
Web browser looks good, but don't know how to enlarge the fonts. Highlighting, copy, paste seems to work, but everything is so tiny.
There is a way to change something called the Desktop mode to left and right, but the difference is not told (or shown)

---

### Post by ventrical on 2016-10-15
The basic highlight of unty8 is Libertine Containers  and Xapps. You can install libertine libertine-scope and create a container and then try to install some deb apps there. A lot of the games works as well as nautilus, gedit, xterm, abiword, firefox, libreoffice etc..

 It basically utilizes Intel Chips with V chip technogy (older dual  and core 2 duos processors). There is also greater security in an lxc container and with snaps there will even be greater security. Iv'e created a lot of threads  here in the forum .. check them out. There are a few hints how to get it rolling.

The unity8 is running in the mir compositor so it is still a work in progress that will gradually develop through the ZZ cycle.




regards..

---

### Post by cariboo on 2016-10-15
I just tried Unity8 on a fresh Yakkety install, it now seems almost usable. I have chromium, vlc, gimp and nautilus installed in a libertine container, they all work but are buggy. This should get you started:

[http://insights.ubuntu.com/2016/10/13/unity-8-preview-session-in-ubuntu-16-10-yakkety-yak/](http://insights.ubuntu.com/2016/10/13/unity-8-preview-session-in-ubuntu-16-10-yakkety-yak/)

---

### Post by ventrical on 2016-10-15
Just a side note- it sometimes takes a little while for a container to create (7mins plus in some cases) and each container builds seperately - so there is a bit of patience required.

regards..

---

### Post by ventrical on 2016-10-15
There are some neat experiments that you can try. If you are a chess enthusiast you can run multi-sessions of brutalchess, 1 each from a separate container - to give you a feel of how containers work and how unique they are.

And of course other programs can run concurrently also .  A very unique property with vChips. This is on a PC over 8 years old. [s] it was using less processor resources  about 2 months back but the final release update seems to have slowed down just a bit.[/s]

..this apparently due to  brutalchess.

Regards..

---

### Post by ventrical on 2016-10-15
Here is three separate chess games running concurrently, each game run from a separate container. By the way ... there is no secondary mouse click needed to engage a running app... just mouse over.

Regards..

---

### Post by ventrical on 2016-10-15
it is not causing too much heat from use of resources.

```

ventrical@ventrical-System-Product-Name:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +45.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +38.0°C  (high = +80.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
GPU core:     +0.90 V  (min =  +0.90 V, max =  +1.11 V)
fan1:           0 RPM
temp1:        +40.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.14 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.14 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +4.94 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +11.93 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      4218 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
POWER FAN Speed:       0 RPM  (min =  800 RPM, max = 7200 RPM)
CPU Temperature:     +43.5°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +35.0°C  (high = +45.0°C, crit = +95.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2016-10-15
Using  dreamchess uses a lot less resources.  So you can run sessions concurrently from individual containers with zesty graphics and low resource use.



Regards..

---

### Post by mrdc76 on 2016-10-15
I tried Unity 8 on 16.10. It did not crash, and it wasn't buggy. Other than that, it looks kind of underwhelming. Not really something I am looking forward using. Are they planning to update the theme later on?

---

### Post by ventrical on 2016-10-15
> **mrdc76 said:**
> I tried Unity 8 on 16.10. It did not crash, and it wasn't buggy. Other than that, it looks kind of underwhelming. Not really something I am looking forward using. Are they planning to update the theme later on?

From what I understand it will eventually become default, perhaps by 18.04 and I think there will be a lot of work this next ZZ cycle. I am adopting it as my main desktop to test for development version, mostly for the reason of Libertine containers and Desktop Xapps which are very unique to work with.

Regards..

---

### Post by Chanath on 2016-10-16
Thanks guys. Unity8 is supposed to work in a touch screen environment. Right now not much touch screen actions can be done, such as pinching, zooming etc. Sure, it is a work in progress.

---

