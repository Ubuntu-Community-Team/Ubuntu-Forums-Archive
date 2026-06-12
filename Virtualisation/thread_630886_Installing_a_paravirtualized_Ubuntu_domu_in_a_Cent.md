---
title: "Installing a paravirtualized Ubuntu domu in a CentOS dom0. Possible ?"
date: 2007-12-03
forum: Virtualisation
---

### Post by far_star on 2007-12-03
I am trying to install Ubuntu 7.10 undoer a CentOS as a domU, but am having trouble with the install location when using the virtual machine manager. I made sure my CPU (Intel) has the virtualization support.
But before I go further, am I wasting my time ?

---

### Post by Speedster on 2008-05-06
I have done this with Hardy (should be a similar process for Gutsy) following these steps:

1. Install the debootstrap RPM from Fedora development in Dom0

2. Create the devices to use as disks and mount the root partition in the Dom0. In my case I use LVM.

```
# lvcreate -n ubuntu -L10G /dev/vgxen
# lvcreate -n ubuntu-swap -L256M /dev/vgxen
# mke2fs -j /dev/vgxen/ubuntu
# mkswap /dev/vgxen/ubuntu-swap
# mkdir -p /mnt/xen
# mount /dev/vgxen/ubuntu /mnt/xen
```

3. Debootstrap a system. Make sure to include extra repositories (multiverse, universe) and tell it to include the correct linux-image-xen, modules, libc6-xen and grub packages. Use a mirror closer to you:

```
# debootstrap --arch=i386 --include=linux-image-2.6.24-16-generic,linux-image-2.6.24-16-xen,linux-ubuntu-modules-2.6.24-16-xen,linux-image-xen,libc6-xen,grub --components=main,universe,multiverse hardy /mnt/xen http://mirror.3fl.net.au/ubuntu/
```

4. Once that has finished chroot into the new debootstrapped tree for the next round of changes.

```
# chroot /mnt/xen
# export LANG=C
```

5. Disable TLS libc libraries:

```
# mv /lib/tls /lib/tls.disabled
```

6. Create /etc/fstab:

```
# cat /etc/fstab
/dev/xvda1       /       ext3    defaults        0 1
/dev/xvdb1       none    swap    defaults        0 0
proc            /proc   proc    defaults        0 0
```

7. Create a folder for GRUB menu and update the config. This is the reason you install the linux-image-generic package:

```
# mkdir -p /boot/grub
# update-grub
```

8. Edit /boot/grub/menu.lst
  - replace "-generic" with "-xen"
  - remove "quiet splash" from the kernel line
  - add "console=xvc0" to both kernel lines (normal and recovery mode)

9. Setup a getty on the Xen console (xvc0):

```
# cd /etc/event.d
# cp tty1 xvc0
# sed -i -e "s/tty1/xvc0/g" xvc0
```

10. Add xvc0 to /etc/securetty to allow root to login

11. Remove references to the hardware clock; these will cause the DomU to hang:

```
# update-rc.d -f hwclockfirst remove
# update-rc.d -f hwclock remove
# rm /etc/udev/rules.d/85-hwclock.rules
```

12. Configure network interfaces (/etc/network/interfaces). In my setup I have DHCP, set static information if you require it:

