---
title: "udev group ownership for a network device"
date: 2011-04-03
forum: Security
---

### Post by tim_godfrey on 2011-04-03
Hello,

I am trying to change the group ownership permissions of one of my network devices to allow a program I am writing to be able to listen to the interface without requiring root privileges. I have created rules in /etc/udev/rules.d/10-group-ownership.rules. The contents of this file are 

```
# My attempt to put eth0 into the 'tim' group

# Match the ethernet device, and set its group ownership to tim
KERNEL=="eth0", GROUP:="tim"
```

I have tested the rule using udevadm test

```

tim@office:/etc/udev/rules.d$ udevadm test /sys/class/net/eth0
run_command: calling: test
udevadm_test: version 151
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/10-group-ownership.rules' as rules file
...

udev_rules_new: rules use 214368 bytes tokens (17864 * 12 bytes), 36293 bytes buffer
udev_rules_new: temporary index used 59140 bytes (2957 * 20 bytes)
udev_device_new_from_syspath: device 0x7f665ff428b0 has devpath '/devices/pci0000:00/0000:00:0a.0/net/eth0'
udev_rules_apply_to_event: GROUP 1000 /etc/udev/rules.d/10-group-ownership.rules:4
udev_device_new_from_syspath: device 0x7f665ff413e0 has devpath '/devices/pci0000:00/0000:00:0a.0'
udev_device_new_from_syspath: device 0x7f665ff41710 has devpath '/devices/pci0000:00'
udev_rules_apply_to_event: MODE 0660 /etc/udev/rules.d/70-persistent-net.rules:8
udev_rules_apply_to_event: NAME 'eth0' /etc/udev/rules.d/70-persistent-net.rules:8
udev_rules_apply_to_event: IMPORT 'pci-db /devices/pci0000:00/0000:00:0a.0/net/eth0' /lib/udev/rules.d/75-net-description.rules:11
util_run_program: 'pci-db /devices/pci0000:00/0000:00:0a.0/net/eth0' started
util_run_program: '/lib/udev/pci-db' (stderr) 'libudev: udev_device_new_from_syspath: '
util_run_program: '/lib/udev/pci-db' (stderr) 'device 0x7f3ff25ee170 has devpath '//devices/pci0000:00/0000:00:0a.0/net/eth0''
util_run_program: '/lib/udev/pci-db' (stderr) 'libudev: udev_device_new_from_syspath: '
util_run_program: '/lib/udev/pci-db' (stderr) 'device 0x7f3ff25ee4a0 has devpath '//devices/pci0000:00/0000:00:0a.0/net''
util_run_program: '/lib/udev/pci-db' (stderr) 'libudev: udev_device_new_from_syspath: '
util_run_program: '/lib/udev/pci-db' (stderr) 'device 0x7f3ff25ee700 has devpath '//devices/pci0000:00/0000:00:0a.0''
util_run_program: '/lib/udev/pci-db' (stdout) 'ID_VENDOR_FROM_DATABASE=nVidia Corporation'
util_run_program: '/lib/udev/pci-db' (stdout) 'ID_MODEL_FROM_DATABASE=MCP77 Ethernet'
util_run_program: 'pci-db /devices/pci0000:00/0000:00:0a.0/net/eth0' returned with exitcode 0
udev_rules_apply_to_event: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
udev_device_update_db: created db file for '/devices/pci0000:00/0000:00:0a.0/net/eth0' in '/dev/.udev/db/net:eth0'
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pci0000:00/0000:00:0a.0/net/eth0
udevadm_test: INTERFACE=eth0
udevadm_test: IFINDEX=2
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=net
udevadm_test: ID_VENDOR_FROM_DATABASE=nVidia Corporation
udevadm_test: ID_MODEL_FROM_DATABASE=MCP77 Ethernet
udevadm_test: ID_BUS=pci
udevadm_test: ID_VENDOR_ID=0x10de
udevadm_test: ID_MODEL_ID=0x0760
udevadm_test: run: 'socket:@/org/freedesktop/hal/udev_event'

```

From what I can tell, it looks like udev is going to add the device into the group 'tim' (you might also notice that I am trying to achieve this in 70-persistent-net.rules, along with a mode setting), but it doesn't seem to change the permissions of the device:

```

tim@office:/etc/udev/rules.d$ ls -l /sys/devices/pci0000\:00/0000\:00\:0a.0/net/eth0/
total 0
-r--r--r-- 1 root root 4096 2011-04-03 22:24 address
-r--r--r-- 1 root root 4096 2011-04-03 22:25 addr_len
-r--r--r-- 1 root root 4096 2011-04-03 22:25 broadcast
-r--r--r-- 1 root root 4096 2011-04-03 22:25 carrier
lrwxrwxrwx 1 root root    0 2011-04-03 22:24 device -> ../../../0000:00:0a.0
-r--r--r-- 1 root root 4096 2011-04-03 22:24 dev_id
-r--r--r-- 1 root root 4096 2011-04-03 22:25 dormant
-r--r--r-- 1 root root 4096 2011-04-03 22:25 features
-rw-r--r-- 1 root root 4096 2011-04-03 22:25 flags
-rw-r--r-- 1 root root 4096 2011-04-03 22:25 ifalias
-r--r--r-- 1 root root 4096 2011-04-03 22:25 ifindex
-r--r--r-- 1 root root 4096 2011-04-03 22:25 iflink
-r--r--r-- 1 root root 4096 2011-04-03 22:25 link_mode
-rw-r--r-- 1 root root 4096 2011-04-03 22:25 mtu
-r--r--r-- 1 root root 4096 2011-04-03 22:25 operstate
drwxr-xr-x 2 root root    0 2011-04-03 22:25 power
drwxr-xr-x 2 root root    0 2011-04-03 22:25 statistics
lrwxrwxrwx 1 root root    0 2011-04-03 22:24 subsystem -> ../../../../../class/net
-rw-r--r-- 1 root root 4096 2011-04-03 22:25 tx_queue_len
-r--r--r-- 1 root root 4096 2011-04-03 22:24 type
-rw-r--r-- 1 root root 4096 2011-04-03 22:24 uevent

```

Does anybody know what I am doing wrong? Anyone got any suggestions?

---

