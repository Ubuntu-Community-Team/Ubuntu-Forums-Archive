---
title: "Managing fan noise from Chipset and Nvidia Graphics card"
date: 2012-01-29
forum: Server Platforms
---

### Post by Aurian on 2012-01-29
I just started using Ubuntu Server and am quite new to Linux/Ubuntu. I wanted to create a file server using old hardware.

The specs are as follows:
[LIST]
[*]CPU: AMD 64 X2 4800+
[*]Motherboard: Asus A8N-E
[*]RAM: 2GB DDR2 800
[*]HDD1: PATA 120GB
[*]HDD2: PATA 160GB
[*]HDD3: SATA 160GB
[*]HDD4: SATA 250GB
[*]GRAPHICS: NVidia GeForce 8600 GTS
[/LIST]
The construction and installation went smoothly enough. The next thing I wanted to do was to make the computer as quiet as possible. So I installed lm-sensors and enabled AMD QCool in the bios.
When I restarted the server the CPU fan dropped to 1100 rpm ( down from 3200rpm) and the CPU clock dropped to 1GHz (down from 2.4GHz)
BUT the system is very loud mainly due to the chipset fan (running at 7000 rpm) and the Nvidia graphics card fan at 100%.

I updated the graphics card drivers by installing the Nvidia ones using the following steps
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

I also installed xfce. When i started it the video card fan dropped to 30% and the noise was reduced. But when I logged out of xfce the fan revved up to 100% and the noise was back again.

So my questions are as follows:
[LIST=1]
[*]How do i make sure that the Nvidia driver are loaded when I am in the CLI ? i do not want to start xfce every time.
[*]How do I manage the speed of the chipset fan? 
[/LIST]

Thank you for your time with this. And I apologize if my post is very long... It's all due to my noobness :D

---

### Post by 2F4U on 2012-01-29
The system will use the nVidia drivers independent of someone logging into the desktop or not. This can be verified by looking into /var/log/Xorg.0.log where it tells you what video driver the system uses. The video driver is loaded as part of the boot process.

I don't know your mainboard, but for some the chipset fan speed can be adjusted in the BIOS.
Since this is a server, you can also think about removing the desktop environment at all. Since then there is no graphical work to do for the card, it could help to reduce the burden placed on the graphics card.

---

### Post by Aurian on 2012-01-29
I checked the log file and it does seem to have nvidia drivers. 

I am just using xfce as a window manager to be used when required. I intend to use the CLI for most things. 

The issue is that the fan spins at high speeds when I am in the CLI. But it slows down only when I start xfce. I don't know but it seems that the fan control on the GPU kicks in only when a GUI is used. It doesn't seem to work while in the CLI.
Also when I log out of xfce back to the CLI, the fan speeds up again. This is confusing since the graphics load should be much lesser than in xfce.

Any ideas?

---

### Post by ian dobson on 2012-01-30
Hi,

What does sensors show from the terminal.

I imagine the chipset fan speed can't be controlled, most 40mm fans that I've seen can't be controlled by PWM.

I'd imagine you can control the NVidia fan speed through the NVidia control pannel. I think there's a command line tool (nvidia-settings) that would allow you to manually adjust the fan speed. Although xfce might put the graphic card under more load, it's able to control the fan speed (As it know's how hard the graphic card is working/what temperature it has). When xfce isn't running no-one is holding the graphic card so no-one controls the fan speed, so it runs at maximum speed, just to be safe.

Also have a look at nv-clock, that should allow you to control the NVidia fan speed from the terminal.

Regards
Ian Dobson

---

### Post by Aurian on 2012-01-31
I did some more research on my chipset. I installed the fancontrol package and tried to run pwmconfig. It tried to slow down my fans during configuration but I didn't really see any fans slow down. So I assumed that it would not be able to control the chipset fan. 
The Asus Q Control was already doing a decent job with the CPU fan. So I tried a little cheating :-)
I just disconnected the chipset fan and booted up. I then left the computer running for a few hours and checked the temp every 30 mins. It never went over 30c. And the alert is at 70c!. It seemed that the chipset really didn't need a fan in this server setup. 

So that issue is solved :D

I started on the Nvidia settings but ran into an issue. With the Nvidia drivers installed, the system will not let me start xfce4 with 'sudo startxfce4'. It says that it cannot find any screens and aborts. But it works with a monitor connected.
Now this is an issue. I plan to leave the server headless and run a GUI on demand. But it seems that I will need a monitor attached if I install the Nvidia proprietary drivers and want to run the GUI. Has anyone else had this issue?

---

### Post by ian dobson on 2012-01-31
Hi,

Why not just use a VGA dongle ([http://www.techpowerup.com/forums/showthread.php?t=86507](http://www.techpowerup.com/forums/showthread.php?t=86507)) or [http://www.geeks3d.com/20110622/vga-hack-test-dummy-vga-dongle-win7-three-radeon-hd-5770-multi-gpu-opencl-single-monitor/](http://www.geeks3d.com/20110622/vga-hack-test-dummy-vga-dongle-win7-three-radeon-hd-5770-multi-gpu-opencl-single-monitor/), this will trick the graphic card into thinking that a monitor is attached.

I have a headless Windows box (don't ask) and the onyl way to get the system to boot correctly is to have a monitor attached or use the above.

Regards
Ian Dobson

---

