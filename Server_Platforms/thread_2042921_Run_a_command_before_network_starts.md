---
title: "Run a command before network starts"
date: 2012-08-15
forum: Server Platforms
---

### Post by bakegoodz on 2012-08-15
I have a wireless adapter that doesn't work until ```
eject
``` has run, because it has a Virtual Install CD embedded into it. I tried putting it into rc.local, but it runs too late in the boot process. The adapter needs to show up before the network is started because it a member of a bridged interface.

 What is a good way to have this command run before the network comes up?

---

### Post by OM55 on 2012-08-15
Hello bakegoodz,

You can accomplish (almost) that by doing the things the other way around:
Running the command 'eject' and after that connect to the wireless network.

There is a nice application called CuttleFish that can help you. CuttleFish waits for events to occur  and automatically runs user-definable actions when they do. You can also launch a series of user-definable actions manually.

I wrote above that it is 'almost' what you want, because in the solution below, you will need to keep your wireless las deactivated, and in order to connect - click on the 'action' line or shortcut. The outcome will be that the 'eject' command will be launched, and after than the wireless connection will be activated, to connect to your network.

To install CuttleFish do the following in a terminal window:

```
sudo add-apt-repository ppa:noneed4anick/cuttlefish
sudo apt-get update
sudo apt-get install cuttlefish

```So your solution would be one of the following (I think the first one is cleaner):

[LIST=1]
[*]Set up CuttleFish to be triggered when 'eject' is running and then activate the wireless network (so 'eject' could have a shortcut on your desktop).
[*]Set up CuttleFish to operation without any trigger, and run 'eject' and then connect the wireless network
[/LIST]
Hope that helps!

---

### Post by bakegoodz on 2012-08-15
If I wanted a triggered event I would figure out a udev rule rather another package. Plus your description sounds like it uses a Window manager. I put this into the Server thread because I'm running Ubuntu Server (command line) No I just want it ran on startup. I would be looking up how to do an init script, but now that init is depreciated for upstart I'm pretty foggy on the startup process.

---

### Post by BkkBonanza on 2012-08-16
You can add a pre-up command to your interfaces file.
See **man interfaces**.

Something like,

```
iface wlan0 inet dhcp
  pre-up eject
```

This will work with Upstart because Upstart is responsible for bringing the interface up using this.

---

### Post by bakegoodz on 2012-08-17
Thank you that was very helpful. Though it took some trial and error to work with a bridge, for some reason putting the pre-up under the bridge would make it not add the eth0 interface.
```
 cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback

manual wlan0
		pre-up /usr/bin/eject

 
auto br0
	iface br0 inet static
        address 192.168.1.20
        netmask 255.255.0.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge-ports eth0 wlan0
```

---

### Post by bakegoodz on 2012-08-24
While I researching chipsets supported by ath9k I found this page. I found this [http://linuxwireless.org/en/users/Drivers/ath9k_htc#Modeswitching_for_AR7010](http://linuxwireless.org/en/users/Drivers/ath9k_htc#Modeswitching_for_AR7010)

Ah ha I found the proper way to start up the adapter. I didn't need to run "eject" anymore.
```
apt-get install usb-modeswitch
```
Then I found out that wlan0 was no longer being added to the bridge. After further research I found that putting in "manual eth0" made it work again. If you look at the man page you'll find that syntax is nowhere to be found, but that gibberish apparently makes the network pause long enough to be able for things to execute in the right order. Weird huh?

```

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback

manual eth0
 
auto br0
	iface br0 inet static
        address 192.168.1.20
        netmask 255.255.0.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge-ports eth0 wlan0

```

---

