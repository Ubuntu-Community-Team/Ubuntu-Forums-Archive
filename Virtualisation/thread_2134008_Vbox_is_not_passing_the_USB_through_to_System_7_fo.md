---
title: "Vbox is not passing the USB through to System 7 for MyTomTom"
date: 2013-04-09
forum: Virtualisation
---

### Post by fester225 on 2013-04-09
While TomTom runs their products on Linux systems, they provide no way to update your maps using Linux-based systems.

I installed System 7 and MyTomTom on VirtualBox (v4.2.10 r84104). When I attach the GPS device to my Ubuntu box, it is recognized, and the top menu (Devices/USB) shows the TomTom device, then I select it. With MyTomTom already running, System 7 does not recognize the GPS attached to the USB port.

How do I get System 7 under VBox to recognize my Ubuntu (12.04) USB port?

---

### Post by papibe on 2013-04-09
Hi fester225.

I'm away from my VMs right not, but I remember that you have to reserve the USB port from the main VirtualBox window, so that I can be access excusively from a particular VM.

Turn off your VM. Once you've set that up, launch the VM again.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by fester225 on 2013-04-10
I thought I already did that from the top menu (Devices/USB). When I click on the USB icon at the bottom of the screen, it shows nothing attached.

---

### Post by papibe on 2013-04-10
Let's check the basics:
[LIST]
[*]Did you install the guest additions on Windows?
[*]Did you install the extension pack on Ubuntu?
[*]Did you add the current Windows user to the 'vboxusers'?
[/LIST]
Regards.

---

### Post by fester225 on 2013-04-10
-guest additions?  Yes.
- extension pack on Ubuntu?   What extension pack?
- VBox Users? Yes.

---

### Post by papibe on 2013-04-10
You need to install the "Oracle VM VirtualBox Extension Pack" in order to use USB devices. Download it [here]("https://www.virtualbox.org/wiki/Downloads").

Let us know how it goes.
Regards.

P.S.: I meant the 'vboxusers' group. Right?

---

### Post by fester225 on 2013-04-11
The Vbox Extension Pack is in.
The current Window is part of the vboxusers' group.

I plug-in TomTom, it is recognised by Ubuntu.
I start VBox, then System 7 (TomTom shows as being disconnected by Ubuntu), which automatically starts MyTomTom.
The TomTom USB is not recognised by TomTom (I'm not sure about System 7).
I disconnect TomTom.
I shut down VBox completely.
I plug the TomTom back in, and it is not recognised by Ubuntu.

There have been times when TomTom shows as available through the top menu (VBox Devices/USB), but after I select it, it becomes unavailable.

---

