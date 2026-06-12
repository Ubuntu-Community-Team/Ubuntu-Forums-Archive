---
title: "Compton configurator freezes 22.04 in KVM/QEMU virtual machine."
date: 2022-01-29
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2022-01-29
I installed Xubuntu in KVM1QEMU two days ago using the daily/current iso file from 26 Jan.
It installed without a problem and runs fine using the xfwm compositor but after installing and running compton the whole system freezes.

I have to move to a tty (Ctrl+Alt+F1) and kill compton to be able to continue using the VM.

I am using the default compton.conf file in my ~/.config folder and tried turning off vsync completely in that thinking it might be the likely problem but that edit made no difference.

in all my hard metal installs I can and always used to use compton successfully but the VM appears to be the reason for this freeze.  It is not a big deal as the inbuilt xfwm works fine but I wonder if there is a way to get compton to run in this situation.

Any thoughts?

---

### Post by TheFu on 2022-01-30
I wouldn't expect any compositor to work without GPU passthru setup or at least virtGPU (or whatever the kids are using these days) to provide direct access to shared Intel GPU for VMs.

Did Compton work in prior KVM VMs?  If so, for which fake GPU and guest VM GPU driver?  Was SPICE/QXL supported?

---

### Post by ajgreeny on 2022-01-30
Hi TheFu.

To be honest I have never bothered to try compton in KVM before; I only use the VMs to see how well different DE versions of new numbered versions of this and other distros are developing.

I do have a VM of Mint-20-Xfce and will see if compton works on that or if that also freezes.
Watch this space.

EDIT:
Just realised I have recently deleted the Mint VM as I never really liked it any more than straight Xubuntu, but the video settings of my Xubuntu 22.04 VM are the same as I have always used since I moved from Virtualbox to KVM/QEMU about 16 months ago.
Display Spice - Spice server
Video Virtio - Virtio

---

### Post by #&amp;thj^% on 2022-01-30
> **ajgreeny said:**
> Hi TheFu.

To be honest I have never bothered to try compton in KVM before; I only use the VMs to see how well different DE versions of new numbered versions of this and other distros are developing.

I do have a VM of Mint-20-Xfce and will see if compton works on that or if that also freezes.
Watch this space.

EDIT:
Just realised I have recently deleted the Mint VM as I never really liked it any more than straight Xubuntu, but the video settings of my Xubuntu 22.04 VM are the same as I have always used since I moved from Virtualbox to KVM/QEMU about 16 months ago.
Display Spice - Spice server
Video Virtio - Virtio

It works here, but only a basic compton.conf
```
backend = "glx";
paint-on-overlay = true;
glx-no-stencil = true;
glx-no-rebind-pixmap = true;
vsync = "opengl-swc";

# These are important. The first one enables the opengl backend. The last one is the vsync method. Depending on the driver you might need to use a different method.
# The other options are smaller performance tweaks that work well in most cases.
# You can find the rest of the options here: https://github.com/chjj/compton/wiki/perf-guide, and here: https://github.com/chjj/compton/wiki/vsync-guide
```
My lovely Wife like a little eye candy.
The Specs are as follows:
```
me@me-Standard-PC-i440FX-PIIX-1996:~$ inxi -F 
System:
  Host: me-Standard-PC-i440FX-PIIX-1996 Kernel: 5.4.0-1040-fips x86_64 
  bits: 64 Desktop: MATE 1.24.0 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996) 
  v: pc-i440fx-6.1 serial: <superuser/root required> 
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: ArchLinux 1.15.0-1 
  date: 04/01/2014 
CPU:
  Topology: 12-Core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64 
  type: MCP L2 cache: 6144 KiB 
  Speed: 2994 MHz min/max: N/A Core speeds (MHz): 1: 2994 2: 2994 3: 2994 
  4: 2994 5: 2994 6: 2994 7: 2994 8: 2994 9: 2994 10: 2994 11: 2994 12: 2994 
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: none 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 
Audio:
  Device-1: Intel 82801FB/FBM/FR/FW/FRW High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-1040-fips 
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge 
  driver: piix4_smbus 
  Device-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter 
  driver: 8139cp 
  IF: ens3 state: up speed: 100 Mbps duplex: full mac: xx.xx00:a0:a4:66 
Drives:
  Local Storage: total: 23.30 GiB used: 7.38 GiB (31.7%) 
  ID-1: /dev/sda vendor: QEMU model: HARDDISK size: 23.30 GiB 
Partition:
  ID-1: / size: 21.38 GiB used: 7.38 GiB (34.5%) fs: ext4 dev: /dev/dm-0 
  ID-2: swap-1 size: 980.0 MiB used: 268 KiB (0.0%) fs: swap dev: /dev/dm-1 
Sensors:
  Message: No sensors data was found. Is sensors configured? 
Info:
  Processes: 256 Uptime: 25m Memory: 1.93 GiB used: 982.1 MiB (49.6%) 
  Shell: bash inxi: 3.0.38 

```
Don't forget to disable the current compositor:
```
gsettings set org.mate.Marco.general compositing-manager false

```
EDIT:[s]Let me know how yours works. :)[/s]
Please read with a grain of salt here.
Arch was the host UbuntuMate was the guest, also dual gpus. (AMD/Nividia )
And a lot of work to get Nvidia installed in kvm.
So apologies to ajgreeny.

---

