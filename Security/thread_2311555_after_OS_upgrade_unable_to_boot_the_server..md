---
title: "after OS upgrade unable to boot the server."
date: 2016-01-28
forum: Security
---

### Post by naresh6 on 2016-01-28
```
* Starting set console keymap[74G[ OK ]
 
* Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 
* Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 
* Starting Bridge udev events into upstart[74G[ OK ]
 
* Starting Signal sysvinit that remote filesystems are mounted[74G[ OK ]
 
* Stopping set console keymap[74G[ OK ]
 
* Starting device node and kernel event manager[74G[ OK ]
 
* Starting load modules from /etc/modules[74G[ OK ]
 
* Stopping cold plug devices[74G[[31mfail[39;49m]
 
* Starting log initial device creation[74G[ OK ]
 
* Stopping log initial device creation[74G[ OK ]
 
* Stopping load modules from /etc/modules[74G[ OK ]
 
* Starting load fallback graphics devices[74G[ OK ]
 
* Stopping load fallback graphics devices[74G[ OK ]
 
* Starting enable remaining boot-time encrypted block devices[74G[ OK ]
 
The disk drive for /dev/xvdf is not ready yet or not present.
 
keys:Continue to wait, or Press S to skip mounting or M for manual recovery
 
cloud-init-nonet[14.55]: waiting 120 seconds for network device
 
cloud-init-nonet[134.55]: gave up waiting for a network device.
 
Cloud-init v. 0.7.5 running 'init' at Mon, 25 Jan 2016 17:10:25 +0000. Up 134.74 seconds.
 
ci-info: ++++++++++++++++++++Net device info++++++++++++++++++++
 
ci-info: +--------+-------+---------+------+-------------------+
 
ci-info: | Device |   Up  | Address | Mask |     Hw-Address    |
 
ci-info: +--------+-------+---------+------+-------------------+
 
ci-info: |   lo   | False |    .    |  .   |         .         |
 
ci-info: |  eth0  | False |    .    |  .   | 0a:70:59:0f:4c:43 |
 
ci-info: +--------+-------+---------+------+-------------------+
```

inputs please

---

