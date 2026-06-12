---
title: "Install Edgy to Sunfire v440 fails"
date: 2007-01-12
forum: Sun Sparc Users
---

### Post by Takanohana on 2007-01-12
Hi !
Netbooting my v440 succeeds with the installation boot.img for Edgy, however in the installation phase the network configuration fails. Here below are extracts from /var/log/syslog which I believe are relevant.
I have tested with Feisty, but that boot.img does not succeed to start the kernel.

Anyone have any suggestions for fixing this based on the log below ?

Jan 11 20:05:48 kernel: [    5.698034] TCP bic registered
Jan 11 20:05:48 kernel: [    5.738089] NET: Registered protocol family 1
Jan 11 20:05:48 kernel: [    5.795286] NET: Registered protocol family 17
Jan 11 20:05:48 kernel: [    6.234316] cassini.c:v1.4 (1 July 2004)
Jan 11 20:05:48 kernel: [    6.288893] cassini: MAC address not found in ROM VPD
Jan 11 20:05:48 kernel: [    6.355874] eth0: Sun Cassini+ (64bit/66MHz PCI/Cu) Ethernet[0] 08:00:20:3f:31:98 
Jan 11 20:05:48 kernel: [    6.459008] cassini: MAC address not found in ROM VPD
Jan 11 20:05:48 kernel: [    6.525973] eth1: Sun Cassini+ (64bit/66MHz PCI/Cu) Ethernet[0] 08:00:20:0f:67:ba 



