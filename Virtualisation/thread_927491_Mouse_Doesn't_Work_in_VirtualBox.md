---
title: "Mouse Doesn't Work in VirtualBox"
date: 2008-09-23
forum: Virtualisation
---

### Post by twoseids on 2008-09-23
Whenever I start my guest OS (Windows XP) in VirtualBox, my mouse immediately stops working. My touchpad continues to work.

If I unplug the mouse and plug it back in, it works for a half second before becoming unresponsive again. When I've shut down Windows, then unplug and reconnect the mouse, it will work fine.

I have the latest guest additions installed, and under Devices->USB Devices, my Logitech mouse has a check mark beside it. Mouse integration is enabled.

Any ideas?

---

### Post by 10gallons on 2008-10-05
Bump!

I have this very same problem, exactly.

My USB mouse works fine until I start Virtualbox. Then it stops working. However my touchpad mouse works fine.

Once I shut down Virtualbox, unplug and replug my USB mouse, it comes back to life.

What I have also found is that my USB mouse seems to run but you can't see it. If I move my USB mouse slowly and it passes over the edge of a window, the cursor changes to the double arrowhead cursor and you can resize windows.

All help greatly appreciated.

---

### Post by waffen on 2008-10-08
I have the same error!!

I use Ubuntu 8.04 and VB 2.02

Any idea??

Thanks in advance!](*,)

---

### Post by 10gallons on 2008-10-08
I didn't get anywhere with this problem I spent some time installing and uninstalling the guest additions software and got different results for different versions of the software as well as when I didn't have it installed.

I can only think it is a bug that needs to be looked at.

I gave up, uninstalled Vbox and am now using VMWare server.

---

### Post by puller on 2008-11-01
Hi, i finally managed to solve this problem in Ubuntu 8.10 Intrepid.
First i activated the usb support adding this line to /etc/fstab:

```
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
```

Warning: this works only in intrepid, activating the usb support in Hardy or previous requires a different procedure.

Than I started the virtual box and installed guest addition (without mouse support, you can reach the menu "Devices" by holding ctrl+home, then release and suddenly press d, from that menu you can install guest additions).

Than I turned off the VM.
Now I enabled the USB support adding all the devices except the mouse!
If I enabled the mouse, I had the described problem.
Without checking it, everything works fine!

---

### Post by puller on 2008-11-01
Hi, i finally managed to solve this problem in Ubuntu 8.10 Intrepid.
First i activated the usb support adding this line to /etc/fstab:

```
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
```

Warning: this works only in intrepid, activating the usb support in Hardy or previous requires a different procedure.

Than I started the virtual box and installed guest addition (without mouse support, you can reach the menu "Devices" by holding ctrl+home, then release and suddenly press d, from that menu you can install guest additions).

Than I turned off the VM.
Now I enabled the USB support adding all the devices except the mouse!
If I enabled the mouse, I had the described problem.
Without checking it, everything works fine!

---

### Post by mad-chad on 2008-12-26
After I updated to version 2.1, I lost wireless mouse support. I re-installed guest additions, and still no mouse. This worked like a charm. Thanks !!
> **puller said:**
> 
Than I turned off the VM.
Now I enabled the USB support adding all the devices except the mouse!
If I enabled the mouse, I had the described problem.
Without checking it, everything works fine!

---

### Post by jflarm on 2008-12-27
Don't know who you are, but you are a life saver!!!
[COLOR="Red"][SIZE="3"]
THANKS!![/SIZE][/COLOR]

---

### Post by guga31bb on 2009-02-28
Wow, thanks for this! Using Virtualbox is much better with a mouse=)

---

### Post by bodhi.zazen on 2009-02-28
In theory the newest version of VirtualBox should not require this change, usb should work out of the box.

But, this is why I left advice on how to use USB devices in the mega thread.

If you have a question on virtualization, please look at the mega thread, there is a reason it is a sticky :twisted:

---

### Post by japase on 2009-03-06
Hi,

I have a related mouse problem.

My VirtualBox runs fine, everything works as expected; the mouse is working both natively in Ubuntu and inside the VB. But sometimes, on releasing mouse and keyboard from VB, the mouse stops responding in a very strange way: I can see the mouse pointer, it reacts to mouse movement, but it doesn’t work – clicks aren’t caught by Ubuntu any longer.

The only thing I can do in such situation is to close all the programs using Alt-Tab and Alt-F4 and restart X.
I’m using Ubuntu 8.10 with USB mouse.

Would be very grateful for any tip!

---

### Post by jimmybarcelona on 2009-03-12
I have the opposite problem. My touchpad won't work, so I effectively have no mouse inf virtual box, because I am running a laptop without way to connect an external mouse,as I am using the virtualbox open source edition, which does not have usb support. How can I get it to recognized my touchpad?

---

### Post by jimmybarcelona on 2009-03-13
I'm running virtualbox opensource edition, which doesn't come with usb support. I'm running a laptop with no mouse peripherals, I think it just assumes that if I want a mouse I'll use usb or bluetooth. Anyway, I'm fine not having a mouse, but I cannot get my touchpad to work. 
I've installed the guest additions on the xp guest operating system, and on my host operating system of Intrepid Ibex. (was I only supposed to install it on the guest operating system?) I can get virtualbox to "capture" my pointer, but it doesn't move anywhere. 
If I use the keyboard to navigate to control panel and open up the mouse controls, it says "unable to connect to synaptic pointing device driver". and then lists some missing .dll's. Any ideas?

---

### Post by jesterfred on 2009-04-13
I have Ubuntu 9.04 Beta x86_64 Desktop installed as host and am running Windows XP SP3 as guest.  All worked well in VirtualBox 2.1.  I Just upgraded to 2.2 using Sun's .deb from their repository.  The upgrade went well but I have lost the mouse integration.  I did update the guest additions to no avail.

The 'Disable Mouse Integration HOST+I' menu item is grayed out.  This is strange as it indicates that the mouse integration is turned on and that I am unable to turn it off.  It is not turned on and I can not change the status.

I am able to use the HOST key to capture and release the mouse.  I'm just looking to get back to the seamless mode.

Anyone else suffer this?  Perhaps have a fix?

---

### Post by newhoggy on 2009-04-18
I'm running Ubuntu 9.04 RC x86_64 as guest inside VirtualBox with guest additions installed on a Windows Vista host and the mouse pointer is visible during the logon screen, but once I log on, the mouse pointer is invisible.  Also mouse integration doesn't work.

---

### Post by MithrandirAgain on 2010-04-19
> **puller said:**
> Hi, i finally managed to solve this problem in Ubuntu 8.10 Intrepid.
First i activated the usb support adding this line to /etc/fstab:

```
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
```Warning: this works only in intrepid, activating the usb support in Hardy or previous requires a different procedure.

Than I started the virtual box and installed guest addition (without mouse support, you can reach the menu "Devices" by holding ctrl+home, then release and suddenly press d, from that menu you can install guest additions).

Than I turned off the VM.
Now I enabled the USB support adding all the devices except the mouse!
If I enabled the mouse, I had the described problem.
Without checking it, everything works fine!

Thank you so much, puller! After someone else here helped me a lot, my mouse began to mess up. You solution makes it all work great. :popcorn:

---

### Post by Toci on 2011-01-23
> **puller said:**
> 

Than I turned off the VM.
Now I enabled the USB support adding all the devices except the mouse!
If I enabled the mouse, I had the described problem.
Without checking it, everything works fine!

 This worked for me too, then the keyboard stopped working, so I disabled USB filters for each item and that solved the problem.

---

