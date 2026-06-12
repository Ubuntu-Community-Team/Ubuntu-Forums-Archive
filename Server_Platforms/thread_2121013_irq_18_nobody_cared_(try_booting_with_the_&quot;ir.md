---
title: "irq 18: nobody cared (try booting with the &quot;irqpoll&quot; option)"
date: 2013-02-28
forum: Server Platforms
---

### Post by SAngeli on 2013-02-28
Hi,
I just completed a fresh new install of ubuntu server 12.10 (previously it was installed 12.04.2 LTS) and it seems I have this error. I can see it when I boot up.
```
cat syslog |grep nobody
Feb 28 20:13:05 ubuntu kernel: [    6.604244] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 28 20:19:50 ubuntu kernel: [    7.020158] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 28 20:25:45 ubuntu kernel: [    7.517111] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 28 20:40:25 ubuntu kernel: [    6.886623] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 28 20:57:48 ubuntu kernel: [    7.286562] irq 18: nobody cared (try booting with the "irqpoll" option)
```

I googled around and found this article: [PCI Ethernet card causes IRQ &#8220;nobody cared&#8221; in syslog [closed]]("http://askubuntu.com/questions/93611/pci-ethernet-card-causes-irq-nobody-cared-in-syslog")
Than, I consulted this [bug link]("https://bugzilla.kernel.org/show_bug.cgi?id=38632") but I am unable to understand if is there a fix or not.
If yes, what do I have to do?
If not, why I did not have this error before on the previous version of ubuntu server (12.04.2 LTS)? Would this create any problem to the performance and usage of the server?

Here is a portion of the error coming from the log file kern.log:
```
Feb 28 20:57:48 ubuntu kernel: [    7.286562] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 28 20:57:48 ubuntu kernel: [    7.286681] Pid: 0, comm: swapper/0 Not tainted 3.5.0-25-generic #39-Ubuntu
Feb 28 20:57:48 ubuntu kernel: [    7.286684] Call Trace:
Feb 28 20:57:48 ubuntu kernel: [    7.286687]  <IRQ>  [<ffffffff810e18bd>] __report_bad_irq+0x3d/0xe0
Feb 28 20:57:48 ubuntu kernel: [    7.286702]  [<ffffffff810e1bc4>] note_interrupt+0x1b4/0x200
Feb 28 20:57:48 ubuntu kernel: [    7.286710]  [<ffffffff810df357>] handle_irq_event_percpu+0xa7/0x1f0
Feb 28 20:57:48 ubuntu kernel: [    7.286717]  [<ffffffff810df4ee>] handle_irq_event+0x4e/0x80
Feb 28 20:57:48 ubuntu kernel: [    7.286724]  [<ffffffff810e26fa>] handle_fasteoi_irq+0x5a/0x100
Feb 28 20:57:48 ubuntu kernel: [    7.286731]  [<ffffffff81015082>] handle_irq+0x22/0x40
Feb 28 20:57:48 ubuntu kernel: [    7.286738]  [<ffffffff8168e5aa>] do_IRQ+0x5a/0xe0
Feb 28 20:57:48 ubuntu kernel: [    7.286746]  [<ffffffff81684b6a>] common_interrupt+0x6a/0x6a
Feb 28 20:57:48 ubuntu kernel: [    7.286749]  <EOI>  [<ffffffff8101baa2>] ? mwait_idle+0x92/0x1e0
Feb 28 20:57:48 ubuntu kernel: [    7.286761]  [<ffffffff8101c4de>] cpu_idle+0xfe/0x120
Feb 28 20:57:48 ubuntu kernel: [    7.286768]  [<ffffffff81651bee>] rest_init+0x72/0x74
Feb 28 20:57:48 ubuntu kernel: [    7.286775]  [<ffffffff81cf3bf7>] start_kernel+0x3cf/0x3dc
Feb 28 20:57:48 ubuntu kernel: [    7.286780]  [<ffffffff81cf3677>] ? do_early_param+0x91/0x91
Feb 28 20:57:48 ubuntu kernel: [    7.286786]  [<ffffffff81cf3356>] x86_64_start_reservations+0x131/0x135
Feb 28 20:57:48 ubuntu kernel: [    7.286791]  [<ffffffff81cf345a>] x86_64_start_kernel+0x100/0x10f
Feb 28 20:57:48 ubuntu kernel: [    7.286794] handlers:
Feb 28 20:57:48 ubuntu kernel: [    7.286835] [<ffffffff814b3c10>] usb_hcd_irq
Feb 28 20:57:48 ubuntu kernel: [    7.286921] Disabling IRQ #18
Feb 28 20:57:49 ubuntu kernel: [    8.796982] tg3 0000:02:00.0: eth0: Link is up at 1000 Mbps, full duplex
Feb 28 20:57:49 ubuntu kernel: [    8.796988] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
Feb 28 20:57:49 ubuntu kernel: [    8.797835] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

Also, when finished installing the server OS, I did not really like the network interface p1p1. So, I renamed following [this article]("http://blogs.bu.edu/mhirsch/2012/12/ubuntu-12-10-renaming-ethernet-interfaces-from-p1p1-to-eth0/"). I wish to know if it is ok. I do not thing this has anything to do with the error as I had it before changing interface name.

```
@ubuntu:/var/log$ cat kern.log | grep p1p1
Feb 28 20:13:05 ubuntu kernel: [    6.976316] IPv6: ADDRCONF(NETDEV_UP): p1p1: link is not ready
Feb 28 20:13:08 ubuntu kernel: [   10.090359] tg3 0000:02:00.0: >p1p1: Link is up at 1000 Mbps, full duplex
Feb 28 20:13:08 ubuntu kernel: [   10.090367] tg3 0000:02:00.0: >p1p1: Flow control is on for TX and on for RX
Feb 28 20:13:08 ubuntu kernel: [   10.091349] IPv6: ADDRCONF(NETDEV_CHANGE): p1p1: link becomes ready
Feb 28 20:24:09 ubuntu kernel: [  265.886738] IPv6: ADDRCONF(NETDEV_UP): p1p1: link is not ready
Feb 28 20:24:13 ubuntu kernel: [  269.148457] tg3 0000:02:00.0: >p1p1: Link is up at 1000 Mbps, full duplex
Feb 28 20:24:13 ubuntu kernel: [  269.148465] tg3 0000:02:00.0: >p1p1: Flow control is on for TX and on for RX
Feb 28 20:24:13 ubuntu kernel: [  269.149333] IPv6: ADDRCONF(NETDEV_CHANGE): p1p1: link becomes ready
Feb 28 20:25:44 ubuntu kernel: [    6.178415] IPv6: ADDRCONF(NETDEV_UP): p1p1: link is not ready
Feb 28 20:25:47 ubuntu kernel: [    9.289399] tg3 0000:02:00.0: >p1p1: Link is up at 1000 Mbps, full duplex
Feb 28 20:25:47 ubuntu kernel: [    9.289404] tg3 0000:02:00.0: >p1p1: Flow control is on for TX and on for RX
Feb 28 20:25:47 ubuntu kernel: [    9.290381] IPv6: ADDRCONF(NETDEV_CHANGE): p1p1: link becomes ready
Feb 28 20:40:25 ubuntu kernel: [    7.849048] IPv6: ADDRCONF(NETDEV_UP): p1p1: link is not ready
Feb 28 20:40:28 ubuntu kernel: [   10.794094] tg3 0000:02:00.0: p1p1: Link is up at 1000 Mbps, full duplex
Feb 28 20:40:28 ubuntu kernel: [   10.794104] tg3 0000:02:00.0: p1p1: Flow control is on for TX and on for RX
Feb 28 20:40:28 ubuntu kernel: [   10.795740] IPv6: ADDRCONF(NETDEV_CHANGE): p1p1: link becomes ready
Feb 28 20:52:08 ubuntu kernel: [  710.345994] IPv6: ADDRCONF(NETDEV_UP): p1p1: link is not ready
Feb 28 20:52:11 ubuntu kernel: [  713.293359] tg3 0000:02:00.0: p1p1: Link is up at 1000 Mbps, full duplex
Feb 28 20:52:11 ubuntu kernel: [  713.293366] tg3 0000:02:00.0: p1p1: Flow control is on for TX and on for RX
Feb 28 20:52:11 ubuntu kernel: [  713.294212] IPv6: ADDRCONF(NETDEV_CHANGE): p1p1: link becomes ready

@ubuntu:/var/log$ cat kern.log | grep eth0
Feb 28 20:13:05 ubuntu kernel: [    0.777564] tg3 0000:02:00.0: >eth0: Tigon3 [partno(BCM95721) rev 4101] (PCI Express) MAC address 00:14:5e:08:83:98
Feb 28 20:13:05 ubuntu kernel: [    0.777589] tg3 0000:02:00.0: >eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Feb 28 20:13:05 ubuntu kernel: [    0.777606] tg3 0000:02:00.0: >eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Feb 28 20:13:05 ubuntu kernel: [    0.777620] tg3 0000:02:00.0: >eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Feb 28 20:13:05 ubuntu kernel: [    3.333207] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 28 20:19:50 ubuntu kernel: [    0.757466] tg3 0000:02:00.0: >eth0: Tigon3 [partno(BCM95721) rev 4101] (PCI Express) MAC address 00:14:5e:08:83:98
Feb 28 20:19:50 ubuntu kernel: [    0.757481] tg3 0000:02:00.0: >eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Feb 28 20:19:50 ubuntu kernel: [    0.757489] tg3 0000:02:00.0: >eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Feb 28 20:19:50 ubuntu kernel: [    0.757496] tg3 0000:02:00.0: >eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Feb 28 20:19:50 ubuntu kernel: [    5.375957] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 28 20:25:43 ubuntu kernel: [    0.790394] tg3 0000:02:00.0: >eth0: Tigon3 [partno(BCM95721) rev 4101] (PCI Express) MAC address 00:14:5e:08:83:98
Feb 28 20:25:43 ubuntu kernel: [    0.790448] tg3 0000:02:00.0: >eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Feb 28 20:25:43 ubuntu kernel: [    0.790465] tg3 0000:02:00.0: >eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Feb 28 20:25:43 ubuntu kernel: [    0.790480] tg3 0000:02:00.0: >eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Feb 28 20:25:43 ubuntu kernel: [    5.443137] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 28 20:40:25 ubuntu kernel: [    0.802015] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95721) rev 4101] (PCI Express) MAC address 00:14:5e:08:83:98
Feb 28 20:40:25 ubuntu kernel: [    0.802039] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Feb 28 20:40:25 ubuntu kernel: [    0.802056] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Feb 28 20:40:25 ubuntu kernel: [    0.802070] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Feb 28 20:40:25 ubuntu kernel: [    3.514770] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 28 20:57:46 ubuntu kernel: [    0.785576] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95721) rev 4101] (PCI Express) MAC address 00:14:5e:08:83:98
Feb 28 20:57:46 ubuntu kernel: [    0.785604] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Feb 28 20:57:46 ubuntu kernel: [    0.785622] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Feb 28 20:57:46 ubuntu kernel: [    0.785639] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Feb 28 20:57:46 ubuntu kernel: [    5.126071] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 28 20:57:46 ubuntu kernel: [    5.521360] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 28 20:57:49 ubuntu kernel: [    8.796982] tg3 0000:02:00.0: eth0: Link is up at 1000 Mbps, full duplex
Feb 28 20:57:49 ubuntu kernel: [    8.796988] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
Feb 28 20:57:49 ubuntu kernel: [    8.797835] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