Jan 11 20:40:28 main-menu[1758]: INFO: Menu item 'netcfg' selected 
Jan 11 20:40:28 kernel: [    8.864407] Unable to handle kernel NULL pointer dereference
Jan 11 20:40:28 kernel: [    8.938992] tsk->{mm,active_mm}->context = 00000000000015c0
Jan 11 20:40:28 kernel: [    9.012270] tsk->{mm,active_mm}->pgd = fffff8323f5a0000
Jan 11 20:40:28 kernel: [    9.080984]               \|/ ____ \|/
Jan 11 20:40:28 kernel: [    9.080986]               "@'/ .. \`@"
Jan 11 20:40:28 kernel: [    9.080988]               /_| \__/ |_\
Jan 11 20:40:28 kernel: [    9.080990]                  \__U_/
Jan 11 20:40:28 kernel: [    9.080996] netcfg(4590): Oops [#1]
Jan 11 20:40:28 kernel: [    9.081003] TSTATE: 0000000080009607 TPC: 000000000041cbf4 TNPC: 000000000041cbf8 Y: 00000000    Not tainted
Jan 11 20:40:28 kernel: [    9.081021] TPC: <request_irq+0x14/0x2e0>
Jan 11 20:40:28 kernel: [    9.081028] g0: e25dbf220000000d g1: 000000000000ac10 g2: fffff80000ba7000 g3: fffff8323fb26ad8
Jan 11 20:40:28 kernel: [    9.081036] g4: fffff8323e3826c0 g5: 00002e3000000000 g6: fffff8323e408000 g7: fffff8323d40aae0
Jan 11 20:40:28 kernel: [    9.081041] o0: 0000000000000000 o1: 0000000000000000 o2: 0000000000000001 o3: 0000000000000002
Jan 11 20:40:28 kernel: [    9.081049] o4: 0000000000000010 o5: fffff8323d5ea6a0 sp: fffff8323e40ada1 ret_pc: 0000000010002070
Jan 11 20:40:28 kernel: [    9.081072] RPC: <cas_spare_recover+0x170/0x1e0 [cassini]>
Jan 11 20:40:28 kernel: [    9.081078] l0: 0000000000000000 l1: fffff8323e40b650 l2: 0000000000000100 l3: 000000000d696910
Jan 11 20:40:28 kernel: [    9.081085] l4: 00000000f7e7a630 l5: 0000000000000002 l6: 00000000f7e82cd8 l7: 00000000f7ff0000
Jan 11 20:40:28 kernel: [    9.081092] i0: ffffffffffffffea i1: 0000000010002e40 i2: 0000000004000000 i3: fffff8323fb20000
Jan 11 20:40:28 kernel: [    9.081101] i4: fffff8323fb20000 i5: 10430000000003b8 i6: fffff8323e40ae71 i7: 00000000100077e4
Jan 11 20:40:28 kernel: [    9.081111] I7: <cas_open+0x1a4/0x240 [cassini]>
Jan 11 20:40:28 kernel: [    9.081115] Caller[00000000100077e4]: cas_open+0x1a4/0x240 [cassini]
Jan 11 20:40:28 kernel: [    9.081125] Caller[00000000005f3310]: dev_open+0x50/0xc0
Jan 11 20:40:28 kernel: [    9.081141] Caller[00000000005f2108]: dev_change_flags+0x128/0x180
Jan 11 20:40:28 kernel: [    9.081148] Caller[000000000063f024]: devinet_ioctl+0x704/0x820
Jan 11 20:40:28 kernel: [    9.081160] Caller[00000000005e6730]: sock_ioctl+0x1d0/0x280
Jan 11 20:40:28 kernel: [    9.081167] Caller[00000000004a8788]: do_ioctl+0x28/0x80
Jan 11 20:40:28 kernel: [    9.081181] Caller[00000000004a884c]: vfs_ioctl+0x6c/0x320
Jan 11 20:40:28 kernel: [    9.081187] Caller[00000000004a8b74]: sys_ioctl+0x74/0xa0
Jan 11 20:40:28 kernel: [    9.081193] Caller[00000000004c84f4]: dev_ifsioc+0x54/0x320
Jan 11 20:40:28 kernel: [    9.081207] Caller[00000000004c40ac]: compat_sys_ioctl+0x14c/0x380
Jan 11 20:40:28 kernel: [    9.081213] Caller[0000000000406a54]: linux_sparc_syscall32+0x34/0x40
Jan 11 20:40:28 kernel: [    9.081227] Caller[00000000000117d0]: 0x117d0
Jan 11 20:40:28 kernel: [    9.081232] Instruction DUMP: 02c6401e  b0103fea  a1322000 <c25c2008> 02c0401a  b0103fed  23001aef  821460f8  80a40001 
Jan 11 20:40:28 main-menu[1758]: WARNING **: Configuring 'netcfg' failed with error code 137 
Jan 11 20:40:28 main-menu[1758]: WARNING **: Menu item 'netcfg' failed. 

///Taka

---

### Post by fajar on 2007-02-17
Some problem here.

Additionally, trying feisty doesn't even give ANY output past "Booting Linux ..." during netboot install.
Feisty works great on v120 though.

---

### Post by osxblade on 2007-10-25
I have a similar installation problem on [Sun Fire v440]("http://www.anysystem.com/workgroup-servers-sunfire-v440.html"). It works fine on v120 though.

---

### Post by Takanohana on 2007-11-01
This:
Jan 11 20:40:28 kernel: [ 9.080996] netcfg(4590): Oops [#1]

was for me solved by going Debian / etch. The installer in etch did
not have problems with the Cassini driver.
(I have not tried Ubuntu since my earlier post here above.)

However, when trying Etch I also found out that my 440 which 
worked fine with Solaris and 4 CPU only worked with Debian if I removed
one or more of the CPU units. So the working setup I ended up with was 
Debian etch running on 2 CPUs.

I'm not sure if this was a hardware problem in my 440, or a kernel 
problem handling 4 CPU. Probably HW, but it would be very interesting 
to know if any other 440 user can get the 440 working with 4 CPU...

Hmm, now I get the feeling it's time to try with Ubuntu again :-)
///Taka

---

### Post by cdr-80 on 2008-03-06
Hi All,

I can confirm an other workaround: put in another nic. I've successfully used both 3com en intel gb nics. Works like a charm also in a 4 cpu setup.

grtz,

Niels

---

### Post by fangrahh on 2008-04-02
Do you mean debian etch and a new nic solved the problem for you?

---

