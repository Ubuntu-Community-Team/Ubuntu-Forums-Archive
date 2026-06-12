---
title: "KVM: qemu - can't start guest as non-root using &quot;runas ...&quot;"
date: 2016-01-10
forum: Virtualisation
---

### Post by heiko_s on 2016-01-10
I start my Windows 10 guest using a batch script and the qemu-system-x86_64 command. Whenever I try to run that script using the qemu
```
-runas kvm
```
option, the guest won't start.

I checked various permissions, added my user to the kvm group, tried both kvm and user in the -runas option, but nothing works. I also made sure the /dev/hugepages have the right permissions.

Can someone help me out and point me to the various places where I need to set or modify permissions?

I don't use virsh, libvirt or virt-manager and prefer not to use them.

Thanks!

Here is the complete qemu command:
```
qemu-system-x86_64 \
  -name $vmname,process=$vmname \
  -runas=kvm \
  -machine type=q35,accel=kvm \
  -cpu host,kvm=off \
  -smp 4,sockets=1,cores=2,threads=2 \
  -enable-kvm \
  -m 4G \
  -mem-path /run/hugepages/kvm \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=localtime \
  -vga none \
  -nographic \
  -serial none \
  -parallel none \
  -soundhw hda \
  -usb -usbdevice host:045e:076c -usbdevice host:045e:0750 \
  -device vfio-pci,host=02:00.0,multifunction=on \
  -device vfio-pci,host=02:00.1 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=c \
  -device virtio-scsi-pci,id=scsi \
  -drive id=disk0,if=virtio,cache=none,format=raw,file=/media/user/win.img \
  -netdev type=tap,id=net0,ifname=tap0,vhost=on \
  -device virtio-net-pci,netdev=net0,mac=00:16:3e:00:01:01

```

Note: No problem running the Windows guest with root permissions.

---

### Post by KillerKelvUK on 2016-01-10
What happens when you try without the network device specified?

---

### Post by MAFoElffen on 2016-01-10
Did you use the KVM Windows virtio drivers from KVM?

EDIT-- Nevermind, I mis-read based on last post mentioning "network device." See next post...

---

### Post by MAFoElffen on 2016-01-12
Quote from Stack Exchange on permissions:
> 
For KVM, you need access to the device /dev/kvm. If your user can read/write to this device, then you can run KVM-based virtual machines as your user.
 
A more detailed explanation of that was at KVM.org:
> 
POSIX users/groups 

In the "session" instance, the POSIX users/groups model restricts QEMU virtual machines (and libvirtd in general) to only have access to resources with the same user/group ID as the client application. There is no finer level of configuration possible for the "session" instances.

In the "system" instance, libvirt releases from 0.7.0 onwards allow control over the user/group that the QEMU virtual machines are run as. A build of libvirt with no configuration parameters set will still run QEMU processes as root:root. It is possible to change this default by using the --with-qemu-user=$USERNAME and --with-qemu-group=$GROUPNAME arguments to 'configure' during build. It is strongly recommended that vendors build with both of these arguments set to 'qemu'. Regardless of this build time default, administrators can set a per-host default setting in the /etc/libvirt/qemu.conf configuration file via the user=$USERNAME and group=$GROUPNAME parameters. When a non-root user or group is configured, the libvirt QEMU driver will change uid/gid to match immediately before executing the QEMU binary for a virtual machine.

If QEMU virtual machines from the "system" instance are being run as non-root, there will be greater restrictions on what host resources the QEMU process will be able to access. The libvirtd daemon will attempt to manage permissions on resources to minimise the likelihood of unintentional security denials, but the administrator / application developer must be aware of some of the consequences / restrictions.

The directories /var/run/libvirt/qemu/, /var/lib/libvirt/qemu/ and /var/cache/libvirt/qemu/ must all have their ownership set to match the user / group ID that QEMU guests will be run as. If the vendor has set a non-root user/group for the QEMU driver at build time, the permissions should be set automatically at install time. If a host administrator customizes user/group in /etc/libvirt/qemu.conf, they will need to manually set the ownership on these directories.

When attaching USB and PCI devices to a QEMU guest, QEMU will need to access files in /dev/bus/usb and /sys/bus/pci/devices respectively. The libvirtd daemon will automatically set the ownership on specific devices that are assigned to a guest at start time. There should not be any need for administrator changes in this respect.

Any files/devices used as guest disk images must be accessible to the user/group ID that QEMU guests are configured to run as. The libvirtd daemon will automatically set the ownership of the file/device path to the correct user/group ID. Applications / administrators must be aware though that the parent directory permissions may still deny access. The directories containing disk images must either have their ownership set to match the user/group configured for QEMU, or their UNIX file permissions must have the 'execute/search' bit enabled for 'others'.

