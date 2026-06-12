---
title: "I just can not setup my first kvm guest"
date: 2010-10-06
forum: Virtualisation
---

### Post by hiukkanen on 2010-10-06
Hi

I have been very unlucky to get kvm to work with 10.04. Actually this is my first time ever trying to virtualize anything with any Linux distribution.

I would like to have 1 virtual machine with bridged network adapter but:

```

root@ippon:~# vmbuilder kvm ubuntu --mirror http://localhost:9999/ubuntu --templates mytemplates --libvirt qemu:///system -o
2010-10-06 19:29:52,473 INFO    : Calling hook: preflight_check
2010-10-06 19:29:52,482 INFO    : Calling hook: set_defaults
2010-10-06 19:29:52,483 INFO    : Calling hook: bootstrap
2010-10-06 19:39:23,160 INFO    : Calling hook: configure_os
2010-10-06 19:39:24,870 INFO    : W: Failed to fetch http://localhost:9999/ubuntu/dists/lucid/Release.gpg  Could not resolve 'localhost'
2010-10-06 19:39:24,871 INFO    :
2010-10-06 19:39:24,871 INFO    : W: Failed to fetch http://localhost:9999/ubuntu/dists/lucid-updates/Release.gpg  Could not resolve 'localhost'
2010-10-06 19:39:24,872 INFO    :
2010-10-06 19:39:24,872 INFO    : W: Some index files failed to download, they have been ignored, or old ones used instead.
2010-10-06 19:39:28,807 INFO    :
2010-10-06 19:39:28,807 INFO    : Current default time zone: 'Etc/UTC'
2010-10-06 19:39:28,809 INFO    : Local time is now:      Wed Oct  6 16:39:28 UTC 2010.
2010-10-06 19:39:28,810 INFO    : Universal Time is now:  Wed Oct  6 16:39:28 UTC 2010.
2010-10-06 19:39:28,810 INFO    :
2010-10-06 19:40:18,502 INFO    : Calling hook: post_install
2010-10-06 19:40:18,503 INFO    : Calling hook: preflight_check
2010-10-06 19:40:19,312 INFO    : Calling hook: configure_networking
2010-10-06 19:40:19,349 INFO    : Calling hook: configure_mounting
2010-10-06 19:40:19,380 INFO    : Calling hook: mount_partitions
2010-10-06 19:40:19,382 INFO    : Mounting target filesystems
2010-10-06 19:40:19,382 INFO    : Creating disk image: "/tmp/tmp4ddvU4" of size: 5120MB
2010-10-06 19:40:19,418 INFO    : Adding partition table to disk image: /tmp/tmp4ddvU4
2010-10-06 19:40:19,659 INFO    : Adding type 4 partition to disk image: /tmp/tmp4ddvU4
2010-10-06 19:40:19,728 INFO    : Adding type 3 partition to disk image: /tmp/tmp4ddvU4
2010-10-06 19:40:19,738 INFO    : [0] ../../libparted/filesys.c:148 (ped_file_system_type_get): File system alias linux-swap(new) is deprecated
2010-10-06 19:40:19,785 INFO    : Creating loop devices corresponding to the created partitions
2010-10-06 19:40:19,813 INFO    : Creating file systems
2010-10-06 19:40:19,928 INFO    : mke2fs 1.41.11 (14-Mar-2010)
2010-10-06 19:40:20,816 INFO    : mkswap: /dev/mapper/loop0p2: warning: don't erase bootbits sectors
2010-10-06 19:40:20,817 INFO    :         on whole disk. Use -f to force.
2010-10-06 19:40:34,865 INFO    : Calling hook: install_bootloader
2010-10-06 19:40:43,127 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2010-10-06 19:40:43,257 INFO    : Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2010-10-06 19:40:43,259 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2010-10-06 19:40:43,262 INFO    : Testing for an existing GRUB menu.lst file ...
2010-10-06 19:40:43,262 INFO    :
2010-10-06 19:40:43,263 INFO    : Could not find /boot/grub/menu.lst file.
2010-10-06 19:40:43,263 INFO    : Generating /boot/grub/menu.lst
2010-10-06 19:40:43,311 INFO    : Searching for splash image ... none found, skipping ...
2010-10-06 19:40:43,423 INFO    : grep: /boot/config*: No such file or directory
2010-10-06 19:40:43,479 INFO    : Updating /boot/grub/menu.lst ... done
2010-10-06 19:40:43,479 INFO    :
2010-10-06 19:40:43,636 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2010-10-06 19:40:43,676 INFO    : Searching for default file ... found: /boot/grub/default
2010-10-06 19:40:43,677 INFO    : Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2010-10-06 19:40:43,759 INFO    : Searching for splash image ... none found, skipping ...
2010-10-06 19:40:43,781 INFO    : grep: /boot/config*: No such file or directory
2010-10-06 19:40:43,841 INFO    : Updating /boot/grub/menu.lst ... done
2010-10-06 19:40:43,841 INFO    :
2010-10-06 19:40:43,860 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2010-10-06 19:40:43,866 INFO    : Calling hook: install_kernel
2010-10-06 19:40:45,350 INFO    : Done.
2010-10-06 19:40:48,748 INFO    : Running depmod.
2010-10-06 19:40:48,918 INFO    : update-initramfs: Generating /boot/initrd.img-2.6.32-25-server
2010-10-06 19:40:54,450 INFO    : Running postinst hook script /usr/sbin/update-grub.
2010-10-06 19:40:54,631 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2010-10-06 19:40:54,725 INFO    : Searching for default file ... found: /boot/grub/default
2010-10-06 19:40:54,726 INFO    : Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2010-10-06 19:40:55,012 INFO    : Searching for splash image ... none found, skipping ...
2010-10-06 19:40:55,100 INFO    : Found kernel: /boot/vmlinuz-2.6.32-25-server
2010-10-06 19:40:55,311 INFO    : Replacing config file /var/run/grub/menu.lst with new version
2010-10-06 19:40:55,361 INFO    : Updating /boot/grub/menu.lst ... done
2010-10-06 19:40:55,361 INFO    :
2010-10-06 19:40:55,405 INFO    : Calling hook: unmount_partitions
2010-10-06 19:40:55,406 INFO    : Unmounting target filesystem
2010-10-06 19:40:58,734 INFO    : Calling hook: convert
2010-10-06 19:40:58,737 INFO    : Converting /tmp/tmp4ddvU4 to qcow2, format ubuntu-kvm/tmp4ddvU4.qcow2
2010-10-06 19:41:12,749 INFO    : Calling hook: fix_ownership
2010-10-06 19:41:12,750 INFO    : Calling hook: deploy
libvir: QEMU error : server closed connection
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 24, in <module>
    cli.main()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/contrib/cli.py", line 121, in main
    hypervisor.finalise(destdir)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/hypervisor.py", line 78, in finalise
    self.call_hooks('deploy', destdir)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/distro.py", line 66, in call_hooks
    call_hooks(self, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/util.py", line 158, in call_hooks
    getattr(plugin, func, log_no_such_method)(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/libvirt/__init__.py", line 83, in deploy
    self.conn.defineXML(vmxml)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1119, in defineXML
    if ret is None:raise libvirtError('virDomainDefineXML() failed', conn=self)
libvirt.libvirtError: server closed connection

```
That is what I have been trying to do for 3 days now.

