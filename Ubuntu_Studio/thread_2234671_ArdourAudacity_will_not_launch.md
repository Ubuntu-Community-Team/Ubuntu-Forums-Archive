---
title: "Ardour/Audacity will not launch"
date: 2014-07-16
forum: Ubuntu Studio
---

### Post by shell3 on 2014-07-16
Please help me, (but bear in mind that I am a newbie)

I have carried out a clean install of the latest ubuntustudio.  The only changes I have made is to update the system and install LibreOffice.

The problem is that neither Ardour or Audacity starts/launches but they seem to have installed successfully.

I read online that Libreoffice could cause problems with Ardour, so I have uninstalled LibreOffice and reinstalled ubuntustudio from the Synaptic Package Manager - but still no joy. 

When I run Ardour from the terminal:

```
Ardour 2.8.12
   (built using 10144 and GCC version 4.6.1)
Copyright (C) 1999-2008 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 4096 open files
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-y3QozL/pkcs11: No such file or directory
loading system configuration file /etc/ardour2/ardour_system.rc
```

I have tried reinstalling the 'gnome-keyring' with no success.


Nothing happens at all when I attempt to start Audacity from the terminal, but if I repeat the action, a message then appears saying that:

```
The system has detected that another copy of Audacity is running.
Running two copies of Audacity simultaneously may cause
data loss or cause your system to crash.

Use the New or Open commands in the currently running Audacity
process to open multiple projects simultaneously.
```

If someone can tell me - in simple baby steps - how to resolve this frustrating problem, I would be very grateful.

---

