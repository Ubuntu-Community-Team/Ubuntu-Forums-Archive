---
title: "Install usb printer in virtualbox"
date: 2009-12-20
forum: Server Platforms
---

### Post by fizgig on 2009-12-20
I'm running virtualbox 3.something on ubuntu 9.10.  The VM is windows XP.

I'm trying to install a printer that's already installed on the host linux system that works fine.  I've shared it on the host and I want to connect the bridged vm to the shared computer so I can print from the VM.

When I try to install the printer on the XP VM, I get through the installation to the point to where it asks me to plugin the printer.  Since the printer is already plugged in and openvpn for ubuntu doesn't appear to support usb passthrough, I can't get the VM to see it to finish the installation.

The problem is the printer installation program expects to see the printer directly attached during installation even though I plan to make it point at a network port later.  Anyone know how to get around this problem?

---

### Post by MontelEdwards on 2009-12-24
You have to have the non-free version of VirtualBox from [http://dlc.sun.com/virtualbox/vboxdownload.html#linux]("http://dlc.sun.com/virtualbox/vboxdownload.html#linux") that will support USB. After that, you need to configure some options on the host.

[https://help.ubuntu.com/community/VirtualBox/USB]("https://help.ubuntu.com/community/VirtualBox/USB")

---

### Post by fizgig on 2009-12-24
I was hoping to find a way that didn't involve usb passthrough.   Perhaps by manually copying drivers or something.

---

### Post by MontelEdwards on 2009-12-24
Why don't you share the printer with Samba

---

### Post by fizgig on 2009-12-24
I do share the printer with samba. That works fine.   The trouble starts when I want to install the printer in the xp vm.   The only way to install it in windows is to run the setup.exe file which expects the printer to be locally connected at some point in the install.  That appears to require the non-free version of virtualbox **unless** there's another way or trick that people have been able to use which is the question/topic of this thread.

---

### Post by Marlonsm on 2009-12-24
To add a network printer in Windows XP (I think in the other versions it's about the same) you have to open the control panel, open the "Printers and other hardware" window and use the "Add new printer" wizard, it might ask you for a driver, just point it to the CD or to the .exe file.

---

### Post by fizgig on 2009-12-24
Appreciate the help.  This printer wasn't meant to be a network printer so going that route in XP doesn't work.  There is only a setup.exe file that goes through a bunch of steps where you hit next, next, next and then it leaves you with a usb printer in your list of printers.

What I then usually do is unplug the printer from XP, add a new network printer from scratch, choose one of the built in HP drivers that XP has inside it and finish the install.  I then go to the printer properties, go to the advanced section and change the driver from the built-in hp driver to the specific driver for the printer that is now an option since the regular printer installation had been done when the printer was attached.

I can't do this with a VM that doesn't have USB passthrough though so it looks like I'll have to install that version of virtualbox.  I was just wondering if anyone had any other tricks I hadn't thought of such as copying files from an XP machine that already had the printer installed or something.

---

### Post by falconindy on 2009-12-24
It's irrelevant that the printer wasn't designed to be a network printer, because CUPS will publish it to the network. You can make windows point to the url: 
```
http://<host IP>:631/printers/<printer_name>
```
This may require changing the CUPS config (in /etc/cups/cupsd.conf) to accept remote connections. Not sure how Ubuntu comes configured by default.

---

### Post by fizgig on 2009-12-28
Sigh.  Not making myself clear...

Cups indeed makes the printer available on the network.  Here's the problem:  The printer installation program that comes with the printer for Windows XP REQUIRES the printer to be attached locally to the USB port at some point of the installation in order for it to copy over the right driver files and get everything going.

This isn't a problem on a standalone XP machine (where XP is the host).  In that case, I just connect the printer to the XP machine, do the driver install and then plug the printer back into the linux cups server.  I then configure the printer in the XP machine to be attached via a network port instead of local USB.

I can't do this procedure on an XP VM since I can't connect the VM to the printer directly via USB.

---

### Post by Andruk Tatum on 2010-10-12
> **fizgig said:**
> Sigh.  Not making myself clear...

Cups indeed makes the printer available on the network.  Here's the problem:  The printer installation program that comes with the printer for Windows XP REQUIRES the printer to be attached locally to the USB port at some point of the installation in order for it to copy over the right driver files and get everything going.

This isn't a problem on a standalone XP machine (where XP is the host).  In that case, I just connect the printer to the XP machine, do the driver install and then plug the printer back into the linux cups server.  I then configure the printer in the XP machine to be attached via a network port instead of local USB.

I can't do this procedure on an XP VM since I can't connect the VM to the printer directly via USB.

Those are some crappy drivers, but that isn't unheard of.  I hope this page helps you get USB passthrough working:
[https://help.ubuntu.com/community/VirtualBox/USB]("https://help.ubuntu.com/community/VirtualBox/USB")

Thanks.
-- Andruk (@) Tatum

---

