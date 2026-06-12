---
title: "Can not restart guest (domU) virtual machine"
date: 2008-09-16
forum: Server Platforms
---

### Post by jrx1 on 2008-09-16
Hi!

I can not solve this problem myself, would appreciate any help.

I have installed Ubuntu Server 8.04 with ubuntu-xen-server package.
-----------------------------------------------------------------------------------
root@server3:~# uname -a
Linux server3 2.6.24-19-xen #1 SMP Sat Jul 12 03:55:08 UTC 2008 i686 GNU/Linux
-----------------------------------------------------------------------------------

Guest OS (domU) is also Ubuntu 8.
When I restart the virtual server it looks like do not finish correctly.
-----------------------------------------------------------------------------------
root@vps01:~# uname -a
Linux vps01 2.6.24-19-xen #1 SMP Sat Jul 12 03:55:08 UTC 2008 i686 GNU/Linux
root@vps01:~# reboot

Broadcast message from jurgis@vps01
(/dev/xvc0) at 22:29 ...

The system is going down for reboot NOW!
root@vps01:~# * Saving the system clock
* Unmounting any overflow tmpfs from /tmp... [ OK ]
* Terminating all remaining processes... [ OK ]
* Sending all processes the KILL signal... [ OK ]
* Deactivating swap... [ OK ]
* Unmounting local filesystems... [ OK ]
* Will now restart
[ 173.340268] Restarting system.
-----------------------------------------------------------------------------------

And so it remains in such a state.
If I check out on the main server (dom0) then guest (domU)
is in shutdown state, but it should not be so.
-----------------------------------------------------------------------------------
root@server3:~# xm list
Name ID Mem VCPUs State Time(s)
Domain-0 0 6828 1 r----- 76.4
vps01 12 256 1 ---s-- 8.8
vps02 2 256 1 -b---- 37.6
vps03 3 256 1 -b---- 37.4
vps04 4 256 1 -b---- 38.2
vps05 5 256 1 -b---- 38.8
-----------------------------------------------------------------------------------

The problem might be because I use LVM over RAID5.
Here is domU configuration file vps01.cfg

----------------------------------------------------------------------------
# Configuration file for the Xen instance vps01, created
# by xen-tools 3.8 on Wed Jul 9 22:51:00 2008.
#

#
# Kernel + memory size
#
kernel = '/boot/vmlinuz-2.6.24-19-xen'
ramdisk = '/boot/initrd.img-2.6.24-19-xen'
memory = '256'

#
# Disk device(s).
#
root = '/dev/hda2 ro'
disk = [
'phy:/dev/raid5/vps01-swap,hda1,w',
'phy:/dev/raid5/vps01-disk,hda2,w',
]


#
# Hostname
#
name = 'vps01'

#
# Networking
#
vif = [ 'ip=192.168.83.21,mac=00:16:3E:30:33:41' ]

#
# Behaviour
#
on_poweroff = 'destroy'
on_reboot = 'restart'
on_crash = 'restart'

extra = '2 console=xvc0'
----------------------------------------------------------------------------

Thank you in advance for taking time to look at this issue.

Jurgis

---

### Post by jrx1 on 2008-09-19
I fixed the problem by commenting out one line in
/etc/xen/xend-config.sxp
#(dom0-cpus 1)

which I had written when I had problems with domU creation.
After system update everything works fine now.

---

