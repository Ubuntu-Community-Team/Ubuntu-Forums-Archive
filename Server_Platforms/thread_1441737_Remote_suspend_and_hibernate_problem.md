---
title: "Remote suspend and hibernate problem"
date: 2010-03-29
forum: Server Platforms
---

### Post by halthur on 2010-03-29
I am new to Ubuntu and Shell Scripts, but I have set up a shell script to backup files from my workstation (Ubuntu 9.10) to my home server (Ubuntu Server 9.10) using incremental backup with rsync.

The script is run from the server and the backup works perfectly. However, at the end of the script I want to send a command to put the client workstation in suspend or hibernate and I have tested the following commands both in script and directly form the server terminal (I have set up RSA keys to allow login without passwords).

```
 ssh 192.168.0.103 'pm-suspend' 
```This works in the sense that the client workstation goes into suspend, the problem is that the server freezes and seems to wait for the client to respond so it does not get back to the prompt or exits the script until the client workstation has been restarted or I press Ctrl+C.

I have also tested with:

```
 ssh -o ConnectTimeout=20 192.168.0.103 'pm-suspend' 
```but this makes no difference so i guess that I have misunderstood that function.

In other words... I would like help with how I can send a pm-suspend or pm-hibernate command to the client and then go on to finishing the rest of the script and exit.

As a note I can say that it does work with:

```
 ssh 192.168.0.103 'shutdown -P now' 
```But I do not want to turn the client off.

Grateful for help.

---

### Post by darthmob on 2010-03-29
Did you try running it in the background? eg.

```
ssh 192.168.0.103 'pm-suspend' &
```

I'm not sure if you have to use brackets but it's worth a try that way. It's quite common in startup scripts when you don't want it to actively wait for a return of a command. :)

---

### Post by airtonix on 2010-03-29
Maybe you could use the DBUS method of suspending the machine?

```

#!/bin/bash
#Suspend
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0

```

The issue i have with using ssh to send the suspend signal is that every time you do so it leaves a tty running.

Over time they will build up.

I would find a way to use DBUS or AVAHI or SNMP to send and receive signals to notify when the RSYNC operation starts and finishes.

When the RSYNC operation finishes, the Server sends a "complete" message, and the Workstation sees this then runs its DBUS suspend command.

---

### Post by halthur on 2010-03-31
Thanks!

Running the process in the background using: 

ssh 192.168.0.103 'pm-suspend' &

works well and was very simple. :p

As for the DBUS method, I have not tried that yet and it seems more complicated so I have to gain some more knowledge of how it works first.
How does it work with these tty running, will they pile up for ever or will they eventually die out, and how does it effect the system... Does the server or the client need to be restarted for them to be killed?

---

