---
title: "A UPS NUT question"
date: 2022-10-08
forum: Server Platforms
---

### Post by cazz on 2022-10-08
Hi
I have install NUT on a ubuntu server and works very nice.
It run on a proxmox server that I have also install some other ubuntu servers on.
One if them I have install the NUT client and got that to work too.

But when I run the command "upsmon -c fsd" to force a shutdown it even shutdown my proxmox server.
I did just want to try to shutdown the server that running NUT client and in my "/etc/nut/upsd.conf" I have 

```

LISTEN 127.0.0.1 3493
LISTEN 192.168.1.45 3493

```

so it should just turn off the local server and my other server (my 192.168.1.45)

Not sure what to do.

---

### Post by Frogs Hair on 2022-10-08
Moved to  Server Platforms.

---

### Post by cazz on 2022-10-08
Hi again
I have google a little and find that I have not finnish the NUT config so I have done that.

But I have install on another server NUT with another UPS but I can't get it to connect.

When I run "nut-scanner -U" I get

```
[nutdev1]
        driver = "blazer_usb"
        port = "auto"
        vendorid = "0665"
        productid = "5161"
        product = "HID UPS"
        serial = "HID UPS"
        vendor = "HID UPS"
        bus = "002"
```


I edit "/etc/nut/ups.conf"

```
[powerwalker]
  driver = blazer_usb
  port = auto
  desc = "PowerWalker VI 800 SCL"
```

have even try with

```
[powerwalker]
  driver = usbhid-ups
  port = auto
  desc = "PowerWalker VI 800 SCL"
```



But when I run "upsdrvctl start" it say

```
Network UPS Tools - UPS driver controller 2.7.4
Network UPS Tools - Generic HID driver 0.41 (2.7.4)
USB communication driver 0.33
No matching HID UPS found
Driver failed to start (exit status=1)

```


Not sure why.

I have even reboot every time I change a settings.

---

### Post by MAFoElffen on 2022-10-09
> **cazz said:**
> Hi
I have install NUT on a ubuntu server and works very nice.
It run on a proxmox server that I have also install some other ubuntu servers on.
One if them I have install the NUT client and got that to work too.

But when I run the command "upsmon -c fsd" to force a shutdown it even shutdown my proxmox server.
I did just want to try to shutdown the server that running NUT client and in my "/etc/nut/upsd.conf" I have 

```

LISTEN 127.0.0.1 3493
LISTEN 192.168.1.45 3493

```

so it should just turn off the local server and my other server (my 192.168.1.45)

Not sure what to do.

Is the promox server running a client NUT upsd driver and listening to a NUT controlled 'primary-mode' UPS?

I am not completely sure, but man upsd.conf, which you posted here, "LISTEN 192.168.1.45" says bind the local listening port to this local physical device...

man upsmon says, with your command of 'upsmon -c fsd':
> 
 **-c** *command* 
  Send the command *command* to the existing upsmon process.  Valid commands are: 

  **fsd** 
  shutdown [COLOR=#ff0000]**all** *primary-mode* UPSes[/COLOR][COLOR=#ff0000] (use with caution) [/COLOR]

 

Anything listening is going to shutdown with a powerdown/shutoff before all UPS('es) listening shutdown.

whereas:
```

**upsdrvctl** [*OPTIONS*] {start | stop | shutdown} [*ups*]
upsdrv shutdown snoopy

```
man upsdrvctl 
> 
 **shutdown** 
  Command the UPS driver(s) to run their shutdown sequence.  Drivers are stopped according to their sdorder value - see [ups.conf(5)]("https://networkupstools.org/docs/man/ups.conf.html"). 

   [TABLE]
[TR]
[TD="class: icon"] Warning[/TD]
[TD="class: content"]this will probably power off your computers, so don&#8217;t play around with this option.  Only use it when your systems are prepared to lose power.
[/TD]
[/TR]
[/TABLE]
 
   [TABLE]
[TR]
[TD="class: icon"] Note[/TD]
[TD="class: content"]refer to [ups.conf(5)]("https://networkupstools.org/docs/man/ups.conf.html") for using the **nowait** parameter.[/TD]
[/TR]
[/TABLE]

That would shutdown a specific UPS...  and just the computers connected to that specific UPS.

which tells me everything there (network wise) is on one network segment, with no subnets or private vlans... So that command you issued ('upsmon -c fsd') broadcasts to all primary-mode upses and their respective upsd clients, right? I think the command you used worked as expected. I just think you just used the wrong command...

That is just what I see and interpret from those... Right? I didn't check into it for what  UPS'es do if they are set up and configured as "secondary-mode" UPS'es...

Disclaimer: The  promox-server didn't physically have to be connected power-wise, but rather just driver-wise for it to get a shutdown signal. Versus physically connected, but not software driver's installed machine would get a pull-the plug shutdown.

---

### Post by cazz on 2022-10-09
Thanks for the replay
Ohh ok, I think Proxmox have a build inside NUT client so I guess that why.
That only thing I have notice that is that NUT client does need so much manual settings to work with NUT server.
Is alot of code that you have to manual write to make it work.

But I going to work some more with the NUT, it is fun and nice to have.
And thanks for the information, now I have some more to read.

---

### Post by MAFoElffen on 2022-10-09
Please tell us how that goes... Because now looking at those, I seem to have an interest in how that works and how things go together.

---

### Post by cazz on 2022-10-09
Sure
At first I recommend you look at this youtube
[https://youtu.be/vyBP7wpN72c](https://youtu.be/vyBP7wpN72c)

Most of my info I have got from this guide.

---