Here is the ifconfig output:
```
@ubuntu:/var/log$ ifconfig -a
eth0      Link encap:Ethernet  IndirizzoHW 00:14:5e:08:83:98
          indirizzo inet:192.168.0.10  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::214:5eff:fe08:8398/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3174 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000
          Byte RX:160745 (160.7 KB)  Byte TX:1527041 (1.5 MB)
          Interrupt:16

lo        Link encap:Loopback locale
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0
          Byte RX:178 (178.0 B)  Byte TX:178 (178.0 B)

```


If needed this is the configuration files:
```
auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

dns-nameservers 8.8.8.8. 8.8.4.4

```

Here is the pci info, if needed:
```
 lspci
00:00.0 Host bridge: Intel Corporation E7230/3000/3010 Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation E7230/3000/3010 PCI Express Root Port (rev 81)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
0a:04.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI ES1000 (rev 02)

```

What to do?? Please advise. 

thank you,
Spiro

---

### Post by cariboo on 2013-03-01
Your link to the bug is broken, which bug tracker is it located on?

---

### Post by SAngeli on 2013-03-01
I apologize for the mistake. I is not corrected it.
Bug 38632 

Please let me kindly know if is there any solution as I wish this to be fixed. I never had any issue with both Centos and Ubuntu server 12.04.2 LTS and Windows server and workstation.

