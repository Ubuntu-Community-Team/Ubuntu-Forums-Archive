---
title: "Ubuntu Server 16.04.3 - How to connect to Ethernet ?"
date: 2017-10-29
forum: Server Platforms
---

### Post by dxmoose on 2017-10-29
I just finished installing Ubuntu server on my old LGA775 machine that will need to work as a small minecraft server hosting machine. As this is my first ever time using Linux or its distros, i dont really know how to do it. Ive already tried some guides but no success yet. Hopefully someone can help me! Thanks.

---

### Post by TheFu on 2017-10-29
The learning curve for a pure server is very steep.  For someone not familiar with Unix/Linux already, it will be very difficult.

The config file you want is in /etc/network/interfaces
There are lots of how-to guides for that file and there is a manpage which explains the different settings. Of course, these explanations require a certain background to understand.
* [https://askubuntu.com/questions/766131/set-static-ip-ubuntu-16-04](https://askubuntu.com/questions/766131/set-static-ip-ubuntu-16-04)
* [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

A basic understanding of IPv4 networking is really needed.

So ... the first step towards getting online is to attempt to get the interfaces file setup.  After you change the file, restart the networking subsystem. No need to reboot.  Use **sudoedit  /etc/network/interfaces** to edit the file. This is the safest method for editing any system file.

If you want to learn more about Linux, here's a link with my best advice: [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed)  About 2 hrs of time reviewing those things will save you hours, days, weeks of frustration.

---

### Post by dxmoose on 2017-10-29
I know that this was a pretty bad idea to do for someone who has no experience with linux. So, im in the file and it shows:

# This fire describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5)

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet dhcp

I know that im literally asking to spoonfeed me, but i really want this to work out somehow. What do i have to do next ?

---

### Post by collisionystm on 2017-10-29
Are you trying to configure a static IP or just get the server on the internet?

---

### Post by wildmanne39 on 2017-10-29
*Thread moved to **Server Platforms for better a better fit **.*

---

### Post by dxmoose on 2017-10-29
Just connect it to the internet so i download the updates if there are any and ubuntu-desktop

do all ubuntu users have to go through this ? Or this is only for the Server OS ?

---

### Post by TheFu on 2017-10-29
> **dxmoose said:**
> do all ubuntu users have to go through this ? Or this is only for the Server OS ?

It is just for the server.  It is assumed that people choosing to run the server have _some_ level of knowledge about Unix. Desktop installations generally don't require any CLI/shell work to do most common things - for the first year or so.  Just be aware that with almost all Unix programs, a GUI provides access to about 20% of the options/commands. For normal end-user stuff, that's usually sufficient, but the real power of Unix systems comes from scripting and automation , using the CLI.   In the hands of an expert, a Unix shell is much more efficient than GUIs. Basically, managing servers 2-20,000 is the same.  I've always been told that 90% of the power in a computer comes from non-GUI stuff. I believe it.

If you want help, and as new as you are, we need to see **exact commands** for everything. If you are editing the file incorrectly, with the wrong program, we cannot help if you don't show us. File permissions are a core security consideration on Unix systems.  Understanding them ASAP will make managing a Unix system much easier.  Everything -EVERYTHING- is related to permissions.  Every process runs under a specific userid, accessing files and directories with that same userid.

I have no way of knowing if that ethernet device is the correct one for your system from the data provided.  Let's step back and validate that first - 

**sudo lshw -C network** will show the device and driver.  **lspci** will as well, but that output is less nice.  If the device driver is loaded, then **ifconfig** will show the available network devices too. I provided multiple commands because not every system install provides the pretty commands.

On 16.04, my ethernet device is enx000ec6c76488 - created from part of the card MAC.  See how it attempts to be unique?  Yours will be different.  If enp2s0 is correct, and it might be, then you should be fine, assuming the file can be saved.
Just run ```
sudo systemctl restart networking.service
```  If everything works, nothing should be output.  Unix has a standard to NOT complain when things work, but to complain loudly when something fails.

It is also normal that when config changes are made, the **admin is expected** to restart/reload the service.  There are different ways to accomplish this based on the specific daemons involved, but in general, **systemctl** is the tool for 16.04 and later releases.  Prior to that, we used "service" and prior to that, we used 30 yr old scripts located in /etc/init.d/    which accepted start|stop|reload|status options and did the right thing.  I preferred the 30 yr old methods. They worked for me all this time and when something broke, I could easily fix it.  systemctl isn't that way, at least not to me, yet.

---

### Post by dxmoose on 2017-10-29
Also, i might have forgot to mention one thing, that might actually change everything. Everything that this pc is going to need to do is just run a KCauldron.jar ( The minecraft server 'software' that im going to run ) file. That is basically it. ive chosen Ubuntu Server cause it some forums have told that it can run for a long time with no need to restart and you can edit the configs of it without rebooting the system.

The result of the first command sudo lshw -C network:

```
*-network DISABLED
description: Ethernet interface
product: attansic L2 Fast Ethernet
Vendor: Quallcom Atheros
Physical id: 0
bus info: pci@0000:02:00.0
logical name: enp2s0
version: a0
serial: 00:1e:8c:05:10:05
capacity: 100mbit/s
width: 64 bits
clock: 33mhz
```

and then it shows its capabilities. Im not going to use lspci cause as you said, its almost the same thing.

As i was guessing, it had complaint: Job for networking service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.

This was the other command [COLOR=#000000][FONT=&quot]sudo systemctl restart networking.service[/FONT][/COLOR]

---

### Post by darkod on 2017-10-29
Well, as it says please run:
```
sudo systemctl status networking.service
```

and show us the full output. You can copy-paste the whole text and post it inside [code] tags for better readability and formatting.

Also I have noticed that sometimes restarting the networking service is complaining and simply rebooting the machine after doing some changes to the networking might be a better option.

And setting up a static IP on the server is a good idea instead of letting it run dhcp.

---

### Post by dxmoose on 2017-10-29
Ill do that tomorrow and update tomorrow too. its 1Am here and i got to go to sleep.

---

### Post by TheFu on 2017-10-30
The lshw capabilities would have showed the driver being used, if any.  It was important to see that if the networking isn't working.  If the file had the correct device name and shown settings, then networking should be working, assuming the DHCP server on your network is doing its job.

If restarting the network didn't work, then there are other issues.

---

