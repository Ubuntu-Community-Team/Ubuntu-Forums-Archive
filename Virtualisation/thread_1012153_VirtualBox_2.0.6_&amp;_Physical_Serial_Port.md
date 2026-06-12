---
title: "VirtualBox 2.0.6 &amp; Physical Serial Port"
date: 2008-12-15
forum: Virtualisation
---

### Post by DirtyBirdNJ on 2008-12-15
Hello, I am trying to get some windows software to work in VirtualBox 2.0.6. The program is called AquaNotes and it lets me interface my desktop PC with their AquaController computers via a Serial RS-232 port. 

I tried to run the program in Wine, but it crashes. The program runs fine on XP in VirtualBox, but I can't figure out how to get virtualbox to let the virtual machine access my physical serial port.

Also, I am very interested in seeing the traffic that gets sent back and forth, the manual for the device lists a few commands you can use but does not give a full list.

---

### Post by DirtyBirdNJ on 2008-12-16
Ok, I still can't get this to work. When I open up VirtualBox I get this error

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

```

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}
```

On the Serial Port configuration panel in VirtualBox, there are 3 options for the serial port mode: disconnected, host pipe, and host device.

I don't really understand these options, but I *do* know that I don't want to run in disconnected or host device mode. The default value when setting up the serial ports in VB is /dev/tty0. Unfortunately that dosn't work for me.

```

NamedPipe#0 failed to bind to local socket /dev/tty0.
VBox status code: -448 (VERR_NET_ADDRESS_IN_USE).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}
```


SO... my question now is how does this host pipe thing work?

---

### Post by HotShotDJ on 2008-12-16
> **DirtyBirdNJ said:**
> SO... my question now is how does this host pipe thing work?I'm pretty sure you do NOT want host-pipe.  You want host device:[QUOTE="VirtualBox End-User Manual"]You can connect the virtual serial port to a physical serial port on your host. (On a Windows host, this will be a name like COM1; on Linux or OpenSolaris hosts, it will be a device node like /dev/ttyS0). VirtualBox will then simply redirect all data received from and sent to the virtual serial port to the physical device.[/QUOTE]
I'm not very familiar with configuring a serial port.  You may want to take a look at pages 50 and 51 of the User Manual (you can find it at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) -- it is a PDF file)

---

### Post by cod.almighty on 2009-02-14
I had problems trying to get virtualbox to recognize my serial port. Here's what I did:
  on the serial ports settings page set Port Number to COM1
  set Port Mode to Host Device
  set Port Path to /dev/ttyS0
then after booting up winXP run Start > Settings > Control Panel > Add Hardware.
the serial port didn't show up in the hardware wizard so I had to use the Advanced option (Install manually from a list.)
After doin this virtualbox recognised my serial port as COM3.

---

### Post by sebasthian777 on 2009-02-20
Hi! (my English is very poor)...

I have a very similar problem...
when i do that (port path = /dev/ttys0) the program crash!!!
in internet says that we must do a pipe whit the virtual port (VirtualBox) and the Phsysical port (COM hard).... this pipe do whit a program, for example: socat....

but i dont understand how can i do it... :S

good luck and sorry 4 my bad English!

if i found a solution, immediately i tell you!

---

### Post by Captain Bosh on 2009-02-25
> **cod.almighty said:**
> I had problems trying to get virtualbox to recognize my serial port. Here's what I did:
  on the serial ports settings page set Port Number to COM1
  set Port Mode to Host Device
  set Port Path to /dev/ttyS0
then after booting up winXP run Start > Settings > Control Panel > Add Hardware.
the serial port didn't show up in the hardware wizard so I had to use the Advanced option (Install manually from a list.)
After doin this virtualbox recognised my serial port as COM3.

Thanks, this worked for me using an Ubuntu Host with an XP Pro guest, I then tried it again with the same setup at a later date and Windows reported a problem with the port.

I have now managed to solve this by:

In Windows:

Device Manager - Ports - Communications Port (COM 3)- Properties - Port Settings - Advanced

Change the port number from COM1 to COM3 (even though it warns of conflict) click OK

Then at the Resources tab change the IRQ of the port to 4 (I used  Basic Configuration 0000).  Then restart.

I have now tried this a few times and it seems to work in each case

---

### Post by cod.almighty on 2009-02-25
Glad my post helped, a lot of the information about virtual box seems quite cryptic and hard to understand. I haven't run into any probs with my own setup yet but I'll keep your fix in mind for any future installs. thanks Captain.

---

### Post by Odemia on 2009-03-23
In my experience XP seems to create Com3 when installed on vbox.

On my 8.10 machine I setup COM1 in vbox then went into the device manager and deleted all the COM ports that magically existed and finally created a new COM port and changed it to COM1.  Seems to be working for me.

Is there a reason why you would setup COM1 in the vbox setting and then use COM3 in the Windows install?

---

### Post by cod.almighty on 2009-03-25
> **Odemia said:**
> Is there a reason why you would setup COM1 in the vbox setting and then use COM3 in the Windows install?

I left the serial port in my windows guest as COM3 simply because it defaulted to this and it worked. I didn't have any reason to change it.

---

