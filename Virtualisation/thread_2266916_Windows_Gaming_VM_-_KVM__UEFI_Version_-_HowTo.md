---
title: "Windows Gaming VM - KVM / UEFI Version - HowTo"
date: 2015-02-26
forum: Virtualisation
---

### Post by redger on 2015-02-26
For the last year or so I've been running Windows under Linux using KVM. I started off with true VGA passthrough using instructions from here   
[LIST]
[*][https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")
[*][http://vfio.blogspot.com.au/]("http://vfio.blogspot.com.au/")
[*][http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support]("http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support")
[*][https://www.suse.com/documentation/sles11/singlehtml/book_kvm/book_kvm.html]("https://www.suse.com/documentation/sles11/singlehtml/book_kvm/book_kvm.html")
[*][https://wiki.debian.org/VGAPassthrough]("https://wiki.debian.org/VGAPassthrough")
[*][https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF]("https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF")
[*][https://www.redhat.com/mailman/listinfo/vfio-users]("https://www.redhat.com/mailman/listinfo/vfio-users")
[/LIST]
NOTE the new VFIO mailing list (last entry above) which takes over where the original Arch discussion left off

Then a UEFI mechanism became available - which meant no need to deal with legacy VGA any more and no need for custom kernels or arcane Qemu commands passed to Libvirt. I use a standard version of Ubuntu Trusty ie. the long term stable release - as you would expect for a server

So here's a relatively easy way to create A Windows VM with real passthrough .... using the GUI to create, manage and start your VM. It's been very very stable for me and very easy to manage.

There are a few tricks along the way, nothing too arcane.

NOTE that you do NOT need the host to be booted using a UEFI bios so you need not change your motherboard bios for this. The only bios change is to ensure VT-d or AMD-VI are turned on

It's definitely worth reading Alex's "how to" series before you begin [http://vfio.blogspot.com.au/2015_05_01_archive.html]("http://vfio.blogspot.com.au/2015_05_01_archive.html")

First off you must have the right hardware. You will need
[LIST=1]
[*]A CPU which supports IOMMU ie. VT-D in Intel or VI for AMD (this generally excludes the "K" versions of Intel CPUs)
[*]A motherboard with BIOS / UEFI which supports IOMMU as above. Note that this can be the most problematic to ensure. Broadly speaking recent Asrock boards are good, Gigabye are probably good and others are hit and miss. Many people are very frustrated with Asus (including me)
[*]A Graphics card to be passed through. Note that you cannot pass an IGP through at present so if your cpu has integrated graphics use it for the host.
[*]A plan for host interaction. You can use ssh or vnc or better (for most people) use your IGP for the host
[*]Sufficient RAM and disk
[/LIST]

If you're planning to pass an NVidia graphics card to your VM, buckle in - you have some fun ahead. You will need 
(a) if installing NVidia driver version 337.88 or later - use the kvm=off parameter which is available in Qemu >= 2.1  and 
(b) if installing NVidia driver version 344.11 or later - set the Hyper-V extensions "off" (all the hv_* options to -cpu) in addition to the above
For those using an AMD R260 R290 (Hawaii) or AMD 7700 (Bonair) you need to use QEMU 2.3+ in which the "reset problem" was fixed so the guest VM can be restarted without trouble

In my case
[LIST]
[*]CPU		Intel 4670
[*]RAM		16 GB
[*]Motherboard	Asrock Z87 Extreme 6
[*]GPU		AMD HD6950
[*]Disk		Sandisk Extreme II 480 GB (boot drive and windows C drive host)
[*]		WD Black 2 Tb
[/LIST]

This spreadsheet lists hardware success stories [https://docs.google.com/spreadsheet/ccc?key=0Aryg5nO-kBebdFozaW9tUWdVd2VHM0lvck95TUlpMlE&usp=drive_web#gid=0]("https://docs.google.com/spreadsheet/ccc?key=0Aryg5nO-kBebdFozaW9tUWdVd2VHM0lvck95TUlpMlE&usp=drive_web#gid=0")

For these instructionsm, you'll also need a UEFI capable graphics card. Mine is an older AMD card for which there is no official UEFI bios .... but I was able to construct one using the instructions here 
[http://www.insanelymac.com/forum/topic/299614-asus-eah6450-video-bios-uefi-gop-upgrade-and-gop-uefi-binary-in-efi-for-many-ati-cards/]("http://www.insanelymac.com/forum/topic/299614-asus-eah6450-video-bios-uefi-gop-upgrade-and-gop-uefi-binary-in-efi-for-many-ati-cards/")
[http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread")
I used the tool from Insanely Mac (Windows version - installed in a temporary non-UEFI, simple VM I created for the purpose), link here [http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460")

I also bought a cheap PCIe USB card (based on the Renesas-NEC chipset) to be passed to the VM. I tried to pass USB devices directly with mixed success, so the add-in card made life much easier at a cost of < AUD$20

Next you need to enable the IOMMU in BIOS. Usually there's a bios setting on Intel boards for VT-d - it will need to be set on. The following command can be used to verify a working iommu
```
dmesg|grep -e DMAR -e IOMMU
```
you should see something like
```
[    0.000000] ACPI: DMAR 0x00000000BDCB1CB0 0000B8 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] Intel-IOMMU: enabled
[    0.028879] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.028883] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.028950] IOAPIC id 8 under DRHD base  0xfed91000 IOMMU 1
[    0.536212] DMAR: No ATSR found
[    0.536229] IOMMU 0 0xfed90000: using Queued invalidation
[    0.536230] IOMMU 1 0xfed91000: using Queued invalidation
[    0.536231] IOMMU: Setting RMRR:
[    0.536241] IOMMU: Setting identity map for device 0000:00:02.0 [0xbf000000 - 0xcf1fffff]
[    0.537490] IOMMU: Setting identity map for device 0000:00:14.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537512] IOMMU: Setting identity map for device 0000:00:1a.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537530] IOMMU: Setting identity map for device 0000:00:1d.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537543] IOMMU: Prepare 0-16MiB unity mapping for LPC
[    0.537549] IOMMU: Setting identity map for device 0000:00:1f.0 [0x0 - 0xffffff]
[    2.182790] [drm] DMAR active, disabling use of stolen memory
```
And check that the more standard VT-x and AMD -v are available
```
egrep -q '^flags.*(svm|vmx)' /proc/cpuinfo && echo virtualization extensions available
```

Ensure you have all the latest versions of packages etc.
```
sudo apt-get update
sudo apt-get upgrade
```

Install KVM
```
sudo apt-get install qemu-kvm seabios spice-client hugepages spice-client
```
or use this tutorial [https://help.ubuntu.com/community/KVM/Installation]("https://help.ubuntu.com/community/KVM/Installation")

Create a new directory for hugepages, we'll use this later (to improve VM performance)
```
sudo mkdir /dev/hugepages
```

find your PCI addresses using the following command
```
lspci -nn
```
or lspci -nnk for additional information or lspci -vnn for even more information

choose the PCI devices you want to pass through and work out which IOMMU groups they belong to. I suggest you start simple and just passthrough the graphics card itself (don't passthrough the built in audio)
Use this script to display the IOMMU groupings (thanks to Alex WIlliamson)
```
#!/bin/sh

# List the devices in each IOMMU group, from AW at
# https://bbs.archlinux.org/viewtopic.php?id=162768&p=29

BASE="/sys/kernel/iommu_groups"

for i in $(find $BASE -maxdepth 1 -mindepth 1 -type d); do
	GROUP=$(basename $i)
	echo "### Group $GROUP ###"
	for j in $(find $i/devices -type l); do
		DEV=$(basename $j)
		echo -n "    "
		lspci -s $DEV
	done
done
```
Find the groups containing the devices you wish to pass through. All the devices in a single group need to be attached to pci-stub together (except bridges and hubs) – this ensures that there is no cross-talk between VMs ie. a security feature which IOMMUs are designed to support.
If the grouping is too inconvenient you can apply the ACS patch to your kernel (refer to the Arch discussion linked at the begging of this post).
If you find that you have 2 devices in a single IOMMU group which you want to pass to different VMS, you're going to need the ACS patch and an additional grub command line parameter (I encountered this on my Asrock motherboard and so am not using 2 passthrough VMs simulataneously so I don't have to patch the kernel - it would be a maintenance irritation)

you're ready to change the Grub entries in /etc/default/grub
in order to enable IOMMU facilities and attach pci devices top pci-stub so they can subsequently be used by vfio. Mine looks like this (at the top) after changes
```
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on pci-stub.ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539"
GRUB_CMDLINE_LINUX=""
```
Update with 
```
sudo update-grub
```

NOTE, if you have installed Xen, you may find it has created another default file in /etc/default/grub.d/xen.conf which overrides the selection of the grub default, in my case (when experimenting) I changed it like this 
```
#
# Uncomment the following variable and set to 0 or 1 to avoid warning.
#
#XEN_OVERRIDE_GRUB_DEFAULT=0
XEN_OVERRIDE_GRUB_DEFAULT=0
```

you probably need to blacklist the drivers for graphics card being passed through (sometimes they grab the card before it's allocated to pci-stub). Change /etc/modprobe.d/blacklist.conf and add the relevant entry. In my case (for amd graphics) I added the following to the end of the file
```
# To support VGA Passthrough
blacklist radeon
```
those using an NVidia card will need to blacklist Nouveau

Whilst in the above directory you may also wish to modify /etc/modprobe.d/kvm.conf to select appropriate options, in my case (I have not used all the options, just “documented” existence)
```
# if vfio-pci was built as a module ( default on arch & ubuntu )
#options vfio_iommu_type1 allow_unsafe_interrupts=1 
# Some applications like Passmark Performance Test and SiSoftware Sandra crash the VM without this:
# options kvm ignore_msrs=1
```

If using hugepages (recommended for better performance), update sysctl whilst in /etc ie. add the following lines to /etc/sysctl.conf
```
# Set hugetables / hugepages for KVM single guest needing 6GB RAM
vm.nr_hugepages = 3200
```

Later on we'll refine the use of hugetables. The above figures are set for my system where, hugepages are 2MB each.
The Windows VM which needs this facility the most is allocated 6GB of ram, so we need 6144 MB which => 6144 / 2 = 3072 … plus add some extra for overhead (about 2% ie. 61 additional pages, so I have overachieved :)

Also update the ulimits in /etc/security/limits.conf   (set limit to an amout sufficient for your VM)
```
<your_user-id>           hard    memlock         8388608
```

If you haven't included pci-stub in the kernel (see the kernel config recommendations above) then you may need to add the module name to your initramfs, update /etc/initramfs-tools/modules to include the following line
```
pci-stub
```
and “update”  your initramfs (use “-c” option to build a new one)
```
sudo update-initramfs -u
```
Note that I usually update initramfs as a matter of course when I update grub – to ensure the two are always synchronised

now you're about ready to reboot and start creating the VM

After rebooting, check that the cards to be passed through are assigned to pci-stub using
```
dmesg | grep pci-stub
```

download the virtio drivers from redhat (Windows will need these to access the vfio devices)
[http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/]("http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/")   eg. Obtain virtio-win-0.1-94.iso  which can be used later as a cd-rom image for the Windows guest
download the spice drivers for enhanced spice experience on windows from
[http://www.spice-space.org/download.html]("http://www.spice-space.org/download.html")

I installed the Ubuntu supplied OVMF so that all the necessary links etc are created but it will NOT work. You may not need to do this, but I felt it was cleaner.
```
sudo apt-get install ovmf
```
You must find the latest OVMF file … preferably download from Gerd Hoffman's site [https://www.kraxel.org/repos/jenkins/edk2/]("https://www.kraxel.org/repos/jenkins/edk2/") and extract OVMF-pure-efi-fd from the rpm and copy to /usr/share/ovmf and create a "reference" copy as OVMF.fd (take a copy of Ubuntu version first – just in case).

install libvirt and virt-manager - this will provide the GUI VM management service
```
sudo apt-get install libvirt-bin virt-manager
```

update the libvirt qemu configuration at /etc/libvirt/qemu.conf -
[LIST]
[*]add this if you want to use host audio (not recommended
```
nographics_allow_host_audio = 1
```
[*]set this to maintain security
```
security_require_confined = 1
```
[*]set these to enable qemu to access hardware. You'll need to work out which VFIO items you're going to provide access to (/dev/vfio) and you may or not want to provide access to "pulse"
```
cgroup_device_acl = [
    "/dev/null", "/dev/full", "/dev/zero",
    "/dev/random", "/dev/urandom",
    "/dev/ptmx", "/dev/kvm", "/dev/kqemu",
    "/dev/rtc","/dev/hpet", "/dev/vfio/vfio",
    "/dev/vfio/1", "/dev/vfio/14", "/dev/vfio/15", "/dev/vfio/16", "/dev/vfio/17",
    "/dev/shm", "/root/.config/pulse", "/dev/snd",
]
```
[*]add this to enable access to the hugepages directory we created earlier
```
hugetlbfs_mount = "/dev/hugepages"
```
maintian the security constraints on VMs - we're running "unpriveleged" and then providing specific accesses with changes above, plus the Apparmor changes below
```
clear_emulator_capabilities = 1
```
[/LIST]


Update apparmor to allow libvirt to allocate hugepages, use VFIO and sound. Add the following to the apparmor definition in /etc/apparmor.d/abstractions/libvirt-qemu
```
  # WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /{dev,run}/shm r,
 # ================ START Changes ================ #
  /{dev,run}/shm/pulse-shm* rw,
  @{HOME}/.config/puls** rwk,
  @{HOME}/** r,
  # Only necessary if running as root, which we no longer are
  #/root/.config/puls** rwk,
  #/root/.asoundrc r,
  /dev/vfio/* rw,
  /dev/hugepages/libvirt** rw,
  # ================ END Changes ================ #
  /{dev,run}/shmpulse-shm* r,
  /{dev,run}/shmpulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
  # spice
```
Then reload the apparmor defintiions so the changes take effect
```
sudo invoke-rc.d apparmor reload
```
Then restart libvirt (just to be sure)
```
sudo service libvirt-bin stop
sudo service libvirt-bin start
```
Be sure to back these change up as updates to Apparmor may overwrite them .....

Start virt-manager (should appear in the menu as "Virtual Machine Manager") and add a connection to QEMU on local host (File/Add Connection), this will give you the ability to create and manage KVM machines

Now we can start creating a new VM (right click on the "localhost (QEMU)" line in the main screen area and select "New")

You'll need a copy of Windows 8 or 8.1. It's apparently possible to install Windows 7 but I found it was more trouble than it's worth. DO NOT try to install the Ultimate version - install Professional or Home

Your graphics card will need to be UEFI capable. Mine is an older AMD card for which there is no official UEFI bios .... but I was able to construct one (see the beginning of this post)

Define the new VM in virt-manager. Remember to -
[LIST]
[*]Select a “dummy” iso to install from … we're going to replace this later
[*]Select UEFI as the bios (Advanced Options on last screen)
[*]use appropriate names etc
[/LIST]

STOP the install triggered by virt-manager BEFORE it installs anything. You should easily have time to stop the install while the UEFI boot process is iniating. 
Stopping is easy if you're working with virt-manager (the gui) - click on the red "shutdown" icon at the top of the screen(use the virt-viewer “force off” option). You'll probably have to stop it twice – on my system it automatically restarts itself even after a forced stop.

Create a new copy of the OVMF-pure-efi.fd file you downloaded from Gerd's site and rename it for your new VM eg.
```
sudo cp /usr/share/ovmf/OVMF-pure-efi.fd /usr/share/ovmf/OVMF-win8-pro.fd
sudo ln -s /usr/share/ovmf/OVMF-win8-pro.fd /usr/share/qemu/OVMF-win8-pro.fd
```

Ensure all the following parameters are set BEFORE attempting an install using 
```
EDITOR=nano virsh edit <your-vm-name>
``` ie.

[LIST]
[*]Initial domain definition – to support direct qemu parameters, right at the top of the file
```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
```
[*]Memory backing
```
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
```
[*]Change the loader in the <os> section ie. The OVMF file name (custom for each VM – create in /usr/share/ovmf and create link in /usr/share/qemu as described above)
```
<loader>OVMF_win8_pro.fd</loader>
```
[*]CPU. I chose to define my real CPU type. You can set it to "host", this seemed the best overall result for me
 ```
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell</model>
    <topology sockets='1' cores='2' threads='1'/>
  </cpu>
```
[*]Features (hv_relaxed etc). NVidia crivers don't seem to like these HyperV optimisations and will probably fail if they're encountered so set to "off" if using an NVidia card
```
  <features>
    <acpi/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
  </features>
```
[*]Clock (hv_time), more performance parameters the NVidia drivers won't like
```
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
    <timer name='hpet' present='no'/>   # Not sure about this one
  </clock>
```
[*]Change emulator in the <devices> section
 ```
<emulator>/usr/bin/qemu-system-x86_64</emulator>
```
[*]Spice access – add to end, just before </domain>. You don't absolutely need this, but I find it useful to be able to control the keyboard during UEFI intialisation before any USB drivers have been loaded, and it doesn't seem to do any harm
```
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
```
[/LIST]

For those of you using NVidia cards you will also need to 
(a) if installing NVidia driver version 337.88 or later - use the kvm=off parameter which is available in Qemu >= 2.1, using the following lines after <qemu:commandline>
```
    <qemu:arg value='-cpu'/>
    <qemu:arg value='host,kvm=off'/>
```or if using Libvirt >= 1.2.8 you can add
```
  <features>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
```
  and 
(b) if installing NVidia driver version 344.11 or later - set the Hyper-V extensions "off" (all the hv_* options to -cpu) in addition to the above

Save the changes. Note that Virsh may respond with an error in which case edit the file again like this ("Failed. Try again? [y,n,f,?]:") .... use the try again option to return to the editor and fix the problem



For what it's worth do NOT set USB = USB2 in the VM setup, leave at default. USB processing seems to cause a lot of grief, so best to use with default. Also Logitech G27 wheel will not work correctly via Renesas USB 3 add-in card but works fine if passed directly from a USB 2 port on host via host USB passthrough - other USB devices may be similarly afflicted one way or the other (some only work when connected to a passed through card, some will only work when passed through fromm the host controller ymmv)

The install iso should be copied to an install partition as accessible to a VM ie. 
[LIST]
[*]Create a new partition for this purpose, can be LVM or 'flat' but must reside on a GPT disk not MBR
[*]Allocate the new partition to a VM – so it can be formatted. DO NOT format this using host format tools, it must be done from a VM
[*]Allocate the new partition to a windows VM
[*]Format as FAT32, consider adding the WIN xx bootloader as well. Not necessary but seems cleaner and make the partition bootable (set “active” or bootable flag in parition table)
[*]Copy the install iso to the newly formatted partition. This can be accomplished by passing the iso to the VM used to format the new install partition as a CD-ROM (use virt-manager)
[*] Check that the \efi\boot directory exists and contains the same files as \efi\microsoft\boot. If necessary copy files into a new \efi\boot directory. The directory must also contain a copy bootmgw.efi named bootx64.efi
[*]Check the contents of \source\ei.cfg to ensure it nominates the correct OS product (best to use “Professional”).
[*]It can be beneficial to use Win Toolkit to include the linux qxl driver (spice screen driver) in the Windows build although I'm not convinced this is necessary.
[*]Exit the VM used to format the install partition
[/LIST]

Now you can use the Virt-Manager gui to further modify the VM definition (the manual edits should not be impacted by this , you an easily check at any time with "virsh edit")
[LIST]
[*]Add the newly created install partition to your new VM definition as created in #3 above and remove the previously added “dummy” install cd iso. The easiest way to do this is to use virt-viewer “information view” - add hardware. Be sure to add as “IDE disk” and not virtio
[/LIST]
also add the following -
[LIST]
[*]virtio drivers iso as cd-rom.
[*]qxl drivers iso as cd-rom (can be part of the virtio if easier). Note that this probably cannot be used during Windows install since they are unsigned. You'll need to add them later
[*]any other files need as cd-rom eg. drivers. You can easily create an iso from any files using the Ubuntu disk burning tools eg. k3b
[*]Ensure that the “boot menu” option is enabled in the boot order section of virt-viewer
[*]Ensure the main partition to be installed to is accessed via virtio (disk bus under the advanced options for the device)
[*]Ensure the network adapter is defined as virtio (device model for the NIC)
[*]ensure the default graphics and display are spice based. Windows doesn't seem to need additional drivers for these (which is why youshould NOT need to build the drivers into the install image).
[/LIST]

Run the install. If necessary press the space key as the UEFI boot progresses and select the disk to boot from. Sometimes uefi doesn't find the correct boot disk. You will need to connect via Spice to enable this (spicec -h 127.0.0.1 -p 5905)

You'll need to install "additional drivers" and select the virtio drivers for disk and network access. This makes a significant difference to VM performance AND the install will fail if you've set the VM definition to provide a virtio disk but Windows cannot find a driver

Add the required PCI devices  Only add PCI passthrough devices AFTER the main install is complete

Windows tuning hints
[LIST]
[*]Turn off all paging. The host will handle this
[*]I tell Windows to optimise for performance. This makes screens lok pretty ordinary, but since I only use the VM for gaming and games take direct control of the screen, it doesn't really matter
[*]Consider turning on update protection ie. Snapshots you can fall back to if an update fails. Then take the first snapshot directly after the install so you have a restore point
[/LIST]

Shut the vm down using the Windows shut-down procedure ie. Normal termination

Add the PCI passthrough cards. In my case I pass
[LIST]
[*]Graphics card – primary address (01:00.0)
[*]Graphics card - sound  address    (01:00.1)
[*]USB add-in card (Renesas based) to which the following are attached via downstream hubs (on display panels)                       (02:00.0)
[*]Host USB device (Logitech wheel)
[/LIST]


Add any USB devices to be passed from the host. In my case there seems to be a problem with USB 3 drivers on the guest (and possibly on the host) so I had to detach the wheel from the add-in card and attach it to a USB 2 port on the host, then pass it through via host usb passthrough – which works well.

Reboot and verify all is working

When the graphics card is working. Shut down the VM. Remove the following from the VM definition
[LIST]
[*]Spice display
[*]qxl graphics
[*]console definition 
[*]serial port definition
[*]channel definition
[/LIST]

Reboot the VM to verify everything continues to work

In my case I now set up eyefinity and gaming software. The AMD control centre seems a bit flaky and sometimes caused a lock up while trying to establish an eyefinity group. 1 or 2 reboots later (forced shutdown-poweroff from the virt-manager interface) it's all working

No more need to customise the kernel or worry about loss of function on the host graphics (due to VGA-Arbiter patch) !!! 
No real performance difference for(for me) between UEFI and BIOS …. more stable, easier to manage using libvirt / virt-manager (everything exposed to libvirt & managed there).
You can connect to the VM using “spicec -h 127.0.0.1 -p 5905” and use the host keyboard during bootup should the need arise – before the guest VM loads any drivers ie. before the guest keyboard and mouse are active

here's what my lspci looks like
```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
00:01.2 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x4 Controller [8086:0c09] (rev 06)
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 [8086:8c18] (rev d5)
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman PRO [Radeon HD 6950] [1002:6719]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman/Antilles HDMI Audio [Radeon HD 6900 Series] [1002:aa80]
02:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller [1912:0014] (rev 03)
04:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
05:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
06:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
```

I chose to pass the AMD card and its audio controller through along with the Renesas USB controller ie. 01:00.0 to 02:00.0

here's my final libvirt definition 
```
cat  /etc/libvirt/qemu/ssd-win8-uefi.xml
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit ssd-win8-uefi
or other application using the libvirt API.
-->

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>ssd-win8-uefi</name>
  <uuid>redacted</uuid>
  <memory unit='KiB'>6291456</memory>
  <currentMemory unit='KiB'>6291456</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static'>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader>OVMF_ssd_win8_pro.fd</loader>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell</model>
    <topology sockets='1' cores='2' threads='1'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/ssd-virt/lvwin8_uefi_kvm'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/wd2t-lvm-data/lvwin7_data'/>
      <target dev='vdb' bus='virtio'/>
      <shareable/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/wd2t-lvm-data/lvwin7_kvm'/>
      <target dev='vdc' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/mnt/programming_data/isos/winfiles_3.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <shareable/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address=<redacted>'/>
      <source bridge='rebr0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='tablet' bus='usb'/>
    <sound model='ac97'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>For the last year or so I've been running Windows under Linux using KVM. I started off with true VGA passthrough using instructions from here   
[LIST]
[*][https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")
[*][http://vfio.blogspot.com.au/]("http://vfio.blogspot.com.au/")
[*][http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support]("http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support")
[*][https://www.suse.com/documentation/sles11/singlehtml/book_kvm/book_kvm.html]("https://www.suse.com/documentation/sles11/singlehtml/book_kvm/book_kvm.html")
[*][https://wiki.debian.org/VGAPassthrough]("https://wiki.debian.org/VGAPassthrough")
[*][https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF]("https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF")
[/LIST]

Then a UEFI mechanism became available - which meant no need to deal with legacy VGA any more and no need for custom kernels or arcane Qemu commands passed to Libvirt. I use a standard version of Ubuntu Trusty ie. the long term stable release - as you would expect for a server

So here's a relatively easy way to create A Windows VM with real passthrough .... using the GUI to create, manage and start your VM. It's been very very stable for me and very easy to manage.

There are a few tricks along the way, nothing too arcane.

NOTE that you do NOT need the host to be booted using a UEFI bios so you need not change your motherboard bios for this. The only bios change is to ensure VT-d or AMD-VI are turned on

It's definitely worth reading Alex's "how to" series before you begin [http://vfio.blogspot.com.au/2015_05_01_archive.html]("http://vfio.blogspot.com.au/2015_05_01_archive.html")

First off you must have the right hardware. You will need
[LIST=1]
[*]A CPU which supports IOMMU ie. VT-D in Intel or VI for AMD (this generally excludes the "K" versions of Intel CPUs)
[*]A motherboard with BIOS / UEFI which supports IOMMU as above. Note that this can be the most problematic to ensure. Broadly speaking recent Asrock boards are good, Gigabye are probably good and others are hit and miss. Many people are very frustrated with Asus (including me)
[*]A Graphics card to be passed through. Note that you cannot pass an IGP through at present so if your cpu has integrated graphics use it for the host.
[*]A plan for host interaction. You can use ssh or vnc or better (for most people) use your IGP for the host
[*]Sufficient RAM and disk
[/LIST]

If you're planning to pass an NVidia graphics card to your VM, buckle in - you have some fun ahead. You will need 
(a) if installing NVidia driver version 337.88 or later - use the kvm=off parameter which is available in Qemu >= 2.1  and 
(b) if installing NVidia driver version 344.11 or later - set the Hyper-V extensions "off" (all the hv_* options to -cpu) in addition to the above
For those using an AMD R260 R290 (Hawaii) or AMD 7700 (Bonair) you need to use QEMU 2.3+ in which the "reset problem" was fixed so the guest VM can be restarted without trouble

In my case
[LIST]
[*]CPU		Intel 4670
[*]RAM		16 GB
[*]Motherboard	Asrock Z87 Extreme 6
[*]GPU		AMD HD6950
[*]Disk		Sandisk Extreme II 480 GB (boot drive and windows C drive host)
[*]		WD Black 2 Tb
[/LIST]

This spreadsheet lists hardware success stories [https://docs.google.com/spreadsheet/ccc?key=0Aryg5nO-kBebdFozaW9tUWdVd2VHM0lvck95TUlpMlE&usp=drive_web#gid=0]("https://docs.google.com/spreadsheet/ccc?key=0Aryg5nO-kBebdFozaW9tUWdVd2VHM0lvck95TUlpMlE&usp=drive_web#gid=0")

For these instructionsm, you'll also need a UEFI capable graphics card. Mine is an older AMD card for which there is no official UEFI bios .... but I was able to construct one using the instructions here 
[http://www.insanelymac.com/forum/topic/299614-asus-eah6450-video-bios-uefi-gop-upgrade-and-gop-uefi-binary-in-efi-for-many-ati-cards/]("http://www.insanelymac.com/forum/topic/299614-asus-eah6450-video-bios-uefi-gop-upgrade-and-gop-uefi-binary-in-efi-for-many-ati-cards/")
[http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread")
I used the tool from Insanely Mac (Windows version - installed in a temporary non-UEFI, simple VM I created for the purpose), link here [http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460")

I also bought a cheap PCIe USB card (based on the Renesas-NEC chipset) to be passed to the VM. I tried to pass USB devices directly with mixed success, so the add-in card made life much easier at a cost of < AUD$20

Next you need to enable the IOMMU in BIOS. Usually there's a bios setting on Intel boards for VT-d - it will need to be set on. The following command can be used to verify a working iommu
[CODE]dmesg|grep -e DMAR -e IOMMU
```
you should see something like
```
[    0.000000] ACPI: DMAR 0x00000000BDCB1CB0 0000B8 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] Intel-IOMMU: enabled
[    0.028879] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.028883] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.028950] IOAPIC id 8 under DRHD base  0xfed91000 IOMMU 1
[    0.536212] DMAR: No ATSR found
[    0.536229] IOMMU 0 0xfed90000: using Queued invalidation
[    0.536230] IOMMU 1 0xfed91000: using Queued invalidation
[    0.536231] IOMMU: Setting RMRR:
[    0.536241] IOMMU: Setting identity map for device 0000:00:02.0 [0xbf000000 - 0xcf1fffff]
[    0.537490] IOMMU: Setting identity map for device 0000:00:14.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537512] IOMMU: Setting identity map for device 0000:00:1a.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537530] IOMMU: Setting identity map for device 0000:00:1d.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537543] IOMMU: Prepare 0-16MiB unity mapping for LPC
[    0.537549] IOMMU: Setting identity map for device 0000:00:1f.0 [0x0 - 0xffffff]
[    2.182790] [drm] DMAR active, disabling use of stolen memory
```
And check that the more standard VT-x and AMD -v are available
```
egrep -q '^flags.*(svm|vmx)' /proc/cpuinfo && echo virtualization extensions available
```

Ensure you have all the latest versions of packages etc.
```
sudo apt-get update
sudo apt-get upgrade
```

Install KVM
```
sudo apt-get install qemu-kvm seabios spice-client hugepages spice-client
```
or use this tutorial [https://help.ubuntu.com/community/KVM/Installation]("https://help.ubuntu.com/community/KVM/Installation")

Create a new directory for hugepages, we'll use this later (to improve VM performance)
```
sudo mkdir /dev/hugepages
```

find your PCI addresses using the following command
```
lspci -nn
```
or lspci -nnk for additional information or lspci -vnn for even more information

choose the PCI devices you want to pass through and work out which IOMMU groups they belong to. I suggest you start simple and just passthrough the graphics card itself (don't passthrough the built in audio)
Use this script to display the IOMMU groupings (thanks to Alex WIlliamson)
```
#!/bin/sh

# List the devices in each IOMMU group, from AW at
# https://bbs.archlinux.org/viewtopic.php?id=162768&p=29

BASE="/sys/kernel/iommu_groups"

for i in $(find $BASE -maxdepth 1 -mindepth 1 -type d); do
	GROUP=$(basename $i)
	echo "### Group $GROUP ###"
	for j in $(find $i/devices -type l); do
		DEV=$(basename $j)
		echo -n "    "
		lspci -s $DEV
	done
done
```
Find the groups containing the devices you wish to pass through. All the devices in a single group need to be attached to pci-stub together (except bridges and hubs) – this ensures that there is no cross-talk between VMs ie. a security feature which IOMMUs are designed to support.
If the grouping is too inconvenient you can apply the ACS patch to your kernel (refer to the Arch discussion linked at the begging of this post).
If you find that you have 2 devices in a single IOMMU group which you want to pass to different VMS, you're going to need the ACS patch and an additional grub command line parameter (I encountered this on my Asrock motherboard and so am not using 2 passthrough VMs simulataneously so I don't have to patch the kernel - it would be a maintenance irritation)

you're ready to change the Grub entries in /etc/default/grub
in order to enable IOMMU facilities and attach pci devices top pci-stub so they can subsequently be used by vfio. Mine looks like this (at the top) after changes
```
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on pci-stub.ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539"
GRUB_CMDLINE_LINUX=""
```
Update with 
```
sudo update-grub
```

NOTE, if you have installed Xen, you may find it has created another default file in /etc/default/grub.d/xen.conf which overrides the selection of the grub default, in my case (when experimenting) I changed it like this 
```
#
# Uncomment the following variable and set to 0 or 1 to avoid warning.
#
#XEN_OVERRIDE_GRUB_DEFAULT=0
XEN_OVERRIDE_GRUB_DEFAULT=0
```

you probably need to blacklist the drivers for graphics card being passed through (sometimes they grab the card before it's allocated to pci-stub). Change /etc/modprobe.d/blacklist.conf and add the relevant entry. In my case (for amd graphics) I added the following to the end of the file
```
# To support VGA Passthrough
blacklist radeon
```
those using an NVidia card will need to blacklist Nouveau

Whilst in the above directory you may also wish to modify /etc/modprobe.d/kvm.conf to select appropriate options, in my case (I have not used all the options, just “documented” existence)
```
# if vfio-pci was built as a module ( default on arch & ubuntu )
#options vfio_iommu_type1 allow_unsafe_interrupts=1 
# Some applications like Passmark Performance Test and SiSoftware Sandra crash the VM without this:
# options kvm ignore_msrs=1
```

If using hugepages (recommended for better performance), update sysctl whilst in /etc ie. add the following lines to /etc/sysctl.conf
```
# Set hugetables / hugepages for KVM single guest needing 6GB RAM
vm.nr_hugepages = 3200
```
Also update the ulimits in /etc/security/limits.conf   (set limit to an amout sufficient for your VM)
```
<your_user-id>           hard    memlock         8388608
```
Later on we'll refine the use of hugetables. The above figures are set for my system where, hugepages are 2MB each.
The Windows VM which needs this facility the most is allocated 6GB of ram, so we need 6144 MB which => 6144 / 2 = 3072 … plus add some extra for overhead (about 2% ie. 61 additional pages, so I have overachieved :)

If you haven't included pci-stub in the kernel (see the kernel config recommendations above) then you may need to add the module name to your initramfs, update /etc/initramfs-tools/modules to include the following line
```
pci-stub
```
and “update”  your initramfs (use “-c” option to build a new one)
```
sudo update-initramfs -u
```
Note that I usually update initramfs as a matter of course when I update grub – to ensure the two are always synchronised

now you're about ready to reboot and start creating the VM

After rebooting, check that the cards to be passed through are assigned to pci-stub using
```
dmesg | grep pci-stub
```

download the virtio drivers from redhat (Windows will need these to access the vfio devices)
[http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/]("http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/")   eg. Obtain virtio-win-0.1-94.iso  which can be used later as a cd-rom image for the Windows guest
download the spice drivers for enhanced spice experience on windows from
[http://www.spice-space.org/download.html]("http://www.spice-space.org/download.html")

I installed the Ubuntu supplied OVMF so that all the necessary links etc are created but it will NOT work. You may not need to do this, but I felt it was cleaner.
```
sudo apt-get install ovmf
```
You must find the latest OVMF file … preferably download from Gerd Hoffman's site [https://www.kraxel.org/repos/jenkins/edk2/]("https://www.kraxel.org/repos/jenkins/edk2/") and extract OVMF-pure-efi-fd from the rpm and copy to /usr/share/ovmf and create a "reference" copy as OVMF.fd (take a copy of Ubuntu version first – just in case).

install libvirt and virt-manager - this will provide the GUI VM management service
```
sudo apt-get install libvirt-bin virt-manager
```

update the libvirt qemu configuration at /etc/libvirt/qemu.conf -
[LIST]
[*]add this if you want to use host audio (not recommended
```
nographics_allow_host_audio = 1
```
[*]set this to maintain security
```
security_require_confined = 1
```
[*]set these to enable qemu to access hardware. You'll need to work out which VFIO items you're going to provide access to (/dev/vfio) and you may or not want to provide access to "pulse"
```
cgroup_device_acl = [
    "/dev/null", "/dev/full", "/dev/zero",
    "/dev/random", "/dev/urandom",
    "/dev/ptmx", "/dev/kvm", "/dev/kqemu",
    "/dev/rtc","/dev/hpet", "/dev/vfio/vfio",
    "/dev/vfio/1", "/dev/vfio/14", "/dev/vfio/15", "/dev/vfio/16", "/dev/vfio/17",
    "/dev/shm", "/root/.config/pulse", "/dev/snd",
]
```
[*]add this to enable access to the hugepages directory we created earlier
```
hugetlbfs_mount = "/dev/hugepages"
```
maintian the security constraints on VMs - we're running "unpriveleged" and then providing specific accesses with changes above, plus the Apparmor changes below
```
clear_emulator_capabilities = 1
```
[/LIST]


Update apparmor to allow libvirt to allocate hugepages, use VFIO and sound. Add the following to the apparmor definition in /etc/apparmor.d/abstractions/libvirt-qemu
```
  # WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /{dev,run}/shm r,
 # ================ START Changes ================ #
  /{dev,run}/shm/pulse-shm* rw,
  @{HOME}/.config/puls** rwk,
  @{HOME}/** r,
  # Only necessary if running as root, which we no longer are
  #/root/.config/puls** rwk,
  #/root/.asoundrc r,
  /dev/vfio/* rw,
  /dev/hugepages/libvirt** rw,
  # ================ END Changes ================ #
  /{dev,run}/shmpulse-shm* r,
  /{dev,run}/shmpulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
  # spice
```
Then reload the apparmor defintiions so the changes take effect
```
sudo invoke-rc.d apparmor reload
```
Then restart libvirt (just to be sure)
```
sudo service libvirt-bin stop
sudo service libvirt-bin start
```
Be sure to back these change up as updates to Apparmor may overwrite them .....

Start virt-manager (should appear in the menu as "Virtual Machine Manager") and add a connection to QEMU on local host (File/Add Connection), this will give you the ability to create and manage KVM machines

Now we can start creating a new VM (right click on the "localhost (QEMU)" line in the main screen area and select "New")

You'll need a copy of Windows 8 or 8.1. It's apparently possible to install Windows 7 but I found it was more trouble than it's worth. DO NOT try to install the Ultimate version - install Professional or Home

Your graphics card will need to be UEFI capable. Mine is an older AMD card for which there is no official UEFI bios .... but I was able to construct one (see the beginning of this post)

Define the new VM in virt-manager. Remember to -
[LIST]
[*]Select a “dummy” iso to install from … we're going to replace this later
[*]Select UEFI as the bios (Advanced Options on last screen)
[*]use appropriate names etc
[/LIST]

STOP the install triggered by virt-manager BEFORE it installs anything. You should easily have time to stop the install while the UEFI boot process is iniating. 
Stopping is easy if you're working with virt-manager (the gui) - click on the red "shutdown" icon at the top of the screen(use the virt-viewer “force off” option). You'll probably have to stop it twice – on my system it automatically restarts itself even after a forced stop.

Create a new copy of the OVMF-pure-efi.fd file you downloaded from Gerd's site and rename it for your new VM eg.
```
sudo cp /usr/share/ovmf/OVMF-pure-efi.fd /usr/share/ovmf/OVMF-win8-pro.fd
sudo ln -s /usr/share/ovmf/OVMF-win8-pro.fd /usr/share/qemu/OVMF-win8-pro.fd
```

Ensure all the following parameters are set BEFORE attempting an install using 
```
EDITOR=nano virsh edit <your-vm-name>
``` ie.

[LIST]
[*]Initial domain definition – to support direct qemu parameters, right at the top of the file
```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
```
[*]Memory backing
```
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
```
[*]Change the loader in the <os> section ie. The OVMF file name (custom for each VM – create in /usr/share/ovmf and create link in /usr/share/qemu as described above)
```
<loader>OVMF_win8_pro.fd</loader>
```
[*]CPU. I chose to define my real CPU type. You can set it to "host", this seemed the best overall result for me
 ```
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell</model>
    <topology sockets='1' cores='2' threads='1'/>
  </cpu>
```
[*]Features (hv_relaxed etc). NVidia crivers don't seem to like these HyperV optimisations and will probably fail if they're encountered so set to "off" if using an NVidia card
```
  <features>
    <acpi/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
  </features>
```
[*]Clock (hv_time), more performance parameters the NVidia drivers won't like
```
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
    <timer name='hpet' present='no'/>   # Not sure about this one
  </clock>
```
[*]Change emulator in the <devices> section
 ```
<emulator>/usr/bin/qemu-system-x86_64</emulator>
```
[*]Spice access – add to end, just before </domain>. You don't absolutely need this, but I find it useful to be able to control the keyboard during UEFI intialisation before any USB drivers have been loaded, and it doesn't seem to do any harm
```
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
```
[/LIST]

For those of you using NVidia cards you will also need to 
(a) if installing NVidia driver version 337.88 or later - use the kvm=off parameter which is available in Qemu >= 2.1, using the following lines after <qemu:commandline>
```
    <qemu:arg value='-cpu'/>
    <qemu:arg value='host,kvm=off'/>
```or if using Libvirt >= 1.2.8 you can add
```
  <features>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
```
  and 
(b) if installing NVidia driver version 344.11 or later - set the Hyper-V extensions "off" (all the hv_* options to -cpu) in addition to the above

Save the changes. Note that Virsh may respond with an error in which case edit the file again like this ("Failed. Try again? [y,n,f,?]:") .... use the try again option to return to the editor and fix the problem



For what it's worth do NOT set USB = USB2 in the VM setup, leave at default. USB processing seems to cause a lot of grief, so best to use with default. Also Logitech G27 wheel will not work correctly via Renesas USB 3 add-in card but works fine if passed directly from a USB 2 port on host via host USB passthrough - other USB devices may be similarly afflicted one way or the other (some only work when connected to a passed through card, some will only work when passed through fromm the host controller ymmv)

The install iso should be copied to an install partition as accessible to a VM ie. 
[LIST]
[*]Create a new partition for this purpose, can be LVM or 'flat' but must reside on a GPT disk not MBR
[*]Allocate the new partition to a VM – so it can be formatted. DO NOT format this using host format tools, it must be done from a VM
[*]Allocate the new partition to a windows VM
[*]Format as FAT32, consider adding the WIN xx bootloader as well. Not necessary but seems cleaner and make the partition bootable (set “active” or bootable flag in parition table)
[*]Copy the install iso to the newly formatted partition. This can be accomplished by passing the iso to the VM used to format the new install partition as a CD-ROM (use virt-manager)
[*] Check that the \efi\boot directory exists and contains the same files as \efi\microsoft\boot. If necessary copy files into a new \efi\boot directory. The directory must also contain a copy bootmgw.efi named bootx64.efi
[*]Check the contents of \source\ei.cfg to ensure it nominates the correct OS product (best to use “Professional”).
[*]It can be beneficial to use Win Toolkit to include the linux qxl driver (spice screen driver) in the Windows build although I'm not convinced this is necessary.
[*]Exit the VM used to format the install partition
[/LIST]

Now you can use the Virt-Manager gui to further modify the VM definition (the manual edits should not be impacted by this , you an easily check at any time with "virsh edit")
[LIST]
[*]Add the newly created install partition to your new VM definition as created in #3 above and remove the previously added “dummy” install cd iso. The easiest way to do this is to use virt-viewer “information view” - add hardware. Be sure to add as “IDE disk” and not virtio
[/LIST]
also add the following -
[LIST]
[*]virtio drivers iso as cd-rom.
[*]qxl drivers iso as cd-rom (can be part of the virtio if easier). Note that this probably cannot be used during Windows install since they are unsigned. You'll need to add them later
[*]any other files need as cd-rom eg. drivers. You can easily create an iso from any files using the Ubuntu disk burning tools eg. k3b
[*]Ensure that the “boot menu” option is enabled in the boot order section of virt-viewer
[*]Ensure the main partition to be installed to is accessed via virtio (disk bus under the advanced options for the device)
[*]Ensure the network adapter is defined as virtio (device model for the NIC)
[*]ensure the default graphics and display are spice based. Windows doesn't seem to need additional drivers for these (which is why youshould NOT need to build the drivers into the install image).
[/LIST]

Run the install. If necessary press the space key as the UEFI boot progresses and select the disk to boot from. Sometimes uefi doesn't find the correct boot disk. You will need to connect via Spice to enable this (spicec -h 127.0.0.1 -p 5905)

You'll need to install "additional drivers" and select the virtio drivers for disk and network access. This makes a significant difference to VM performance AND the install will fail if you've set the VM definition to provide a virtio disk but Windows cannot find a driver

Add the required PCI devices  Only add PCI passthrough devices AFTER the main install is complete

Windows tuning hints
[LIST]
[*]Turn off all paging. The host will handle this
[*]I tell Windows to optimise for performance. This makes screens lok pretty ordinary, but since I only use the VM for gaming and games take direct control of the screen, it doesn't really matter
[*]Consider turning on update protection ie. Snapshots you can fall back to if an update fails. Then take the first snapshot directly after the install so you have a restore point
[/LIST]

Shut the vm down using the Windows shut-down procedure ie. Normal termination

Add the PCI passthrough cards. In my case I pass
[LIST]
[*]Graphics card – primary address (01:00.0)
[*]Graphics card - sound  address    (01:00.1)
[*]USB add-in card (Renesas based) to which the following are attached via downstream hubs (on display panels)                       (02:00.0)
[*]Host USB device (Logitech wheel)
[/LIST]


Add any USB devices to be passed from the host. In my case there seems to be a problem with USB 3 drivers on the guest (and possibly on the host) so I had to detach the wheel from the add-in card and attach it to a USB 2 port on the host, then pass it through via host usb passthrough – which works well.

Reboot and verify all is working

When the graphics card is working. Shut down the VM. Remove the following from the VM definition
[LIST]
[*]Spice display
[*]qxl graphics
[*]console definition 
[*]serial port definition
[*]channel definition
[/LIST]

Reboot the VM to verify everything continues to work

In my case I now set up eyefinity and gaming software. The AMD control centre seems a bit flaky and sometimes caused a lock up while trying to establish an eyefinity group. 1 or 2 reboots later (forced shutdown-poweroff from the virt-manager interface) it's all working

No more need to customise the kernel or worry about loss of function on the host graphics (due to VGA-Arbiter patch) !!! 
No real performance difference for(for me) between UEFI and BIOS …. more stable, easier to manage using libvirt / virt-manager (everything exposed to libvirt & managed there).
You can connect to the VM using “spicec -h 127.0.0.1 -p 5905” and use the host keyboard during bootup should the need arise – before the guest VM loads any drivers ie. before the guest keyboard and mouse are active

here's what my lspci looks like
```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
00:01.2 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x4 Controller [8086:0c09] (rev 06)
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 [8086:8c18] (rev d5)
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman PRO [Radeon HD 6950] [1002:6719]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman/Antilles HDMI Audio [Radeon HD 6900 Series] [1002:aa80]
02:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller [1912:0014] (rev 03)
04:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
05:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
06:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
```

I chose to pass the AMD card and its audio controller through along with the Renesas USB controller ie. 01:00.0 to 02:00.0

here's my final libvirt definition 
```
cat  /etc/libvirt/qemu/ssd-win8-uefi.xml
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit ssd-win8-uefi
or other application using the libvirt API.
-->

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>ssd-win8-uefi</name>
  <uuid>redacted</uuid>
  <memory unit='KiB'>6291456</memory>
  <currentMemory unit='KiB'>6291456</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static'>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader>OVMF_ssd_win8_pro.fd</loader>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell</model>
    <topology sockets='1' cores='2' threads='1'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/ssd-virt/lvwin8_uefi_kvm'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/wd2t-lvm-data/lvwin7_data'/>
      <target dev='vdb' bus='virtio'/>
      <shareable/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/wd2t-lvm-data/lvwin7_kvm'/>
      <target dev='vdc' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/mnt/programming_data/isos/winfiles_3.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <shareable/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address=<redacted>'/>
      <source bridge='rebr0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='tablet' bus='usb'/>
    <sound model='ac97'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x046d'/>
        <product id='0xc29b'/>
      </source>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
</domain>

```

Some people may need to force pci-stub and vfio modules to load at boot time. Update /etc/modules 
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_amd
```
and then update your intramfs at /etc/initramfs-tools/modules
```
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
pci_stub ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539
```





If you also want to be able to start the VM without using libvirt (ie. without using virsh or virt-manager), then you will need the following (6 steps) ....
1) Create following script at /usr/bin/vfio-bind, this is from NBHS at [https://bbs.archlinux.org/viewtopic.php?id=162768&p=1](https://bbs.archlinux.org/viewtopic.php?id=162768&p=1), and make it executable (sudo chmod ug+x /usr/bin/vfio-bind)
```
#!/bin/bash

modprobe vfio-pci

for dev in "$@"; do
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
done 
```

2) Create the script which actually binds PCI cards to VFIO, this is from NBHS at [https://bbs.archlinux.org/viewtopic.php?id=162768&p=1](https://bbs.archlinux.org/viewtopic.php?id=162768&p=1), and save it as /etc/init.d/vfio-bind-init.sh and make it executable (sudo chmod ug+x /etc/init.d/vfio-bind-init.sh)
```
#!/bin/sh

### BEGIN INIT INFO
# Provides:          vfio-bind
# Required-Start:    
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: vfio-bindings
# Description:       bind selected PCI devices to VFIO for use by KVM
### END INIT INFO

# Script to perform VFIO-BIND function as described at https://bbs.archlinux.org/viewtopic.php?id=162768
#
#
# /usr/bin/vfio-bind /etc/vfio-pci.cfg
/usr/bin/vfio-bind 0000:01:00.0 0000:01:00.1 0000:02:00.0
exit 0
```
3) To make this run automatically on startup in Ubuntu (there are no dependencies)
```
sudo update-rc.d vfio-bind-init.sh defaults
```


4) Create the config file for vfio-bind at /etc/vfio-pci.cnf, again from NBHS on the Arch forums. This is my example – I link multiple entries, though I only actually use 4 at most (currently 2)
```
# List of all devices to be held by VFIO = taken from pci_stub ..... 
# IMPORTANT – no blank lines (DEVICES line is the last line in the file)
DEVICES="0000:01:00.0 0000:01:00.1 0000:02:00.0 0000:04:00.0 0000:05:00.0 0000:06:00.0"
```

5) Also increase the “ulimit” max by adding the following to /etc/security/limits.conf so your user-id is permitted to allocate memory to the VM
```
<your user-id>           hard    memlock         8388608  # value based on required memory
```

6) Set vfio-bind-init.sh to start automatically at boot
```
sudo update-rc.d vfio-bind-init.sh defaults
```


I created these notes as I installed the VM so they may not be complete or may contain inaccuracies (though they should be close). For reference see the Arch thread and VFIO links at the start of this post
I'm happy to update the post to improve accuracy if anyone has constructive comments
      <source>
        <vendor id='0x046d'/>
        <product id='0xc29b'/>
      </source>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
</domain>
[/CODE]

Some people may need to force pci-stub and vfio modules to load at boot time. Update /etc/modules 
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_amd
```
and then update your intramfs at /etc/initramfs-tools/modules
```
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
pci_stub ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539
```





If you also want to be able to start the VM without using libvirt (ie. without using virsh or virt-manager), then you will need the following (6 steps) ....
1) Create following script at /usr/bin/vfio-bind, this is from NBHS at [https://bbs.archlinux.org/viewtopic.php?id=162768&p=1](https://bbs.archlinux.org/viewtopic.php?id=162768&p=1), and make it executable (sudo chmod ug+x /usr/bin/vfio-bind)
```
#!/bin/bash

modprobe vfio-pci

for dev in "$@"; do
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
done 
```

2) Create the script which actually binds PCI cards to VFIO, this is from NBHS at [https://bbs.archlinux.org/viewtopic.php?id=162768&p=1](https://bbs.archlinux.org/viewtopic.php?id=162768&p=1), and save it as /etc/init.d/vfio-bind-init.sh and make it executable (sudo chmod ug+x /etc/init.d/vfio-bind-init.sh)
```
#!/bin/sh

### BEGIN INIT INFO
# Provides:          vfio-bind
# Required-Start:    
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: vfio-bindings
# Description:       bind selected PCI devices to VFIO for use by KVM
### END INIT INFO

# Script to perform VFIO-BIND function as described at https://bbs.archlinux.org/viewtopic.php?id=162768
#
#
# /usr/bin/vfio-bind /etc/vfio-pci.cfg
/usr/bin/vfio-bind 0000:01:00.0 0000:01:00.1 0000:02:00.0
exit 0
```
3) To make this run automatically on startup in Ubuntu (there are no dependencies)
```
sudo update-rc.d vfio-bind-init.sh defaults
```


4) Create the config file for vfio-bind at /etc/vfio-pci.cnf, again from NBHS on the Arch forums. This is my example – I link multiple entries, though I only actually use 4 at most (currently 2)
```
# List of all devices to be held by VFIO = taken from pci_stub ..... 
# IMPORTANT – no blank lines (DEVICES line is the last line in the file)
DEVICES="0000:01:00.0 0000:01:00.1 0000:02:00.0 0000:04:00.0 0000:05:00.0 0000:06:00.0"
```

5) Also increase the “ulimit” max by adding the following to /etc/security/limits.conf so your user-id is permitted to allocate memory to the VM
```
<your user-id>           hard    memlock         8388608  # value based on required memory
```

6) Set vfio-bind-init.sh to start automatically at boot
```
sudo update-rc.d vfio-bind-init.sh defaults
```


I created these notes as I installed the VM so they may not be complete or may contain inaccuracies (though they should be close). For reference see the Arch thread and VFIO links at the start of this post
I'm happy to update the post to improve accuracy if anyone has constructive comments

---

### Post by redger on 2015-02-26
For the last year or so I've been running Windows under Linux using KVM. I started off with true VGA passthrough using instructions from here   
[LIST]
[*][https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")
[*][http://vfio.blogspot.com.au/]("http://vfio.blogspot.com.au/")
[*][http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support]("http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support")
[*][https://www.suse.com/documentation/sles11/singlehtml/book_kvm/book_kvm.html]("https://www.suse.com/documentation/sles11/singlehtml/book_kvm/book_kvm.html")
[*][https://wiki.debian.org/VGAPassthrough]("https://wiki.debian.org/VGAPassthrough")
[*][https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF]("https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF")
[/LIST]


Then a UEFI mechanism became available - which meant no need to deal with legacy VGA any more and no need for custom kernels or arcane Qemu commands passed to Libvirt. I use a standard version of Ubuntu Trusty ie. the long term stable release - as you would expect for a server

So here's a relatively easy way to create A Windows VM with real passthrough .... using the GUI to create, manage and start your VM. It's been very very stable for me and very easy to manage.

There are a few tricks along the way, nothing too arcane.

NOTE that you do NOT need the host to be booted using a UEFI bios so you need not change your motherboard bios for this. The only bios change is to ensure VT-d or AMD-VI are turned on

First off you must have the right hardware. You will need
[LIST=1]
[*]A CPU which supports IOMMU ie. VT-D in Intel or VI for AMD (this generally excludes the "K" versions of Intel CPUs)
[*]A motherboard with BIOS / UEFI which supports IOMMU as above. Note that this can be the most problematic to ensure. Broadly speaking recent Asrock boards are good, Gigabye are probably good and others are hit and miss. Many people are very frustrated with Asus (including me)
[*]A Graphics card to be passed through. Note that you cannot pass an IGP through at present so if your cpu has integrated graphics use it for the host.
[*]A plan for host interaction. You can use ssh or vnc or better (for most people) use your IGP for the host
[*]Sufficient RAM and disk
[/LIST]

In my case
[LIST]
[*]CPU		Intel 4670
[*]RAM		16 GB
[*]Motherboard	Asrock Z87 Extreme 6
[*]GPU		AMD HD6950
[*]Disk		Sandisk Extreme II 480 GB (boot drive and windows C drive host)
[*]		WD Black 2 Tb
[/LIST]

This spreadsheet lists hardware success stories [https://docs.google.com/spreadsheet/ccc?key=0Aryg5nO-kBebdFozaW9tUWdVd2VHM0lvck95TUlpMlE&usp=drive_web#gid=0]("https://docs.google.com/spreadsheet/ccc?key=0Aryg5nO-kBebdFozaW9tUWdVd2VHM0lvck95TUlpMlE&usp=drive_web#gid=0")

For these instructionsm, you'll also need a UEFI capable graphics card. Mine is an older AMD card for which there is no official UEFI bios .... but I was able to construct one using the instructions here 
[http://www.insanelymac.com/forum/topic/299614-asus-eah6450-video-bios-uefi-gop-upgrade-and-gop-uefi-binary-in-efi-for-many-ati-cards/]("http://www.insanelymac.com/forum/topic/299614-asus-eah6450-video-bios-uefi-gop-upgrade-and-gop-uefi-binary-in-efi-for-many-ati-cards/")
[http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread")
I used the tool from Insanely Mac (Windows version - installed in a temporary non-UEFI, simple VM I created for the purpose), link here [http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread/30#post_23400460")

I also bought a cheap PCIe USB card (based on the Renesas-NEC chipset) to be passed to the VM. I tried to pass USB devices directly with mixed success, so the add-in card made life much easier at a cost of < AUD$20

Next you need to enable the IOMMU in BIOS. Usually there's a bios setting on Intel boards for VT-d - it will need to be set on. The following command can be used to verify a working iommu
```
dmesg|grep -e DMAR -e IOMMU
```
you should see something like
```
[    0.000000] ACPI: DMAR 0x00000000BDCB1CB0 0000B8 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] Intel-IOMMU: enabled
[    0.028879] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.028883] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.028950] IOAPIC id 8 under DRHD base  0xfed91000 IOMMU 1
[    0.536212] DMAR: No ATSR found
[    0.536229] IOMMU 0 0xfed90000: using Queued invalidation
[    0.536230] IOMMU 1 0xfed91000: using Queued invalidation
[    0.536231] IOMMU: Setting RMRR:
[    0.536241] IOMMU: Setting identity map for device 0000:00:02.0 [0xbf000000 - 0xcf1fffff]
[    0.537490] IOMMU: Setting identity map for device 0000:00:14.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537512] IOMMU: Setting identity map for device 0000:00:1a.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537530] IOMMU: Setting identity map for device 0000:00:1d.0 [0xbdea8000 - 0xbdeb6fff]
[    0.537543] IOMMU: Prepare 0-16MiB unity mapping for LPC
[    0.537549] IOMMU: Setting identity map for device 0000:00:1f.0 [0x0 - 0xffffff]
[    2.182790] [drm] DMAR active, disabling use of stolen memory
```
And check that the more standard VT-x and AMD -v are available
```
egrep -q '^flags.*(svm|vmx)' /proc/cpuinfo && echo virtualization extensions available
```

Ensure you have all the latest versions of packages etc.
```
sudo apt-get update
sudo apt-get upgrade
```

Install KVM
```
sudo apt-get install qemu-kvm seabios spice-client hugepages spice-client
```
or use this tutorial [https://help.ubuntu.com/community/KVM/Installation]("https://help.ubuntu.com/community/KVM/Installation")

If you're going to pass an NVidia card through you will need to "hide" KVM and windows hypervisor optimisations. And that's going to need a newer version of Qemu (2.1+) than provided in the standard Trusty repos - try ppa:jacob/virtualisation. I can't vouch for NVidia cards since I don't use one and the NVidia driver developers are getting into an arms race with the Qemu developers so NVidia cards drivers are a moving target.

Create a new directory for hugepages, we'll use this later (to improve VM performance)
```
sudo mkdir /dev/hugepages
```

find your PCI addresses using the following command
```
lspci -nn
```
or lspci -nnk for additional information or lspci -vnn for even more information

choose the PCI devices you want to pass through and work out which IOMMU groups they belong to. I suggest you start simple and just passthrough the graphics card itself (don't passthrough the built in audio)
Use this script to display the IOMMU groupings (thanks to Alex WIlliamson)
```
#!/bin/sh

# List the devices in each IOMMU group, from AW at
# https://bbs.archlinux.org/viewtopic.php?id=162768&p=29

BASE="/sys/kernel/iommu_groups"

for i in $(find $BASE -maxdepth 1 -mindepth 1 -type d); do
	GROUP=$(basename $i)
	echo "### Group $GROUP ###"
	for j in $(find $i/devices -type l); do
		DEV=$(basename $j)
		echo -n "    "
		lspci -s $DEV
	done
done
```
Find the groups containing the devices you wish to pass through. All the devices in a single group need to be attached to pci-stub together (except bridges and hubs) – this ensures that there is no cross-talk between VMs ie. a security feature which IOMMUs are designed to support.
If the grouping is too inconvenient you can apply the ACS patch to your kernel (refer to the Arch discussion linked at the beginning of this post).
If you find that you have 2 devices in a single IOMMU group which you want to pass to different VMS, you're going to need the ACS patch and an additional grub command line parameter (I encountered this on my Asrock motherboard and so am not using 2 passthrough VMs simulataneously so I don't have to patch the kernel - it would be a maintenance irritation)

you're ready to change the Grub entries in /etc/default/grub
in order to enable IOMMU facilities and attach pci devices to pci-stub so they can subsequently be used by vfio. Mine looks like this (at the top) after changes
```
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on pci-stub.ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539"
GRUB_CMDLINE_LINUX=""
```
Update with 
```
sudo update-grub
```

NOTE, if you have installed Xen, you may find it has created another default file in /etc/default/grub.d/xen.conf which overrides the selection of the grub default, in my case (when experimenting) I changed it like this 
```
#
# Uncomment the following variable and set to 0 or 1 to avoid warning.
#
#XEN_OVERRIDE_GRUB_DEFAULT=0
XEN_OVERRIDE_GRUB_DEFAULT=0
```

you probably need to blacklist the drivers for graphics card being passed through (sometimes they grab the card before it's allocated to pci-stub). Change /etc/modprobe.d/blacklist.conf and add the relevant entry. In my case (for amd graphics) I added the following to the end of the file
```
# To support VGA Passthrough
blacklist radeon
```
those using an NVidia card will need to blacklist Nouveau

Whilst in the above directory you may also wish to modify /etc/modprobe.d/kvm.conf to select appropriate options, in my case (I have not used any of the options, just “documented” existence)
```
# if vfio-pci was built as a module ( default on arch & ubuntu )
#options vfio_iommu_type1 allow_unsafe_interrupts=1 
# Some applications like Passmark Performance Test and SiSoftware Sandra crash the VM without this:
# options kvm ignore_msrs=1
```

If using hugepages (recommended for better performance), update sysctl whilst in /etc ie. add the following lines to /etc/sysctl.conf
```
# Set hugetables / hugepages for KVM single guest needing 6GB RAM
vm.nr_hugepages = 3200
```
Later on we'll refine the use of hugetables. The above figures are set for my system where, hugepages are 2MB each.
The Windows VM which needs this facility the most is allocated 6GB of ram, so we need 6144 MB which => 6144 / 2 = 3072 … plus add some extra for overhead (about 2% ie. 61 additional pages, so I have overachieved :)

If you haven't included pci-stub in the kernel (see the kernel config recommendations above) then you may need to add the module name to your initramfs, update /etc/initramfs-tools/modules to include the following line
```
pci-stub
```
and “update”  your initramfs (use “-c” option to build a new one)
```
sudo update-initramfs -u
```
Note that I usually update initramfs as a matter of course when I update grub – to ensure the two are always synchronised

now you're about ready to reboot and start creating the VM

After rebooting, check that the cards to be passed through are assigned to pci-stub using
```
dmesg | grep pci-stub
```

download the virtio drivers from redhat (Windows will need these to access the vfio devices)
[http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/]("http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/")   eg. Obtain virtio-win-0.1-94.iso  which can be used later as a cd-rom image for the Windows guest
download the spice drivers for enhanced spice experience on windows from
[http://www.spice-space.org/download.html]("http://www.spice-space.org/download.html")

I installed the Ubuntu supplied OVMF so that all the necessary links etc are created but it will NOT work. You may not need to do this, but I felt it was cleaner.
```
sudo apt-get install ovmf
```
You must find the latest OVMF file … preferably download from Gerd Hoffman's site [https://www.kraxel.org/repos/jenkins/edk2/]("https://www.kraxel.org/repos/jenkins/edk2/") and extract OVMF-pure-efi-fd from the rpm and copy to /usr/share/ovmf and create a "reference" copy as OVMF.fd (take a copy of Ubuntu version first – just in case).
Note that it's even better to use the split OVMF (code in one file and variables in another - but I think this requires a later version of Qemu than stock Trusty provides)

install libvirt and virt-manager - this will provide the GUI VM management service
```
sudo apt-get install libvirt-bin virt-manager
```

update the libvirt qemu configuration at /etc/libvirt/qemu.conf -
[LIST]
[*]add this if you want to use host audio (not recommended)
```
nographics_allow_host_audio = 1
```
[*]set this to maintain security
```
security_require_confined = 1
```
[*]set these to enable qemu to access hardware. You'll need to work out which VFIO items you're going to provide access to (/dev/vfio) and you may or not want to provide access to "pulse"
```
cgroup_device_acl = [
    "/dev/null", "/dev/full", "/dev/zero",
    "/dev/random", "/dev/urandom",
    "/dev/ptmx", "/dev/kvm", "/dev/kqemu",
    "/dev/rtc","/dev/hpet", "/dev/vfio/vfio",
    "/dev/vfio/1", "/dev/vfio/14", "/dev/vfio/15", "/dev/vfio/16", "/dev/vfio/17",
    "/dev/shm", "/root/.config/pulse", "/dev/snd",
]
```
[*]add this to enable access to the hugepages directory we created earlier
```
hugetlbfs_mount = "/dev/hugepages"
```
maintian the security constraints on VMs - we're running "unpriveleged" and then providing specific accesses with changes above, plus the Apparmor changes below
```
clear_emulator_capabilities = 1
```
[/LIST]


Update apparmor to allow libvirt to allocate hugepages, use VFIO and sound. Add the following to the apparmor definition in /etc/apparmor.d/abstractions/libvirt-qemu
```
  # WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /{dev,run}/shm r,
 # ================ START Changes ================ #
  /{dev,run}/shm/pulse-shm* rw,
  @{HOME}/.config/puls** rwk,
  @{HOME}/** r,
  # Only necessary if running as root, which we no longer are
  #/root/.config/puls** rwk,
  #/root/.asoundrc r,
  /dev/vfio/* rw,
  /dev/hugepages/libvirt** rw,
  # ================ END Changes ================ #
  /{dev,run}/shmpulse-shm* r,
  /{dev,run}/shmpulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
  # spice
```
Then reload the apparmor defintiions so the changes take effect
```
sudo invoke-rc.d apparmor reload
```
Then restart libvirt (just to be sure)
```
sudo service libvirt-bin stop
sudo service libvirt-bin start
```
Be sure to back these change up as updates to Apparmor may overwrite them .....

Start virt-manager (should appear in the menu as "Virtual Machine Manager") and add a connection to QEMU on local host (File/Add Connection), this will give you the ability to create and manage KVM machines

Now we can start creating a new VM (right click on the "localhost (QEMU)" line in the main screen area and select "New")

You'll need a copy of Windows 8 or 8.1. It's apparently possible to install Windows 7 but I found it was more trouble than it's worth. DO NOT try to install the Ultimate version - install Professional or Home

Your graphics card will need to be UEFI capable. Mine is an older AMD card for which there is no official UEFI bios .... but I was able to construct one (see the beginning of this post)

Create a disk image for the VM - I recommend an LVM partition. In my case I allocate LVM partitions on the mechanical drive until I'm happy everything's running ok and then copy them across to the SSD using dd.
You'll also need a small (4GB) Fat32 partition on a "GPT" drive which we'll copy the installation files to. The install iso should be copied to an install partition as accessible to a VM ie. 
[LIST]
[*]Create a new partition for this purpose, can be LVM or 'flat' but must reside on a GPT disk not MBR
[*]Allocate the new partition to a VM – so it can be formatted. DO NOT format this using host format tools, it must be done from a VM
[*]Allocate the new partition to a windows VM
[*]Format as FAT32, consider adding the WIN xx bootloader as well. Not necessary but seems cleaner and make the partition bootable (set “active” or bootable flag in parition table)
[*]Copy the install iso to the newly formatted partition. This can be accomplished by passing the iso to the VM used to format the new install partition as a CD-ROM (use virt-manager)
[*] Check that the \efi\boot partition exists and contains the same files as \efi\microsoft\boot. If necessary copy files into a new \efi\boot partition. Also must contain a copy bootmgw.efi named bootx64.efi in \efi\boot
[*]Check the contents of \source\ei.cfg to ensure it nominates the correct OS product (best to use “Professional”).
[*]It can be beneficial to use Win Toolkit to include the linux qxl driver (spice screen driver) in the Windows build although I'm not convinced this is necessary.
[*]Exit the VM used to format the install partition
[/LIST]

Define the new VM in virt-manager. Remember to -
[LIST]
[*]Select a “dummy” iso to install from … we're going to replace this later
[*]Select UEFI as the bios (Advanced Options on last screen)
[*]use appropriate names etc
[/LIST]

STOP the install triggered by virt-manager BEFORE it installs anything. You should easily have time to stop the install while the UEFI boot process is iniating. 
Stopping is easy if you're working with virt-manager (the gui) - click on the red "shutdown" icon at the top of the screen(use the virt-viewer “force off” option). You'll probably have to stop it twice – on my system it automatically restarts itself even after a forced stop.

Create a new copy of the OVMF-pure-efi.fd file you downloaded from Gerd's site and rename it for your new VM eg.
```
sudo cp /usr/share/ovmf/OVMF-pure-efi.fd /usr/share/ovmf/OVMF-win8-pro.fd
sudo ln -s /usr/share/ovmf/OVMF-win8-pro.fd /usr/share/qemu/OVMF-win8-pro.fd
```

Ensure all the following parameters are set BEFORE attempting an install using 
```
EDITOR=nano virsh edit <your-vm-name>
``` ie.

[LIST]
[*]Initial domain definition – to support direct qemu parameters, right at the top of the file
```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
```
[*]Memory backing
```
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
```
[*]Change the loader in the <os> section ie. The OVMF file name (custom for each VM – create in /usr/share/ovmf and create link in /usr/share/qemu as described above)
```
<loader>OVMF_win8_pro.fd</loader>
```
[*]CPU. I chose to define my real CPU type. You can set it to "host", this seemed the best overall result for me
 ```
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell</model>
    <topology sockets='1' cores='2' threads='1'/>
  </cpu>
```
[*]Features (hv_relaxed etc). NVidia drivers don't seem to like these HyperV optimisations and will probably fail if they're encountered, so set to 'off' for NVidia cards
```
  <features>
    <acpi/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
  </features>
```
[*]Clock (hv_time), more performance parameters the NVidia drivers won't like, so set to 'off for NVidia cards
```
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
    <timer name='hpet' present='no'/>   # Not sure about this one
  </clock>
```
[*]Change emulator in the <devices> section
 ```
<emulator>/usr/bin/qemu-system-x86_64</emulator>
```
[*]Spice access – add to end, just before </domain>. You don't absolutely need this, but I find it useful to be able to control the keyboard during UEFI intialisation before any USB drivers have been loaded, and it doesn't seem to do any harm
```
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
```
[*]For those of you using NVidia cards you will also need to 
(a) use the kvm=off parameter which became available with Qemu v2.1+ (try ppa:jacob/virtualisation).  Add this code to the qemu:commandline section (at the end -
```
    <qemu:arg value='-cpu'/>
    <qemu:arg value='host,hv_time,kvm=off'/>
```If you're using an updated version of Libvirt you could use 
```
  <features>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
``` 
(b) choose the version of NVidia Windows driver carefully because NVidia seems to be intent on not supporting passthrough. See the VFIO blog for more information and options
[/LIST]

Save the changes. Note that Virsh may respond with an error in which case edit the file again like this ("Failed. Try again? [y,n,f,?]:") .... use the try again option to return to the editor and fix the problem

For those using NVidia cards there were changes to drivers -
[LIST][*]Version 338.77 was changed so you need kvm=off to hide the hypervisor for that version and all those after it.  
[*]From version 344.11 you'll need to remove all the "hv_foo" enablers.[/LIST]
Alex advises - the graphics performance gain from newer drivers trumps the benefit of the hyper-v extensions.  If graphics performance isn't your #1 priority then maybe there are cases for using older drivers.


For what it's worth do NOT set USB = USB2 in the VM setup, leave at default. USB processing seems to cause a lot of grief, so best to use with default. Also Logitech G27 wheel will not work correctly via Renesas USB 3 add-in card but works fine if passed directly from a USB 2 port on host via host USB passthrough - other USB devices may be similarly afflicted one way or the other (some only work when connected to a passed through card, some will only work when passed through fromm the host controller ymmv)

The install iso should be copied to an install partition as accessible to a VM ie. 
[LIST]
[*]Create a new partition for this purpose, can be LVM or 'flat' but must reside on a GPT disk not MBR
[*]Allocate the new partition to a VM – so it can be formatted. DO NOT format this using host format tools, it must be done from a VM
[*]Allocate the new partition to a windows VM
[*]Format as FAT32, consider adding the WIN xx bootloader as well. Not necessary but seems cleaner and make the partition bootable (set “active” or bootable flag in parition table)
[*]Copy the install iso to the newly formatted partition. This can be accomplished by passing the iso to the VM used to format the new install partition as a CD-ROM (use virt-manager)
[*] Check that the \efi\boot partition exists and contains the same files as \efi\microsoft\boot. If necessary copy files into a new \efi\boot partition. Also must contain a copy bootmgw.efi named bootx64.efi in \efi\boot
[*]Check the contents of \source\ei.cfg to ensure it nominates the correct OS product (best to use “Professional”).
[*]It can be beneficial to use Win Toolkit to include the linux qxl driver (spice screen driver) in the Windows build although I'm not convinced this is necessary.
[*]Exit the VM used to format the install partition
[/LIST]

Now you can use the Virt-Manager gui to further modify the VM definition (the manual edits should not be impacted by this , you an easily check at any time with "virsh edit")
[LIST]
[*]Add the newly created install partition to your new VM definition as created in #3 above and remove the previously added “dummy” install cd iso. The easiest way to do this is to use virt-viewer “information view” - add hardware. Be sure to add as “IDE disk” and not virtio
[/LIST]
also add the following -
[LIST]
[*]virtio drivers iso as cd-rom.
[*]qxl drivers iso as cd-rom (can be part of the virtio if easier). Note that this probably cannot be used during Windows install since they are unsigned. You'll need to add them later
[*]any other files need as cd-rom eg. drivers. You can easily create an iso from any files using the Ubuntu disk burning tools eg. k3b
[*]Ensure that the “boot menu” option is enabled in the boot order section of virt-viewer
[*]Ensure the main partition to be installed to is accessed via virtio (disk bus under the advanced options for the device)
[*]Ensure the network adapter is defined as virtio (device model for the NIC)
[*]ensure the default graphics and display are spice based. Windows doesn't seem to need additional drivers for these (which is why youshould NOT need to build the drivers into the install image).
[/LIST]

Run the install. If necessary press the space key as the UEFI boot progresses and select the disk to boot from. Sometimes uefi doesn't find the correct boot disk. You will need to connect via Spice to enable this (spicec -h 127.0.0.1 -p 5905)

You'll need to install "additional drivers" and select the virtio drivers for disk and network access. This makes a significant difference to VM performance AND the install will fail if you've set the VM definition to provide a virtio disk but Windows cannot find a driver

Add the required PCI devices  Only add PCI passthrough devices AFTER the main install is complete

Windows tuning hints
[LIST]
[*]Turn off all paging. The host will handle this
[*]I tell Windows to optimise for performance. This makes screens lok pretty ordinary, but since I only use the VM for gaming and games take direct control of the screen, it doesn't really matter
[*]Consider turning on update protection ie. Snapshots you can fall back to if an update fails. Then take the first snapshot directly after the install so you have a restore point
[/LIST]

Shut the vm down using the Windows shut-down procedure ie. Normal termination

Add the PCI passthrough cards. In my case I pass
[LIST]
[*]Graphics card – primary address (01:00.0)
[*]Graphics card - sound  address    (01:00.1)
[*]USB add-in card (Renesas based) to which the following are attached via downstream hubs (on display panels)                       (02:00.0)
[*]Host USB device (Logitech wheel)
[/LIST]


Add any USB devices to be passed from the host. In my case there seems to be a problem with USB 3 drivers on the guest (and possibly on the host) so I had to detach the wheel from the add-in card and attach it to a USB 2 port on the host, then pass it through via host usb passthrough – which works well.

Reboot and verify all is working

When the graphics card is working. Shut down the VM. Remove the following from the VM definition
[LIST]
[*]Spice display
[*]qxl graphics
[*]console definition 
[*]serial port definition
[*]channel definition
[/LIST]

Reboot the VM to verify everything continues to work

In my case I now set up eyefinity and gaming software. The AMD control centre seems a bit flaky and sometimes caused a lock up while trying to establish an eyefinity group. 1 or 2 reboots later (forced shutdown-poweroff from the virt-manager interface) it's all working

No more need to customise the kernel or worry about loss of function on the host graphics (due to VGA-Arbiter patch) !!! 
No real performance difference for(for me) between UEFI and BIOS …. more stable, easier to manage using libvirt / virt-manager (everything exposed to libvirt & managed there).
You can connect to the VM using “spicec -h 127.0.0.1 -p 5905” and use the host keyboard during bootup should the need arise – before the guest VM loads any drivers ie. before the guest keyboard and mouse are active

here's what my lspci looks like
```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
00:01.2 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x4 Controller [8086:0c09] (rev 06)
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 [8086:8c18] (rev d5)
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman PRO [Radeon HD 6950] [1002:6719]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman/Antilles HDMI Audio [Radeon HD 6900 Series] [1002:aa80]
02:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller [1912:0014] (rev 03)
04:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
05:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
06:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
```

I chose to pass the AMD card and its audio controller through along with the Renesas USB controller ie. 01:00.0 to 02:00.0

here's my final libvirt definition 
```
cat  /etc/libvirt/qemu/ssd-win8-uefi.xml
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit ssd-win8-uefi
or other application using the libvirt API.
-->

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>ssd-win8-uefi</name>
  <uuid>redacted</uuid>
  <memory unit='KiB'>6291456</memory>
  <currentMemory unit='KiB'>6291456</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static'>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader>OVMF_ssd_win8_pro.fd</loader>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell</model>
    <topology sockets='1' cores='2' threads='1'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/ssd-virt/lvwin8_uefi_kvm'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/wd2t-lvm-data/lvwin7_data'/>
      <target dev='vdb' bus='virtio'/>
      <shareable/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/wd2t-lvm-data/lvwin7_kvm'/>
      <target dev='vdc' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/mnt/programming_data/isos/winfiles_3.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <shareable/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address=<redacted>'/>
      <source bridge='rebr0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='tablet' bus='usb'/>
    <sound model='ac97'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x046d'/>
        <product id='0xc29b'/>
      </source>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
</domain>

```

Some people may need to force pci-stub and vfio modules to load at boot time. Update /etc/modules 
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_amd
```
and then update your intramfs at /etc/initramfs-tools/modules
```
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
pci_stub ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539
```





If you also want to be able to start the VM without using libvirt (ie. without using virsh or virt-manager), then you will need the following (8 steps) ....
1) Create following script at /usr/bin/vfio-bind, this is from NBHS at [https://bbs.archlinux.org/viewtopic.php?id=162768&p=1](https://bbs.archlinux.org/viewtopic.php?id=162768&p=1), and make it executable (sudo chmod ug+x /usr/bin/vfio-bind)
```
#!/bin/bash

modprobe vfio-pci

for dev in "$@"; do
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
done 
```

2) Create the script which actually binds PCI cards to VFIO, this is from NBHS at [https://bbs.archlinux.org/viewtopic.php?id=162768&p=1](https://bbs.archlinux.org/viewtopic.php?id=162768&p=1), and save it as /etc/init.d/vfio-bind-init.sh and make it executable (sudo chmod ug+x /etc/init.d/vfio-bind-init.sh)
```
#!/bin/sh

### BEGIN INIT INFO
# Provides:          vfio-bind
# Required-Start:    
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: vfio-bindings
# Description:       bind selected PCI devices to VFIO for use by KVM
### END INIT INFO

# Script to perform VFIO-BIND function as described at https://bbs.archlinux.org/viewtopic.php?id=162768
#
#
# /usr/bin/vfio-bind /etc/vfio-pci.cfg
/usr/bin/vfio-bind 0000:01:00.0 0000:01:00.1 0000:02:00.0
exit 0
```
3) To make this run automatically on startup in Ubuntu (there are no dependencies)
```
sudo update-rc.d vfio-bind-init.sh defaults
```


4) Create the config file for vfio-bind at /etc/vfio-pci.cnf, again from NBHS on the Arch forums. This is my example – I link multiple entries, though I only actually use 4 at most (currently 2)
```
# List of all devices to be held by VFIO = taken from pci_stub ..... 
# IMPORTANT – no blank lines (DEVICES line is the last line in the file)
DEVICES="0000:01:00.0 0000:01:00.1 0000:02:00.0 0000:04:00.0 0000:05:00.0 0000:06:00.0"
```

5) Also increase the “ulimit” max by adding the following to /etc/security/limits.conf so your user-id is permitted to allocate memory to the VM
```
<your user-id>           hard    memlock         8388608  # value based on required memory
```

6) Set vfio-bind-init.sh to start automatically at boot
```
sudo update-rc.d vfio-bind-init.sh defaults
```

7) Create a new security group containing users libvirt and <your-id> eg. libvirt_mine

8) create and execute the following script to give yourself access to all the necessary files
```
#!/bin/sh

echo "Setting ownership and access for vfio, hugepages and primary disk"

sudo chown :libvirt_mine /dev/vfio/vfio
sudo chown :libvirt_mine /dev/vfio/1
sudo chown :libvirt_mine /dev/vfio/15

sudo chmod g+rw /dev/vfio/vfio
sudo chmod g+rw /dev/vfio/1
sudo chmod g+rw /dev/vfio/15

sudo chown -R :libvirt_mine /dev/hugepages

sudo chmod -R g+rw /dev/hugepages

if [ !-e /dev/hugepages/libvirt ]; then
  sudo mkdir /dev/hugepages/libvirt
fi
sudo chown -R libvirt-qemu:libvirt_mine /dev/hugepages/libvirt
sudo chmod -R g+rw /dev/hugepages/libvirt


# in my case the VM image at /dev/ssd-virt/lvwin7_kvm is “linked” to /dev/dm-5, but write logic to find it wherever
REF_FILE=$(ls -l /dev/ssd-virt | grep lvwin7_kvm | awk '{print $11}')
STRIP=".."
ACCESSFILE="/dev"${REF_FILE#$STRIP}
#chown -R :libvirt_mine /dev/dm-5
sudo chown -R :libvirt_mine $ACCESSFILE
#chmod -R g+rw /dev/dm-5
sudo chmod -R g+rw $ACCESSFILE

# Set global user ulimit -l ie. locked memory to size of vm + working area = 6GB + 2 Gb = 8388608 kB, is accomplished in /etc/defaults/libvirt-bin by adding line "ulimit -l 8388608"
# Depnds on upper limit set in /etc/security/limits

exit 0
```


I created these notes as I installed the VM so they may not be complete or may contain inaccuracies (though they should be close). For reference see the Arch thread and VFIO links at the start of this post
I'm happy to update tje post to improve accuracy if anyone has constructive comments

---

### Post by TheFu on 2015-02-26
The **('svm|vmx)' /proc/cpuinfo** check is for VT-x or AMD-v. Don't think it does anything for VT-d.  I think for that, we have to check the dmesg output.  
[http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support](http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM#VT-d_support) has details.  Seems strange to me that you didn't reference that website at all. Is there a reason?

Didn't read the rest. Sorry, I don't game but it would be nice to move video editing into a VM - but my video card isn't supported and I don't have any UEFI here.

---

### Post by redger on 2015-02-26
Thanks for pointing that out - Link is now added

I had so many references it wa difficult to know now which ones I used all the time. Some  of the RedHat and Suse references are really good, but I didn't use them much. Mostly I followed along with the Arch discussion ... starting in Jan 2014.

UEFI was completed in January this year


You don't have to use UEFI, but without it you're up for compiling kernels etc. ... as I did for most of 2014. It works, performs the same and can also be managed via libvirt - virt-manager .... but isn't quite as stable (partly because I started off using the Q35 chipset insted of the default which had some adverse consequences).
I have the patch set for Ubuntu Trusty to support true VGA passthrough if you need them, it includes all the functional patches, plus some performance patches. Additionally I have notes on setting up a true VGA passthrough but I've not published them anywhere and there's even more work in that than this. The tricky bits that don't seem documented elsewhere related to running the VMs as a "normal" user, not "root" either via libvirt or from the command line - it was a pain to get that going the first time. The instruction in the first post should be sufficient to make that work for UEFI'd guests

---

### Post by TheFu on 2015-02-26
For me, a $40 KVM switch solves the hassle of rebuilding kernels for stuff like this just to have Windows with local graphics performance.  

I did my time on the bleeding edge in the mid-90s - rebuilding kernels all the time trying to get disk/network controllers to work at all.
It is amazing how far we've come and that we are still improving things all the time. Thanks for pushing forward.

---

### Post by jclaeyssens on 2015-02-28
Awesome write-up Redger, big thumbs up to you!!

I'm trying to build a Windows VM with passthrough hardware at the moment and now I'm a bit stuck at recompiling the kernel for the vga arbiter patch (like you mentioned). Your tutorial almost makes me want to buy a new (uefi-compatible) graphics card and try this out myself :-)

---

### Post by redger on 2015-02-28
which part of the VGA abriter patch is causing problems ? Is it the download & compile or getting the patch to apply cleanly ?

fwiw here are my notes for compiling the kernel with patches (some are performance related)

```
To compile a new kernel
https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel
https://help.ubuntu.com/community/Kernel/Compile
https://wiki.ubuntu.com/KernelTeam/KernelMaintenance
https://www.debian.org/releases/stable/i386/ch08s06.html.en

architecture is "amd64" or "x86_64"

1) download the source into the current directory using "apt-get source linux-image-xxxxx"   where xxxx is the name of the version eg. apt-get source linux-image-3.13.0-32-generic
OR   sudo apt-get source linux-image-`uname -r`

This should download the tarball(s) and extract the source code into a directory (which should be renamed immediately because all versions use the same directory name !!!)

2) Open the new directory, clean up and prepare
  chmod a+x debian/scripts/*
  chmod a+x debian/scripts/misc/*
  fakeroot debian/rules clean

  and generate the required config by either -
  a) editing using "fakeroot debian/rules editconfigs"  (for all targets, one after another)      ... (choose <arch>...generic, )**_ USE THIS_** OR YOU'LL GET A "make mrproper" ERROR ...
  b) "make menuconfig" and work through the various options. Remember to save before exit
  c) copy the current config from the boot directory as ".config" in the root directory for the new kernel and then use  "make oldconfig" ... which will ask a question for the value of each new config option
  
  Required config options are
    HZ_1000=y                     in Processor Type & Features (last page, Timer Frequency)
    PREEMPT=voluntary                 (Preemption Model on first page)
    CONFIG_PCI_STUB=y             in Bus Options, second page down (PCI Stub Driver)
    CONFIG_VFIO_IOMMU_TYPE1=y     in Device Drivers. 2 pages back from end
    CONFIG_VFIO=y                     (VFIO Non-Priveleged userspace driver framework)
    CONFIG_VFIO_PCI=y
    CONFIG_VFIO_PCI_VGA=y

3) apply any patches /// remember to verify that they worked ok (look for fail)
   "sh re_apply_patches.sh > re_output_patch.txt"

4) "fakeroot debian/rules clean"   to remove any old build information / files

5) Ignore modules not created with new parameters ... copy re_modules.ignore to ...debian.master/abi/<previous-version>/modules.ignore

   and ignore other ABI errors by copying re_prevrelease_arch_ignore (rename to  "ignore") to debian.master/abi/<previous-version>/<arch>    eg. to debian.master/abi/3.13.0-32.56/amd64/
   
   Also, update the ABI version tags in /mnt/programming_data/kernel/linux-3.13.0-36-re/debian/changelog .... by copying the last set of changes and change name etc.
   This will generate a new name for the resuling Deb packages once compiled

6) "DEB_BUILD_OPTIONS=parallel=3 skipmodule=true fakeroot debian/rules binary-headers binary-generic  > re_output_compile.txt"   to generate the deb files which can be installed (second thoughts don't pipe the poutput to a file - it will prevent selection of the CPU type)
  If you receive an error indicating you need to "make mrproper" then you need to start again and use the "fakeroot debian/rules editconfigs" command to create the Config file (step 2)

7) Install all the Debs (from the dir one level higher than compile dir) with command "sudo dpkg -i linux*<ver>*.deb
eg.   sudo dpkg -i linux*3.13.0-32_3.13.0-32.57*.deb
      sudo dpkg -i linux*3.13.0-32-generic_3.13.0-32.57*.deb

8) go into Synaptic and lock all the newly installed elements (linux-image*, linux-header*, linux-tool*, linx-cloud-tool*) - to prevent the new kernel and components being overwritten in the next upgrade
```

and here's the script I use to apply the patches
```
#!/bin/bash
# patch --dry-run --verbose -p 1 -i re_xxxxxxxxxxxxx

echo
echo ... PATCHING ... VGA Arbiter
patch -b -p 1 -i re_patch_01_i915_313rc4.patch
echo
echo ... PATCHING ... acs override
patch -b -p 1 -i re_patch_02_override_for_missing_acs_capabilities.patch
echo
echo ... PATCHING ... memleak
patch -b -p 1 -i re_patch_03_fix_memleak.patch
echo
echo ... PATCHING ... read DR6
patch -b -p 1 -i re_patch_04_fix_reading_of_DR6.patch
echo
echo ... PATCHING ... debug registers - has problem, needs to follow DR6 patch
patch -b -p 1 -i re_patch_05_debug_registers.patch
# patch -b -p 1 -i re_debug_registers_RE.patch   # Corrected to add additional lines before DR6 patch runs
echo
echo ... PATCHING ... kernel__gcc
patch -b -p 1 -i re_patch_06_kernel-38-gcc48-2.patch

```

I have all those patches for the Ubuntu kernel if you can't find them elsewhere

You might also want to look for a new bios for your graphics card, there are methods for creating UEFI versions for AMD cards as linked above.
What sort of graphics card, cpu and motherboard  do you have ?   You know that you only need to compile a new kernel if you have an Intel cpu with ingrated graphics - and even then you can actually run everything without modifying the kernel BUT the guest VM will corrupt your host graphics (mostly just wierd colours) because of Intel's poorly implemented graphics driver - so it's a good way to test viability without the need to compile a new kernel
AMD cpus should not require any kernel modifications

Enable the ACS Override Patch with the following kernel parameter on the GRUB command line ```
pcie_acs_override=downstream
```

Enable the VGA Arbiter Patch with the following kernel parmeter on the GRUB command line ```
i915.enable_hd_vgaarb=1
```

---

### Post by jclaeyssens on 2015-03-01
Wow, thanks redger! I'll have a closer look to what you posted tomorrow, because I'm a bit limited in time today, but thanks already for sharing your patching proces!

I have an Asrock C226WS motherboard with intel I7 4790S, so with integrated HD4600 and a dedicated ATI Radeon HD 6870. Using ubuntu 14.04 LTS. When I pass the boot-parameter intel_iommu=on in grub, ubuntu crashes right after grub, it just gives me a nice screen of blue and green stripes. Removing the 'quiet splash' didn't reveal anything, it crashes directly after grub... So I searched the internet a bit and I stumbled upon the vga arbiter patch by Alex Williamson.

I'm quite new to the patching kernel stuff, so for now I just downloaded a kernel 
with 
> [COLOR=#333333][FONT=UbuntuMono]sudo apt-get build-dep linux-image-`uname -r`[/FONT][/COLOR]

I unpacked it all, and then ran the patch command 

> sudo patch -p1 < vga_arbiter_patch

which gave me

> 
sudo patch -p1 < vga_arbiter_patch.diff 
[sudo] password for jclaeyssens: 
patching file drivers/gpu/drm/i915/i915_dma.c
Hunk #1 succeeded at 1297 (offset -9 lines).
Hunk #2 succeeded at 1370 (offset -9 lines).
patching file drivers/gpu/drm/i915/i915_drv.h
Hunk #1 FAILED at 2080.
1 out of 1 hunk FAILED -- saving rejects to file drivers/gpu/drm/i915/i915_drv.h.rej
can't find file to patch at input line 58
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/gpu/drm/i915/i915_params.c b/drivers/gpu/drm/i915/i915_params.c
|index d1d7980..64d96c6 100644
|--- a/drivers/gpu/drm/i915/i915_params.c
|+++ b/drivers/gpu/drm/i915/i915_params.c
--------------------------
File to patch: 
Skip this patch? [y] y
Skipping patch.
2 out of 2 hunks ignored
patching file drivers/gpu/drm/i915/intel_display.c
Hunk #1 succeeded at 10628 with fuzz 1 (offset -656 lines).
Hunk #2 succeeded at 10942 (offset -679 lines).
Hunk #3 succeeded at 11151 (offset -725 lines).
patching file drivers/gpu/drm/i915/intel_drv.h
Hunk #1 succeeded at 868 (offset -66 lines).
patching file include/linux/vgaarb.h


So if I understand the output, it didn't find the file i915_params.c. I looked it up, and it isn't their at all... So as you can see, I didn't get far :)

But I'll try out your notes tomorrow morning! Thanks again!

---

### Post by redger on 2015-03-01
This should contain the full set of patches ... ready to go. 
[ATTACH]260348[/ATTACH]

Drop them into the directory containing the kernel files (the lowest level), which will also contain the CREDITS, COPYING and README files

the last Trusty kernel I compiled was linux-3.13.0-44, and it was successful with these patches

here are the "ignore" files used to overcome the kernel compile errors (very small files to be dropped in as per the notes above)
[ATTACH]260349[/ATTACH]

the boot failure sounds more like a parameter error ... I don't suppose you've specified NOMODESET have you ... it gave me trouble. Here's my current /etc/default/grub (first lines)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#GRUB_DEFAULT=0
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT=true
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on enable_hd_vgaarb=1 pci-stub.ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539"
GRUB_CMDLINE_LINUX=""
```

and to confirm - you don't have to use the vga-arbiter patch ..... without it you will experience graphics corruption on the host display when the guest starts writing to it's display ... and it may not be all that bad so worth trying without any patches first, just to see if you can get it working

also .. there are UEFI bioses for your graphics card on this page [http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread]("http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread"). You can specify the graphics bios as a file to qemu - without having to flash the card (I haven't done it, but some of the folk on the Arch discussion seem to have, search for "romfile" here [https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")), the xml might look something like this
```
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
      <rom bar='on' file='/home/<your-id>/gpu-uefi.bin'/>
    </hostdev>
```

Note that I haven't tried this, I took the syntax from here [https://libvirt.org/formatdomain.html]("https://libvirt.org/formatdomain.html"), search for "<rom", and you may be better not to specify the "bar" option (AW made a comment about it in the Arch forums which I couldn't immediately find)

---

### Post by KillerKelvUK on 2015-03-03
Hey, for the Spice connection to work does the guest need to have a virtual display adapter as well as the passed through VGA adapter...Spice then uses the virtual to capture the output for the client to render?

My current progress is just a passed through VGA adapter, my spice client connects but doesn't render a screen just a black/blank box...USB redirection still works though.

Also regards all the upfront effort with shell scripts for unbinding the VGA device and adding it into the VFIO-PCI device before starting the guest...virt-manager & libvirt automates all of this, have confirmed this as my setup only has /dev/vfio/vfio until I start a guest when the /dev/vfio/1 device is created to mirror the IOMMU group by GTX is in.  I guess what I'm saying is that the shell scripts should only be required for users who only ever intend to use qemu via the cli but virt-manager users can omit all of those steps.

EDIT:

Sorry redger I should have started by saying Thank You, this is a great tutorial and helped me out no end :-)

---

### Post by KillerKelvUK on 2015-03-03
> **jclaeyssens said:**
> 
I have an Asrock C226WS motherboard with intel I7 4790S, so with integrated HD4600 and a dedicated ATI Radeon HD 6870. Using ubuntu 14.04 LTS. When I pass the boot-parameter intel_iommu=on in grub, ubuntu crashes right after grub, it just gives me a nice screen of blue and green stripes. Removing the 'quiet splash' didn't reveal anything, it crashes directly after grub... So I searched the internet a bit and I stumbled upon the vga arbiter patch by Alex Williamson.


If your ubuntu host is crashing on boot then I don't believe the i915 patch from Alex is the solution/problem.

If you do some googling on the 'intel_iommu=on' kernel flag there are lots of posts saying the code around this is broken in lots of places, all of it looks like hardware vendor implementation of IOMMU and not the linux kernels.  I have an ASRock Z97 Extreme 6, with the same boot flag as you I loose HDMI audio for my host...again all searches point to a bug.  Try amending the flag to 'intel_iommu=on,igfx_off'.  For me this fixes/enables my HDMI audio but breaks iommu virtualisation on my ubuntu host aka I can start virtual machines but I cannot achieve VGA pass through.  In your instance if it allows the host to boot :-) but if you can't do VGA pass through, what's the point :-(...now this *could* be related to the i915 arbitration but I'm way to green to make that call.

I'd recommend reviewing the kernel logs from the failed boots @ /var/log/syslog and see if it shows any errors that you can research.

EDIT:  should have said also I have the same CPU but am passing through a Nvidia GTX 650.

---

### Post by redger on 2015-03-04
the Spice graphics etc. are needed during install, but once the passed through graphics card is running I found it's better to remove them .... so the graphics card is "primary". And if I didn't remove the Spice "channel" some of the libvirt commands failed so it was better to remove that too. Are they causing any operational or performance problems for you ? Bear in mind that the original instructions were about getting VGA passthrough to run as a "primary" graphics adapter .... ie the one and only, so I've just retained that approach. Do you recommend I change them (and I wonder if they'd work as well for both NVidia and AMD cards)

wrt vfio scripts you're prolly correct - I had them all set up from when I started and was (a) using direct qemu commands and (b) using true legacy VGA passthrough rather than UEFI based passthrough. The instructions aren't that different in either case.

actually the instructions would be much simpler if I removed all the performance enhancements and security changes so you can run under your own user id (ie. make libvirt use "root" to run VMs .... which i wasn't so keen on hence these instructions). In a way I just threw the kitchen sink in :)
The instructions could do with a good edit and some verification ... I'll get to it at some stage

thanks for the feedback / suggestions

---

### Post by KillerKelvUK on 2015-03-04
My use case is slightly different, I have only a single monitor with multiple HDMI inputs and so I have to manually switch between these when passing through rather than using a separate monitor.  My day-to-day requirements on Windows are just corporate type email and office apps which for this Spice is more than sufficient and coupled with USB redirection for my webcam, headsets etc its quite a convenient solution.  Obviously when I want to benefit from the VGA passthrough I switch monitor inputs and pass through my USB keyboard and mouse.

I'm uncertain as to whether Spice *should* work in cooperation with the passed-through adapter...at present it isn't although as I noted the client shows its connected just without a picture.  If I add in a 2nd display adapter e.g. the virtual QXL option then I get Code 43 on the Nvidia card within the guest.  Don't know whether this is the i915 arbitration problem so have grabbed the patches you reposted and intent to build a custom kernel to find out.

Regards your guide, think the performance stuff around huge pages (which I haven't tried yet) and similar are spot on..it was the "root" parts which I avoided (no offence).  I guess these could be modified a little as you can change the ownership of the VFIO-PCI group once created so that the qemu run user can access them...small modification to your init script would do this I think although the efforts to write this are beyond my own skills and appetites TBH [-(

---

### Post by jclaeyssens on 2015-03-05
a quick follow-up, your patches worked flawlessly Redger, thank you for that!
As soon as I compiled the custom kernel I'll report back!

> **redger said:**
> This should contain the full set of patches ... ready to go. 
[ATTACH]260348[/ATTACH]

Drop them into the directory containing the kernel files (the lowest level), which will also contain the CREDITS, COPYING and README files

the last Trusty kernel I compiled was linux-3.13.0-44, and it was successful with these patches

here are the "ignore" files used to overcome the kernel compile errors (very small files to be dropped in as per the notes above)
[ATTACH]260349[/ATTACH]

the boot failure sounds more like a parameter error ... I don't suppose you've specified NOMODESET have you ... it gave me trouble. Here's my current /etc/default/grub (first lines)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#GRUB_DEFAULT=0
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT=true
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on enable_hd_vgaarb=1 pci-stub.ids=1002:6719,1002:aa80,8086:1539,1912:0014,1412:1724,1849:1539"
GRUB_CMDLINE_LINUX=""
```

and to confirm - you don't have to use the vga-arbiter patch ..... without it you will experience graphics corruption on the host display when the guest starts writing to it's display ... and it may not be all that bad so worth trying without any patches first, just to see if you can get it working

also .. there are UEFI bioses for your graphics card on this page [http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread](http://www.overclock.net/t/1474306/radeon-6000-series-uefi-bios-thread). You can specify the graphics bios as a file to qemu - without having to flash the card (I haven't done it, but some of the folk on the Arch discussion seem to have, search for "romfile" here [https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)), the xml might look something like this
```
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
      <rom bar='on' file='/home/<your-id>/gpu-uefi.bin'/>
    </hostdev>
```

Note that I haven't tried this, I took the syntax from here [https://libvirt.org/formatdomain.html](https://libvirt.org/formatdomain.html), search for "<rom", and you may be better not to specify the "bar" option (AW made a comment about it in the Arch forums which I couldn't immediately find)

---

### Post by jclaeyssens on 2015-03-06
you were right [**[COLOR=#000000]KillerKelvUK[/COLOR]**]("http://ubuntuforums.org/member.php?u=1728893"), compiling a custom kernel didn't solve the problem... Back to the drawing board...
Ah well, at least I made my first baby steps in customizing kernels...

I actually use the same setup as you do, one screen attached to my computer and I switch inputs via screen's osd. 

Guess I'm gonna try using Redger tutorial from the beginning...

---

### Post by KillerKelvUK on 2015-03-06
> **jclaeyssens said:**
> you were right [**[COLOR=#000000]KillerKelvUK[/COLOR]**]("http://ubuntuforums.org/member.php?u=1728893"), compiling a custom kernel didn't solve the problem... Back to the drawing board...
Ah well, at least I made my first baby steps in customizing kernels...

I actually use the same setup as you do, one screen attached to my computer and I switch inputs via screen's osd. 

Guess I'm gonna try using Redger tutorial from the beginning...

Just been looking at your earlier posts...

You have an Asrock with intel IGD...I'm presuming this has UEFI instead of legacy BIOS...but you're stating your Radeon doesn't have a UEFI compatible firmware, how have you validated this?

Could it be your EFI booting ubuntu and boot is using one of the video cards and at the point grub loads the Ubuntu efi its failing on one card only...have you tried altering the EFI on your Asrock to specify the card it should use as primary, I'd recommend your Intel IGD?  Also EFI on the host isn't a pre-requisite for VGA passthrough to a guest i.e. you could legacy boot your ubuntu host but OVMF boot the virtual machines (i think :?).

EDIT:

Also did you try the amended boot flag as per my earlier post...'intel_iommu=on,igfx_off'?

---

### Post by jclaeyssens on 2015-03-07
I didn't pay attention to that. I'll try this in Monday and see if it works... Just saw another post you made here in the virtualisation forum, I'll read that one as well.

---

### Post by tsend4u on 2015-03-09
**Hello!**
At begining I want to thank for your work, redger. (not only here ;) )

Am not posting much in net - almost always I solve my problems w/o asking for help.
But now am stuck - time to post and ask for some ideas or I will get crazy :).

Because I've read a lot in web about this, also tried many ways to achieve aims,
so here is only some basic info about my environment and things done:

**Hardware:**
Notebook Leneovo ThinkPad W540, Core i7 Extreme 4930MX, 32GB RAM, NVidia Quadro K2100M

**Software:**
Host: Ubuntu 14.04 with custom kernels (compiled for this purpose, based on 3.13.0-3.13.11, 3.16, 3.18, 3.19)
Guest: Windows8.1Pro / Windows7Pro

**Aim:**
Passthrough NVidia to VM. Display on Built-In LCD.

After a week of long reading and nights w/o sleep I get to this point:
[U]- in Device Manager NVidia Quadro K2100M has yellow triangle with exclamation mark.
(Code 10 - "This device cannot start")
[/U]or
_(Code 12 -"This device cannot find enough free resources that it can use")_
("If you want to use this device, you will need to disable one of the other devices on this system")

[B]Dunno where is my problem.
I will be very grateful for any ideas.[/B]

[B]Some Info:
[/B]
I did/tried almost all from your posts.
Some/or more in my own way, but am sure they doesn't affect results.

I didn't install OFVM as I don't need (atm) UEFI in VM.
Or should I? 
[probably I will try - need to passthrough dmi codes to VM to activate my Win OEM (I use legal stuff)]

Didn't applied script from your #2 post - no crash yet.

security_require_confined = 0, because
security_require_confined = 1 @ /etc/libvirt/qemu.conf provides
```
root@TP-W540:/ # libvirtd
error : virSecurityManagerNew :195 : unsupported configuration: Security driver "none" can not create confined guests 
error : qemusecurityinit: 444 : Failed to initialize security drivers
error : virStateInitialize: 749 : Initialization of QEMU state driver failed: unsupported configuration: Security driver "none" can not create confined guests
error : daemonRunStateInit:956 : Driver state initialization failed
```
Should I install selinux and set "security_driver=selinux" @ /etc/libvirt/qemu.conf  ?

/etc/apparmor.d/usr.sbin.libvirtd : line 44: unix,
```
root@TP-W540:/ # invoke-rc.d apparmor reload
 * Reloading AppArmor profiles
AppArmor parser error for /etc/apparmor.d/usr.sbin.libvirtd in /etc/apparmor.d/usr.sbin.libvirtd at line 44: syntax error, unexpected TOK_END_OF_RULE, expecting TOK_MODE
```
I ignore this error :)

- nvidia bound to vfio-pci (with bridge) (will try w/o)
```
root@TP-W540:/ # lspcigroups
[...]
### Group 1 ###
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
    01:00.0 VGA compatible controller: NVIDIA Corporation GK106GLM [Quadro K2100M] [10de:11fc] (rev a1)
[...]
```

/etc/modules
```
lprtc
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel
```

/etc/initramfs-tools/modules
```
pci_stub ids=10de:11fc
```

linux start parameters - tried various options
```
 [...] intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 pcie_acs_override=downstream i915.enable_hd_vgaarb=1
```

kernel compilations:
```
- for 3.13 I used your patch set (313)
- for 3.16, 3.18 3.19 i used patches from https://bbs.archlinux.org/viewtopic.php?id=162768
- patch rejects fixed manually
- kernel parameters CONFIG_KVM=y CONFIG_KVM_INTEL=y CONFIG_PCI_STUB=y CONFIG_VHOST_NET=m CONFIG_VGA_ARB=y CONFIG_VFIO=y CONFIG_VFIO_PCI=y CONFIG_VFIO_PCI_VGA=y CONFIG_VIRTIO_PCI=m CONFIG_VIRTIO_BALLOON=m CONFIG_VIRTUALIZATION=y HZ_1000=y CONFIG_PREEMPT_VOLUNTARY=y
```


Added cpu=...,kvm=off ( [https://libvirt.org/formatdomain.html#elementsFeatures](https://libvirt.org/formatdomain.html#elementsFeatures) / [http://vfio.blogspot.com/2014/08/primary-graphics-assignment-without-vga.html](http://vfio.blogspot.com/2014/08/primary-graphics-assignment-without-vga.html) )

/etc/libtvirt/qemu/*.xml
```
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>Win8.1x64</name>
  <uuid>hidden</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-2.1'>hvm</type>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='host-passthrough'>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/itnupl/Qemu/win8.img'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='dmi-to-pci-bridge'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1e' function='0x0'/>
    </controller>
    <controller type='pci' index='2' model='pci-bridge'>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x01' function='0x0'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='scsi' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x04' function='0x0'/>
    </controller>
    <controller type='scsi' index='1' model='virtio-scsi'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x08' function='0x0'/>
    </controller>
    <controller type='ide' index='0'/>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x05' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:d5:92:41'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x01' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x02' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x06' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
</domain>
```

Thank you for your interest,
kind regards,
T_Send.

---

### Post by jclaeyssens on 2015-03-09
From what I know, you either have AppArmor or SELinux on your system. They dont get along too well on one system. AppArmor is installed by default on Ubuntu. SELinux doesn't seem to be actively maintained
Reference post about SELinux:
[http://askubuntu.com/questions/481293/selinux-implementation-in-ubuntu](http://askubuntu.com/questions/481293/selinux-implementation-in-ubuntu)
For the rest I won't be able to help much further, I'm on the same struggling path as you are :-)

KillerKelvUk:
I tried the igfx_off parameter in grub and it worked :o for some stupid reason my system didn't find one particular hard drive, but meh, I'll have to figure that out later
Cheers to you!

---

### Post by KillerKelvUK on 2015-03-09
> **jclaeyssens said:**
> 
KillerKelvUk:
I tried the igfx_off parameter in grub and it worked :o for some stupid reason my system didn't find one particular hard drive, but meh, I'll have to figure that out later
Cheers to you!

Glad you got some luck with this.  Definitely some thing wrong with IOMMU somewhere, whether its EFI or linux kernel or both.  I've had to raise a bug ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1428121](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1428121)) for my audio issue as the 'igfx_off' for me stops VGA pass through working.

---

### Post by KillerKelvUK on 2015-03-09
> **tsend4u said:**
> **Hello!**
At begining I want to thank for your work, redger. (not only here ;) )

Am not posting much in net - almost always I solve my problems w/o asking for help.
But now am stuck - time to post and ask for some ideas or I will get crazy :).

Because I've read a lot in web about this, also tried many ways to achieve aims,
so here is only some basic info about my environment and things done:

**Hardware:**
Notebook Leneovo ThinkPad W540, Core i7 Extreme 4930MX, 32GB RAM, NVidia Quadro K2100M


Does the notebook give you the option of selecting the hosts video device and display, guess this would be in the EFI?  Struggling to see how pass through would work for you with a single display unless you can manually choose in the EFI both the primary video adapter as well as the output display...then you'd output host video via a HDMI using Intel IGD and could therefore passthrough the Nvidia and use the built-in screen.

---

### Post by tsend4u on 2015-03-10
> **KillerKelvUK said:**
> Does the notebook give you the option of selecting the hosts video device and display, guess this would be in the EFI?  Struggling to see how pass through would work for you with a single display unless you can manually choose in the EFI both the primary video adapter as well as the output display...then you'd output host video via a HDMI using Intel IGD and could therefore passthrough the Nvidia and use the built-in screen.
Later I will provide EFI System Settings screenshot.
- NO option to select primary graphics (this system doesn't work that way)
- Option to set discrete graphics (NVidia) power mode (Balance / Performance)
- Option to set BOOT display output [ThinkPad LCD / Analog Output (VGA) / Digital Output (DisplayPort) / Display Dock]
- no HDMI Port
- D-Sub and mDP (mini Display Port) available (obviously supporting HDMI Display via mDP-HDMI cable)

But you gave me an idea to change System Settings, as I use High Security Option - Secure Chip / Secure Boot etc.
I disabled all for testing and switched to legacy mode, but no difference - supposed that as since purchase I made my own system configuration and created Custom Security Setup to support full secure EFI mode and full unsecured Legacy. This notebook is portable workstation and I use to many different purposes (as it was created for). But off work I'd like to use VM for some windows gaming. :)

**Fixed**
[I]```
libvirtd error : virSecurityManagerNew :195 : unsupported configuration: Security driver "none" can not create confined guests
AppArmor parser error for /etc/apparmor.d/usr.sbin.libvirtd in /etc/apparmor.d/usr.sbin.libvirtd at line 44: syntax error, unexpected TOK_END_OF_RULE, expecting TOK_MODE
```[/I]
- Reinstalled Apparmor (just in case), fixed config overwrites, removed syntax "unix" from line 44. ~ invoke-rc.d apparmor reload **SUCCESS**
- Set security_driver=apparmor @ /etc/libvirt/qemu.conf . ~ /etc/init.d/libvirt-bin restart **SUCCESS**
I think that's cause of higher version of libvirt, which provides unknow syntax for older apprmor.
Maybe this should be included in 1st post, cause default security driver is "none" and option is commented out /etc/libvirt/qemu.conf ?

**More detailed information** (I will upgrade my previous post also):
- Qemu version 2.1.2 (from xorg-edgers)
- I completely removed nouveau from system
- I use some custom xorg init options for my rare ThinkPad to achieve: (but am pretty sure it shouldn't affect this problem)
  -- brightness control (for both NVidia and Intel)
  -- full usage of ThinkPad ClickPad (TouchPad) which I ported from AUR.arch (here is my script: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683/comments/50](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1246683/comments/50) )
-- blackscreen / blankdesktop solution (by [http://vxlabs.com/2015/02/05/solving-the-ubuntu-14-04-nvidia-346-nvidia-prime-black-screen-issue/](http://vxlabs.com/2015/02/05/solving-the-ubuntu-14-04-nvidia-346-nvidia-prime-black-screen-issue/) ) for which I made easy switch scripts.
- Host Driver - NVidia 346 Drivers on Host from [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)
- VM Driver - old NVidia for Quadro (332.21) (According to ISSUES @ very end of 1st post [https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768) )
[B]
According to[/B] [http://www.mail-archive.com/qemu-devel@nongnu.org/msg174066.html](http://www.mail-archive.com/qemu-devel@nongnu.org/msg174066.html)
&#8203;```
root@TP-W540:/ # head --lines=1 /dev/vga_arbiter
count:1,PCI:0000:00:02.0,decodes=io,owns=io,locks=none(0:0)
```

---

### Post by redger on 2015-03-14
@tsend4u
are you still working on this ?
From my reading on the Arch KVM VFIO forum the only way this will work is if the NVidia "card" has a hardware dedicated output connector ie. one (or more) connectors dedicated just to the extra graphics card which is defined in hardware, unchangeable, and not related to the integrated graphics. Apparently many / most implementations use the integrated chip for rendering ..... in which case it's impossible to pass the extra processor through to a VM (because it still needs the IGP for rendering)

Furthermore Intel integrated graphics cannot be passed through either because of the way they're entangled with the other hardware

On the other hand you could try KVM-GT or XEN-GT [http://lists.freedesktop.org/archives/intel-gfx/2014-December/056652.html]("http://lists.freedesktop.org/archives/intel-gfx/2014-December/056652.html") which may achieve something close to what you want

---

### Post by tsend4u on 2015-03-18
@redger
Thank you for your reply.

Last days I was busy, but yes I'm still working on this - and I will until successful passthrough. I'm sick of rebooting to GatesOS.

That I was afraid and not sure about - implementation of combined IGP and discrete VGA on this ThinkPad's system in aspect of passing trough.
I didn't want to start XEN til this will be the last way possible. First I will read about and try KVM-GT. If you have any helpful info about it before I will start googling, I will be very grateful for providing it.

Kind regards,
T_Send.

---

### Post by jclaeyssens on 2015-05-14
Finally gave this another try, got my motherboard replaced and lo and behold, everything boots just fine when I pass the intel-iommu=on to the kernel, without having to apply any patch whatsoever! I tried it on Ubuntu 15.04, completely messes up DMAR, back to 14.04, everything fine so far... 

> 
[COLOR=#000000]Create a disk image for the VM - I recommend an LVM partition. In my case I allocate LVM partitions on the mechanical drive until I'm happy everything's running ok and then copy them across to the SSD using dd.[/COLOR]
[COLOR=#000000]You'll also need a small (4GB) Fat32 partition on a "GPT" drive which we'll copy the installation files to. The install iso should be copied to an install partition as accessible to a VM ie. [/COLOR]

[LIST]
[*]Create a new partition for this purpose, can be LVM or 'flat' but must reside on a GPT disk not MBR
[*]Allocate the new partition to a VM – so it can be formatted. DO NOT format this using host format tools, it must be done from a VM
[*]Allocate the new partition to a windows VM
[*]Format as FAT32, consider adding the WIN xx bootloader as well. Not necessary but seems cleaner and make the partition bootable (set “active” or bootable flag in parition table)
[*]Copy the install iso to the newly formatted partition. This can be accomplished by passing the iso to the VM used to format the new install partition as a CD-ROM (use virt-manager)
[*]Check that the \efi\boot partition exists and contains the same files as \efi\microsoft\boot. If necessary copy files into a new \efi\boot partition. Also must contain a copy bootmgw.efi named bootx64.efi in \efi\boot
[*]Check the contents of \source\ei.cfg to ensure it nominates the correct OS product (best to use “Professional”).
[*]It can be beneficial to use Win Toolkit to include the linux qxl driver (spice screen driver) in the Windows build although I'm not convinced this is necessary.
[*]Exit the VM used to format the install partition
[/LIST]


[COLOR=#000000]Define the new VM in virt-manager. Remember to -[/COLOR]

[LIST]
[*]Select a “dummy” iso to install from … we're going to replace this later
[*]Select UEFI as the bios (Advanced Options on last screen)
[*]use appropriate names etc
[/LIST]


Redger ,I don't quite understand what you're aiming at here: do I need to make a new partition and allocate that to another windows VM to have formatted it in fat32?

---

### Post by jclaeyssens on 2015-05-15
Seems like I was to quick to state everything went fine... When I use the IGP from my I7 cpu in combination with IOMMU this completely messes up DMAR, hundreds of errors in the output of 

> dmesg | grep -DMAR 

looked it up, known problem. [https://www.kernel.org/doc/Documentation/Intel-IOMMU.txt](https://www.kernel.org/doc/Documentation/Intel-IOMMU.txt)
They advise to give the following parameter to the kernel: intel_iommu=igfx_off, but this disables iommu as well so... 
Seems like I'm going to have to buy a second graphics card after all...

---

### Post by devin-a-hudson on 2015-05-15
OP, ever consider spinning your setups as a distro/Modified Ubuntu image?

Make an image for AMD gpu's and Nvidia gpu's specifically. Add some scripts to hand-hold the windows OS installation and other post installation setup's. Post a "this is the cpu/gpu/mobo hardware that work list. Would be a great resource for those non-1337 enough to figure this kinda thing out by themselves.

---

### Post by redger on 2015-05-21
hi jclaeyssens

your first question about the partitions required ..... the Fat32 partition is used as a source for the install DVD. It gives you full control of the executables used by the Windows installer and overcomes some UEFI boot issues. It can be discarded once installation is completed
All the checking is to ensure that the Windows installation programs will run and do what you want

We originally define the VM with a "dummy" install so we don't accidentally start the install before the VM definition has been modified ie. defined the basics, stop the process early in the boot process  before anything is actually installed, make a number of definition changes (virsh edit)  and then restart the VM to commence the actual install

if you'd like to clarify the text I'll be happy to paste it in :)



did you resolve your DMAR issues ? I'm a bit confused with that. What sort of hardware are you using (the Asrock C226WS motherboard ?) ... and how are you allocating it (the PCI ports etc.) Are you trying to allocate the IGP to a VM ?
Asrock motherboards (BIOS) are usually pretty good for IOMMU functionality .... are you running the latest firmware ? It's possible there's a fix

---

### Post by redger on 2015-05-21
@devin-a-hudson

it's a great idea .... I'm not that much of a masochist. Too many variables & support "opportunities" ... even if I had the expertise

---

### Post by jclaeyssens on 2015-05-27
> **redger said:**
> hi jclaeyssens

your first question about the partitions required ..... the Fat32 partition is used as a source for the install DVD. It gives you full control of the executables used by the Windows installer and overcomes some UEFI boot issues. It can be discarded once installation is completed
All the checking is to ensure that the Windows installation programs will run and do what you want

We originally define the VM with a "dummy" install so we don't accidentally start the install before the VM definition has been modified ie. defined the basics, stop the process early in the boot process  before anything is actually installed, make a number of definition changes (virsh edit)  and then restart the VM to commence the actual install

if you'd like to clarify the text I'll be happy to paste it in :)



did you resolve your DMAR issues ? I'm a bit confused with that. What sort of hardware are you using (the Asrock C226WS motherboard ?) ... and how are you allocating it (the PCI ports etc.) Are you trying to allocate the IGP to a VM ?
Asrock motherboards (BIOS) are usually pretty good for IOMMU functionality .... are you running the latest firmware ? It's possible there's a fix

Bought myself a second graphics card last week, since I found out the IGP messed up my DMAR. Deactivated the IGP in bios, installed the new one, passed the intel_iommu=on in grub and DMAR seems to work fine, no more errors! 
But off course, things can't go this smoothly... I just found out that the motherboard paired the two graphic cards to one vfio group... So this means I'll have to apply the ACS patch after all... The never-ending story continues...:? I saw KillerKelvUk opened a thread on the ACS patching of the 15.04 kernel, guess I'll have to take a look at that...

---

### Post by KillerKelvUK on 2015-05-27
> **jclaeyssens said:**
> Bought myself a second graphics card last week, since I found out the IGP messed up my DMAR. Deactivated the IGP in bios, installed the new one, passed the intel_iommu=on in grub and DMAR seems to work fine, no more errors! 
But off course, things can't go this smoothly... I just found out that the motherboard paired the two graphic cards to one vfio group... So this means I'll have to apply the ACS patch after all... The never-ending story continues...:? I saw KillerKelvUk opened a thread on the ACS patching of the 15.04 kernel, guess I'll have to take a look at that...

Maybe this is frowned on for some good reasons but if you want to d/l the patched kernel debs i built have a look here... [https://www.dropbox.com/sh/moybwdvvg2c84by/AABtlZ3E2byZu1Iqw8zqcnwMa?dl=0](https://www.dropbox.com/sh/moybwdvvg2c84by/AABtlZ3E2byZu1Iqw8zqcnwMa?dl=0) ...obviously be a good idea for you to get the process down yourself for keeping up-to-date with kernel releases.

---

### Post by jclaeyssens on 2015-05-28
Thanks a bunch KillerKelvUK! I do understand some people will frown for me asking a patched file, I would do the same if I knew all the it's and out's of the patching business :-) but this is the perfect situation to learn how this works: the original file, patched file and the patch itself. If I can't figure it out now I never will :-D

---

### Post by redger on 2015-05-31
fwiw I posted all the passhtrough patches for Trusty, plus patching instructions on page 1

you can easily extract just the elements required for ACS Override ( a single patch, chop the others from the script) if you'd like repeatability :)

---

### Post by carl39 on 2015-06-03
Fantastic guide! I've made my way up to the part where I have to connect using "spicec -h 127.0.0.1 -p 5905" the first time for the install. It keeps saying:
> Warning: failed to connect: Connection refused (111)

I suspect it has something to do with my network configuration
```

<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit Win81
or other application using the libvirt API.
-->

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>Win81</name>
  <uuid>32a03ecd-0b5b-9f6b-381c-fbc13aa2c70b</uuid>
  <memory unit='KiB'>12582912</memory>
  <currentMemory unit='KiB'>12582912</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static'>8</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader>OVMF-win8-pro.fd</loader>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <cpu>
    <topology sockets='1' cores='8' threads='1'/>
  </cpu>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/dongcarl/windows1.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/home/dongcarl/Downloads/virtio-win-0.1.96.iso'/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address=iredacttoo/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='vga' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x1b1c'/>
        <product id='0x1a0a'/>
      </source>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
</domain>

```

here's my ifconfig:
```

eth0      Link encap:Ethernet
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae22:bff:fe52:cc44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1412446 (1.4 MB)  TX bytes:259858 (259.8 KB)
          Interrupt:18 Memory:fbe00000-fbe20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65884 (65.8 KB)  TX bytes:65884 (65.8 KB)

virbr0    Link encap:Ethernet
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1556 (1.5 KB)  TX bytes:1755 (1.7 KB)

vnet0     Link encap:Ethernet
          inet6 addr: fe80::fc54:ff:fe0e:53c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1612 (1.6 KB)  TX bytes:18863 (18.8 KB)

```

Again, thanks for all the help and contributions!!

---

### Post by KillerKelvUK on 2015-06-05
> **carl39 said:**
> ... I have to connect using "spicec -h 127.0.0.1 -p 5905" the first time for the install. 


EDIT:  Apols ignore the rubbish below, I re-read your guest config and you're manually fudging the qemu commandline to specify the spice port rather than using libvirt XML syntax.


***original rubbish post***
So the 5905 in this line pertains to the port used to connect to the spice server on your host...spice server connections start from port 5900, each virtual machine that is running uses a port...so if you have only a single vm running try using 5900 if you have other vm's running just keep adding 1 to the number until you find the connection i.e 5901..2..3 and so on.

---

### Post by KillerKelvUK on 2015-06-05
> 
<qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/> 
</qemu:commandline>
[COLOR=#222222]

[FONT=Verdana]So these lines are fudging the libvirt syntax to inject qemu arguments, typically this is used if a qemu feature hasn't been adopted by libvirt yet.  Try ripping these lines out, and assuming you're using something like virt-manager to admin the vm's just re-add the display adapter configured for spice, this will generate the libvirt XML equivalent.  You could manually specify to us the same port 5905 although this isn't required so you could just leave it to auto and then my original rubbish upstairs applies i.e. using 5900..1..2 etc.[/FONT][/COLOR]

---

### Post by carl39 on 2015-06-05
Worked fantastically! However, I can't seem to connect the Windows install drive. I followed all the instructions on the original post except I put it on a USB instead of a SATA drive, I've added the USB by ID in my config, but here's what it says:

[ATTACH=CONFIG]262458[/ATTACH]

---

### Post by KillerKelvUK on 2015-06-06
So my experiences with OVMF vary in that some devices it picks up and some it doesn't.  Typically you have to let iPXE do its stuff and error, this will drop you to an EFI Shell, type 'exit' here and it will drop you into the OVMF admin page.  In here you need to see if the OVMF EFI can see your USB device and then add it into the boot list....from the main menu select "Boot Maintenance Manager" then "Boot Options" then "Add boot option"...this should give you a list of everything the OVMF EFI can see, if you can find your boot drive in this list add it in and you should get moving pretty quick and it will be a one time thing.  If not then either you've either added the usb to the guest incorrectly or you've hit a permissions issue for adding the USB device to the guest or your USB device just isn't compatible with OVMF.

The permission issue one is easy to confirm and work around just look in /var/log/libvirt/qemu/your-vm-name.log...follow the timestamps and when the guest starts if you see a bunch of lines pertaining to your usb device and not having permissions to assign then post back and I'll talk you through how to overcome this.

On a side note, I just use the normal win.iso file and add this into the guest as a CDROM using virt-manager...this has none of the above challenges and so if this is an option you might try it instead of putting the win install onto a usb drive.

---

### Post by carl39 on 2015-06-10
Thanks so much for all the help! Everything's working except my guest is not detecting my display... It's a bit peculiar as I remember it did detect the display on a previous reboot (but on that reboot it didn't detect my R9 290 properly, it was simple a generic Display Adapter).

---

### Post by KillerKelvUK on 2015-06-10
> **carl39 said:**
> Thanks so much for all the help! Everything's working except my guest is not detecting my display... It's a bit peculiar as I remember it did detect the display on a previous reboot (but on that reboot it didn't detect my R9 290 properly, it was simple a generic Display Adapter).

Does the R9 show up in the windows device manager or not i.e. listed but disable or such like?

On the host can you see the card being reassigned from the stub driver to the guest in the dmesg output...just after you start the guest up?

This maybe because of the SPICE *fix*...by added the spice display back into the libvirt xml using virt-manager it also adds in a display adapter automatically i.e the QXL driver likely...this can cause windows to get confused.  I think this is why the qemu commandline hack is used to get spice working without libvirt adding back in a separate virtual display adapter.  Check and confirm the stuff above first and if thats all okay we'll try and get the original spice code working.

---

### Post by cobra30689 on 2015-06-10
I don't know if this is the place to ask, or whether I should start my own thread, but here goes.  I'm thinking about virtualizing a Win98 gaming machine with QEMU/KVM on 14.10, using VGA passthrough to a PCI Voodoo 3 card....anyone have any experience trying this, or is it even possible?

---

### Post by redger on 2015-06-10
@cobra30689

in theory ... yes it's possible though I haven't tried it

however .... you won't be able to use the UEFI process, since Win98 preceeds UEFI.

Process is quite similar, BUT 
[LIST]
[*]you should be able to pass the PCI card through. You may have some issues if there are other PCI cards in the system
[*]if using Intel integrated graphics for the host you're probably going to have to patch the kernel with the VGA Arbiter patch ... not required for AMD. Try without patches first and then consider the patches after you demonstrate feasibility
[/LIST]

it's easiest to use Virt-Manager to define the VM, be sure to use the default machine type and DON'T select UEFI

I set up a Win XP guest using virt-manager very very easily ... but I haven't passed a graphics card to it, just some USB devices

---

### Post by carl39 on 2015-06-13
> **KillerKelvUK said:**
> Does the R9 show up in the windows device manager or not i.e. listed but disable or such like?

On the host can you see the card being reassigned from the stub driver to the guest in the dmesg output...just after you start the guest up?

This maybe because of the SPICE *fix*...by added the spice display back into the libvirt xml using virt-manager it also adds in a display adapter automatically i.e the QXL driver likely...this can cause windows to get confused.  I think this is why the qemu commandline hack is used to get spice working without libvirt adding back in a separate virtual display adapter.  Check and confirm the stuff above first and if thats all okay we'll try and get the original spice code working.

The most curious thing just happened... Just as I was writing up this reply, the ubuntu machine's display slowly darkened, then disconnected from the display. When I force rebooted and tried to start the windows VM, it worked! The display attached to the R9 290 was detected!

Edit: I now realize how stupid I sound... That was just ubuntu going into sleep mode... The detection of the monitor was an accident apparently because on the next restart, it disappeared again. I then downloaded and installed the R9 290 drivers, and it's been working well. Thanks again.

---

### Post by KillerKelvUK on 2015-06-14
> **carl39 said:**
> The most curious thing just happened... Just as I was writing up this reply, the ubuntu machine's display slowly darkened, then disconnected from the display. When I force rebooted and tried to start the windows VM, it worked! The display attached to the R9 290 was detected!

Edit: I now realize how stupid I sound... That was just ubuntu going into sleep mode... The detection of the monitor was an accident apparently because on the next restart, it disappeared again. I then downloaded and installed the R9 290 drivers, and it's been working well. Thanks again.

Glad you've managed to get it sorted. My attempt was with an old Nvidia card so had all the troubles associated with that...the whole setup was v.unstable when running graphical intensive apps however I got it to work consistently and predicatbly at boot...which I guess is something :). Let us know how you get on with the R9 and the VM performance & consistency...might have to make a purchase.

---

### Post by mikew2 on 2015-07-18
> **redger said:**
> 

The install iso should be copied to an install partition as accessible to a VM ie. 
[LIST]
[*]Create a new partition for this purpose, can be LVM or 'flat' but must reside on a GPT disk not MBR
[*]Allocate the new partition to a VM – so it can be formatted. DO NOT format this using host format tools, it must be done from a VM
[*]Allocate the new partition to a windows VM
[*]Format as FAT32, consider adding the WIN xx bootloader as well. Not necessary but seems cleaner and make the partition bootable (set “active” or bootable flag in parition table)
[*]Copy the install iso to the newly formatted partition. This can be accomplished by passing the iso to the VM used to format the new install partition as a CD-ROM (use virt-manager)
[*] Check that the \efi\boot partition exists and contains the same files as \efi\microsoft\boot. If necessary copy files into a new \efi\boot partition. Also must contain a copy bootmgw.efi named bootx64.efi in \efi\boot
[*]Check the contents of \source\ei.cfg to ensure it nominates the correct OS product (best to use “Professional”).
[*]It can be beneficial to use Win Toolkit to include the linux qxl driver (spice screen driver) in the Windows build although I'm not convinced this is necessary.
[*]Exit the VM used to format the install partition
[/LIST]

Now you can use the Virt-Manager gui to further modify the VM definition (the manual edits should not be impacted by this , you an easily check at any time with "virsh edit")
[LIST]
[*]Add the newly created install partition to your new VM definition as created in #3 above and remove the previously added “dummy” install cd iso. The easiest way to do this is to use virt-viewer “information view” - add hardware. Be sure to add as “IDE disk” and not virtio
[/LIST]


I've been using this excellent HowTo over the past week to create a VM server which contains 2 Ubuntu guest VMs to run Kodi and 1 Windows 8 guest VM to run as a gaming machine. All three VMs will have GPU passthrough. I've been working on getting the Ubuntu/Kodi guest VMs working first before attempting the Windows 8 guest VM. After TONS of reading and several re-installs of the host OS along with patching kernels, etc, I finally have the Ubuntu Guest VMs working with GPU passthrough on Nvidia and Radeon cards which have been flashed with UEFI firmware. I thought I had the hard part done, but I just don't know how to perform the quoted items above.

Can someone give me a little more detail regarding the steps above? I'm not sure if these steps (i.e. Format as FAT32) are suppose to be done in the Ubuntu host OS, within Virt Manager, or within a Windows VM itself. Even the first step, "Create a new partition for this purpose, can be LVM or 'flat' but must reside on a GPT disk not MBR" is confusing to me because I don't know if this needs to be done in the host or somehow within Virt Manager.

I'm hoping this is the last obstacle I face in getting my "proof of concept" VM server up and running.

Thanks.

---

### Post by redger on 2015-07-18
Hi Mike,
yes that description seems to have created a bit of confusion. I tried to improve it a bit later in the thread, without success :)

Anyway, you just need an install image the VM can read and use. 

The easiest way to do this is to use a VM (any VM will do really) to construct a partition for the purpose. It sounds as tho you have successfully created some linux VMs, so you can use one of them.

Create a new partition on the host, of >=4GB size. It only needs to be big enough to contain the Windows iso, plus a little (like 100MB)

Allocate that new partition to one of your existing VMs and also allocate the Windows install iso to that VM (as a CD-ROM using the virt-manager gui)

Start the VM with the new partition

In the VM, create a new GPT partition table on the partition you created on the host and passed through

Now that you have a new GPT partition table create a partition and format it as FAT32 / VFAT. (it sounds like you've created 2  partitions so far, but from the VM perspective you have only created one ... what you created on the host looks like a complete disk to the VM guest rather than a partition)
Ensure the "bootable" flag is set on the partition

Copy the contents of the Windows install iso to the newly formatted partition

Check that you have the \efi\boot directory because the efi boot process is going to look for it. 
If the \efi\boot directory wasn't copied across from the Windows install you can easily create it by copying files from  \efi\microsoft\boot  into a \efi\boot directory and create a copy of bootmgw.efi named bootx64.efi in \efi\boot

Now you can shut down your VM and attach this partition to the new Windows VM as storage

The final piece is to ensure that EFI knows to boot from this newly constructed VM ... 
Sometimes uefi doesn't find the correct boot disk. I found the best way was to press the space key as the UEFI boot progresses and select the disk to boot from. 
In order to ensure you can see the UEFI boot and send keys to it you will need to connect via Spice   (spicec -h 127.0.0.1 -p 5905) and that in turn requires that you have added the Spice definition to your XML ie
```
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5905,disable-ticketing'/>
    <qemu:env name='DISPLAY' value=':0'/>
  </qemu:commandline>
```

Does that clarify ?

More importantly did it work ? If so, can you help me re-write the instructions to clarify for others .... thx :)

I'm in Australia so my times are probably different to yours, I'll check your feedback later

---

### Post by mikew2 on 2015-07-19
Thanks for the clarification. I'm going out of town for several days so won't be able to try this right now. Also, I've been experimenting with several methods and right now I'm trying out unRAID which now supports VMs. I had an unused license from several years ago and they are now on version 6 which includes some neat features such as VM (via KVM) and Docker support. If I run into any issues with this then I'll go back to your method. 

But either way, I think your response clarifies what I need to do.

Thanks!

---

### Post by ilmmpk on 2015-09-01
I've got a question.

I'm trying to set this up using a MSI H67MA-E35, a Geforce GTX 460 for passthru, and the IGD on the MSI mobo as the host.

My question, I've found that my IGD is using the i915 driver.  I'm stuck at the point where Windows will start in the guest session, but the GTX 460 never activates the second monitor.  I can start the win7 KVM up in safe mode and it does boot up completely.  I'm thinking I may need to use the i915 VGA arbitration patch you mentioned.  

I spoke with another person doing passthru, and they mentioned that if I'm using OVMF, I shouldn't need the i915 arbitration patch.

Is this true?

---

### Post by KillerKelvUK on 2015-09-01
> **ilmmpk said:**
> I've got a question.

I'm trying to set this up using a MSI H67MA-E35, a Geforce GTX 460 for passthru, and the IGD on the MSI mobo as the host.

My question, I've found that my IGD is using the i915 driver.  I'm stuck at the point where Windows will start in the guest session, but the GTX 460 never activates the second monitor.  I can start the win7 KVM up in safe mode and it does boot up completely.  I'm thinking I may need to use the i915 VGA arbitration patch you mentioned.  


I spoke with another person doing passthru, and they mentioned that if I'm using OVMF, I shouldn't need the i915 arbitration patch.

Is this true?

Yes but only if your GTX has a UEFI bios on it and a quick Google would suggest it doesn't ([http://forums.evga.com/m/tm.aspx?m=2108070&p=1](http://forums.evga.com/m/tm.aspx?m=2108070&p=1)). This isn't necessarily the end as some cards can be re flashed so they do have UEFI bios, but you'll need to read around to see how likely this is for you.

---

### Post by moffa on 2015-09-07
I can't get to create the machine, with UEFI.  If I leave it on BIOS the window opens and it starts booting.  I've tried changing permissions on the /var/lib/libvirt/qemu/win8-pro and the other files in /usr/share/ovmf but I keep getting the same error.  It's so frustrating.

I get the following error:
```
Unable to complete install: 'internal error: process exited while connecting to monitor: 2015-09-07T23:08:25.864947Z qemu-system-x86_64: -drive file=/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd,if=pflash,format=raw,unit=1: Could not open '/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd': Permission denied
'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1873, in do_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 414, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 478, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3574, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: 2015-09-07T23:08:25.864947Z qemu-system-x86_64: -drive file=/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd,if=pflash,format=raw,unit=1: Could not open '/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd': Permission denied

```

---

### Post by redger on 2015-09-07
that's odd .. haven't seen that before (mind you I'm not using a host based Vars file)
do you need to use a separate vars file ? windows will create it's own so you could just use that ... if only to prove the process

I'm assuming you have already created the required file .... at the specified location, with appropriate access (for libvirt-qemu)

sadly, the original Arch thread has been closed so it's no longer available, you could try sending a request to the new mailing list
> Send vfio-users mailing list submissions to
	[email]vfio-users@redhat.com[/email]

To subscribe or unsubscribe via the World Wide Web, visit
	[https://www.redhat.com/mailman/listinfo/vfio-users](https://www.redhat.com/mailman/listinfo/vfio-users)
or, via email, send a message with subject or body 'help' to
	[email]vfio-users-request@redhat.com[/email]

You can reach the person managing the list at
	[email]vfio-users-owner@redhat.com[/email]

---

### Post by KillerKelvUK on 2015-09-08
> **moffa said:**
> I can't get to create the machine, with UEFI.  If I leave it on BIOS the window opens and it starts booting.  I've tried changing permissions on the /var/lib/libvirt/qemu/win8-pro and the other files in /usr/share/ovmf but I keep getting the same error.  It's so frustrating.

I get the following error:
```
Unable to complete install: 'internal error: process exited while connecting to monitor: 2015-09-07T23:08:25.864947Z qemu-system-x86_64: -drive file=/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd,if=pflash,format=raw,unit=1: Could not open '/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd': Permission denied
'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1873, in do_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 414, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 478, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3574, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: 2015-09-07T23:08:25.864947Z qemu-system-x86_64: -drive file=/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd,if=pflash,format=raw,unit=1: Could not open '/var/lib/libvirt/qemu/nvram/win8-pro_VARS.fd': Permission denied

```

Hey, could you be experiencing an AppArmor issue?  If you haven't already check your dmesg output to see if AA is denying any libvirt processes.

---

### Post by moffa on 2015-09-08
I added the line ```
 /var/lib/libvirt/qemu/nvram** rw,
``` and it does seem to boot.

Thank you so much. I was thinking it was file permissions.  I don't know anything about apparmor so did I add the line correctly?

---

### Post by T.J. on 2015-09-08
Since it is likely that a VM will never access the hardware directly, would someone please clue me in?  I feel like I am missing something. I do not understand why anyone would want to use UEFI instead of a standard BIOS module in a VM at the present time - for Windows at least.  A BIOS module is probably a lot less buggy.
 
I admit that I am new at VGA passthrough, but if I might say so, it has also been my experience that virt-manager tells me that it is seriously behind the bundled version of qemu, especially in exposing the switches needed for successful passthrough and gaming. I know a lot of people like the convenience of virt-manager, but I had to abandon it to get pass-through working correctly. I'm happy to leave virt-manager behind.   I've had a lot fewer headaches since.

Now I have a working VM of Windows 7, using an Nvidia GTX 960. =)

---

### Post by KillerKelvUK on 2015-09-09
> **moffa said:**
> I added the line ```
 /var/lib/libvirt/qemu/nvram** rw,
``` and it does seem to boot.

Thank you so much. I was thinking it was file permissions.  I don't know anything about apparmor so did I add the line correctly?

Sorry I'm useless with AppArmor issues, I've spent plenty of time trying to do what your doing and always end up just removing AppArmor altogether...this I guarantee will work ;)

---

### Post by redger on 2015-09-09
presumably you added that line to /etc/apparmor.d/abstractions/libvirt-qemu ... in which case you just allowed libvirt-qemu to access and write to files in the directory /var/lib/libvirt/qemu/nvram and all it contents and children

It seems pretty low risk since it appears to be a library named for .. and used by ... libvirt - for qemu operations

I'm not concerned - mind you, it's not my machine, easy for me to say :)

---

### Post by LaferriereJC on 2015-12-06
Spent the greater part of the weekend trying to get this up and running.  Running 14.04.03 server

Error starting domain: internal error: process exited while connecting to monitor: Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: vfio: No available IOMMU models
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: vfio: failed to setup container for group 11
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: vfio: failed to get group 11
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: Device initialization failed.
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: Device 'vfio-pci' could not be initialized


Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 117, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1162, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 866, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error: process exited while connecting to monitor: Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
Warning: path not on HugeTLBFS: /dev/hugepages/libvirt/qemu
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: vfio: No available IOMMU models
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: vfio: failed to setup container for group 11
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: vfio: failed to get group 11
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: Device initialization failed.
qemu-system-x86_64: -device vfio-pci,host=04:00.0,id=hostdev0,bus=pci.0,addr=0x6: Device 'vfio-pci' could not be initialized



Am I not supposed to mount /dev/hugepages? this guide here says something about mounting it, but I'm not sure if libvirt does it automatically.

[https://fedoraproject.org/wiki/Features/KVM_Huge_Page_Backed_Memory](https://fedoraproject.org/wiki/Features/KVM_Huge_Page_Backed_Memory)

here's output of my dmesg | grep AMD-Vi

root@ubu32c:/etc/init.d# dmesg | grep AMD-Vi
[    2.639262] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    2.639264] AMD-Vi: Found IOMMU at 0000:40:00.2 cap 0x40
[    2.639266] AMD-Vi: Interrupt remapping enabled
[    2.658070] AMD-Vi: Lazy IO/TLB flushing enabled

relevant lspci -nn

04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X] [1002:6658]
04:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:aac0]

find /sys/kernel/iommu_groups/ -type l

/sys/kernel/iommu_groups/0/devices/0000:00:00.0
/sys/kernel/iommu_groups/1/devices/0000:00:02.0
/sys/kernel/iommu_groups/2/devices/0000:00:0b.0
/sys/kernel/iommu_groups/3/devices/0000:00:0d.0
/sys/kernel/iommu_groups/4/devices/0000:00:11.0
/sys/kernel/iommu_groups/5/devices/0000:00:12.0
/sys/kernel/iommu_groups/5/devices/0000:00:12.1
/sys/kernel/iommu_groups/5/devices/0000:00:12.2
/sys/kernel/iommu_groups/6/devices/0000:00:13.0
/sys/kernel/iommu_groups/6/devices/0000:00:13.1
/sys/kernel/iommu_groups/6/devices/0000:00:13.2
/sys/kernel/iommu_groups/7/devices/0000:00:14.0
/sys/kernel/iommu_groups/8/devices/0000:00:14.3
/sys/kernel/iommu_groups/9/devices/0000:00:14.4
/sys/kernel/iommu_groups/9/devices/0000:01:04.0
/sys/kernel/iommu_groups/10/devices/0000:00:14.5
/sys/kernel/iommu_groups/11/devices/0000:04:00.0
/sys/kernel/iommu_groups/11/devices/0000:04:00.1
/sys/kernel/iommu_groups/12/devices/0000:03:00.0
/sys/kernel/iommu_groups/13/devices/0000:02:00.0
/sys/kernel/iommu_groups/13/devices/0000:02:00.1
/sys/kernel/iommu_groups/14/devices/0000:40:00.0
/sys/kernel/iommu_groups/15/devices/0000:40:02.0
/sys/kernel/iommu_groups/16/devices/0000:40:04.0
/sys/kernel/iommu_groups/17/devices/0000:40:0b.0
/sys/kernel/iommu_groups/18/devices/0000:44:00.0
/sys/kernel/iommu_groups/19/devices/0000:43:00.0
/sys/kernel/iommu_groups/20/devices/0000:41:00.0
/sys/kernel/iommu_groups/20/devices/0000:42:04.0

cgroup_device_acl = [
    "/dev/null", "/dev/full", "/dev/zero",
    "/dev/random", "/dev/urandom",
    "/dev/ptmx", "/dev/kvm", "/dev/kqemu",
    "/dev/rtc","/dev/hpet", "/dev/vfio/vfio",
    "/dev/vfio/11", "/dev/vfio/20",
    "/dev/shm", "/root/.config/pulse", "/dev/snd",
]

**note: /dev/vfio does not have any entries** other than /dev/vfio/vfio edit: actually, I do have an 11 now.  Odd, I didn't before.  I ran the script mentioned in the second post on page 1.  The vfio_bind scripts, so maybe that's what created grouping 11.

I tried

 setting KVM_HUGEPAGES=1 in the file /etc/default/qemu-kvm and restart.

still no go

**Update: apparently there is a bug** damnit... still no go 

[https://bugs.launchpad.net/ubuntu/vivid/+source/qemu/+bug/1461012](https://bugs.launchpad.net/ubuntu/vivid/+source/qemu/+bug/1461012)
"
I've investigated this issue in Willy:

Hugepages are now mounted on /dev/hugepages and not in /run/hugepages

And also libvirt wants to use /dev/hugepages and more precisely /dev/hugepages/libvirt/qemu (so without the kvm in the middle of the path)

This means, the apparmor rule for huge pages points to the wrong path. The following change should be made in the profile /etc/apparmor.d/abstractions/libvirt-qemu
remove: owner "/run/hugepages/kvm/libvirt/qemu/**" rw,
add: owner "/dev/hugepages/libvirt/qemu/**" rw,

(reload the profile with service apparmor reload)

I had to create this path with the right owner-rights like this:
mkdir -p /dev/hugepages/libvirt/qemu
chown libvirt-qemu:kvm /dev/hugepages/libvirt/qemu

Now hugepages works again...

Please pay attention to the fact that in /usr/share/qemu/init/qemu-kvm-init the mountpoint /run/hugepages is created and mounted but apparently, this isn't useful any more (to my opinion)...
"

---

### Post by ragora2 on 2015-12-09
I've got it working on a [COLOR=#000000][FONT=Arial]Asus M5A99X EVO R2.0 with a [/FONT][/COLOR][COLOR=#000000][FONT=Arial]NVidia GT 630 for my host GPU and a NVidia GTX 660 for my pass-thru GPU for both Windows 10 64bit and Linux Mint 64bit. However, both guests exhibit extreme CPU performance detriments (Cinebench CPU tests have been getting scores as low as 270) and very often the software using the GPU is bottlenecking to the point that the GTX 660 is almost completely useless. I am using hugepages (4GB, 8GB physical memory), using taskset to lock QEMU to specific cores, using virtio for HDD & network and nothing seems to want to work. Under Windows across a 140 second sample taken by Sleepy in Tribes 2 (a game released 2001) during a 20 FPS choke indicates that literally 98% of my game time is spent in ntdll or User32 dealing with RtlSetCurrentTransaction or BaseThreadInitThunk. Everything else looks good, relatively speaking. All other games exhibit some form of this extreme detriment, BattleZone 2 would operate fine but at 300 FPS max without vsync (when the 660 was running as my host GPU, I scored 500+ regularly). So, I'm not really sure what's wrong with my config at this point but here's the full setup:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Processor: AMD FX-8350
RAM: G. Skill Ripjaws 2x4GB
Motherboard: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Asus M5A99X EVO R2.0 
Host GPU: NVidia GT 630
Pass-Thru GPU: NVidia GTX 660
Host Operating System: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Linux Mint 17.2 Rafaela
Kernel Version: 3.19.8 Custom (a slimmed down kernel build for this system)
QEMU Version: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]2.4.1 GIT build
[/FONT][/COLOR]
QEMU VM Config:
[CENTER][COLOR=#000000][FONT=Arial]
[LIST]
[*=left]VirtIO HDD
[*=left]VirtIO Network
[*=left]VFIO GPU Pass-Thru
[*=left]pc-q35-2.4 / pc-i440fx-2.4  (Both exhibit roughly the same performance)
[*=left]QEMU & all threads bound to cores 0-3
[*=left]Hugepages 4GB
[*=left]Host flag invtsc disabled
[/LIST]
[/FONT][/COLOR][/CENTER]

I've been doing a lot of screwing around to no avail. Wonder if anyone here has any idea.

**Edit:**

Turns out I just had to disable EPT. (Well, NPT for AMD) Now the VM can run Crysis 2 on Ultra settings with no lag.

---

### Post by TGiFallen on 2015-12-29
Hello and thank you for the tutorial. between it, another tutorial and a friend I was able to get mine working. Though I am wondering, what is the difference between the two first posts?

---

### Post by zloe on 2016-01-12
Hello!
I'm playing via KVM (OVMF, pci-stub, nvidia 970, spyos10) and periodicity getting micro freezes and sound crackles, especially under heavy loads.
Kernel is stock, pulseaudio config is almost stock (and sound in linux works well), sound card is generic USB, vm config is q35 and hda. Guest drivers is default.
I was tried to passthrough sound card but it works terrible.
Any ideas how to fix it?

My VM config (no libvirt, just qemu):
```

#!/bin/sh
sudo qemu-system-x86_64 \
        -nodefaults \
        -nodefconfig \
        -nographic \
        -serial none \
        -parallel none \
        -name fail10 \
        -machine q35,accel=kvm \
        -enable-kvm \
        -cpu host,kvm=off,check \
        -smp cpus=4,sockets=1,cores=4,threads=1 \
        -m 8G \
        -balloon virtio \
        -rtc base=localtime,clock=host \
        -drive if=pflash,format=raw,readonly,file=/opt/vm/OVMF-pure-efi.fd \
        -drive if=pflash,format=raw,file=/opt/vm/OVMF_VARS-pure-efi.fd \
        -soundhw hda \
        -device virtio-net-pci,netdev=virt0,mac=FA:KE:MA:C0:HE:RE  -netdev tap,id=virt0 \
        -vga none \
        -device vfio-pci,host=01:00.0,multifunction=on \
        -device vfio-pci,host=01:00.1 \
        -usb \
        -drive file=/opt/vm/fail10/fail10_HD0.qcow2,if=virtio,format=qcow2,index=1,media=disk,cache=none,aio=native \
        -boot order=a \
        -monitor stdio \
        -qmp tcp:localhost:4444,server,nowait \
        "$@"

```

**UPD: **fixed after kernel update. Linux is so linux.

---

### Post by razing32 on 2016-02-11
Tried this guide myself.

Got about as far as the libvirt daemon and manager.

Strangely after configuring apparmor I could not start the service - as if the system did not know what it was.

Then , when I start the daemon using "sudo service libvirt-bin start" I grep for it right away but the only thing in ps aux output is my own grep.

Finally , virt-manager gives a permission error on trying to create a socket:
> 
Unable to connect to libvirt.

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group

Unable to connect to libvirt.

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group

Libvirt URI is: qemu:///system

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 1027, in _open_thread
    self.vmm = self._try_open()
  File "/usr/share/virt-manager/virtManager/connection.py", line 1009, in _try_open
    flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 105, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory



If anyone has run into similar issues and has some advice I would greatly appreciate it.

---

### Post by KillerKelvUK on 2016-02-11
@razing32....forget virt-manager for now... just stick with libvirt & virsh.  Have you checked your dmesg/syslog outputs...if you're manually trying to start the libvirt-bin process and you can't see it running afterwards I'd suggest you should have error logs somewhere? (/var/log/syslog)

What is returned when you manually start the service, can you post back the command and output?

What happens with you issue a 'virsh list --all' command

---

### Post by razing32 on 2016-02-11
> **KillerKelvUK said:**
> @razing32....forget virt-manager for now... just stick with libvirt & virsh.  Have you checked your dmesg/syslog outputs...if you're manually trying to start the libvirt-bin process and you can't see it running afterwards I'd suggest you should have error logs somewhere? (/var/log/syslog)

What is returned when you manually start the service, can you post back the command and output?

What happens with you issue a 'virsh list --all' command

Dmesg provides the following :

> [70003.510879] init: libvirt-bin main process ended, respawning
[70013.266013] init: libvirt-bin post-start process (7639) terminated with status 1
[70018.876656] init: libvirt-bin main process ended, respawning
[70028.615817] init: libvirt-bin post-start process (7719) terminated with status 1

Syslog the following :

> Feb 11 19:30:51 razing-mintBA kernel: [70003.510879] init: libvirt-bin main process ended, respawning
Feb 11 19:31:01 razing-mintBA kernel: [70013.266013] init: libvirt-bin post-start process (7639) terminated with status 1
Feb 11 19:31:06 razing-mintBA kernel: [70018.876656] init: libvirt-bin main process ended, respawning
Feb 11 19:31:16 razing-mintBA kernel: [70028.615817] init: libvirt-bin post-start process (7719) terminated with status 1



The commands provides the following :
> 
**razing@razing-mintBA ~ $ **sudo service libvirt-bin start
libvirt-bin stop/post-start, (post-start) process 7719

> 
**razing@razing-mintBA ~ $** virsh list --all
error: failed to connect to the hypervisor
error: no valid connection
error: Failed to connect socket to '/var/run/libvirt/libvirt-sock': No such file or directory

---

### Post by KillerKelvUK on 2016-02-11
Do you see any log messages about AppArmor denying the libvirt daemon...I'd be tempted to stop and unload AA and re-test.

---

### Post by razing32 on 2016-02-11
> **KillerKelvUK said:**
> Do you see any log messages about AppArmor denying the libvirt daemon...I'd be tempted to stop and unload AA and re-test.

That's the thing.
I did setup the "/etc/apparmor.d/abstractions/libvirt-qemu" config and I clearly have configs for apparmor in the "apparmor.d" folder.
However , when I try to stop the bloody thing :

> **razing@razing-mintBA ~ $** /etc/init.d/apparmor stop
bash: /etc/init.d/apparmor: No such file or directory

> **razing@razing-mintBA ~ $** sudo invoke-rc.d apparmor reload
invoke-rc.d: unknown initscript, /etc/init.d/apparmor not found.

> **razing@razing-mintBA ~ $ **apparmor_status
The program 'apparmor_status' is currently not installed. You can install it by typing:
[COLOR=#ff0000]sudo apt-get install apparmor[/COLOR]


---

### Post by KillerKelvUK on 2016-02-13
Whats your output for 'dpkg -l | grep apparmor'?

---

### Post by razing32 on 2016-02-13
> **KillerKelvUK said:**
> Whats your output for 'dpkg -l | grep apparmor'?


razing@razing-mintBA ~ $ dpkg -l | grep apparmor
ii  libapparmor1:amd64                          2.8.95~2430-0ubuntu5.3                              amd64        changehat AppArmor library

---

### Post by KillerKelvUK on 2016-02-14
Have I got this right, you setup libvirt including the apparmor profiles but didn't have apparmor installed?  Or have things moved around a bit since?

Have you build libvirt yourself or installing from ppa?

I'm no linux guru here but I'd say install apparmor so that is functioning properly and then see if you get any error messages that help debug libvirt?  Thinking maybe somehow libvirt is being hampered by the profiles you configured but as the main daemon isn't installed there aren't any log outs showing denied or otherwise? #longshot

---

### Post by hermes5 on 2016-02-15
Hi everyone,

I'm currently attempting to apply the i915 patch and I'm getting failure several times throughout the patch.

> ~/kernels/linux$ patch -p1 < i915_arbiter.patch
patching file drivers/gpu/drm/i915/i915_dma.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 378 (offset -928 lines).                                                                                                                                                              
Hunk #2 succeeded at 424 with fuzz 2 (offset -945 lines).                                                                                                                                                  
patching file drivers/gpu/drm/i915/i915_drv.h                                                                                                                                                              
Hunk #1 FAILED at 2080.                                                                                                                                                                                    
1 out of 1 hunk FAILED -- saving rejects to file drivers/gpu/drm/i915/i915_drv.h.rej                                                                                                                       
patching file drivers/gpu/drm/i915/i915_params.c                                                                                                                                                           
Hunk #1 FAILED at 47.                                                                                                                                                                                      
Hunk #2 FAILED at 152.                                                                                                                                                                                     
2 out of 2 hunks FAILED -- saving rejects to file drivers/gpu/drm/i915/i915_params.c.rej                                                                                                                   
patching file drivers/gpu/drm/i915/intel_display.c                                                                                                                                                         
Hunk #1 succeeded at 14879 with fuzz 1 (offset 3595 lines).                                                                                                                                                
Hunk #2 FAILED at 11621.                                                                                                                                                                                   
Hunk #3 succeeded at 15583 with fuzz 2 (offset 3708 lines).                                                                                                                                                
1 out of 3 hunks FAILED -- saving rejects to file drivers/gpu/drm/i915/intel_display.c.rej                                                                                                                 
patching file drivers/gpu/drm/i915/intel_drv.h                                                                                                                                                             
Hunk #1 succeeded at 1478 with fuzz 2 (offset 544 lines).                                                                                                                                                  
patching file include/linux/vgaarb.h                                                                                                                                                                       
Hunk #1 FAILED at 65.                                                                                                                                                                                      
patch unexpectedly ends in middle of line                                                                                                                                                                  
1 out of 1 hunk FAILED -- saving rejects to file include/linux/vgaarb.h.rej                                                                                                                                
patch unexpectedly ends in middle of line   


To be honest, I have no idea how to fix this =/ I'm attempting to patch kernel 4.4.1 any ideas?

---

### Post by ubuserone on 2016-03-27
I had similar hardware of yours but would it be better for new attempt to create a new thread or to post here for help ?
Since there are tons of changes on kernal and etc on 14.04.

---

### Post by ubuserone on 2016-03-29
Not getting a reply , just make me think it maybe a hard way for me to go through it. I will open a new thread since there is no reply here.

---

### Post by znprapra on 2016-11-22
Hi.
Please someone can help me with gpu passtrough?
I'm on slackware 14.2,i use libvirt and qemu 2.7
my cards are nvidia(host) and ati hd(for guest)
I have installed windows 81 as guest,using the ati drivers
and connected to vga port of my tv.
The output is ok,3d works
But I want to use the gpu card via vnc
on my linux screen.
I know is possible,at least on this video

[https://www.youtube.com/watch?v=Qi1LdFkRzIs](https://www.youtube.com/watch?v=Qi1LdFkRzIs)

I have setup vnc but result is a little different..

[IMG]https://s14.postimg.org/ihp1okt6p/ricevuta_ram5.jpg[/IMG]

Someone have some suggestion to get gpu monitor via vnc like the youtube video?
Thanks

This is my xml machine libvirt

 ```
<name>win8.1</name>
  <uuid>87fb7bb3-b073-46d6-bafc-c94fbe4b76bf</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>2</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-i440fx-2.7'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
    <vmport state='off'/>
  </features>
  <cpu mode='host-model'>
    <model fallback='allow'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2' cache='unsafe' io='threads'/>
      <source file='/home/giuseppe/.local/libvirt/images/win7.qcow2'/>
      <backingStore/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <alias name='ide0-0-1'/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='sda' bus='sata'/>
      <readonly/>
      <alias name='sata0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='floppy'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='fda' bus='fdc'/>
      <alias name='fdc0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/win8.1.qcow2'/>
      <backingStore/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <alias name='usb'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <alias name='usb'/>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <alias name='usb'/>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <alias name='usb'/>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'>
      <alias name='pci.0'/>
    </controller>
    <controller type='ide' index='0'>
      <alias name='ide'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <alias name='virtio-serial0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <controller type='fdc' index='0'>
      <alias name='fdc0'/>
    </controller>
    <controller type='sata' index='0'>
      <alias name='sata0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address=':**:**::**::**::**:**:**'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='e1000'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/1'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/1'>
      <source path='/dev/pts/1'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0' state='connected'/>
      <alias name='channel0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='tablet' bus='usb'>
      <alias name='input0'/>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'>
      <alias name='input1'/>
    </input>
    <input type='keyboard' bus='ps2'>
      <alias name='input2'/>
    </input>
    <graphics type='vnc' port='5900' autoport='yes' listen='127.0.0.1' keymap='it'>
      <listen type='address' address='127.0.0.1'/>
    </graphics>
    <sound model='ac97'>
      <alias name='sound0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x06' slot='0x00' function='0x0'/>
      </source>
      <alias name='hostdev0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x06' slot='0x00' function='0x1'/>
      </source>
      <alias name='hostdev1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x046d'/>
        <product id='0xc21a'/>
        <address bus='4' device='2'/>
      </source>
      <alias name='hostdev2'/>
      <address type='usb' bus='0' port='4'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
      <alias name='redir0'/>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <alias name='redir1'/>
      <address type='usb' bus='0' port='3'/>
    </redirdev>
    <memballoon model='virtio'>
      <stats period='5'/>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='none' model='none'/>
  <seclabel type='dynamic' model='dac' relabel='yes'>
    <label>+0:+100</label>
    <imagelabel>+0:+100</imagelabel>
  </seclabel>
</domain>

giuseppe@slack64:/home/giuseppe$ virsh dumpxml win8.1
<domain type='kvm' id='3'>
  <name>win8.1</name>
  <uuid>87fb7bb3-b073-46d6-bafc-c94fbe4b76bf</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>2</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-i440fx-2.7'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
    <vmport state='off'/>
  </features>
  <cpu mode='host-model'>
    <model fallback='allow'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2' cache='unsafe' io='threads'/>
      <source file='/home/giuseppe/.local/libvirt/images/win7.qcow2'/>
      <backingStore/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <alias name='ide0-0-1'/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='sda' bus='sata'/>
      <readonly/>
      <alias name='sata0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='floppy'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='fda' bus='fdc'/>
      <alias name='fdc0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/win8.1.qcow2'/>
      <backingStore/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <alias name='usb'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <alias name='usb'/>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <alias name='usb'/>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <alias name='usb'/>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'>
      <alias name='pci.0'/>
    </controller>
    <controller type='ide' index='0'>
      <alias name='ide'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <alias name='virtio-serial0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <controller type='fdc' index='0'>
      <alias name='fdc0'/>
    </controller>
    <controller type='sata' index='0'>
      <alias name='sata0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:5d:15:e6'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='e1000'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/1'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/1'>
      <source path='/dev/pts/1'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0' state='connected'/>
      <alias name='channel0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='tablet' bus='usb'>
      <alias name='input0'/>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'>
      <alias name='input1'/>
    </input>
    <input type='keyboard' bus='ps2'>
      <alias name='input2'/>
    </input>
    <graphics type='vnc' port='5900' autoport='yes' listen='127.0.0.1' keymap='it'>
      <listen type='address' address='127.0.0.1'/>
    </graphics>
    <sound model='ac97'>
      <alias name='sound0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x06' slot='0x00' function='0x0'/>
      </source>
      <alias name='hostdev0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x06' slot='0x00' function='0x1'/>
      </source>
      <alias name='hostdev1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x046d'/>
        <product id='0xc21a'/>
        <address bus='4' device='2'/>
      </source>
      <alias name='hostdev2'/>
      <address type='usb' bus='0' port='4'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
      <alias name='redir0'/>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <alias name='redir1'/>
      <address type='usb' bus='0' port='3'/>
    </redirdev>
    <memballoon model='virtio'>
      <stats period='5'/>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='none' model='none'/>
  <seclabel type='dynamic' model='dac' relabel='yes'>
    <label>+0:+100</label>
    <imagelabel>+0:+100</imagelabel>
  </seclabel>
</domain>

```

---

### Post by yanman on 2017-02-09
Hi all. I discovered this thread late in my quest (derp) but doing so got me over my last hurdle and I now have it working!!

I'd like to share what I did as it's slightly different from these instructions - if it can help anyone that is. Please correct any of my stupid mistakes though. I don't really understand most of this but have just pieced different bits together and experimented.

My setup:
Lenovo D30 (Intel C602 chipset) board with UEFI BIOS (for some reason the only label that works is "Windows Boot Manager" even for Ubuntu)
2 x Intel Xeon E2670
Ubuntu 16.10 (GNU/Linux 4.8.0-37-generic x86_64) booting in UEFI mode
Nvidia GTX1070

- Installed the packages mentioned in other guides
- Added the missing modules to /etc/modules
- Changed GRUB /etc/default/grub
```
GRUB_TIMEOUT=0
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"
```
- Manually installed OVMF as it didn't install correctly (apparently a bug, possibly?)
```
apt install ovmf
```
- Created a disk image and sparsify'd it:
```
dd if=/dev/zero of=/nvme/win10a_os.img bs=1M seek=120000 count=0
virt-sparsify -q --in-place /nvme/win10a_os.img 
```
- Now this is where I different from the Pugetsound guide and instead used some bits from Arch guides via Reddit. They were now using vfio-pci instead of pci-stub which is supposedly better.
  Initially I'd used pci-stub and defined the devices there, also having to blacklist nouvou. Having done that pci-stub correctly takes the devices. I've now done the same but with vfio:
```
$ cat /etc/modprobe.d/local.conf
options vfio-pci ids=10de:1b81,10de:10f0
$ lspci -nnk -d 10de:1b81
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP104 [GeForce GTX 1070] [10de:1b81] (rev a1)
        Subsystem: Gigabyte Technology Co., Ltd GP104 [GeForce GTX 1070] [1458:36fc]
        Kernel driver in use: vfio-pci
        Kernel modules: nvidiafb, nouveau
```
- I also had a few things to get around the new Nvidia error 43
- And lastly I had to update apparmor to allow vfio

There's a few things I also did I just want to confirm first are actually required and then I'll update. One was to add a grub line to block the frame buffer, and another was to load a vBIOS in libvirtd for the GPU. Since other users have mentioned they didn't need these I'll test to make sure.

---

### Post by ODTech on 2017-02-09
Just sharing my success story and setup.
I also didn't follow one guide but i initialy got it working using the pudget systems guide for ubuntu 14.04. I had issues with my non uefi GTX670 which i eventualy fixed by flashing it with a official Gigabyte uefi bios. The problem was between the gpu and my sata controller.

Host
MSI Z97A Gaming 9 ACK Motherboard
ADATA 1600L 6Gig RAM
Kingston SV300 128Gig SSD
Intel i7-4790 2Cores 2 Threads
Corsair GS700 PSU
Intel IGP (Changing to GTX 670 soon)
2 x 24" Display
Linux Mint 18.1 with kernel 4.9 

Guest
Qemu KVM and OVMF repo version
ADATA 1600L 10Gig RAM
Sunix SATA2600 2 Port SATA6G PCI-e Controller Marvel Chipset  (Can not boot a windows drive through this if you are using Seabios. Must use OVMF)
^Samsung 850 Evo 256Gig SSD
^^Seagate 3TB HDD
Intel i7-4790 2Cores 2 Threads
Gigabyte GTX670 2Gig Windforce 3 (Changing to GTX 980 soon)
Windows 10 Home 64 bit build 1607
NVIDIA Driver Version 378.49
Sunix 2 Port USB 3.0 Pci-E Card Renesas chipset
^USB 2 4xPort Hub (XBox 360 Controller, WLess MS Keyboard and Mouse, CMedia USB Sound Card)
^^J5 Create USB3.0 3xPort HuB with integrated Gigabit LAN (USB 3.0 External HDD adapter)
Cheapie 27" Telefunken Display

I've got the VM screen and input to a 90 degree angle from my "work" desk so i can just pick up the controller and turn ^^

My script. I couldn't get vfio to work so i claim with pci-stub then with the startup script the devices gets passed to vfio.

```
#!/bin/bash

configfile=/etc/vfio-pci1.cfg

vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id

}

modprobe vfio-pci

cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done

cp /usr/share/ovmf/OVMF.fd /tmp/my_vars.fd

qemu-system-x86_64 \
  -machine type=q35,accel=kvm \
  -cpu host,kvm=off \
  -smp 4,sockets=1,cores=2,threads=2 \
  -enable-kvm \
  -m 10G \
  -mem-path /run/hugepages/kvm \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=localtime \
  -vga none \
  -nographic \
  -serial none \
  -parallel none \
  -usb -usbdevice host:045e:0745 \
  -device vfio-pci,host=02:00.0,multifunction=on \
  -device vfio-pci,host=02:00.1 \
  -device vfio-pci,host=09:00.0 \
  -device vfio-pci,host=0b:00.0 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/ovmf/OVMF.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=dc

   exit 0
fi
```

---

### Post by yanman on 2017-02-25
I have to retract my earlier statement - It's still not stable and I'm pretty much ready to throw in the towel :(

I thought it was all going well but then I had some complete lock-ups - afterward the host was even offline. I managed to get the host to come back after a hard power off but the VM was hosed from then on, possibly in the EFI config? I tried rebuilding it and that was also fine for a while but then again the lock up, and this time every time I tried to reboot the VM it'd hang the host.

I'm going to go back over the initial instructions and try and do it exactly, then I'll point out anything I come across.

Some point about mine though:
- I'm using 16.10
- Using VFIO instead of pci-stub
- For some reason (newer version?) I have to have an NVRAM section in my OVMF section. I wondered why it was working without renaming it but it seems to have autogenerated the VARS file:

```
  <os>
    <type arch='x86_64' machine='pc-i440fx-yakkety'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/qemu/OVMF-win10a.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/win10a_VARS.fd</nvram>
    <bootmenu enable='no'/>
```

If my system *was* running fine for 24h and I was able to game - what would you suggest could be the cause of the crash? Given that pass-through worked fine initially.

---

### Post by KillerKelvUK on 2017-02-25
@yanman, difficult to offer you fix suggestions without any error logs, does the host not report any issues in the syslog (/var/log/syslog)?  You could also inspect the guest specific libvirt logs, they are stored in /var/log/libvirt/qemu/*name*-of-*guest*.

Regards OVMF there are few different flavours for different reasons, having a separate VARS file per guest which is specified in the nvram line of your XML is normal behaviour for Libvirt.  Other guides maybe referring to one of the OVMF flavours that combines the main loader and VARS file into one, this isn't practical however for running many different guests hence libvirt handling it the way you've noticed.

My experiences of working with passthrough (3+ years now)...
[LIST]
[*]USB device assignment is buggy (could be my hardware but lots of forum posts and bugs raised from others so...).  For me my Windows 10 vm would sometimes not boot with a USB drive attached, stability has improved with the later Ubuntu and kernel releases but if in doubt..take 'em out.
[*]Maybe about once every two weeks, sometimes more sometimes less I need to fully reboot the host to recover stability, guest boot fails and host logs complaining about DMAR exceptions. The message here is to expect this as by-product of passthrough although its probable other forum users may say they have better stability, truth is your experiences will be specific to your hardware and configurations.
[/LIST]

Maybe one more targeted recommendation but which would normally be informed by your error logs is to update your /etc/modprobe.d/local.conf file to incorporate the following additional lines...

```

options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio_iommu_type1 allow_unsafe_interrupts=1
softdep nouveau pre: vfio-pci

```

'ignore_msrs' makes your host more tolerant of your guest attempting to use some CPU features that aren't present or supported in kvm/qemu.
'allow_unsage_assigned_interrupts' is similar to the above but for interrupt remapping.  Its unlikely you need this as your guest is/has been working and you'd have logout somewhere specifically calling this out.
'allow_unsafe_interrupts' is the same as what you have added to your grub line, I'd recommend adding them all here though so you have all these modifications together in one place (means you can ditch the edits to your grub file apart of the intel_iommu=on).
'softdep nouveau pre: vfio-pci' this line attempts to ensure the vfio-pci module loads before the nouveau module so as to ensure vfio claims your passthrough hardware before nouveau does.  I don't believe you have a problem with this but having this line there won't hurt.

Remember to 'update-initramfs -u' after you make any changes to modprobes configuration files.

---

### Post by yanman on 2017-02-25
> **KillerKelvUK said:**
> @yanman, difficult to offer you fix suggestions without any error logs, does the host not report any issues in the syslog (/var/log/syslog)?  You could also inspect the guest specific libvirt logs, they are stored in /var/log/libvirt/qemu/*name*-of-*guest*.

Regards OVMF there are few different flavours for different reasons, having a separate VARS file per guest which is specified in the nvram line of your XML is normal behaviour for Libvirt.  Other guides maybe referring to one of the OVMF flavours that combines the main loader and VARS file into one, this isn't practical however for running many different guests hence libvirt handling it the way you've noticed.

My experiences of working with passthrough (3+ years now)...
[LIST]
[*]USB device assignment is buggy (could be my hardware but lots of forum posts and bugs raised from others so...).  For me my Windows 10 vm would sometimes not boot with a USB drive attached, stability has improved with the later Ubuntu and kernel releases but if in doubt..take 'em out.
[*]Maybe about once every two weeks, sometimes more sometimes less I need to fully reboot the host to recover stability, guest boot fails and host logs complaining about DMAR exceptions. The message here is to expect this as by-product of passthrough although its probable other forum users may say they have better stability, truth is your experiences will be specific to your hardware and configurations.
[/LIST]

Maybe one more targeted recommendation but which would normally be informed by your error logs is to update your /etc/modprobe.d/local.conf file to incorporate the following additional lines...

```

options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio_iommu_type1 allow_unsafe_interrupts=1
softdep nouveau pre: vfio-pci

```

'ignore_msrs' makes your host more tolerant of your guest attempting to use some CPU features that aren't present or supported in kvm/qemu.
'allow_unsage_assigned_interrupts' is similar to the above but for interrupt remapping.  Its unlikely you need this as your guest is/has been working and you'd have logout somewhere specifically calling this out.
'allow_unsafe_interrupts' is the same as what you have added to your grub line, I'd recommend adding them all here though so you have all these modifications together in one place (means you can ditch the edits to your grub file apart of the intel_iommu=on).
'softdep nouveau pre: vfio-pci' this line attempts to ensure the vfio-pci module loads before the nouveau module so as to ensure vfio claims your passthrough hardware before nouveau does.  I don't believe you have a problem with this but having this line there won't hurt.

Remember to 'update-initramfs -u' after you make any changes to modprobes configuration files.
Thanks for the reply mate. It's funny even tho after a long day of fails I'm ready to just throw it out and go a regular build, I get some tendril of hope and can't wait to keep trying =D

To answer your question first - I don't see a lot of logs. Here's what syslog shows:

```
Feb 26 00:23:43 			Last significant 5 minutes prior to crash

Feb 26 00:23:43 lensvr kernel: [ 7637.741525] audit_printk_skb: 12 callbacks suppressed
Feb 26 00:23:43 lensvr kernel: [ 7637.741528] audit: type=1400 audit(1488029023.966:1098): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14064/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:23:44 lensvr kernel: [ 7638.192986] audit: type=1400 audit(1488029024.418:1099): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14067/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:24:42 lensvr kernel: [ 7695.898836] audit: type=1400 audit(1488029082.123:1100): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14124/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:25:23 lensvr kernel: [ 7737.552019] audit: type=1400 audit(1488029123.779:1101): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14149/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:25:26 lensvr kernel: [ 7740.630751] audit: type=1400 audit(1488029126.855:1102): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14155/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:25:26 lensvr kernel: [ 7740.631094] audit: type=1400 audit(1488029126.855:1103): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14156/comm" pid=14155 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.043415] audit: type=1400 audit(1488029169.268:1104): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.043468] audit: type=1400 audit(1488029169.268:1105): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.043524] audit: type=1400 audit(1488029169.268:1106): apparmor="ALLOWED" operation="truncate" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.047765] audit: type=1400 audit(1488029169.272:1107): apparmor="ALLOWED" operation="unlink" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="d" denied_mask="d" fsuid=0 ouid=0
Feb 26 00:27:01 lensvr CRON[14216]: (root) CMD (if test -x /usr/sbin/apticron; then /usr/sbin/apticron --cron; else true; fi)
Feb 26 00:27:20 lensvr kernel: [ 7854.043572] audit: type=1400 audit(1488029240.269:1108): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14230/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.043677] audit: type=1400 audit(1488029240.269:1109): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14231/comm" pid=14230 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.044545] audit: type=1400 audit(1488029240.269:1110): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14232/comm" pid=14231 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.044943] audit: type=1400 audit(1488029240.269:1111): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14233/comm" pid=14232 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045302] audit: type=1400 audit(1488029240.269:1112): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14234/comm" pid=14233 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045473] audit: type=1400 audit(1488029240.269:1113): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14235/comm" pid=14234 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045622] audit: type=1400 audit(1488029240.273:1114): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14237/comm" pid=14235 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045747] audit: type=1400 audit(1488029240.273:1115): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14238/comm" pid=14237 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.046148] audit: type=1400 audit(1488029240.273:1116): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14239/comm" pid=14238 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.046441] audit: type=1400 audit(1488029240.273:1117): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14240/comm" pid=14239 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:57 lensvr kernel: [ 7890.889992] audit_printk_skb: 39 callbacks suppressed
Feb 26 00:27:57 lensvr kernel: [ 7890.889996] audit: type=1400 audit(1488029277.117:1131): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
Feb 26 00:27:57 lensvr kernel: [ 7890.890032] audit: type=1400 audit(1488029277.117:1132): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0
Feb 26 00:27:57 lensvr kernel: [ 7890.890093] audit: type=1400 audit(1488029277.117:1133): apparmor="ALLOWED" operation="truncate" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 26 00:28:07 lensvr kernel: [ 7901.567265] audit: type=1400 audit(1488029287.794:1134): apparmor="ALLOWED" operation="unlink" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="d" denied_mask="d" fsuid=0 ouid=0

Sun Feb 26 00:35:15 2017		Hard power-off after lockup. Prior to this I was making the MSI change. I did 3:00.1 first (the 1070's HDMI Audio) rebooted - worked ok. So I proceeded to enable the 3:00.0 (1070) and 7:00.0 (NEC USB3 onboard controller) then rebooted. I then started doing some installs, copying some files and  randomly it locked up.

Feb 26 00:35:52 lensvr rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="3360" x-info="http://www.rsyslog.com"] start

```

Here's the domain XML file - another difference in mine vs most is I don't use kvm args

```
<domain type='kvm'>
  <name>win10a</name>
  <uuid>cf20aa5f-2bb9-4899-99bf-cd8174127439</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>8</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-yakkety'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/qemu/OVMF-win10a.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/win10a_VARS.fd</nvram>
    <bootmenu enable='no'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
      <vendor_id state='on' value='1234567890ab'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='host-passthrough'>
    <topology sockets='1' cores='4' threads='2'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/nvme/win10a_os.img'/>
      <target dev='vda' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/zp1/vm/win10a_temp.img'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:4f:0d:7d'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'>
      <listen type='address'/>
    </graphics>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
      </source>
      <rom bar='on' file='/home/user/gv1070bios.dump'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x03' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x07' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='1'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

Here's the virt domain logs.. nothing much there as far as I can see :( One interesting thing tho is that it doesn't seem to show the PCI pass-through device or the ROM..... ??

```
2017-02-25 12:18:08.267+0000: starting up libvirt version: 2.1.0, package: 1ubuntu9.1 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Thu, 01 Dec 2016 09:44:12 +0100), qemu version: 2.6.1 (Debian 1:2.6.1+dfsg-0ubuntu5.1), hostname: lensvr
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/qemu-system-x86_64 -name guest=win10a,debug-threads=on -S -object secret,id=masterKey0,format=raw,file=/var/lib/libvirt/qemu/domain-9-win10a/master-key.aes -machine pc-i440fx-yakkety,accel=kvm,usb=off -cpu host,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1fff,hv_vendor_id=1234567890ab,kvm=off -drive file=/usr/share/qemu/OVMF-win10a.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/win10a_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -realtime mlock=off -smp 8,sockets=1,cores=4,threads=2 -uuid cf20aa5f-2bb9-4899-99bf-cd8174127439 -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-9-win10a/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot strict=on -device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 -device lsi,id=scsi0,bus=pci.0,addr=0x5 -device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x7 -drive file=/nvme/win10a_os.img,format=raw,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x6,drive=drive-virtio-disk0,id=virtio-disk0 -drive file=/zp1/filestore/os-iso/Win10__install_feb17.iso,format=raw,if=none,id=drive-ide0-0-1,readonly=on -device ide-cd,bus=ide.0,unit=1,drive=drive-ide0-0-1,id=ide0-0-1,bootindex=1 -drive file=/home/virtio-win.iso,format=raw,if=none,id=drive-ide0-1-0,readonly=on -device ide-cd,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 -drive file=/home/virtio-win_amd64.vfd,format=raw,if=none,id=drive-fdc0-0-0 -global isa-fdc.driveA=drive-fdc0-0-0 -netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=28 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:4f:0d:7d,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -chardev spicevmc,id=charchannel0,name=vdagent -device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchannel0,id=channel0,name=com.redhat.spice.0 -vnc 127.0.0.1:0 -device qxl-vga,id=video0,ram_size=67108864,vram_size=67108864,vram64_size_mb=0,vgamem_mb=16,max_outputs=1,bus=pci.0,addr=0x2 -device intel-hda,id=sound0,bus=pci.0,addr=0x4 -device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 -chardev spicevmc,id=charredir0,name=usbredir -device usb-redir,chardev=charredir0,id=redir0,bus=usb.0,port=1 -chardev spicevmc,id=charredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1,bus=usb.0,port=2 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on
Domain id=9 is tainted: high-privileges
Domain id=9 is tainted: host-cpu
char device redirected to /dev/pts/1 (label charserial0)
2017-02-25T12:28:22.462410Z qemu-system-x86_64: terminating on signal 15 from pid 3772
2017-02-25 12:28:22.662+0000: shutting down
2017-02-25 12:28:37.528+0000: starting up libvirt version: 2.1.0, package: 1ubuntu9.1 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Thu, 01 Dec 2016 09:44:12 +0100), qemu version: 2.6.1 (Debian 1:2.6.1+dfsg-0ubuntu5.1), hostname: lensvr
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/qemu-system-x86_64 -name guest=win10a,debug-threads=on -S -object secret,id=masterKey0,format=raw,file=/var/lib/libvirt/qemu/domain-10-win10a/master-key.aes -machine pc-i440fx-yakkety,accel=kvm,usb=off -cpu host,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1fff,hv_vendor_id=1234567890ab,kvm=off -drive file=/usr/share/qemu/OVMF-win10a.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/win10a_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -realtime mlock=off -smp 8,sockets=1,cores=4,threads=2 -uuid cf20aa5f-2bb9-4899-99bf-cd8174127439 -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-10-win10a/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot menu=on,strict=on -device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 -device lsi,id=scsi0,bus=pci.0,addr=0x5 -device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x7 -drive file=/nvme/win10a_os.img,format=raw,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x6,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -drive file=/zp1/filestore/os-iso/Win10__install_feb17.iso,format=raw,if=none,id=drive-ide0-0-1,readonly=on -device ide-cd,bus=ide.0,unit=1,drive=drive-ide0-0-1,id=ide0-0-1 -drive file=/home/virtio-win.iso,format=raw,if=none,id=drive-ide0-1-0,readonly=on -device ide-cd,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 -drive file=/home/virtio-win_amd64.vfd,format=raw,if=none,id=drive-fdc0-0-0 -global isa-fdc.driveA=drive-fdc0-0-0 -netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=28 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:4f:0d:7d,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -chardev spicevmc,id=charchannel0,name=vdagent -device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchannel0,id=channel0,name=com.redhat.spice.0 -vnc 127.0.0.1:0 -device qxl-vga,id=video0,ram_size=67108864,vram_size=67108864,vram64_size_mb=0,vgamem_mb=16,max_outputs=1,bus=pci.0,addr=0x2 -device intel-hda,id=sound0,bus=pci.0,addr=0x4 -device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 -chardev spicevmc,id=charredir0,name=usbredir -device usb-redir,chardev=charredir0,id=redir0,bus=usb.0,port=1 -chardev spicevmc,id=charredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1,bus=usb.0,port=2 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on
Domain id=10 is tainted: high-privileges
Domain id=10 is tainted: host-cpu
char device redirected to /dev/pts/1 (label charserial0)
```

Here's the modprobe conf:
```
$ cat /etc/modprobe.d/local.conf
options vfio-pci ids=10de:1b81,10de:10f0,1033:0194

```

So last night before your reply I came across one more thing I tried, which didn't work but might be interesting if anyone else is affected. It was a bug id for kvm where they had similar behavior to mine - Win10 guests would crash and lock the entire host up. The bug was particular to rebooting which has happened for me, but not exclusively. A few times it's happened in game, others in Windows while doing installs/copys. The bug comments at the end referred to one solution of enabling MSI interrupt for the HDMI Audio device in Windows. Info here:

[https://bugs.launchpad.net/qemu/+bug/1580459](https://bugs.launchpad.net/qemu/+bug/1580459)

Instructions mention this as a fix which I tried:

[http://lime-technology.com/wiki/index.php/UnRAID_6/VM_Guest_Support#Enable_MSI_for_Interrupts_to_Fix_HDMI_Audio_Support](http://lime-technology.com/wiki/index.php/UnRAID_6/VM_Guest_Support#Enable_MSI_for_Interrupts_to_Fix_HDMI_Audio_Support)
[http://forums.guru3d.com/showthread.php?t=378044](http://forums.guru3d.com/showthread.php?t=378044)

So to summarise, my method for creating the last VM was:

- Delete the old VM (leaving the drive img file)
- Create new VM based on the VFIO guide and this guide where I don't attach the PCI devices intially.
  - RAM 8GB
  - CPU host-passthrough with specific topology
  - Set it to UEFI and 440 (using the latest OVMF file)
  - Let it start but quickly interrupt it and force-off
  - Edit it to add a CDROM for Win10 install ISO, another for the Virt-IO drivers
  - Add the VirtIO drive (win10a-os.img) as VirtIO (not SCSI - doesn't seem to work)
  - Set NIC to VirtIO
  - Change USB controller from USB2 to Hypervisor Default
  - Change Spice to VNC ... can't control the damn mouse :/
  - Edit in CLI to add the Hyper-V vendor, add kvm hidden bits
  - Boot - for some reason I have no EFI issue here, it just pops up the "Press any key to install..." prompt of the Win10 installer
  - Install Windows, adding the VirtIO drivers for NIC and VirtIO-SCSI
  - Shut it down, attach the GPU, GPU's HDMI Audio, and NEC USB controller with virt-manager
  - Edit in CLI to add the GPU's BIOS line
  - Boot, install NVIDIA drivers... seems ok at this point (connected via HDMI since I haven't swapped the DVI off my temp laptop)
  - Shut down, clean up unnecessary devices, hook up my USB hub and DVI connection to GPU. Boot. Use until lockup :(

---

### Post by yanman on 2017-02-25
Just tried your suggested modprobe changes, rebooted, then tried to fire up the VM that locked up last night.

Interestingly I can still ping the host fine which is not usually the case - pings usually drop just after other services fairly quickly.

In this case the pings have been solid for 5 mins although my ssh and xRDP sessions dropped. All connections to the host seem down except ping.

I'm really curious to know what happens with that initial lock-up to render the guest so corrupt that any later attempt to fire it up either immediately locks the host up, or just becomes unrecoverable. Earlier ones were in a loop of booting into Windows recovery, but nothing would recover.

For this last VM i've been prepared tho =D I took a backup of the disk image which I'll use my BartPE bootable USB to restore from, even if I just restore the small system partitions like EFI. I also took a backup of the OVMF VARs, the domain XML .

This is the annoying part of having headless host. I can't tell if something is just blocking network attempts (beyond ping) or whether the host is seriously in a bad state, maybe 100% CPU but that doesn't seem likely given the steady pings.

[edit1] Interesting... 10 minutes later and the repeated <ENTER> I hit on my SSH shell came through! It's still completely unresponsive though but it hasn't closed the SSH session. So something is really hitting up some resources in some way?

[edit2] a few hours later and no change. Didn't see any more characters appearing on the SSH session even tho it still hasn't closed.
I ended up hard powering off again :(

Here's the logs I collected - looks like a bit more that time!
```
Feb 26 00:23:43 			Last significant 5 minutes prior to crash

Feb 26 00:23:43 lensvr kernel: [ 7637.741525] audit_printk_skb: 12 callbacks suppressed
Feb 26 00:23:43 lensvr kernel: [ 7637.741528] audit: type=1400 audit(1488029023.966:1098): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14064/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:23:44 lensvr kernel: [ 7638.192986] audit: type=1400 audit(1488029024.418:1099): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14067/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:24:42 lensvr kernel: [ 7695.898836] audit: type=1400 audit(1488029082.123:1100): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14124/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:25:23 lensvr kernel: [ 7737.552019] audit: type=1400 audit(1488029123.779:1101): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14149/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:25:26 lensvr kernel: [ 7740.630751] audit: type=1400 audit(1488029126.855:1102): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14155/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:25:26 lensvr kernel: [ 7740.631094] audit: type=1400 audit(1488029126.855:1103): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14156/comm" pid=14155 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.043415] audit: type=1400 audit(1488029169.268:1104): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.043468] audit: type=1400 audit(1488029169.268:1105): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.043524] audit: type=1400 audit(1488029169.268:1106): apparmor="ALLOWED" operation="truncate" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 26 00:26:09 lensvr kernel: [ 7783.047765] audit: type=1400 audit(1488029169.272:1107): apparmor="ALLOWED" operation="unlink" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14177" pid=14177 comm="lpqd" requested_mask="d" denied_mask="d" fsuid=0 ouid=0
Feb 26 00:27:01 lensvr CRON[14216]: (root) CMD (if test -x /usr/sbin/apticron; then /usr/sbin/apticron --cron; else true; fi)
Feb 26 00:27:20 lensvr kernel: [ 7854.043572] audit: type=1400 audit(1488029240.269:1108): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14230/comm" pid=12507 comm="qemu-system-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.043677] audit: type=1400 audit(1488029240.269:1109): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14231/comm" pid=14230 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.044545] audit: type=1400 audit(1488029240.269:1110): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14232/comm" pid=14231 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.044943] audit: type=1400 audit(1488029240.269:1111): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14233/comm" pid=14232 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045302] audit: type=1400 audit(1488029240.269:1112): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14234/comm" pid=14233 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045473] audit: type=1400 audit(1488029240.269:1113): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14235/comm" pid=14234 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045622] audit: type=1400 audit(1488029240.273:1114): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14237/comm" pid=14235 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.045747] audit: type=1400 audit(1488029240.273:1115): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14238/comm" pid=14237 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.046148] audit: type=1400 audit(1488029240.273:1116): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14239/comm" pid=14238 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:20 lensvr kernel: [ 7854.046441] audit: type=1400 audit(1488029240.273:1117): apparmor="ALLOWED" operation="open" profile="libvirt-cf20aa5f-2bb9-4899-99bf-cd8174127439" name="/proc/12507/task/14240/comm" pid=14239 comm="worker" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 26 00:27:57 lensvr kernel: [ 7890.889992] audit_printk_skb: 39 callbacks suppressed
Feb 26 00:27:57 lensvr kernel: [ 7890.889996] audit: type=1400 audit(1488029277.117:1131): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
Feb 26 00:27:57 lensvr kernel: [ 7890.890032] audit: type=1400 audit(1488029277.117:1132): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0
Feb 26 00:27:57 lensvr kernel: [ 7890.890093] audit: type=1400 audit(1488029277.117:1133): apparmor="ALLOWED" operation="truncate" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 26 00:28:07 lensvr kernel: [ 7901.567265] audit: type=1400 audit(1488029287.794:1134): apparmor="ALLOWED" operation="unlink" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/14278" pid=14278 comm="smbd" requested_mask="d" denied_mask="d" fsuid=0 ouid=0

Sun Feb 26 00:35:15 2017		Reboot

Feb 26 00:35:52 lensvr rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="3360" x-info="http://www.rsyslog.com"] start

Feb 25 15:55:05 lensvr systemd[6027]: Startup finished in 946ms.

Feb 25 15:57:16 lensvr kernel: [  202.385991] audit: type=1400 audit(1487998636.266:103): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" pid=6363 comm="apparmor_parser"
Feb 25 15:57:16 lensvr kernel: [  202.386299] audit: type=1400 audit(1487998636.266:104): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757//qemu_bridge_helper" pid=6363 co
mm="apparmor_parser"
Feb 25 15:57:16 lensvr systemd[1]: Started Virtual machine log manager.

Feb 25 15:57:16 lensvr libvirtd[3808]: Domain id=1 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: high-privileges
Feb 25 15:57:16 lensvr libvirtd[3808]: Domain id=1 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: host-cpu

Feb 25 15:57:16 lensvr kernel: [  203.117249] audit: type=1400 audit(1487998636.998:107): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6410/task/6425/comm" pid=6410 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 15:57:17 lensvr kernel: [  203.129471] audit: type=1400 audit(1487998637.010:108): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6410/task/6426/comm" pid=6410 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 15:57:17 lensvr kernel: [  203.139544] audit: type=1400 audit(1487998637.018:109): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6410/task/6427/comm" pid=6410 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 15:57:17 lensvr kernel: [  203.152504] audit: type=1400 audit(1487998637.030:110): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6410/task/6428/comm" pid=6410 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 15:57:17 lensvr kernel: [  203.161889] audit: type=1400 audit(1487998637.042:111): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6410/task/6429/comm" pid=6410 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 15:57:17 lensvr kernel: [  203.170823] audit: type=1400 audit(1487998637.050:112): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6410/task/6430/comm" pid=6410 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 15:57:19 lensvr kernel: [  205.168750] vfio_ecap_init: 0000:03:00.0 hiding ecap 0x19@0x900
Feb 25 15:57:19 lensvr kernel: [  205.192505] vfio-pci 0000:03:00.1: enabling device (0000 -> 0002)
Feb 25 15:57:20 lensvr libvirtd[3808]: host doesn't support hyperv 'relaxed' feature
Feb 25 15:57:20 lensvr libvirtd[3808]: host doesn't support hyperv 'vapic' feature
Feb 25 15:57:20 lensvr virtlogd[6364]: libvirt version: 2.1.0, package: 1ubuntu9.1 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Thu, 01 Dec 2016 09:44:12 +0100)
Feb 25 15:57:20 lensvr virtlogd[6364]: hostname: lensvr
Feb 25 15:57:20 lensvr virtlogd[6364]: End of file while reading data: Input/output error
Feb 25 15:57:26 lensvr kernel: [  212.382705] kvm: zapping shadow pages for mmio generation wraparound
Feb 25 15:57:26 lensvr kernel: [  212.511993] kvm: zapping shadow pages for mmio generation wraparound

Feb 25 16:01:09 lensvr libvirtd[3808]: Domain id=2 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: high-privileges
Feb 25 16:01:09 lensvr libvirtd[3808]: Domain id=2 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: host-cpu

Feb 25 16:01:11 lensvr kernel: [  437.493594] vfio_ecap_init: 0000:03:00.0 hiding ecap 0x19@0x900
Feb 25 16:01:12 lensvr libvirtd[3808]: host doesn't support hyperv 'relaxed' feature
Feb 25 16:01:12 lensvr libvirtd[3808]: host doesn't support hyperv 'vapic' feature
Feb 25 16:01:12 lensvr virtlogd[6364]: End of file while reading data: Input/output error

Feb 25 16:01:54 lensvr libvirtd[3808]: Domain id=3 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: high-privileges
Feb 25 16:01:54 lensvr libvirtd[3808]: Domain id=3 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: host-cpu

Feb 25 16:05:44 lensvr libvirtd[3808]: Failed to terminate process 7320 with SIGKILL: Device or resource busy

Feb 25 16:05:48 lensvr libvirtd[3808]: internal error: End of file from monitor

Feb 25 16:05:49 lensvr virtlogd[6364]: End of file while reading data: Input/output error

Feb 25 16:27:20 lensvr kernel: [    1.316583] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Feb 25 16:27:20 lensvr kernel: [    1.316586] ACPI: Power Button [PWRB]
Feb 25 16:27:20 lensvr kernel: [    1.316631] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Feb 25 16:27:20 lensvr kernel: [    1.316632] ACPI: Power Button [PWRF]

Feb 25 16:27:20 lensvr kernel: [   23.679396] VFIO - User Level meta-driver version: 0.3
Feb 25 16:27:20 lensvr kernel: [   23.689663] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Feb 25 16:27:20 lensvr kernel: [   23.707523] vfio_pci: add [10de:1b81[ffff:ffff]] class 0x000000/00000000
Feb 25 16:27:20 lensvr kernel: [   23.727605] vfio_pci: add [10de:10f0[ffff:ffff]] class 0x000000/00000000
Feb 25 16:27:20 lensvr kernel: [   23.727613] vfio_pci: add [1033:0194[ffff:ffff]] class 0x000000/00000000

Feb 25 16:30:55 lensvr libvirtd[3843]: libvirt version: 2.1.0, package: 1ubuntu9.1 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Thu, 01 Dec 2016 09:44:12 +0100)
Feb 25 16:30:55 lensvr libvirtd[3843]: hostname: lensvr
Feb 25 16:30:55 lensvr libvirtd[3843]: Domain id=1 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: high-privileges
Feb 25 16:30:55 lensvr libvirtd[3843]: Domain id=1 name='win10a' uuid=fd38ddfd-2c12-4759-a2b3-08de7eacc757 is tainted: host-cpu
Feb 25 16:30:55 lensvr kernel: [  261.588131] audit: type=1400 audit(1488000655.976:110): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6740/task/6757/comm" pid=6740 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 16:30:55 lensvr kernel: [  261.602570] audit: type=1400 audit(1488000655.988:111): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6740/task/6758/comm" pid=6740 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 16:30:56 lensvr kernel: [  261.614495] audit: type=1400 audit(1488000656.000:112): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6740/task/6759/comm" pid=6740 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 16:30:56 lensvr kernel: [  261.627761] audit: type=1400 audit(1488000656.016:113): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6740/task/6760/comm" pid=6740 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 16:30:56 lensvr kernel: [  261.639357] audit: type=1400 audit(1488000656.024:114): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6740/task/6761/comm" pid=6740 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 16:30:56 lensvr kernel: [  261.649583] audit: type=1400 audit(1488000656.036:115): apparmor="DENIED" operation="open" profile="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" name="/proc/6740/task/6762/comm" pid=6740 comm="qemu-syst
em-x86" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Feb 25 16:30:58 lensvr kernel: [  263.615685] vfio_ecap_init: 0000:03:00.0 hiding ecap 0x19@0x900
Feb 25 16:30:58 lensvr kernel: [  263.639468] vfio-pci 0000:03:00.1: enabling device (0000 -> 0002)
Feb 25 16:30:59 lensvr libvirtd[3843]: host doesn't support hyperv 'relaxed' feature
Feb 25 16:30:59 lensvr libvirtd[3843]: host doesn't support hyperv 'vapic' feature
Feb 25 16:30:59 lensvr virtlogd[6693]: libvirt version: 2.1.0, package: 1ubuntu9.1 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Thu, 01 Dec 2016 09:44:12 +0100)
Feb 25 16:30:59 lensvr virtlogd[6693]: hostname: lensvr
Feb 25 16:30:59 lensvr virtlogd[6693]: End of file while reading data: Input/output error
Feb 25 16:31:06 lensvr kernel: [  272.575574] kvm: zapping shadow pages for mmio generation wraparound
Feb 25 16:31:06 lensvr kernel: [  272.604843] kvm: zapping shadow pages for mmio generation wraparound

Feb 25 16:39:34 lensvr kernel: [  780.039217] pcieport 0000:00:02.0: AER: Multiple Corrected error received: id=0010
Feb 25 16:39:34 lensvr kernel: [  780.039235] pcieport 0000:00:02.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=0010(Transmitter ID)
Feb 25 16:39:34 lensvr kernel: [  780.039255] pcieport 0000:00:02.0:   device [8086:3c04] error status/mask=00001080/00002000
Feb 25 16:39:34 lensvr kernel: [  780.039269] pcieport 0000:00:02.0:    [ 7] Bad DLLP
Feb 25 16:39:34 lensvr kernel: [  780.039278] pcieport 0000:00:02.0:    [12] Replay Timer Timeout
Feb 25 16:39:34 lensvr kernel: [  780.039883] pcieport 0000:00:02.0: AER: Corrected error received: id=0010
Feb 25 16:39:34 lensvr kernel: [  780.039895] pcieport 0000:00:02.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=0010(Transmitter ID)
Feb 25 16:39:34 lensvr kernel: [  780.039909] pcieport 0000:00:02.0:   device [8086:3c04] error status/mask=00001000/00002000
Feb 25 16:39:34 lensvr kernel: [  780.039921] pcieport 0000:00:02.0:    [12] Replay Timer Timeout
Feb 25 16:39:34 lensvr kernel: [  780.047966] pcieport 0000:00:02.0: AER: Multiple Corrected error received: id=0010
Feb 25 16:39:34 lensvr kernel: [  780.047979] pcieport 0000:00:02.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=0010(Receiver ID)
Feb 25 16:39:34 lensvr kernel: [  780.047993] pcieport 0000:00:02.0:   device [8086:3c04] error status/mask=00000080/00002000
Feb 25 16:39:34 lensvr kernel: [  780.048006] pcieport 0000:00:02.0:    [ 7] Bad DLLP
Feb 25 16:39:34 lensvr kernel: [  780.050179] pcieport 0000:00:02.0: AER: Corrected error received: id=0010
Feb 25 16:39:34 lensvr kernel: [  780.050191] pcieport 0000:00:02.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=0010(Transmitter ID)
Feb 25 16:39:34 lensvr kernel: [  780.050223] pcieport 0000:00:02.0:   device [8086:3c04] error status/mask=00001000/00002000
Feb 25 16:39:34 lensvr kernel: [  780.050235] pcieport 0000:00:02.0:    [12] Replay Timer Timeout
Feb 25 16:39:34 lensvr kernel: [  780.050600] pcieport 0000:00:02.0: AER: Corrected error received: id=0010
Feb 25 16:39:34 lensvr kernel: [  780.050611] pcieport 0000:00:02.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=0010(Transmitter ID)
Feb 25 16:39:34 lensvr kernel: [  780.050624] pcieport 0000:00:02.0:   device [8086:3c04] error status/mask=00001000/00002000
Feb 25 16:39:34 lensvr kernel: [  780.050636] pcieport 0000:00:02.0:    [12] Replay Timer Timeout
Feb 25 16:39:34 lensvr kernel: [  780.050913] pcieport 0000:00:02.0: AER: Corrected error received: id=0010
Feb 25 16:39:34 lensvr kernel: [  780.050930] pcieport 0000:00:02.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=0010(Transmitter ID)
Feb 25 16:39:34 lensvr kernel: [  780.050943] pcieport 0000:00:02.0:   device [8086:3c04] error status/mask=00001000/00002000
Feb 25 16:39:34 lensvr kernel: [  780.050955] pcieport 0000:00:02.0:    [12] Replay Timer Timeout
Feb 25 16:39:34 lensvr kernel: [  780.050969] pcieport 0000:00:02.0: AER: Corrected error received: id=0010
Feb 25 16:39:34 lensvr kernel: [  780.050976] pcieport 0000:00:02.0: can't find device of ID0010
Feb 25 16:39:34 lensvr virtlogd[6693]: End of file while reading data: Input/output error
Feb 25 16:39:34 lensvr kernel: [  780.557904] audit: type=1400 audit(1488001174.918:124): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" pid=10396 comm="apparmor_pars
er"

Feb 25 16:42:23 lensvr libvirtd[3843]: XML error: The PCI controller with index='0' must be model='pci-root' for this machine type, but model='(null)' was found instead

Feb 25 16:58:49 lensvr kernel: [ 1934.821742]       Tainted: P           O    4.8.0-39-generic #42-Ubuntu
Feb 25 16:58:49 lensvr kernel: [ 1934.821750] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 25 16:58:49 lensvr kernel: [ 1934.821762] txg_sync        D ffff94eac0c23cd0     0  2846      2 0x00000000
Feb 25 16:58:49 lensvr kernel: [ 1934.821771]  ffff94eac0c23cd0 00cca3735cbdc47a ffff94e2dc372c40 ffff94ead57cac40
Feb 25 16:58:49 lensvr kernel: [ 1934.821776]  0000000000000000 ffff94eac0c24000 ffff94e2db835068 ffff94e2db835040
Feb 25 16:58:49 lensvr kernel: [ 1934.821780]  ffff94e2db835088 0000000000000000 ffff94eac0c23ce8 ffffffffabc9bd35
Feb 25 16:58:49 lensvr kernel: [ 1934.821784] Call Trace:
Feb 25 16:58:49 lensvr kernel: [ 1934.821795]  [<ffffffffabc9bd35>] schedule+0x35/0x80
Feb 25 16:58:49 lensvr kernel: [ 1934.821813]  [<ffffffffc0812e70>] cv_wait_common+0x110/0x130 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.821818]  [<ffffffffab4c7510>] ? wake_atomic_t_function+0x60/0x60
Feb 25 16:58:49 lensvr kernel: [ 1934.821828]  [<ffffffffc0812ea5>] __cv_wait+0x15/0x20 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.821906]  [<ffffffffc0b58854>] spa_config_enter+0xe4/0x100 [zfs]
Feb 25 16:58:49 lensvr kernel: [ 1934.821970]  [<ffffffffc0b5f097>] txg_sync_thread+0x2a7/0x600 [zfs]
Feb 25 16:58:49 lensvr kernel: [ 1934.822031]  [<ffffffffc0b5edf0>] ? txg_delay+0x160/0x160 [zfs]
Feb 25 16:58:49 lensvr kernel: [ 1934.822040]  [<ffffffffc080dfb1>] thread_generic_wrapper+0x71/0x80 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.822048]  [<ffffffffc080df40>] ? __thread_exit+0x20/0x20 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.822053]  [<ffffffffab4a40d8>] kthread+0xd8/0xf0
Feb 25 16:58:49 lensvr kernel: [ 1934.822059]  [<ffffffffabca071f>] ret_from_fork+0x1f/0x40
Feb 25 16:58:49 lensvr kernel: [ 1934.822063]  [<ffffffffab4a4000>] ? kthread_create_on_node+0x1e0/0x1e0
Feb 25 16:58:49 lensvr kernel: [ 1934.822167] INFO: task spa_async:12487 blocked for more than 120 seconds.
Feb 25 16:58:49 lensvr kernel: [ 1934.822176]       Tainted: P           O    4.8.0-39-generic #42-Ubuntu
Feb 25 16:58:49 lensvr kernel: [ 1934.822183] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 25 16:58:49 lensvr kernel: [ 1934.822194] spa_async       D ffff94e86093fd48     0 12487      2 0x00000000
Feb 25 16:58:49 lensvr kernel: [ 1934.822199]  ffff94e86093fd48 00ff94e86093fd40 ffff94e2dc376740 ffff94ead57d2c40
Feb 25 16:58:49 lensvr kernel: [ 1934.822203]  ffffffffab4b7185 ffff94e860940000 ffff94e2db835218 ffff94e2db8351f0
Feb 25 16:58:49 lensvr kernel: [ 1934.822207]  ffff94e2db835238 0000000000000000 ffff94e86093fd60 ffffffffabc9bd35
Feb 25 16:58:49 lensvr kernel: [ 1934.822211] Call Trace:
Feb 25 16:58:49 lensvr kernel: [ 1934.822215]  [<ffffffffab4b7185>] ? pick_next_entity+0x85/0x130
Feb 25 16:58:49 lensvr kernel: [ 1934.822219]  [<ffffffffabc9bd35>] schedule+0x35/0x80
Feb 25 16:58:49 lensvr kernel: [ 1934.822229]  [<ffffffffc0812e70>] cv_wait_common+0x110/0x130 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.822232]  [<ffffffffab4c7510>] ? wake_atomic_t_function+0x60/0x60
Feb 25 16:58:49 lensvr kernel: [ 1934.822240]  [<ffffffffc0812ea5>] __cv_wait+0x15/0x20 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.822301]  [<ffffffffc0b587fd>] spa_config_enter+0x8d/0x100 [zfs]
Feb 25 16:58:49 lensvr kernel: [ 1934.822360]  [<ffffffffc0b58cf2>] spa_vdev_state_enter+0x32/0x90 [zfs]
Feb 25 16:58:49 lensvr kernel: [ 1934.822418]  [<ffffffffc0b539e9>] spa_async_thread+0xf9/0x2a0 [zfs]
Feb 25 16:58:49 lensvr kernel: [ 1934.822422]  [<ffffffffab60bd2f>] ? kfree+0x14f/0x160
Feb 25 16:58:49 lensvr kernel: [ 1934.822479]  [<ffffffffc0b538f0>] ? spa_vdev_resilver_done+0x160/0x160 [zfs]
Feb 25 16:58:49 lensvr kernel: [ 1934.822488]  [<ffffffffc080dfb1>] thread_generic_wrapper+0x71/0x80 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.822496]  [<ffffffffc080df40>] ? __thread_exit+0x20/0x20 [spl]
Feb 25 16:58:49 lensvr kernel: [ 1934.822500]  [<ffffffffab4a40d8>] kthread+0xd8/0xf0
Feb 25 16:58:49 lensvr kernel: [ 1934.822505]  [<ffffffffabca071f>] ret_from_fork+0x1f/0x40
Feb 25 16:58:49 lensvr kernel: [ 1934.822508]  [<ffffffffab4a4000>] ? kthread_create_on_node+0x1e0/0x1e0

Feb 25 17:02:50 lensvr kernel: [ 2176.499158] INFO: task txg_sync:2846 blocked for more than 120 seconds.
Feb 25 17:02:50 lensvr kernel: [ 2176.499175]       Tainted: P           O    4.8.0-39-generic #42-Ubuntu
Feb 25 17:02:50 lensvr kernel: [ 2176.499183] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 25 17:02:50 lensvr kernel: [ 2176.499195] txg_sync        D ffff94eac0c23cd0     0  2846      2 0x00000000
Feb 25 17:02:50 lensvr kernel: [ 2176.499204]  ffff94eac0c23cd0 00cca3735cbdc47a ffff94e2dc372c40 ffff94ead57cac40
Feb 25 17:02:50 lensvr kernel: [ 2176.499208]  0000000000000000 ffff94eac0c24000 ffff94e2db835068 ffff94e2db835040
Feb 25 17:02:50 lensvr kernel: [ 2176.499213]  ffff94e2db835088 0000000000000000 ffff94eac0c23ce8 ffffffffabc9bd35
Feb 25 17:02:50 lensvr kernel: [ 2176.499217] Call Trace:
Feb 25 17:02:50 lensvr kernel: [ 2176.499228]  [<ffffffffabc9bd35>] schedule+0x35/0x80
Feb 25 17:02:50 lensvr kernel: [ 2176.499246]  [<ffffffffc0812e70>] cv_wait_common+0x110/0x130 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499251]  [<ffffffffab4c7510>] ? wake_atomic_t_function+0x60/0x60
Feb 25 17:02:50 lensvr kernel: [ 2176.499261]  [<ffffffffc0812ea5>] __cv_wait+0x15/0x20 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499339]  [<ffffffffc0b58854>] spa_config_enter+0xe4/0x100 [zfs]
Feb 25 17:02:50 lensvr kernel: [ 2176.499403]  [<ffffffffc0b5f097>] txg_sync_thread+0x2a7/0x600 [zfs]
Feb 25 17:02:50 lensvr kernel: [ 2176.499466]  [<ffffffffc0b5edf0>] ? txg_delay+0x160/0x160 [zfs]
Feb 25 17:02:50 lensvr kernel: [ 2176.499476]  [<ffffffffc080dfb1>] thread_generic_wrapper+0x71/0x80 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499484]  [<ffffffffc080df40>] ? __thread_exit+0x20/0x20 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499489]  [<ffffffffab4a40d8>] kthread+0xd8/0xf0
Feb 25 17:02:50 lensvr kernel: [ 2176.499494]  [<ffffffffabca071f>] ret_from_fork+0x1f/0x40
Feb 25 17:02:50 lensvr kernel: [ 2176.499498]  [<ffffffffab4a4000>] ? kthread_create_on_node+0x1e0/0x1e0
Feb 25 17:02:50 lensvr kernel: [ 2176.499599] INFO: task spa_async:12487 blocked for more than 120 seconds.
Feb 25 17:02:50 lensvr kernel: [ 2176.499609]       Tainted: P           O    4.8.0-39-generic #42-Ubuntu
Feb 25 17:02:50 lensvr kernel: [ 2176.499616] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 25 17:02:50 lensvr kernel: [ 2176.499627] spa_async       D ffff94e86093fd48     0 12487      2 0x00000000
Feb 25 17:02:50 lensvr kernel: [ 2176.499632]  ffff94e86093fd48 00ff94e86093fd40 ffff94e2dc376740 ffff94ead57d2c40
Feb 25 17:02:50 lensvr kernel: [ 2176.499636]  ffffffffab4b7185 ffff94e860940000 ffff94e2db835218 ffff94e2db8351f0
Feb 25 17:02:50 lensvr kernel: [ 2176.499640]  ffff94e2db835238 0000000000000000 ffff94e86093fd60 ffffffffabc9bd35
Feb 25 17:02:50 lensvr kernel: [ 2176.499644] Call Trace:
Feb 25 17:02:50 lensvr kernel: [ 2176.499649]  [<ffffffffab4b7185>] ? pick_next_entity+0x85/0x130
Feb 25 17:02:50 lensvr kernel: [ 2176.499652]  [<ffffffffabc9bd35>] schedule+0x35/0x80
Feb 25 17:02:50 lensvr kernel: [ 2176.499663]  [<ffffffffc0812e70>] cv_wait_common+0x110/0x130 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499666]  [<ffffffffab4c7510>] ? wake_atomic_t_function+0x60/0x60
Feb 25 17:02:50 lensvr kernel: [ 2176.499675]  [<ffffffffc0812ea5>] __cv_wait+0x15/0x20 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499738]  [<ffffffffc0b587fd>] spa_config_enter+0x8d/0x100 [zfs]
Feb 25 17:02:50 lensvr kernel: [ 2176.499799]  [<ffffffffc0b58cf2>] spa_vdev_state_enter+0x32/0x90 [zfs]
Feb 25 17:02:50 lensvr kernel: [ 2176.499858]  [<ffffffffc0b539e9>] spa_async_thread+0xf9/0x2a0 [zfs]
Feb 25 17:02:50 lensvr kernel: [ 2176.499863]  [<ffffffffab60bd2f>] ? kfree+0x14f/0x160
Feb 25 17:02:50 lensvr kernel: [ 2176.499921]  [<ffffffffc0b538f0>] ? spa_vdev_resilver_done+0x160/0x160 [zfs]
Feb 25 17:02:50 lensvr kernel: [ 2176.499931]  [<ffffffffc080dfb1>] thread_generic_wrapper+0x71/0x80 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499939]  [<ffffffffc080df40>] ? __thread_exit+0x20/0x20 [spl]
Feb 25 17:02:50 lensvr kernel: [ 2176.499942]  [<ffffffffab4a40d8>] kthread+0xd8/0xf0
Feb 25 17:02:50 lensvr kernel: [ 2176.499948]  [<ffffffffabca071f>] ret_from_fork+0x1f/0x40
Feb 25 17:02:50 lensvr kernel: [ 2176.499951]  [<ffffffffab4a4000>] ? kthread_create_on_node+0x1e0/0x1e0

Feb 25 17:04:51 lensvr kernel: [ 2297.338293] INFO: task txg_sync:2846 blocked for more than 120 seconds.
Feb 25 17:04:51 lensvr kernel: [ 2297.338306]       Tainted: P           O    4.8.0-39-generic #42-Ubuntu
Feb 25 17:04:51 lensvr kernel: [ 2297.338313] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 25 17:04:51 lensvr kernel: [ 2297.338326] txg_sync        D ffff94eac0c23cd0     0  2846      2 0x00000000
Feb 25 17:04:51 lensvr kernel: [ 2297.338334]  ffff94eac0c23cd0 00cca3735cbdc47a ffff94e2dc372c40 ffff94ead57cac40
Feb 25 17:04:51 lensvr kernel: [ 2297.338339]  0000000000000000 ffff94eac0c24000 ffff94e2db835068 ffff94e2db835040
Feb 25 17:04:51 lensvr kernel: [ 2297.338343]  ffff94e2db835088 0000000000000000 ffff94eac0c23ce8 ffffffffabc9bd35
Feb 25 17:04:51 lensvr kernel: [ 2297.338347] Call Trace:
Feb 25 17:04:51 lensvr kernel: [ 2297.338358]  [<ffffffffabc9bd35>] schedule+0x35/0x80
Feb 25 17:04:51 lensvr kernel: [ 2297.338375]  [<ffffffffc0812e70>] cv_wait_common+0x110/0x130 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.338380]  [<ffffffffab4c7510>] ? wake_atomic_t_function+0x60/0x60
Feb 25 17:04:51 lensvr kernel: [ 2297.338389]  [<ffffffffc0812ea5>] __cv_wait+0x15/0x20 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.338467]  [<ffffffffc0b58854>] spa_config_enter+0xe4/0x100 [zfs]
Feb 25 17:04:51 lensvr kernel: [ 2297.338531]  [<ffffffffc0b5f097>] txg_sync_thread+0x2a7/0x600 [zfs]
Feb 25 17:04:51 lensvr kernel: [ 2297.338593]  [<ffffffffc0b5edf0>] ? txg_delay+0x160/0x160 [zfs]
Feb 25 17:04:51 lensvr kernel: [ 2297.338602]  [<ffffffffc080dfb1>] thread_generic_wrapper+0x71/0x80 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.338610]  [<ffffffffc080df40>] ? __thread_exit+0x20/0x20 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.338615]  [<ffffffffab4a40d8>] kthread+0xd8/0xf0
Feb 25 17:04:51 lensvr kernel: [ 2297.338621]  [<ffffffffabca071f>] ret_from_fork+0x1f/0x40
Feb 25 17:04:51 lensvr kernel: [ 2297.338624]  [<ffffffffab4a4000>] ? kthread_create_on_node+0x1e0/0x1e0
Feb 25 17:04:51 lensvr kernel: [ 2297.338707] INFO: task spa_async:12487 blocked for more than 120 seconds.
Feb 25 17:04:51 lensvr kernel: [ 2297.338717]       Tainted: P           O    4.8.0-39-generic #42-Ubuntu
Feb 25 17:04:51 lensvr kernel: [ 2297.338724] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 25 17:04:51 lensvr kernel: [ 2297.338735] spa_async       D ffff94e86093fd48     0 12487      2 0x00000000
Feb 25 17:04:51 lensvr kernel: [ 2297.338740]  ffff94e86093fd48 00ff94e86093fd40 ffff94e2dc376740 ffff94ead57d2c40
Feb 25 17:04:51 lensvr kernel: [ 2297.338744]  ffffffffab4b7185 ffff94e860940000 ffff94e2db835218 ffff94e2db8351f0
Feb 25 17:04:51 lensvr kernel: [ 2297.338748]  ffff94e2db835238 0000000000000000 ffff94e86093fd60 ffffffffabc9bd35
Feb 25 17:04:51 lensvr kernel: [ 2297.338752] Call Trace:
Feb 25 17:04:51 lensvr kernel: [ 2297.338757]  [<ffffffffab4b7185>] ? pick_next_entity+0x85/0x130
Feb 25 17:04:51 lensvr kernel: [ 2297.338760]  [<ffffffffabc9bd35>] schedule+0x35/0x80
Feb 25 17:04:51 lensvr kernel: [ 2297.338770]  [<ffffffffc0812e70>] cv_wait_common+0x110/0x130 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.338779]  [<ffffffffab4c7510>] ? wake_atomic_t_function+0x60/0x60
Feb 25 17:04:51 lensvr kernel: [ 2297.338788]  [<ffffffffc0812ea5>] __cv_wait+0x15/0x20 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.338852]  [<ffffffffc0b587fd>] spa_config_enter+0x8d/0x100 [zfs]
Feb 25 17:04:51 lensvr kernel: [ 2297.338911]  [<ffffffffc0b58cf2>] spa_vdev_state_enter+0x32/0x90 [zfs]
Feb 25 17:04:51 lensvr kernel: [ 2297.338969]  [<ffffffffc0b539e9>] spa_async_thread+0xf9/0x2a0 [zfs]
Feb 25 17:04:51 lensvr kernel: [ 2297.338973]  [<ffffffffab60bd2f>] ? kfree+0x14f/0x160
Feb 25 17:04:51 lensvr kernel: [ 2297.339029]  [<ffffffffc0b538f0>] ? spa_vdev_resilver_done+0x160/0x160 [zfs]
Feb 25 17:04:51 lensvr kernel: [ 2297.339039]  [<ffffffffc080dfb1>] thread_generic_wrapper+0x71/0x80 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.339047]  [<ffffffffc080df40>] ? __thread_exit+0x20/0x20 [spl]
Feb 25 17:04:51 lensvr kernel: [ 2297.339050]  [<ffffffffab4a40d8>] kthread+0xd8/0xf0
Feb 25 17:04:51 lensvr kernel: [ 2297.339055]  [<ffffffffabca071f>] ret_from_fork+0x1f/0x40
Feb 25 17:04:51 lensvr kernel: [ 2297.339059]  [<ffffffffab4a4000>] ? kthread_create_on_node+0x1e0/0x1e0

Feb 25 17:06:20 lensvr kernel: [ 2386.656282] pcieport 0000:00:02.0: AER: Multiple Corrected error received: id=0010
Feb 25 17:06:20 lensvr kernel: [ 2386.656297] pcieport 0000:00:02.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=0010(Transmitter ID)
Feb 25 17:06:20 lensvr kernel: [ 2386.656313] pcieport 0000:00:02.0:   device [8086:3c04] error status/mask=00001080/00002000
Feb 25 17:06:20 lensvr kernel: [ 2386.656324] pcieport 0000:00:02.0:    [ 7] Bad DLLP
Feb 25 17:06:20 lensvr kernel: [ 2386.656332] pcieport 0000:00:02.0:    [12] Replay Timer Timeout
Feb 25 17:06:21 lensvr virtlogd[6693]: End of file while reading data: Input/output error
Feb 25 17:06:21 lensvr kernel: [ 2387.164556] audit: type=1400 audit(1488002781.436:195): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757" pid=16821 comm="apparmor_pars
er"


```

---

### Post by KillerKelvUK on 2017-02-26
@yanman, so I think you're suffering lots of issues based on a quick whizz through of your configurations, I'd say the reason is because you're trying to stitch together an old passthrough guide (Pudget) with newer solutions.  Some guide pointers for you and then I'll dig into your config...

[http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html) <--the guy who wrote this and runs the blog is called Alex Williamson.  He's the redhat dev who maintains VFIO and has contributed significantly to VFIO development in the form of PCI passthrough.  So in terms of knowledge owners and whom you can trust, he's top of the list for me.  If you look at other articles in his blog he talks about coaxing PCI passthrough to use MSI interrupts as well as others which are useful.  The only challenge you will have is that he uses Fedora for his host OS and so the configuration examples he provides are specific to that distro as such some of it doesn't map directly onto Ubuntu.

I believe one of the forum members here @heiko_s has written a passthrough guide based on Alex Williamson's (above) but for Linux Mint, whilst this is yet another distro Mint is Ubuntu based and so the content will directly work for you.  I can't seem to find it however, I saw it once and it was extremely detailed and useful so go hunting for it.

Onto your config...
[LIST]
[*]Host
[LIST]
[*]Apparmor...has good intentions but gets in the way IMO.  I always suggest disabling it whilst you get passthrough up and stable, you can then re-enable it and re-configure it to not get in the way.  Whilst your logs seem to suggest it is ALLOWING libvirt requests you've only provided a snapshot so it doesn't rule it out.  To disable 'sudo systemctl disable apparmor.service' then to re-enable it 'sudo systemctl enable apparmor.service'
[*]Update the /etc/modprobe.d/local.conf with the additional lines I provided in my previous post and 'sudo update-initramfs -u'
[/LIST]

[*]Guest
[LIST]
[*]Chipset...you're using i440fx but you could switch to Q35.  Personally I think Q35 interacts better with OVMF plus you get a more modern chipset with virtual device optimisations.
[*]Guest image file/storage...why run before you can walk...if you believe using a raw image file has performance improvements vs. native qcow2 then park that for now.  Let libvirt describe and build as much as possible for you to eliminate user error.  I'd also argue qcow2 provides capabilities that outweigh raw images.  Again a debatable point but one that isn't **_needed_** for passthrough, you can optimise later.
[*]You "don't use kvm args", if by that you mean you don't disable the Hyper-V enlightenment's then yes that's clear from your guest XML...its also daft and probably a large contributor to your issues.  Why?
[*]You still have a virtual display adaptor configured (QXL) in the guest.  This will confuse everything including you, the biggest factor will be whether the guest OS considers the QXL device the primary graphics or the GTX1070, based on the bus and slot config of your guest XML I'd say Windows thinks the QXL device is the primary which is likely why you're getting away with not having the Hyper-V enlightenment's disabled.  Again a large contributor to your issues I'd suggest.
[*]You have a VNC graphics device attached, guessing you're using this to get mouse and keyboard to the guest.  However without the QXL display adaptor this won't work, so ditch it anyway and read below as I'll offer you a suggestion on how to move beyond this.
[/LIST]
[/LIST]

```

To disable the Hyper-V enlightenment's modify your guest XML to include the below...

<features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='off'/>
      <vapic state='off'/>
      <spinlocks state='off'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>

<clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='yes'/>
  </clock>


```

The approach I'd recommend you take is the following...
[LIST=1]
[*]Scrap your current VM
[*]Start again and use virt-manager as a GUI tool to create a new Windows 10 VM
[*]Don't even try and use PCI passthrough yet, just get your basic Windows guest working with a virtual QXL device
[*]Make sure you strip out anything that isn't needed i.e. virtual sound and make sure you configure everything as you need it i.e. Q35, OVMF, virtio buses etc
[*]Get Windows installed, install the virtio drivers inside windows e.g. for network and QXL
[*]Once Windows is fully installed and you have all the device drivers installed and it's working fine then move onto modifying the guest XML to add the KVM and Hyper-V modifications to get your guest ready to take on PCI passthrough.  _**But don't add in your GTX1070 yet.**_
[*]Make sure your guest can boot with all the KVM and Hyper-V modification and that its still working.
[*]Right now onto PCI Passthrough.  Using virt-manager remove in this order the QXL display adaptor and then the VNC/SPICE graphics display and then add in your GTX1070 both the display and audio devices.
[*]When you run the guest now the monitor you have connected to the GTX1070 *should* display the machine boot processes e.g. OVMF and start into Windows, although the resolution will be bad as Windows doesn't have any drivers now for its new primary GFX the GTX1070.  _You will also have no way of moving the mouse of entering keyboard inputs within the guest, this is expected._
[*]If your guest boots as per #9 above then the next step is to leave the Windows guest running, go back to virt-manager and add into the running guest (as a USB Host Device) your hosts keyboard and mouse or any separate keyboard and mouse you were planning to use with Windows.
[*]Now that you are in the guest get the Nvidia drivers installed and finish off getting Windows where you want it.  NOTE:  if you added in your hosts keyboard and mouse you will need to shutdown the Windows guest to get them back onto your host.
[*]Once #11 is done, make sure you can reboot/shutdown and restart your guest successfully.
[*]This is pretty much it, if you're stuck with what to do as a permanent solution for keyboard and mouse in the guest then look at [https://symless.com/synergy/](https://symless.com/synergy/) as one possibility.
[/LIST]

---

### Post by yanman on 2017-02-27
Thanks again KillerKelvUK - really appreciate the detailed replies :D

Regarding mixed guides - yes you're right I've gone through this process with a mixture of different guides, however my current config reflects mostly the VFIO guide site and this thread. Pugetsound vs mine I see:
- pci-stub whereas I have been using vfio.
- Scripts to unbind their devices but I don't need to with my later kernel and vfio
- Scripts to start their VM and pass parameters to qemu but I've instead relied on virsh and having everything defined in the domain XML (including the kvm hidden state)
- IOMMU troubles whereas with my C602 chipset board I don't have any trouble. Being a workstation board it seems to have everything nicely arranged.

What I've done differently from this thread and some other later guides:
- Used the GPU vBIOS passed through to the card (```
<rom bar='on' file='/home/user/gv1070bios.dump'/>
```). I got this from troubleshooting the Error 43 from Nvidia blocking the detected Guest. I had to use a spare card to boot from and extracted the BIOS of the 1070 while it was on a PCI riser card :)
- Enabled MSI on the NVIDIA devices in Win10
- Used only the domain XML parameters instead of arguments. Not sure why it's still required?? I thought if you were using UEFI BIOS instead of SeaBIOS you didn't need the args - that it could all be defined in the XML variables.
- I had disabled the hyper-v earlier but then re-enabled them, not being sure if it was required or not.
  is this what you meant by Hyper-V enlightenment?

```
   <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
      <vendor_id state='on' value='1234567890ab'/>
    </hyperv>
```

So this is what I've done since:

I had enabled the modprobe section as you suggested: (the 3rd device is the NEC USB3 controller)
```
$ cat /etc/modprobe.d/local.conf
options vfio-pci ids=10de:1b81,10de:10f0,1033:0194
options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio_iommu_type1 allow_unsafe_interrupts=1
softdep nouveau pre: vfio-pci
```

I did create the VM initially without any PCI pass-through (I've never had any stability with the Win10 VMs before pass-through btw. I used to have one running 24/7 as a Plex server and that has never had any issues so it seems there's definitely evidence to point towards either pass-through or the VFIO? since the earlier Win10 VM I had running had neither - just regular IDE raw drive).
I took a backup of three things at this stage:
- The VM disk image
- The domain XML
- The OVMF VARs file

Regarding apparmor I managed to get it to be APPROVED by using a complain command: 
```
sudo aa-complain /etc/apparmor.d/libvirt/libvirt-fd38ddfd-2c12-4759-a2b3-08de7eacc757
```
...however prior to that I was getting DENIED. I did try to completely disable it with some suggested commands but it's still there, and I had read it's not easy to completely remove - better to just use "complain" ...?

Regarding the QXL device - I had pasted in a non-final domain XML. When the VM was in it's final state I had all that removed. It was just there as I added the PCI passthrough devices.

So when the host locked up 2 days ago I created a new one, copied over the backed up VARS file, copied over the disk, and replaced the domain config with the backup

That 440 was a total derp on my part! I thought the 440 was the newer one since comments I'd read seemed to say the 440 was the more "advanced". I'll change that right away.

As above - the kvm args comment was just referring to the fact that all my parameters are defined in XML syntax variables and not as arguments passed to qemu.
i.e.

```
-cpu host, kvm=off
```

vs 

```
    <kvm>
      <hidden state='on'/>
    </kvm>

```
...or have i totally screwed up here and wrongly assumed those two are the same? :/

I'm going to start again now as you suggested and use:
- Q35 chipset still with latest OVMF?
- VirtIO but with qcow2 instead of raw
- Turn OFF all hyper-v options as suggested in Alex's guide
- Should I peg the CPU cores to the VM? does that mean withhold them the host so they're for exclusive use by the guest?

I've never had any issue getting control of the device because I either: just use mouse/keyboard attached to the NEC USB controller I pass through, or use RDP that I've previously allowed. Windows 10 also seems to include a decent 1070 driver in a download that comes pretty quickly anyway. I think within 5 mins of the VM being idle with the pass through 1070 it had resized to full res!

Once again thanks so much. I'd really like to contribute to the thread and/or Alex's posts if I have anything useful.

---

### Post by KillerKelvUK on 2017-02-27
Hey, so dumping the rom on your card is a valid step but I was under the impression this was only needed if the host couldn't access the memory region the card stored the ROM at...again I thought this would show in a clear error on the host and be specifically related to the guest not being able to boot.  If your only reason for doing this is because you got a code 43 on the guest driver then you may have taken a superfluous step and one that maybe worth reverting as a test.

The code 43 error is all about the Nvidia drivers detecting that they are being run in a KVM/Qemu guest virtual machine...Nvidia saying they didn't specifically build in this restriction but they won't code it away either.  As such we must spoof the Nvidia driver so as to stop it believing it is being run in a vm, to do this by turning on kvm's "hidden state" and disabling the hyperv enlightenment's (the stuff within the <hyperv> tags of the XML).

Regards the kvm args you've not screwed up...your understanding is accurate think...you aren't passing any custom qemu commandline parameters within the XML...some older guides will show you to do this but its not necessary anymore so you're good with that.

Regards Apparmor, if it was denying before and you've simply put it into complain mode then I'd disable it as per my instructions last time.  You could remove the packages but disabling it is quicker and safer.  You might still see dmesg lineouts about audits but these are fine its the apparmor specific lineouts that will have gone which is what you want.

When you say "latest OVMF" are you grabbing the development builds from Kraxel's repo?  If so don't, they are what they say...dev builds.  You should have no issues with Ubuntu's stock OVMF package, i've been using it since 16.04 was released and have had zero issues with it...

```
dpkg -l | grep ovmf
ii  ovmf                                        0~20160408.ffea0a2c-2                         all          UEFI firmware for virtual machines

```

CPU pinning is a fine tuning processes for optimising further a stable vm so you don't need to bother with it yet, similarly if you haven't found it yet hugepages is another memory optimisation that adds value in terms of performance.  Leave these alone until you are stable is my advice.

Keeping my fingers crossed for you \\:D/

---

### Post by yanman on 2017-03-01
Thanks :p

The reason I ended up passing through the ROM for the GPU was I'd tried everything else suggested to fix the dreaded Error 43 for Nvidia cards :/ 

By way of update - I've got my new VM running *without* any PCI devices yet. I figured I may as well load up software and games etc while making sure the VM itself is stable just to be sure. I'm doing all this via RDP. The VM now has no display adapter at all, lol. I removed everything superfluous.

While doing this I had a thought - that initial test of pass-through that had no issues - with the 3DMark and Furmark tests, displaying via HDMI on my TV had no issues. The real major difference between that scenario and my setups that locked-up was that I later started passing through the NEC USB controller. Although it's onboard it's not part of the chipset and it's on it's own IOMMU group. 

Now while I wasn't able to unbind the NEC USB controller from it's normal kernel module, when I start the VM it does unbind it and bind it to vfio. I don't know if that's optimal though.

Here's the lspci -vv output for it:

```
07:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
        Subsystem: Lenovo uPD720200 USB 3.0 Host Controller
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at df200000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
                Vector table: BAR=0 offset=00001000
                PBA: BAR=0 offset=00001080
        Capabilities: [a0] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <4us, L1 unlimited
                        ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Not Supported
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                         EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [140 v1] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
        Capabilities: [150 v1] Latency Tolerance Reporting
                Max snoop latency: 0ns
                Max no snoop latency: 0ns
        Kernel driver in use: xhci_hcd

```

So if this VM locks up.. when I'm ready to test again then that might be the next suspect?

---

### Post by yanman on 2017-03-02
Hmmm well that was unexpected!!

Update just from now..

I had my VM nicely stable and loaded up with software I wanted. I'd just backed up a copy of the disk image, the OVMF and VARS, the XML config. I added PCI devices briefly, without the GPU rom and fired it up.. not surprisingly it worked but with the GPU showing Error code 43. Then I realised I'd forgotten to set the KVM state and Hyper V things to off.

So I shut it down. Change the Hyper-V all to off, added the KVM hidden, and also removed the PCI devices again to sure. Went to start the Guest - instant lock up of the host!

Here's the domain XML i'd started:

```
$ sudo virsh dumpxml win10
<domain type='kvm'>
  <name>win10</name>
  <uuid>ba3e460b-6df0-43ec-8679-5915ef7ca106</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>8</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-2.6'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/win10_VARS.fd</nvram>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='off'/>
      <vapic state='off'/>
      <spinlocks state='off'/>
      <vendor_id state='on' value='1234567890ab'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='host-passthrough'>
    <topology sockets='1' cores='4' threads='2'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/nvme/win10a.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='dmi-to-pci-bridge'>
      <model name='i82801b11-bridge'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1e' function='0x0'/>
    </controller>
    <controller type='pci' index='2' model='pci-bridge'>
      <model name='pci-bridge'/>
      <target chassisNr='2'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:87:03:f4'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x01' function='0x0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x04' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

And it looks like the same crash

```
Mar  2 22:23:47 lensvr libvirtd[3803]: Domain id=16 name='win10' uuid=ba3e460b-6df0-43ec-8679-5915ef7ca106 is tainted: high-privileges
Mar  2 22:23:47 lensvr libvirtd[3803]: Domain id=16 name='win10' uuid=ba3e460b-6df0-43ec-8679-5915ef7ca106 is tainted: host-cpu

```

All this without PCI!

After a bit of comparing I notice there was big differences in the XML files (i took lots of backups and various stages and did Diffs)

So after rolling back from a backup of XML, disk image, and nvram it started just as before.

This time I edited the XML exactly as Alex' page suggested - I was meant to remove the entire <hyperv> stuff </hyperv> section and the clock line! So I did that, saved and started the VM. This time the Host didn't lock up but the VM wasn't online so no RDP :/ I have no idea what happened because I had no VNC or Spice :/

One other thing I noticed - mine VMs all come with emulator set to /usr/bin/kvm-spice instead of /usr/bin/qemu-kvm in Alex' blog. Should I change that too?

---

### Post by KillerKelvUK on 2017-03-02
Hey sorry I've been away with work so haven't checked back here in a couple of days.

Firstly, regarding passthrough of your USB controller and the fact you can't bind it to vfio but it does unbind/bind on guest start/stop...this I think is perfectly normal, I have the exact same happen and I recall another forum members post asking the same and a lot of people saying the same so don't let that put you off.  It does look like you're not passing that through yet which makes sense, get VGA passthrough working first and then get the controller in as well.

Tthe binary location for qemu i.e. /usr/bin/kvm-spice vs /usr/bin/qemu-kvm is one distro specific example I mentioned i.e. ubuntu vs fedora.  If you actually look at the ubuntu binary with 'ls -l /usr/bin/kvm-spice' you'll notice its actually a symlink to another file, no issues here either so best leave alone.

A host lockup without evening passing through your PCI though is a real concern!  Those libvirtd reports I think are because you're running virsh with escalated privileges, you aren't start/stopping the guest using sudo are you?  In a default configuration of libvirt and kvm-qemu you should not need to use sudo at all so if you hacked that around that's going to be a problem?  When the host locks have you tried connecting to it via SSH from another device on your local network aka is it really a host lock up or could it possibly be something more desktop related that feels/looks like a host lock?

---

### Post by teste74 on 2017-03-02
Hello,
Could explain how to install the nvidia driver with qemu please. Error 43 for me.


**Hardware:**
```

SLOT	Type	Référence		ID		Subsystem	Kernel Driver	Kernel modules
00:14.2	[HDA]	HDA Realtek		[1002:4383]	[1043:8410]	snd_hda_intel	snd_hda_intel


01:00.0	[VGA] 	Radeon HD 6950  	[1002:6719]	[XXXX:XXXX]	radeon		radeon
01:00.1	[HDA] 	Radeon HD 6950  	[1002:aa80]	[174b:aa80]	snd_hda_intel	snd_hda_intel


02:00.0	[VGA]	Nvidia GTX 1060		[10de:1c03]	[XXXX:XXXX]	[-----------]	nvidiafb, nouveau
02:00.1	[HDA]	Nvidia GTX 1060		[10de:10f1]	[1043:85ae]	snd_hda_intel	snd_hda_intel

```

**Modules:**
```

/etc/modules
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_amd
kvm_intel

```



**VFIO Configuration:**
```
/etc/modprobe.d/vfio.conf
options vfio-pci ids=10de:1c03,10de:10f1
	
/etc/vfio-pci.cfg
DEVICES="0000:02:00.0 0000:02:00.1"

```

[B]Blacklist:
[/B]```

/etc/modprobe.d/blacklist.conf

blacklist nvidia
blacklist nvidia_drm
blacklist nvidiafb
blacklist nouveau

```

#M5A99X (Required fix iommu)
```
/etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivrs_ioapic[9]=00:14.0 ivrs_ioapic[10]=00:00.2 amd_iommu=on"


```

**Apply:**
```
sudo update-grub ; sudo update-initramfs -u ; reboot

```

```
Qemu:


sudo qemu-system-x86_64 \
-boot c,menu=off \
-cpu host,kvm=off \
-smp cpus=8,maxcpus=8,cores=1,threads=2 \
-m 8192 \
-soundhw hda \
-device vfio-pci,host=02:00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=02:00.1 \
-vga none \
-hda "/mnt/Black/OS/Virtual_Machines/Qemu/Stockage/Windows.qcow2" \
-enable-kvm 


```

**Could you tell me if I make a mistake and how to fix the NVIDIA driver installation**

---

### Post by yanman on 2017-03-03
> **KillerKelvUK said:**
> ...

A host lockup without evening passing through your PCI though is a real concern!  Those libvirtd reports I think are because you're running virsh with escalated privileges, you aren't start/stopping the guest using sudo are you?  In a default configuration of libvirt and kvm-qemu you should not need to use sudo at all so if you hacked that around that's going to be a problem?  When the host locks have you tried connecting to it via SSH from another device on your local network aka is it really a host lock up or could it possibly be something more desktop related that feels/looks like a host lock?
Thanks for the USB info - you confirmed what I was hoping was true. 

Actually yes I've been doing everything with sudo :| I'll stop right away!

Regarding access - my host is headless, even though I built it with Ubuntu Desktop. I initially built it with an AMD card but have removed it in place of the 1070, and only manage the host via SSH and xRDP. Unfortunately I don't have room for both GPU's and my PCI-e to NVMe lane adapter card.

Networking-wise I have bridging enabled (br0) and also docker running that's created it's own bridge virtual interfaces. I'm sure there's been times when the host has been knocked off the LAN but was not actually locked up and I had no way to manage it! The board does have an RS232 serial port so I could try getting that working for an emergency console =D

I'm just about to try one more test. After today I'll be away for a week and a bit :/ 

- Restore everything from backup
- Add in PCI devices with the ROM passed to nvidia card
- Leave hyper-v and kvm settings alone
- See if that works

---

### Post by yanman on 2017-03-03
Ok.. more progress in terms of narrowing down the issue but still no success:

All now performed without sudo!

Test1 - OK: Restore from backup to test
Test2 - OK: Minor change - realised I had USB controller set to USB 2 (virsh default) and so changed it to "Hypervisor Default"
Test3 - OK: Add PCI devices with virt-manager. No dramas. Naturally the GPU didn't work yet. Error code 43
Test4 - OK: Add GPU ROM with virsh as per my old config, no change
Test5 - Fail: Added the <vendor_id state='on' value='1234567890ab'/> line without changing any others. Guest got past the OVMF splash, loading windows then froze. CPU at 1000% on the host, so slightly more than it's permitted. It got as far as 1100% i watched while running top. At this stage the original ssh session to the Host was still alive so I tried to open another, froze at the login screen as if it got stuck somewhere with the shell. xRDP still was ok at this stage too. Tried issuing virsh destroy win10 from SSH... got stuck. Tried Force Off from virt-manager, eventually errored with SIG KILL something erroring, although i noticed a sharp drop in CPU for a moment in virt-manager graph. Tried 3 more times with the same result. Then the host ping dropped, xRDP dropped, SSH same :(

---

### Post by yanman on 2017-03-03
And now I think I've killed my host completely :| BIOS won't even post.

Yep.. code 00 on the board after removing everything except the last 2 dimms :( I've killed something. That's the last straw. Thanks for all your help but it's defeated me. I'll be off to buy a Kaby Lake system and a Synology NAS tomorrow. :(

---

### Post by KillerKelvUK on 2017-03-03
> **yanman said:**
> And now I think I've killed my host completely :| BIOS won't even post.

Yep.. code 00 on the board after removing everything except the last 2 dimms :( I've killed something. That's the last straw. Thanks for all your help but it's defeated me. I'll be off to buy a Kaby Lake system and a Synology NAS tomorrow. :(

Damn, best of luck with the new hardware.

---

