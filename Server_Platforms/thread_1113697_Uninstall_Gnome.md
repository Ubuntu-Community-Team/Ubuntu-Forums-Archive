---
title: "Uninstall Gnome"
date: 2009-04-01
forum: Server Platforms
---

### Post by koontz on 2009-04-01
Hello again,

I wanted to see what people had to say about what I am about to do.

I have Ubuntu Server 8.04 running currently.  I was using desktop to get a better understanding, but now I am moving onto server.  My issue is ndiswrapper.  I understand it a lot more when using Gnome.  I had major issues editing the config file at the command line.

So what I want to do is Install Gnome, set-up ndiswrapper, wireless card connect to my network automatically at boot.  If the automatic part is in the guide, I think I missed it since i could never get that far.  Would it be wise to keep Gnome since I am an obvious newbie or should I just uninstall it after setting up ndiswrapper.  Also would uninstalling Gnome mess with my ndsiwrapper settings?  I know I ask a lot of you, and if you only feel like answering one of my questions, all help is appreciated.

Thanks

---

### Post by cariboo on 2009-04-02
When you type ndiswrapper at the command line, it shows you all the options you need to install and configure the Windows drivers.

```
 ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
```

to install the .inf file type:

```
sudo ndiswrapper -i /path/to/inf/file
```

To check that you installed the correct driver type:

```
sudo ndiswrapper -l
```

this should echo back the device and driver name. Next to add the configuration  file to /etc/modprobe.d, type:

```
sudo ndiswrapper -m
```

then insert the module:

```
sudo modprobe ndiswrapper
```

To make sure what you done worked type:

```
sudo lshw -C network
```

the output should tell you if the driver has loaded. To save yourself from typing sudo all the time you can use:

```
sudo -i
```

Jim

---

### Post by mocoloco on 2009-04-02
As far as your question on if you should keep Gnome, I would say it depends on what your goals are and what you're using the box for.  If you're serious about learning "real" server admin stuff, you'll need to learn command line.  Also one major reason most servers have no GUI is they run headless (no monitor, keyboard, etc, just accessed remotely).
You could of course keep Gnome and just try to use the terminal as much as possible as you learn. Also if you're machine in not just a dedicated server but also a desktop system you might have reason to keep the GUI.

---

### Post by koontz on 2009-04-02
I appreciate the help.  Yeah its just a dedicated server.  On desktop i installed LAMP and SSH and was just accessing it through putty.  The only real problem I had was hooking up the wireless card.

Ill try reconfiguring ndiswrapper again, then we'll see.  I am just really curious if I configure Ndiswrapper using the Gnome and then uninstall Gnome will that mess with the ndiswrapper settings?

---

### Post by mocoloco on 2009-04-04
Nope. The GUI is just a frontend, the back end ndiswrapper app and module would not be removed along with gnome.

---