```
# cat /etc/network/interfaces
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

13. Create /etc/hosts file

```
# cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	hardy
```

14. Create /etc/hostname file

```
# cat /etc/hostname
hardy
```

15. Exit chroot and unmount the filesystem.

```
# exit
# umount /mnt/xen
```

16. Create DomU configuration. Because you have installed a kernel in DomU you can use pygrub:

```
# cat /etc/xen/ubuntu
bootloader = '/usr/bin/pygrub'
memory = 256
name = "ubuntu"
vif = [ '' ]
disk = [ 'phy:/dev/vgxen/ubuntu,xvda1,w', 'phy:/dev/vgxen/ubuntu-swap,xvdb1,w' ]
```

Start your DomU and it should be all good! There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218126") with Hardy at the moment where the network driver will cause a kernel panic on ifup, but the kernel from the Bug Tracker will resolve that - it can be installed while in the chroot.

---

### Post by iler on 2008-05-08
I have one question for you Speedster. How should I apply that patch to Hardy domU? I have everything else working but my domU is crashing with kernel panic.

---

### Post by Speedster on 2008-05-08
I used the kernel image from [http://www.il.is.s.u-tokyo.ac.jp/~hiranotaka/](http://www.il.is.s.u-tokyo.ac.jp/~hiranotaka/)

1. Download the appropriate kernel from above website.
2. Mount the Ubuntu filesystem in Dom0 (as in the setup instructions)
3. Copy the kernel to /tmp in the Ubuntu filesystem (eg /mnt/xen/tmp)
4. chroot into the Ubuntu filesystem
5. dpkg -i <path_to_downloaded_kernel> (should be /tmp if you copied it to /mnt/xen/tmp above)
6. Make sure /boot/grub/menu.lst is correct
7. Exit the chroot, unmount the filesystem and the DomU should now start.

---

### Post by iler on 2008-05-09
Heh, I managed to find those packages too but thanks anyway! Your howto works great. Now I have finally a working system after days and days of testing :)

---

### Post by Millard73 on 2008-05-12
The howto is indeed excellent - I got Ubuntu 8.04 running on RHEL 5.1 Xen. However, my problem is that using the fixed kernel, I get a kernel panic on any network activity over a few bytes. Does anyone else see this problem?


Doing a ping -f (or pretty much any other network activity) I get:


# ping -f 192.168.122.1
PING 192.168.122.1 (192.168.122.1) 56(84) bytes of data.
.[16782.052696] ------------[ cut here ]------------
[16782.052711] kernel BUG at /home/hiranotaka/src/debian/linux-2.6.24.2/debian/build/custom-source-xen/drivers/xen/netfront/netfront.c:1460!
[16782.052716] invalid opcode: 0000 [#1] SMP 
[16782.052720] Modules linked in: ipv6 af_packet evdev ext3 jbd mbcache
[16782.052730] 
[16782.052733] Pid: 2729, comm: ping Not tainted (2.6.24-16-xen #2)
[16782.052737] EIP: 0061:[<c026bb30>] EFLAGS: 00010202 CPU: 0
[16782.052755] EIP is at netif_poll+0x840/0xc80
[16782.052756] EAX: fffffffd EBX: ed4299d4 ECX: 00000001 EDX: 00000001
[16782.052765] ESI: ed4299d4 EDI: 00000000 EBP: ecab8194 ESP: ed421aa8
[16782.052787]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[16782.052789] Process ping (pid: 2729, ti=ed420000 task=ed4af1d0 task.ti=ed420000)
[16782.052791] Stack: 00000000 ec4efcc0 0000001a ed421b50 ed421b40 ed421b30 ed42b9e0 e4262063 
[16782.052799]        0002cab9 00000040 ed428510 eca6b6a0 01413700 ed428480 ed428000 0000c28b 
[16782.052813]        0000c28c 00000001 00000000 002e4262 00000001 00000013 0000c28b ed421b10 
[16782.052820] Call Trace:
[16782.052824]  [<c02b671e>] net_rx_action+0x14e/0x270
[16782.052829]  [<c027556b>] add_timer_randomness+0xdb/0x190
[16782.052834]  [<c012c212>] __do_softirq+0x92/0x130
[16782.052837]  [<c012c33c>] do_softirq+0x8c/0x90
[16782.052840]  [<c0107030>] do_IRQ+0x40/0x70
[16782.052844]  [<c02540b6>] evtchn_do_upcall+0xc6/0x1e0
[16782.052848]  [<c0105976>] hypervisor_callback+0x46/0x4e
[16782.052851]  [<c011007b>] mtrr_ioctl+0x14b/0x3f0
[16782.052854]  [<c0252d0a>] force_evtchn_callback+0xa/0x10
[16782.052857]  [<c0121f99>] finish_task_switch+0x69/0xa0
[16782.052861]  [<c03263d4>] schedule+0x244/0x600
[16782.052866]  [<c0130d57>] lock_timer_base+0x27/0x60
[16782.052869]  [<c0130e9f>] __mod_timer+0x9f/0xb0
[16782.052882]  [<c0326adc>] schedule_timeout+0x4c/0xd0
[16782.052886]  [<c0130980>] process_timeout+0x0/0x10
[16782.052889]  [<c0326ad7>] schedule_timeout+0x47/0xd0
[16782.052892]  [<c02b0cf4>] skb_recv_datagram+0x124/0x220
[16782.052901]  [<c013be80>] autoremove_wake_function+0x0/0x50
[16782.052906]  [<c02f7826>] raw_recvmsg+0x96/0x170
[16782.052910]  [<c02aa227>] sock_common_recvmsg+0x47/0x70
[16782.052925]  [<c02a847c>] sock_recvmsg+0x12c/0x140
[16782.052929]  [<c013be80>] autoremove_wake_function+0x0/0x50
[16782.052933]  [<c025708f>] __xencons_tx_flush+0xff/0x140
[16782.052955]  [<c0257272>] xencons_tx+0x12/0x20
[16782.052959]  [<c025792f>] handle_input+0x9f/0x110
[16782.052962]  [<c021100e>] copy_from_user+0x2e/0x70
[16782.052967]  [<c02a8721>] sys_sendmsg+0x161/0x270
[16782.052970]  [<c021100e>] copy_from_user+0x2e/0x70
[16782.052980]  [<c02a9567>] sys_recvmsg+0x147/0x220
[16782.052983]  [<c011ccf3>] dequeue_entity+0x13/0x40
[16782.053004]  [<c0257a6a>] xencons_ring_send+0xca/0x150
[16782.053008]  [<c032821c>] __reacquire_kernel_lock+0x1c/0x3c
[16782.053011]  [<c0257a6a>] xencons_ring_send+0xca/0x150
[16782.053014]  [<c025708f>] __xencons_tx_flush+0xff/0x140
[16782.053018]  [<c010856c>] xen_clocksource_read+0xc/0x140
[16782.053027]  [<c0276b96>] tty_ldisc_deref+0x46/0x70
[16782.053030]  [<c02a9e4f>] sys_socketcall+0x29f/0x2b0
[16782.053033]  [<c012bc38>] sys_gettimeofday+0x28/0x80
[16782.053036]  [<c0105772>] syscall_call+0x7/0xb
[16782.053039]  =======================
[16782.053041] Code: d2 7f 19 90 8d b4 26 00 00 00 00 e9 3a fc ff ff 83 ea 01 0f 84 31 fc ff ff 83 c6 20 8b 46 04 85 c0 74 ed 85 d2 0f 84 1f fc ff ff <0f> 0b eb fe 8b 54 24 5c 0f b7 02 0f bf 52 06 c7 04 24 80 86 3c 
[16782.053093] EIP: [<c026bb30>] netif_poll+0x840/0xc80 SS:ESP 0069:ed421aa8
[16782.053100] Kernel panic - not syncing: Fatal exception in interrupt

---

### Post by iler on 2008-05-19
I get the same error and have stopped using Ubuntu 8.04 domU because it's really unusable with that bug. At a better time I will try to trace that problem because I really want to use Ubuntu aswell.

---

### Post by SoftDux on 2008-07-26
Hi Speedster, 

I'm trying to install Ubuntu 7.10 as a domU on a Fedora Core 8 server, but get stuck with the section where I need to run "grub-update" - but there's no actuall command called grub-update. 

Is there another way to get grub configured?

---

### Post by Speedster on 2008-10-19
It should be "update-grub" not "grub-update". If you have installed the grub package then that command should be there...

---

