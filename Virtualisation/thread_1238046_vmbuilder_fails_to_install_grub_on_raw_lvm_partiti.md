---
title: "vmbuilder fails to install grub on raw lvm partition (Jaunty)"
date: 2009-08-12
forum: Virtualisation
---

### Post by eas on 2009-08-12
Trying to use vmbuilder to create jaunty vm on a lvm partition, but it never makes it into grub when I try to boot it, it just sits there spinning 100% of one core until I kill it.  Running the vm creation with debug messages on, I see that it has trouble installing grub after copying the files to the target partition.  

The exact problem seems to depend on whether or not the universe packages are used.

If I specify only "--components=main"  I get this:

```
2009-08-11 20:39:23,652 INFO     Installing bootloader
2009-08-11 20:39:23,652 DEBUG    ['grub', '--device-map=/tmp/vmbuildervq1CcS/device.map', '--batch']
2009-08-11 20:39:23,653 DEBUG    stdin was set and it was a string: root (hd0,0)
setup (hd0)
EOT
2009-08-11 20:39:27,657 DEBUG    
2009-08-11 20:39:27,659 DEBUG           [ Minimal BASH-like line editing is supported.   For
2009-08-11 20:39:27,659 DEBUG             the   first   word,  TAB  lists  possible  command
2009-08-11 20:39:27,660 DEBUG             completions.  Anywhere else TAB lists the possible
2009-08-11 20:39:27,661 DEBUG             completions of a device/filename. ]
2009-08-11 20:39:27,661 DEBUG    grub> root (hd0,0)
2009-08-11 20:39:27,661 DEBUG    grub> setup (hd0)
2009-08-11 20:39:27,662 DEBUG     Checking if "/boot/grub/stage1" exists... no
2009-08-11 20:39:27,662 DEBUG     Checking if "/grub/stage1" exists... no
2009-08-11 20:39:27,663 DEBUG    
2009-08-11 20:39:27,663 DEBUG    Error 15: File not found
2009-08-11 20:39:27,663 DEBUG    grub> EOT

```
full log is available here: http://paste.ubuntu.com/251780/


If I specify "--components=main,universe" or if I leave the option off all together, I get:

```
2009-08-11 19:46:54,618 INFO     Installing bootloader
2009-08-11 19:46:54,619 DEBUG    ['grub', '--device-map=/tmp/vmbuildercbOxXt/device.map', '--batch']
2009-08-11 19:46:54,619 DEBUG    stdin was set and it was a string: root (hd0,0)
setup (hd0)
EOT
2009-08-11 19:46:58,575 DEBUG    
2009-08-11 19:46:58,576 DEBUG           [ Minimal BASH-like line editing is supported.   For
2009-08-11 19:46:58,577 DEBUG             the   first   word,  TAB  lists  possible  command
2009-08-11 19:46:58,577 DEBUG             completions.  Anywhere else TAB lists the possible
2009-08-11 19:46:58,578 DEBUG             completions of a device/filename. ]
2009-08-11 19:46:58,578 DEBUG    grub> root (hd0,0)
2009-08-11 19:46:58,579 DEBUG    grub> setup (hd0)
2009-08-11 19:46:58,579 DEBUG     Checking if "/boot/grub/stage1" exists... no
2009-08-11 19:46:58,580 DEBUG     Checking if "/grub/stage1" exists... no
2009-08-11 19:46:58,580 DEBUG    
2009-08-11 19:46:58,581 DEBUG    Error 15: File not found
2009-08-11 19:46:58,581 DEBUG    grub> EOT
```

Full log is here: http://paste.ubuntu.com/251781/

How do I get this to work?

---

### Post by sendmoreinfo on 2011-11-14
vote for [https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/610652](https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/610652) and/or [https://bugs.launchpad.net/vmbuilder/+bug/654723](https://bugs.launchpad.net/vmbuilder/+bug/654723)

---

