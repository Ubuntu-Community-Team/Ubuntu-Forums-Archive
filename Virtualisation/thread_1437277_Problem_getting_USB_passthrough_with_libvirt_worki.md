---
title: "Problem getting USB passthrough with libvirt working"
date: 2010-03-23
forum: Virtualisation
---

### Post by RoboJ1M on 2010-03-23
Hi,

I have an Ubuntu 9.10 Server x64 and libvirt 0.7.2.
I run ebox 1.3.5 over this to power my network infrastructure.

I created a routed virtual network (using virt-manager) and configured it with DHCP and DNS using ebox.

I created a VM, installed another copy of Ubuntu 9.10 Server x64 and I'm trying to pass my Hauppage Nova T 500 through to it.

It's a USB device hosted on a PCI card so I see this in lsusb:

```
Bus 003 Device 002: ID 2040:9950 Hauppauge 
```

So I created this file: dvb.xml


```
    <hostdev mode='subsystem' type='usb'>
      <source>
        <vendor id='0x2040'/>
        <product id='0x9950'/>
      </source>
    </hostdev>
```

in virsh:

```
virsh # attach-device myth /home/james/dvb.xml
Device attached successfully
```

However, in the VM itself:

```
james@myth:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

And in /var/log/libvirt/qemu/myth.log

```
husb: open device -603240760.32767
husb: USB Host Device Path not set: No such file or directory

```

Can anybody help me get this working?

Thanks,

James.

---

### Post by fgiff on 2010-04-09
Sounds like you need to look at apparmor: look here: [http://ubuntuforums.org/showthread.php?t=1300952](http://ubuntuforums.org/showthread.php?t=1300952)

---

### Post by RoboJ1M on 2010-04-10
Nothing is commented out, I take it they were referring to this section:


```
  # WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /dev/shm/ r,
  /dev/shm/pulse-shm* r,
  /dev/shm/pulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
  # 'kill' is not required for sound and is a security risk. Do not enable
  # unless you absolutely need it.
  deny capability kill,

  # Uncomment the following if you need access to /dev/fb*
  #/dev/fb* rw,

```

So, just looking at this file, do I have to add a line for my TV tuner to this file? Like" /dev/something rw,"? What does the k mean? Can I put in /dev/* rw?

Should, at this point, I just go read the apparmour manual? ;)

Anyway, I've upgraded to the 10.04 beta and it's working better... except that now I don't have any network access for the VMs.

J.

---

### Post by RoboJ1M on 2010-04-10
Tried adding this to the profile and restarting apparmour:


```
  /dev/dvb/ r,
  /dev/dvb/adapter* r,
  /dev/dvb/adapter* rwk,

```

Which is a copy of the bit about allowing access to sound hardware.

But it did nothing.

---

### Post by davidpmays on 2011-06-08
> **RoboJ1M said:**
> Nothing is commented out, I take it they were referring to this section:


```
  # WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /dev/shm/ r,
  /dev/shm/pulse-shm* r,
  /dev/shm/pulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
  # 'kill' is not required for sound and is a security risk. Do not enable
  # unless you absolutely need it.
  deny capability kill,

  # Uncomment the following if you need access to /dev/fb*
  #/dev/fb* rw,

```So, just looking at this file, do I have to add a line for my TV tuner to this file? Like" /dev/something rw,"? What does the k mean? Can I put in /dev/* rw?

Should, at this point, I just go read the apparmour manual? ;)

Anyway, I've upgraded to the 10.04 beta and it's working better... except that now I don't have any network access for the VMs.

J.

I am having a similar problem trying to attach a Konica Minolta Scan Dual IV to my virtual XP machine.  XP seems to work find but viewing details reveals no USB.
The following 3 lines are from my libvirt-qemu file.  I changed the r at the end of the line to rw to see if it would show up.   However, on the details screen of my XP Machine I cannot see any usb devices.
 # For hostdev access. The actual devices will be added dynamically
  /sys/bus/usb/devices/ rw,
  /sys/devices/*/*/usb[0-9]*/** rw,

My details screen has the following catagories
Overview
Performance
Processor
Memory
Boot Options
IDE Disk 1
IDE CDROM 1
NIC :7b:a1:f1
Tablet
Mouse
Display vnc
Console
Video

Hypervisor Details
Hypervisor: kvm
Architecture: x86_64
Emulator: /usr/bin/kvm

Is there any help for us?
It has to be something simple considering the file says the devices will be added dynamically.  I think I need a little more dynamic ;)

Thanks to everyone that takes a look.

---

### Post by davidpmays on 2011-06-08
OK, I have the Konica Minolta Scan Dual IV working.
Here are the steps I took.
After modifying the libvirt-qemu (I do not know if this was nessesary)
In the Virtual Machine I selected "View / Details"
At the bottom of the screen was "Add Hardware"
I changed the Hardware Type to "Physical Host Device"  Clicked "Forward"
Changed the Device Type to "USB Device"
Changed Device to my scanner and clicked "Forward" and then "Finish"
I rebooted the XP virtual machine and did not find the new hardware.
I rebooted the HOST computer.
running the XP virtual Machine now revealed the Scanner.

Hope this Helps

---

