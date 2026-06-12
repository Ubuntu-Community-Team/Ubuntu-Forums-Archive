---
title: "USB Host devices enabled in Virt Manager for VM not redirecting"
date: 2021-12-18
forum: Virtualisation
---

### Post by aljames2 on 2021-12-18
My system becomes unstable when I enable a USB host device for use in my VM.  Unstable means the VM is slow starting with an occasional video artifact that flashes on the screen.  Shutdowns of the VM from inside the VM using "Power-off" gives black screen that often freezes.  If I just "X" out of the VM console and try to stop the VM from Virt-Manager I get the same freezing result.  When I restart the host, I get screen messages that the VM is not shutting down giving this:

```
USB 5-2: device descriptor read /64, error -110
libvirt-guests.sh[4242]: Waiting for guest Ubuntu-20.04 to stop...
```

When I remove all USB host devices from the VM in Virt-Manager, the VM seems to start and stop ok.  Then I thought I would try the USB redirection icon at the top of the screen from within the VM and select the Printer or USB stick, but after selecting a device the system starts freezing again.

In some of my readings, I am suspicious that Apparmor is causing the  problem.  I have seen an occasional Apparmor Denied lines in some logs.  I am not sure if disabling Apparmor on either the host or VM would solve it, but that doesn't sound good for security. I could disable one and try again but not sure if it is the host or VM apparmor that is causing the problem.

My host and guest VM are running on the same bare metal.
My host OS is debian 11 stable desktop w/KVM, qemu, Virt-Manager, & Virt-Viewer.  The network is a bridge setup (br0).  All seems good on the host side.
My VM is Ubuntu 20.04 Dekstop, configured to autostart when the host is started or restarted.  I have a link on my host desktop that launches a Virt-viewer command for my wife to have quick access to the VM desktop to do her things.  
Display is set to Spice and Video is set to QXL.  My host has the proprietary Nvidia driver installed.  I don't seem to have video issues and things seem to run well in the VM, except for when I do USB things, then everything freaks out. 

The USB devices I need to redirect to the VM is a USB connected HP Officejet printer, and occasionally a USB stick.  My USB keyboard and mouse seem to just work in the VM.

---

### Post by MAFoElffen on 2021-12-19
Please post which version of 'libvirt'... 
```

virsh --version 
libvirtd --version

```

---

### Post by aljames2 on 2021-12-19
```
~$ virsh --version
7.0.0
```

```
~$ sudo libvirtd --version
libvirtd (libvirt) 7.0.0
```

Thanks

---

### Post by MAFoElffen on 2021-12-20
Not related then. libvirt version 6.9.0 had a problem with the sourcecode, that had a Bug related to USB redirection, where it needed a patch to correct it... LibVirt Version 7.0 would be after that Patch.

It is not related to your Ubuntu 20.04 VM Guest. It is related to LibVirt on your host. The physical pass-through of USB issue, that throws apparmor errors, has to do with the interaction between the host and the VM 'Machine' (before the installed OS)... It is not an AppArmor Problem, but AppArmor is effected by it, as a result. So the AppArmor errors are more a byproduct and indicator when that happens.,. the physical/metal hardware combination. I have no found a problem with an Ubuntu VM Guest where it was the cause of a USB redirection problem.

Mostly that occurs between the Host system, the Host's KVM configuration, and the Host's and the Hosting connection between the VM Machine configuration... Before the OS is installed. Although sometimes it may be the Virtio Drivers of the OS... But that is more common with OS'es other than Linux, such as Windows.

Current version of LibVirt in Ubuntu 20.04 LTS is 6.0.0. It does not have that problem. Current version of LibVirt in Ubuntu 22.04 DEV is 7.6.0. It does not have that problem. 

I spun up an instance of Debian 11.2... and it says LibVirt is Version 7.0.0... IDK... I passed-through one of my USB ports into KVM,... from my host (Ubuntu 20.04 LTS) running LibVirt 6.0.0) into a KVM Debain 11.2 VM Guest... Running LibVirt 7.0.0, into a nested KVM Ubuntu 20.04 Guest... Passing the physical USB pass-through each instance... and it is running stable. I can say that I cannot recreate your problem. It seems if there was problem with an install of KVM on Debian 11, it would surely show on a nested virtualization... Maybe because of difference in hardware between me and you? In the way I tested it, the Debian 11 KVM Host is on virtualized hardware, nested within KVM on Ubuntu 20.04...

