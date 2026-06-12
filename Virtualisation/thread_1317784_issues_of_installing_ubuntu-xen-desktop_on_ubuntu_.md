---
title: "issues of installing ubuntu-xen-desktop on ubuntu 9.10"
date: 2009-11-07
forum: Virtualisation
---

### Post by shoutrain on 2009-11-07
i am a beginner of virtualiztion.

followed this page: [http://mediakey.dk/~cc/ubuntu-howto-install-xen/]("http://mediakey.dk/%7Ecc/ubuntu-howto-install-xen/"), I got ubuntu-xen-destop installed, but it can not work. my ubuntu is 9.10.  following is my steps.

1. 
rafael@rafael-laptop:~$ sudo aptitude install ubuntu-xen-desktop bridge-utils

it's looks the upper command got everything installed, include xen-tools. and the option of "(network-script network-bridge)" in /etc/xen/xend-config.sxp is ok. then rebooted the machine.

2. 
after rebooted, enter the boot menu, a new item appears: 2.6.31-14-generic-pae(and corresponding recovery mode), the new kernel was selected to boot. 

3. 
change /etc/xen-tools/xen-tools conf, following is the details:
==================xen-tools.conf starts=================
dir = /home/xen

install-method = debootstrap

size   = 4Gb      # Disk image size.
memory = 128Mb    # Memory size
swap   = 128Mb    # Swap size
fs     = ext3     # use the EXT3 filesystem for the disk image.
dist   = dapper   # Default distribution to install.
image  = sparse   # Specify sparse vs. full disk images.

dhcp = 1

passwd = 1

kernel      = /boot/vmlinuz-2.6.31-14-generic-pae
initrd      = /boot/initrd.img-2.6.31-14-generic-pae

mirror = [http://ubuntu.srt.cn/ubuntu/](http://ubuntu.srt.cn/ubuntu/)

ext3_options   = noatime,nodiratime,errors=remount-ro
ext2_options   = noatime,nodiratime,errors=remount-ro
xfs_options    = defaults
reiser_options = defaults
===============xen-tools.conf ends====================

and then: 
rafael@rafael-laptop:~$ mkdir /home/xen
rafael@rafael-laptop:~$ mkdir /home/xen/domains
rafael@rafael-laptop:~$ xen-create-image -hostname=vm1

upper commonds got through successfully. everything is ok for now. and:

rafael@rafael-laptop:~$ ls /home/xen/domains/vm1/
disk.img  swap.img
rafael@rafael-laptop:~$ 

4. (ISSUES HAPPEN HERE)
rafael@rafael-laptop:~$ xm create vm1.cfg

execute upper command, i got following error messages:

ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in <module>
    from xen.xm import main
  File "/usr/lib/python2.6/dist-packages/xen/xm/main.py", line 61, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')

and: 

rafael@rafael-laptop:~$ sudo xm list
ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in <module>
    from xen.xm import main
  File "/usr/lib/python2.6/dist-packages/xen/xm/main.py", line 61, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')
rafael@rafael-laptop:~$ 

so what's wrong, how can i make vm1 work? attached is vm1.log

---

### Post by shoutrain on 2009-11-07
maybe there is only one isuue, it is why xm list can not work?

rafael@rafael-laptop:~$ sudo xm list
ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in <module>
    from xen.xm import main
  File "/usr/lib/python2.6/dist-packages/xen/xm/main.py", line 61, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')
rafael@rafael-laptop:~$

---