The simplest option is the latter one, of just enabling the 'execute/search' bit. For any directory to be used for storing disk images, this can be achieved by running the following command on the directory itself, and any parent directories
```

chmod o+x /path/to/directory

```
In particular note that if using the "system" instance and attempting to store disk images in a user home directory, the default permissions on $HOME are typically too restrictive to allow access.


---

### Post by heiko_s on 2016-09-07
Sorry for the late response - thanks for the replies! I need to check it.

---

### Post by redger on 2016-09-08
Is this still an issue ?

I managed to get it all going some time back on Trusty and still have notes if they're of any value (have now moved to Xenial and using libvirt so not adjusting permissions any more)

---

### Post by heiko_s on 2016-09-09
Yes, it's still an issue. I tried the recommendations from Mafoelffen but either did I miss something, or it just doesn't work for me. Any help is appreciated.

---

### Post by redger on 2016-09-10
does your id have update access to ALL the files and devices mentioned in the qemu command ? eg.
[LIST]
[*]/run/hugepages/kvm
[*]/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd
[*]/tmp/my_vars.fd
[*]/media/user/win.img
[*]USB Device 045e:076c
[*]USB Device 045e:0750
[*]/var/lib/libvirt/qemu
[/LIST]

And the devices implied (note that qemu's mempath parameter is usually set to /dev/hugepages)
[LIST]
[*]/dev/vfio
[*]/dev/hugepages
[*]/dev/usb
[/LIST]

In my case I added a new group, gave it update access to the necessary files (sudo chown -R :<group> /dev/<dir>, sudo chmod -R g+rw /dev/<dir>) and added myself, libvirt-qemu etc. to the group.

For USB devices you'll probably need a udev rule to set appropriate permissions (I avoided that by passing a complete USB card through, the necessary USB devices are attached to that)

Have you set ulimits in /etc/security/limits.conf (this is actually set for an 8GB guest, so the number could be reduced). Note that you need to reboot after changing this
```
<your user-id>           hard    memlock         8388608  # value based on required memory, 8GB in this case
```

Set limits for Hugepages by editing /etc/sysctl.conf and adding the following to the end (note that it's set up for my system, 6GB guests)
```
# Set hugetables / hugepages for KVM guest of 6GB RAM (actually need 3133)
vm.nr_hugepages = 3600  # value here depends on page size
```

Also, you may need to clear and recreate the hugepages allocation if memory is too fragmented. I use the **hugeadm** command to release the space
Here's the script I use (messy but it works for me) ... this will usually clear a hugepages error. (Note that I allocate 6GB = 6144 to the guest - you probably need to adjust this to 4096 say ie. 4GB)
```
#!/bin/sh
# 
# needs to run as root
#
# First calculate what we need vs what's available
#
# cat /proc/meminfo |grep HugePage     will print all the relevant info on Hugepages
echo "Allocating Hugepages (hopefully)"
# Set the amount we want (I allocate 6GB to the guest)
MEM=6144
# Set the Hugepages PageSize factor for MEM above
FACTOR=2
# Set the standard pagesize
HPAGESIZE=2048
# Swapsize (in hugepages) used by hugeadm to consolidate existing pages into contiguous area
SWAPSIZE=1000
# Set the amount of total system memory to reserve
RESERVE=6144
# Set the parameter text for qemu
HUGE="-mem-path /dev/hugepages"
# Calculate required number of pages assuming each page = 2048kB
NEED=$(( $MEM / $FACTOR ))
# Calculate the amount we want (allowing for management overhead)
# WANT=$(( $TOTAL + $NEED ))
WANT=$(( $NEED + (( $MEM / 100 )) ))
# Find the total system memory
MEMTOTAL=$(grep MemTotal /proc/meminfo | awk '{print $2}')
# Find current total Hugepages memory
TOTAL=$(grep HugePages_Total /proc/meminfo | awk '{print $NF}')
# Find the number of HugePages available
AVAIL=$(grep HugePages_Free /proc/meminfo | awk '{print $NF}')
# Is there enough for us ?
NEWTOTAL_RAM=$MEMTOTAL
# How much do we need to capture ?
NEWTOTAL_PAGES=$(( $TOTAL + $WANT - $AVAIL ))
#
#  Debugging
if [ "$1" = "debug" ]; then
    echo "reserve " $RESERVE
    echo "need " $NEED
    echo "want " $WANT
    echo "total " $TOTAL
    echo "avail " $AVAIL
    echo "memtotal " $MEMTOTAL
    echo "newtotal " $NEWTOTAL
    echo "NEWTOTAL_RAM " $NEWTOTAL_RAM
    echo "NEWTOTAL_PAGES " $NEWTOTAL_PAGES
    echo "memtotal " $MEMTOTAL
    echo "avail upd " $AVAILUPD
    echo "total upd " $TOTALUPD
    echo "newtotal upd " $NEWTOTALUPD
    echo "NEWTOTAL_RAM upd " $NEWTOTAL_RAMUPD
    echo "HUGE = " $HUGE
    echo
    cat /proc/meminfo |grep HugePage
    exit
fi
#
if [ $AVAIL -lt $WANT ]; then
    # Try to allocate an additional amount
    echo "Re-establishing and defragmenting hugepages "
    hugeadm --pool-pages-min=DEFAULT:$NEWTOTAL_PAGES &#8211;add-temp-swap=$SWAPSIZE
fi
# Find the updated number of HugePages available
AVAIL=$(grep HugePages_Free /proc/meminfo | awk '{print $NF}')
#
echo &#8220; &#8220;
echo &#8220;Updated hugepages &#8220;
cat /proc/meminfo |grep HugePage
read -p "press Enter to continue " any_key
```

Here's my full list of permissions changes, plus the Ulimits command to be added immediately before calling Qemu. Note that <my-group> could be "kvm" if you add yourself to it.
```
#!/bin/bash
#

# enable access to the VFIO units (for passthrough)
sudo chown -R libvirt-qemu:<my-group> /dev/vfio
sudo chmod -R ug+rwx /dev/vfio

# Enable access to create the monitor etc
sudo chown -R :<my-group> /var/lib/libvirt/qemu/
sudo chmod -R g+rw /var/lib/libvirt/qemu/

# Enable access to the LVM partition the VM is hosted on ie. the boot disk
sudo chown -R :<my-group> /dev/<lvm-vg>/<lvm-lv>
sudo chmod -R g+rw /dev/<lvm-vg>/<lvm-lv>

# Enable access to the device which backs the LVM partition used as host
sudo chown -R :<my-group> /dev/dm-8

# Enable access to create Hugepages
sudo chown -R :<my-group> /dev/hugepages
sudo chmod -R g+rw /dev/hugepages

# Enable access to the "bios" eg. uefi vars
sudo chown  :<my-group> /usr/share/OVMF/OVMF_CODE.fd
sudo chmod g+rw /usr/share/OVMF/OVMF_CODE.fd
sudo chown  :<my-group> /var/lib/libvirt/qemu/nvram/ssd-win8-uefi_VARS.fd
sudo chmod g+rw /var/lib/libvirt/qemu/nvram/ssd-win8-uefi_VARS.fd

# set the limit for locked memory equal to all of guest memory size + [some amount large enough to encompass all of io space]
# THIS IS SESSION SPECIFIC SO NEEDS TO BWE INCLUDED IN THE qemu SHELL FILE ie. in the session immediately before calling qemu
ulimit -l 8388608

```

Does that help ? I know it works for me because I just tested it on my new Xenial build ! The Ulimit changes are critical (a) the limit in /etc/security/limits.conf and then AGAIN in the session from which you call Qemu (add it to the script before the Qemu call)

Are you seeing any Apparmor errors ?


PS I just noticed a note to self from my Qemu script (with a comment about a game doubling it's framerate once that was set), After trying on Xenial it didn't seem to have much impact so I'm interested in your experience
**NOTE TO SELF ... -nodefaults parameter is KEY to performance gain**

---

### Post by redger on 2016-09-11
oh, also worth noting that if you sometimes use virt-manager / libvirt it will reset the permissions. 

I overcame that by
[LIST]
[*]Adding libvirt-qemu to my new group
[*]Moving the passthrough elements to the <qemu:commandline> section of the xml (not ideal but it sort of worked) ... not sure I'd recommend / repeat this
[/LIST]

These days I just use libvirt

---

### Post by heiko_s on 2016-09-11
Thanks redger, that is very helpful! I just made the upgrade to Xenial / Linux Mint 18 and have to iron out some stuff before I get to deal with this.

---

### Post by redger on 2016-09-12
I just realised that my test case used a seabios based VM for which I had previously copied the bios file and changed its permissions, so I've updated the script with a line for the "bios" (uefi)

---

### Post by adili on 2016-11-07
I've also been working on getting my qemu session to run as an unprivileged user, I've mostly got it working albeit with some restrictions on being able to re-attach usb devices due to said user not having write permission to write to /dev/bus/usb/

The main thing that helped me successfully start the guest using -runas kvm was to modify the /etc/security/limits.conf and provide limits for memlock. Running 1 machine requiring 8GB use (RAM + 20MB + 512MB) e.g.

kvm  hard  memlock  893337
kvm  soft   memlock  893337

---

