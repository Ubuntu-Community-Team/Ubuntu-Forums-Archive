---
title: "How to change ethernet connections in Ubuntu Studio?"
date: 2010-07-17
forum: Ubuntu Studio
---

### Post by raymondvillain on 2010-07-17
I installed Ubuntu Studio on a flash drive (on a notebook computer). During installation, the parameters (IP address, etc.) particular to the network to which I was connected became part of the installation.

Now I've plugged the flash drive into a different machine, a desktop, and I can't connect to the new ethernet network.

Is there a way to do this? I've tried system>administration>network tools but I could not find a way to manually enter the IPv6 and IPv4 info.

Do I need to install some sort of network manager from synaptic?

Ubuntu Studio has no provision for wireless, and adding a "notification area" to the taskbar did not give me any connection options.

---

### Post by pytheas22 on 2010-07-17
If you can get the NetworkManager applet running, you can configure a static IP from there by right-clicking and selecting "Edit Connections."  There are some instructions [here]("http://ubuntuforums.org/showthread.php?t=1074132") that should help you get the applet running on Ubuntu Studio.

A simpler approach might be just to edit /etc/network/interfaces, which is the file that stores your networking configuration, by typing:
```

sudo gedit /etc/network/interfaces
```

To set a static IP address on eth0, you need to create a section in that file along the lines of:
```

iface eth0 inet **static**
address 10.0.0.2
netmask 255.255.255.0
gateway 10.0.0.1
```

Run:
```

sudo /etc/init.d/networking restart
```

for changes to that file to take effect.

---

### Post by raymondvillain on 2010-07-19
Thanks very much, Pytheas22.  I was able to try your suggestion but it didn't work, because there was a conflict of computer names due to my carelessness when setting up the flash drive.

When installing Ubuntu Studio on the flash drive, I gave it the same name as a desktop on my home ethernet.  I was trying to boot the notebook computer with Ubuntu Studio on the flash drive at the same time that the desktop was already running.  As soon as I turned off the "same named" desktop and rebooted the notebook with the flash drive I was able to connect with /etc/network/interfaces set to:

auto eth0
iface eth0 inet dhcp

which is what it was in the first place.

So I'm going to mark this solved, and thank you very much for your suggestion.

Does anyone know if it is possible to rename an installation?  I'm talking about the Name that shows up when you log into the router.

---

### Post by pytheas22 on 2010-07-19
Glad to hear you got connected again.

I'm pretty sure the name you're referring to is just the hostname, which you can reset with a simple:
```

sudo hostname new-hostname
```

Alternatively, you can edit the file /etc/hostname.

You need to log out, or possibly reboot, for changes to the hostname to take effect.

---

### Post by raymondvillain on 2010-07-20
Right again you are, Pytheas22.

Many thanks, smooth sailing for now.

---

