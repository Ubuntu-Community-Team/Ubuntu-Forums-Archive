---
title: "no mouse pointer in VMware under unity mode"
date: 2010-07-27
forum: Virtualisation
---

### Post by RikoW on 2010-07-27
Dear all,

after some time, I wanted to work in unity mode again. However, in unity, the mouse pointer disappears when the mouse is in the application window. Is their an work-around?

When having Vmware in a window or in full screen mode, the mouse is visible as it should be.

I'm running WS7.1 on an Ubuntu 10.04 host with a XP SP3 guest.

Thanks and cheers,
Riko

---

### Post by RikoW on 2010-07-28
Some more information:

seems to have something to do with the mouse. The host is a laptop. When I use the internal touch-pad of the laptop, the mouse pointer is visible in unity mode without problems.

However, in the office, the laptop usually sits in a port replicator with an external USB mouse and keyboard. Only with the USB mouse the pointer disappears in unity mode.

I already tried 3 different USB mice (2x wireless, 1 cable). Always the pointer is invisible in Unity mode.

Maybe one needs to fiddle with the mouse driver of the VM, but I have no idea how and where. :(

Cheers,
          Riko

---

### Post by dcstar on 2010-07-31
> **RikoW said:**
> Some more information:

seems to have something to do with the mouse. The host is a laptop. When I use the internal touch-pad of the laptop, the mouse pointer is visible in unity mode without problems.

However, in the office, the laptop usually sits in a port replicator with an external USB mouse and keyboard. Only with the USB mouse the pointer disappears in unity mode.

I already tried 3 different USB mice (2x wireless, 1 cable). Always the pointer is invisible in Unity mode.

Maybe one needs to fiddle with the mouse driver of the VM, but I have no idea how and where. :(

Cheers,
          Riko
See if you can add another USB Controller in the Hardware settings of the VM (when it is docked), and ensure VMware Tools is updated in the VM.

---

### Post by RikoW on 2010-08-02
Hi David,

I can't add another USB controller. vmware claims with 1 present the maximum is reached.

Meanwhile, I don't think anymore it's a problem with the mouse. When I undock the laptop, use an (any) external mouse and run the VM in unity mode, the mouse works just fine. So the only immediate difference I see is the resolution of the screen (1920x1200 docked vs 1280x800 un-docked). But even if I force the lower resolution on the external screen, still no mouse pointer :(

VMware tools are (of course:) up to date.

Thanks again,

              Riko

---

### Post by RikoW on 2010-10-04
OK, here's what worked for me:

1) in the VM, create a new hardware profile (that's just a precaution, in case something goes wrong

2) set it in a way, that you select the HW profile during boot

3) restart the VM into the new profile

4) open the device manager in the VM, open the mice entry and de-install mouse driver (mine was called "vmware ..."

5) restart the VM again into the new profile with the mouse connected you want to have working properly; XP will now detect new HW and install the correct driver

6) reboot again and everything should work

I guess, now you could remove the old HW profile (or at least boot into the new one automatically)

In case someone has the same problem .... :)

Cheers,

             Riko

---