Spiro

---

### Post by SAngeli on 2013-03-01
To be more precise, here is what I get when I boot the server.
[IMG]http://i.imgur.com/tt1g3uI.jpg[/IMG]

The text is:
```
Ubuntu 12.10 ubuntu tty1
ubuntu login: [    7.153845] irq 18: nobody cared (try booting with the "irqpool" option)
[       7.154082] handlers:
[       7.154123] [<ffffffff814b3c10>] usb_hcd_irq
[       7.154210] Disabling IRQ 18
  * Starting AppAmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
```

Hope this can be of help hoping to find a solution.
Spiro

---

### Post by matt_symes on 2013-03-01
Hi

Do you have the problematic PCI->PCIE chipset ? 

The chipset is the [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]ASM108[SIZE=2]3.[/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]  You can check with lscpi as instructed in the discussion. 

```
lspci | grep ASM
```

^^^case sensitive.

If you do have this chipset then you are affected by this issue. If not then you are looking at a different issue.

Whether you have the workaround (there is no fix acccording to the discussion) is dependent on your kernel version.

You can check that with

```
uname -r
```

Kind regards

---

### Post by SAngeli on 2013-03-01
Hi and thank you very much for your updates.
No, I do not have the ASM1083 Chipset as when executed the "lspci | grep ASM" command nothing came out.
BTW, you can see yourself the output of lspci above.

_**I have to restate that **_I was also able to find out with ubuntu server 12.04.2 LTS I have the same issue. I was wrong about it.
I was unable to see at boot time but I went and look into syslog and found it.

So, I bet it is something I do not know how to solve it but also believe I should not be concerned. I guess.

Thank you,
Spiro

---