My teplates:

```
::::::::::::::
mytemplates/libvirt/libvirtxml_fsimage.tmpl
::::::::::::::
<domain type='kvm'>
  <name>$hostname</name>
  <memory>#echo $mem * 1024 #</memory>
  <vcpu>$cpus</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <interface type='network'>
      <source network='default'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
#for $fs in $filesystems
    <disk type='file' device='disk'>
      <source file='$fs.filename' />
      <target dev='hd$fs.devletters()' />
    </disk>
#end for
  </devices>
</domain>
::::::::::::::
mytemplates/libvirt/libvirtxml.tmpl
::::::::::::::
<domain type='$domain_type'>
  <name>$hostname</name>
  <memory>#echo int($mem) * 1024 #</memory>
  <vcpu>$cpus</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <interface type='bridge'>
      <source bridge='br0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
#for $disk in $disks
    <disk type='file' device='disk'>
      <source file='$disk.filename' />
      <target dev='hd$disk.devletters()' />
    </disk>
#end for
  </devices>
</domain>
```

And here is also my interfaces:

```
::::::::::::::
/etc/network/interfaces
::::::::::::::
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

What might go wrong?

---

### Post by slooksterpsv on 2010-10-08
Instead of localhost above, try using your IP Address of your system to see if it can find it that way. I believe it's an issue with localhost, not being able to connect, then closing down the connection.

---

### Post by hiukkanen on 2010-10-08
Like this?

```
kvm ubuntu --mirror http://127.0.0.1:9999/ubuntu --templates mytemplates --libvirt qemu:///system
```

---

### Post by slooksterpsv on 2010-10-08
> **hiukkanen said:**
> Like this?

```
kvm ubuntu --mirror http://127.0.0.1:9999/ubuntu --templates mytemplates --libvirt qemu:///system
```

Almost, what is the public/private ip your computer is getting? e.g. 192.168.5.25 or what not, try that IP address.

---

### Post by hiukkanen on 2010-10-11
I was able to avoid these warnings changing the localhost to my dns name:

```
2010-10-06 19:39:24,870 INFO    : W: Failed to fetch http://localhost:9999/ubuntu/dists/lucid/Release.gpg  Could not resolve 'localhost'
2010-10-06 19:39:24,871 INFO    :
2010-10-06 19:39:24,871 INFO    : W: Failed to fetch http://localhost:9999/ubuntu/dists/lucid-updates/Release.gpg  Could not resolve 'localhost'
2010-10-06 19:39:24,872 INFO    :
2010-10-06 19:39:24,872 INFO    : W: Some index files failed to download, they have been ignored, or old ones used instead.
```

, but still the deploy part fails (see my 1. post).

---

### Post by hiukkanen on 2010-10-13
Any ideas out there?

---

### Post by hiukkanen on 2010-10-24
I debugged the call that returns an error. That is ret = libvirtmod.virDomainDefineXML(self._o, xml). I also printed the xml given as argument:

```
<domain type='kvm'>
  <name>ubuntu</name>
  <memory>131072</memory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <interface type='bridge'>
      <source bridge='br0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
    <disk type='file' device='disk'>
      <source file='/root/ubuntu-kvm/tmpnMJX2n.qcow2' />
      <target dev='hda' />
    </disk>
  </devices>
</domain>
```

Does this xml look like it should?

---