Maybe if you ran the Ubuntu Forum's 'system-info' script in my signature line so we can see what the difference may be(???)

Other than that. all I can recommend is that you file a Bug against LibVirt on your Host's OS Bug Report System... Which for you, would be Debian.

EDIT: I ran a report on the VM. It is at: [https://termbin.com/lsgx](https://termbin.com/lsgx)

Look under the 'lsusb' section, Port 01.x...

---

### Post by aljames2 on 2021-12-30
Thanks for the help.  Things were a little rocky working off the Debian stable GUI host, I thought I would try something new.  Plus it was the Xfce environment which was new to me, it felt old, and I really didn't like it.  The good was that Htop reported less than 700mb of ram being used by the host.

Anyway, I blew it up and started over with Ubuntu MATE as host.  Better to my taste and about 1gb of ram used at rest, and 3.8gb used with my Ubuntu 20.04 Gnome VM running, from which I am writing this post.

All wasn't smooth with MATE either regarding the USB redirection.  The USB stick would pass through (USB2), however trying to pass my USB printer would make the whole system unstable again.  After some troubleshooting I discovered that I had the printer connected to a USB-3.  When I switched the connection to a USB-2, the printer passed through automatically, no issues.

I would think a USB-3 connection should pass through....wait.... nope it doesn't....   I just unplugged the printer from USB2 & tried the USB3 again and the connection was lost & the virt-viewer froze, it gave a message that the printer was in use (interesting, hadn't seen that before)...unplugged and plugged back into a USB2 and pass-through to VM reconnected.  Good thing, because I thought I was going to have to retype all this.

Thanks again!

---

### Post by MAFoElffen on 2021-12-31
Just "How" are you "redecting" the USB ports to the VM?

Are you doing a hardware pass-through using the VM configuration, such as from the Details View of Virt-Manager, Add Hardware, hardware USB Port Device?

Or are you talking about from the VM Viewer Window, Redirect USB?

Because, yes... If you do it in the configuration, it is set to a specific USB Hub, then the specific channel and port of that hub, and is set to a specific device.. Which is initialized on VM startup. Right then, the hardware is hard-bound to the VM, from the host system, through to the VM Machine, and it's OS. If you change anything after the VM starts, it breaks that bond and it will become unstable. That includes, (On the Host) having it in another port, than from where it was when it was configured, or unplugging it while it is running. That sounds like what you described. An Example of that hard-wiring is the XML snippet for something like that:
```

<hostdev mode="subsystem" type="usb" managed="yes">
  <source>
    <vendor id="0x04f2"/>
    <product id="0xb217"/>
  </source>
  <address type="usb" bus="0" port="4"/>
</hostdev>

```
How I would describe what happens when you do that... Imagine what would happen if you passed through a PCI card to a VM... It is assigned by the Bus and Slot hardware ID's. Change where that card is, and that changes... Then look at how USB ID's are assigned. They re dynamically assigned an ID. Adds a bit more to complexity.

For a VM dynamic/virtual redirection, for an Ubuntu flavored VM in KVM, the default for OS type Ubuntu, is to add only 2 USB Redirectors through the Channel Spice. You can add more, through Add Hardware > USB Redirection, or add the XML snippet for it. Here Example USB Redirector Snippets:
```

<channel type="spicevmc">
  <target type="virtio" name="com.redhat.spice.0"/>
  <address type="virtio-serial" controller="0" bus="0" port="2"/>
</channel>
<redirdev bus="usb" type="spicevmc">
  <address type="usb" bus="0" port="2"/>
</redirdev>
<redirdev bus="usb" type="spicevmc">
  <address type="usb" bus="0" port="3"/>
</redirdev>

```
If it was done through that VM viewer window or through the resultant XML define of the domain, you can see where that is more dynamic, through the menu item "Redirect USB X", that is more a virtual link, than a hard-wired hardware bond....

---

### Post by aljames2 on 2022-01-02
At first I did not know the difference between the USB assignment via the VM viewer (VM details), and the USB redirection option within the VM.  Your explanation explains why I was having my problems.  Using the VM details to assign a USB device is for devices that remain physically connected through VM startup & shutdown, such as a printer.  My trouble first came when trying to use this “hard connection” for a USB thumb drive…I noticed if the device is not always plugged in, the VM would not shut down or start.

It is still unclear why a device on my USB-3 port is unstable, unless I have a bad port.  Everything works when plugged into USB-2.

On second thought, it’s not a bad USB-3 port because that port works outside the VM.

---

