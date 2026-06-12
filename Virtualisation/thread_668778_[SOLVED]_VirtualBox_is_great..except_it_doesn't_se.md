---
title: "[SOLVED] VirtualBox is great..except it doesn't see my ipaq"
date: 2008-01-15
forum: Virtualisation
---

### Post by MikeyXX on 2008-01-15
If I plug in a memory stick via USB it's found, and works in both linux and my guest OS (XP).

I got USB to work via [http://www.arsgeek.com/?p=2776]("http://www.arsgeek.com/?p=2776")
Worked great.

Now when I plug in my ipaq I get:

Failed to attach the USB device Intel. PocketPC Smartphone to the virtual machine XP.

Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).

Result Code:   0x80004005
Component:    Console
Interface:        IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Any suggestions? If I do a sudo modprobe ipaq and then a dmesg | tail it does show my ipaq on TTYUSB0

I really need to sync my ipaq and I was hoping this VM would be my answer.

---

### Post by uncata on 2008-01-22
Same with the Nokia N70. :-(

(Sorry, I don't speak english at all.)

Thanks

---

### Post by fjgaude on 2008-01-22
Did anykind of install disk come the the ipaq? If so, did you try to use it in the guest VM?

---

### Post by MikeyXX on 2008-04-16
No, the install cd would only work if the vm saw my ipaq.


I did finally get it to work. 

What I did was go into the VirtualBox and go to the OS's settings. Go to USB and create a blank filter (top icon on the right).

Then I ran the XP VM and when it was up and running I plugged in my IPAQ. I then clicked the USB icon on the bottom of VirtualBox and clicked the IPAQ. This unhooked it from Ubuntu and offered it to the VM. This worked fine.


Now I had to use the real VirtualBox, not the open source. I also had to have an IPAQ that was willing to be seen on a Windows box. Turns out the one I was using was flaky even with Windows so it only added to the frustration.

---

### Post by aks2008 on 2008-06-05
Hi
 Method described by MikeyXX in last post didn't work for me directly for my bluetooth dongle. Ubuntu's Bluetooth device management service refuses to hand over control of my bluetooth dongle to virtualbox resulting in same error as 1st post.
 I had to deactivate that service from system>administration>services before virtualbox could unhook my dongle from ubuntu host and make it available to XP guest.

---

