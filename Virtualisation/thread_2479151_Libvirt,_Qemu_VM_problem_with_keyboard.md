---
title: "Libvirt, Qemu VM problem with keyboard"
date: 2022-09-15
forum: Virtualisation
---

### Post by Watchintv on 2022-09-15
I am building a system comprised of Linux 5.9.18 and Busybox.

I am able to get a shell open. But, my keyboard does not work.

I am using libvirt with Qemu.

My kernel config is configured as the following (allnoconfig, and then the settings below):
```
[*] 64-bit kernel
-> General setup
  -> Configure standard kernel features
[*] Enable support for printk
-> General setup
[*] Initial RAM filesystem and RAM disk (initramfs/initrd) support
-> Executable file formats / Emulations
[*] Kernel support for ELF binaries
[*] Kernel support for scripts starting with #!
-> Device Drivers
  -> Character devices
[*] Enable TTY
-> Device Drivers
  -> Character devices
    -> Serial drivers
[*] 8250/16550 and compatible serial support
[*]   Console on 8250/16550 and compatible serial port
-> File systems
  -> Pseudo filesystems
[*] /proc file system support
[*] sysfs file system support
-> Kernel hacking                                                     
    -> Compile-time checks and compiler options 
[*] Debug filesystem
-> Kernel hacking   
[*] Early printk

```
I edited my VM's XML file like so:
```

<device>
...
    <input type='evdev'>
      <source dev='/dev/input/by-id/usb-Dell_Dell_USB_Keyboard-event-kbd' grab='all' repeat='on'/>
    </input>
...
</device>
```

The keyboard seems to catch on to the VM window, but it does not type anything when I press any keys. Not sure what the issue could be. Any help would be greatly appreciated!

Thank you!

---

### Post by TheFu on 2022-09-16
If it were me, I'd take a standard distro and use virt-manager to setup the VM environment (that's libvirt + kvm/qemu), install a normal distro into the VM, then dump the libvirt XML generated.  Usually, physical devices aren't used inside VMs.  Fake hardware is simulated for use by a VM - the NIC, the HDD, the RAM, the CPU, and the GPU - all fake.  Same for the keyboard and mouse.  You should do those same things in your setup.

I doubt you really want just qemu, since software virtualization is slow. KVM unlocks the CPU hardware support to qemu for much faster, hardware-based, context switching that blows away what qemu does alone.

After you see what a number VM that works uses, you can setup your special VM to be the same.

---

### Post by MAFoElffen on 2022-09-20
I have to add keyboards and framebuffers to emulated ARM64 Servers... It's a lot easier than that (just a one liner).
```

<devices>
    ...
    <input type="keyboard" bus="ps2"/>
    ...
</devices>

```

---

