---
title: "QEMU Networking Not Working But RootFSFromScratch's Does"
date: 2009-06-16
forum: Virtualisation
---

### Post by nfox on 2009-06-16
I've been looking at this:
[https://wiki.edubuntu.org/ARM/RootfsFromScratch]("https://wiki.edubuntu.org/ARM/RootfsFromScratch")

It lets you bootstrap for a different architecture (ARM in this case) and uses QEMU to set up the environment. My attempts at QEMU networking have failed but this script works. I've logged the initialization scripts and the command to launch QEMU but nothing seems to give me Internet access on the VM. What am I overlooking?

It does this while the image is mounted:
```
echo "proc /proc proc defaults 0 0" >$MOUNTPOINT/etc/fstab
echo "auto lo" >$MOUNTPOINT/etc/network/interfaces
echo "iface lo inet loopback" >>$MOUNTPOINT/etc/network/interfaces
echo "127.0.0.1 localhost" >$MOUNTPOINT/etc/hosts
echo "127.0.1.1 ubuntu" >>$MOUNTPOINT/etc/hosts
echo "ubuntu" >$MOUNTPOINT/etc/hostname

```

It launches QEMU with:
```
qemu-system-arm -M versatilepb -kernel /tmp/tmp.SqGgvBCyQE/qemu-vmlinuz -no-reboot -nographic -pidfile /tmp/tmp.SqGgvBCyQE/qemu.pid -hda /tmp/tmp.SqGgvBCyQE/qemu-armel.img -m 256M -append "console=ttyAMA0,115200n8 root=/dev/sda rw init=/bin/installer quiet"

```

Here is the script it runs inside the VM upon bootup:
```
#!/bin/bash
set -e
export PATH
export LC_ALL=C
/debootstrap/debootstrap --second-stage

echo "I: Starting basic services in VM"
/etc/init.d/mountkernfs.sh start || true
/etc/init.d/hostname.sh start || true
mount -o remount -a || true
/etc/init.d/loopback start || true
/etc/init.d/udev start || true
/etc/init.d/mountdevsubfs.sh start || true
/etc/init.d/procps start || true
/etc/init.d/mtab.sh start || true
/etc/init.d/mountall.sh start || true
/etc/init.d/udev-finish start || true
/etc/init.d/networking start || true

echo "deb http://ports.ubuntu.com/ubuntu-ports jaunty main universe" >/etc/apt/sources.list
ifconfig eth0 up
dhclient eth0

locale-gen --no-purge en || true
locale-gen --no-purge en_US.UTF-8 || true
echo LANG=en_US.UTF-8 >>/etc/environment

sed -i -e 's/^XKBMODEL=.*$/XKBMODEL="pc105"/' /etc/default/console-setup || true
sed -i -e 's/^XKBLAYOUT=.*$/XKBLAYOUT="us"/' /etc/default/console-setup || true
sed -i -e 's/^XKBVARIANT=.*$/XKBVARIANT=""/' /etc/default/console-setup || true
sed -i -e 's/^XKBOPTIONS=.*$/XKBOPTIONS=""/' /etc/default/console-setup || true

echo America/New_York > /etc/timezone
cp -f /usr/share/zoneinfo/America/New_York /etc/localtime || true
apt-get update
apt-get clean
apt-get -y install ubuntu-minimal
apt-get clean

groupadd admin || true
useradd -G admin,adm,dialout,cdrom,floppy,audio,dip,video -s /bin/bash -m -p qeEJcg/TXNrVU -c "Ubuntu System User" user || true
echo '%admin  ALL=(ALL) ALL' >>/etc/sudoers

passwd -l root || true

```

---

### Post by dyfet on 2009-06-19
What kernel image did you use?  What seed did you build your image with?  I did the same and have a working root with networking on qemu.  

If you do dmesg in the arm image, you should see a eth0: smc9c11xfd or similar device.

This is my qemu command.  I built a separate flat pre-allocated image for swap and a cow for the rootfs itself.

qemu-system-arm -hdb images/armel.swap -M versatilepb -redir tcp:2203::22 -m 256 -hda images/armel.cow -no-reboot -net nic,vlan=0 -net user,vlan=0,hostname=armel  -kernel kernels/vmlinuz-2.6.28-versatile -append "root=/dev/sda rw"

---

### Post by nfox on 2009-06-20
I copied what the RootfsFromScratch script does with the finished img file. 
```
qemu-system-arm -M versatilepb -kernel qemu-vmlinuz -no-reboot -hda qemu-armel.img -m 256M -append "root=/dev/sda rw"
```
The kernel is the same as you posted. As with the script, it pulls it from the latest link. I tried everything in the first post since that does work in the script. I've made br0 and created tap0 merging eth0 and wlan0, been able to browse online so I know the bridge is correct. Best I get is a 10.x.x.x IP and no pings reaching out.

---

