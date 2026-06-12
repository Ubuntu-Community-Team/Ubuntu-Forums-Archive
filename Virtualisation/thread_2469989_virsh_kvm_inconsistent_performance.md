---
title: "virsh kvm inconsistent performance"
date: 2021-12-16
forum: Virtualisation
---

### Post by notstirred on 2021-12-16
I've been having bizarre performance issues when connecting to a VM hosted locally (machines have gigabit connection & ~5ms latency, so that shouldn't be an issue)

I used `virt-install` like so (using even deprecated `--accelerate`) `virt-install --name accelerated-test --ram 10240 --cdrom /home/tom/ubuntu-20.04.3-desktop-amd64.iso --os-variant ubuntu20.04 --virt-type kvm --accelerate --graphics vnc,listen=0.0.0.0`
after installing the vm, and connecting (via `vnc` or `spice`) the performance is bad, super high latency ~200ms, moving a window around the desktop causes lots of lag and many artefacts

After many debugging steps and reboot for some unrelated bios change; I started 2 vms, one felt near-native performance, the other terrible. After restarting them, it was terrible for both again.

The system is H11DSI-NT 2xEPYC-7601 + random 750ti I had lying around

---

### Post by TheFu on 2021-12-16
I've never used virt-install.  Just use **kvm** + **libvirt** and **virt-manager**. The defaults are pretty good today.  Also, don't use VNC. Stick with SPICE.
[https://blog.jdpfu.com/2012/07/30/improving-kvm-performance](https://blog.jdpfu.com/2012/07/30/improving-kvm-performance) outlines choices that need to be made whenever setting up a VM.  Mainly, use virtio for disk and network drivers.  There might be a virtGPU driver (use that instead of SPICE). If not, use SPICE and load the QXL drivers into each guest.

For Windows guests, you'll need to load QXL and virtio drivers from Redhat post-install.

Also, manually setup a linux-bridge. There's something not-so-great about the bridge setup in libvirt that has poor performance. An example for netplan with static IPs. You'll need to change the eth0 to match your ethernet card. Don't use DHCP.
```
#   [ for bridge + static - KVM ]
network:
 version: 2 
  renderer: networkd
  ethernets:
     [COLOR="#FF0000"]eth0[/COLOR]:
       dhcp4: false
       dhcp6: false
  bridges:
      br0:
        interfaces: [[COLOR="#FF0000"]eth0[/COLOR]]
        dhcp4: false
        dhcp6: false
        addresses: [192.168.1.15/24]
        gateway4: 192.168.1.1
        nameservers:
           addresses: [192.168.1.1]
```

Use either fully pre-allocated storage or QCOW2 storage. On an SSD, this isn't too important, but on spinning HDDs, it matters 30+%. Of course, you can use LVM storage - an LV for each VM is how I do it. Works great and integrates into libvirt nicely.

Don't expect GUI stuff to be fast. That isn't where VMs shine.  They shouldn't be slow for productivity apps, but they aren't fast for games either.
The GPU in the physical machine doesn't matter. With SPICE, nothing a typical office worker would use should seem slow.  Oh ... and don't use Gnome3+. Stick with any other non-bloated Linux DE.  Excellent results come from Mate, XFCE, LXQt, Cinnamon, or any desktop that doesn't use any DE, just a pure window-manager. I use fvwm. It flies and has for the last 5 yrs.

Don't allocate too many vCPUs or too much vRAM to any guest.  10G is almost certainly way too much.  For linux systems, start with 1 vCPU and 4G of RAM for desktops. You can easily tweak them later, as needed.  For Windows, use 2 vCPUs, since Microsoft will install a different kernel for 1 CPU vs more than 1 CPU.  NONE of my Linux VMs have more than 2 vCPUs allocated to a VM. NONE.  None have more than 4GB of RAM either. Here's a hardware report for my main desktop, a VM:
```
$ inxi -b
System:    Host: regulus Kernel: 5.4.0-91-generic x86_64 bits: 64 Desktop: N/A 
           Distro: [COLOR="#008000"]Ubuntu 20.04.3[/COLOR] LTS (Focal Fossa) 
Machine:   Type: [COLOR="#008000"]Kvm[/COLOR] System: QEMU product: Standard PC (i440FX + PIIX, 1996) v: pc-i440fx-xenial 
           serial: <superuser/root required> 
           Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.10.2-1ubuntu1 date: 04/01/2014 
CPU:       [COLOR="#008000"]2x Single Core [/COLOR](4-Die): AMD EPYC (with IBPB) type: MCM SMP speed: 3409 MHz 
Graphics:  Device-1: Red Hat [COLOR="#008000"]QXL[/COLOR] paravirtual graphic card driver: qxl v: kernel 
           Display: server: X.Org 1.20.8 driver: none unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: N/A v: N/A 
Network:   Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge driver: piix4_smbus 
           Device-2: Red Hat [COLOR="#008000"]Virtio network driver[/COLOR]: virtio-pci 
Drives:    Local Storage: total: 40.00 GiB used: 18.44 GiB (46.1%) 
Info:      Processes: 173 Uptime: 1d 16h 09m Memory: 3.84 GiB used: 1.29 GiB (33.6%) Shell: bash inxi: 3.0.38 
```

That VM was first setup in 2010 and has been moved forward for years. The OS has been upgraded and wiped+fresh installed a few times. For 20.04, I did the 32-bit --> 64-bit transition.  I connect to this "desktop" from both the machine it runs on and over the network. I don't always use a GUI connection. It is running this browser window, thunderbird, keepassxc and a few other GUI programs, while their windows are displayed on my local system. For me, the network really is the computer.  Both firefox and thunderbird run in firejail constrained environments.  

If I'm using Windows to connect, I'll use virt-viewer which is a spice client. It is very fast.  From my laptop, it just depends on the tasks to be done whether any GUI is uses or not.  The desktop VM does hold my personal wiki, so I'll look up already-solved-stuff on it and I do nearly all scripting on that VM too. It is configured with a number of different versions of my preferred development language. Maintaining those different versions on 1 system is the easiest solution I've found. Packaging up the specific version for deployment to a client's server is pretty easy. Plus it keeps my code from being dependent on the OS versions of the language.

If you are not a Linux admin and just want a system that will run a desktop on a desktop, you probably want to load virtualbox instead.

---

