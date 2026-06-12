---
title: "reset adapter problem with ethernet on ubuntu 20.04"
date: 2020-10-05
forum: Server Platforms
---

### Post by andre.friesen on 2020-10-05
Hi,

Hardware: Supermicro X9SCM-F

I was running arch on my server and was pretty happy.
Pretty minimal setup with docker containers as workload and a btrfs raid.
At some point in time after months the server got unavailable.
I could see **Reset adapter unexpectedly / Detected Hardware Unit Hang **in the IPMI console. SSH was not working anymore but IPMI was not a problem.

Then I decided to leave the arch route and switched back to ubuntu 20.04.

I installed the Kernel: 5.8.9 because I need btrfs with zstd which is not possible with the 5.4 version.
Again just running a few docker containers and one VM with kvm + qemu which I want to connect via a bridge.
After again getting the problem with Reset Adapter and investigation I decided to get a new network card since I thought I suffered from this bug: [https://serverfault.com/questions/616485/e1000e-reset-adapter-unexpectedly-detected-hardware-unit-hang](https://serverfault.com/questions/616485/e1000e-reset-adapter-unexpectedly-detected-hardware-unit-hang)

New card and this netplan conf and it worked fine up to today (weeks):
**card:** 10Gtek® Gigabit PCIE Netzwerkkarte E1G42ET - Intel 82576 Chip, Dual RJ45 Ports, 1Gbit PCI Express Ethernet LAN Card, 10/100/1000Mbps


/etc/netplan/00-installer-config.yaml
```
network:
  version: 2
  ethernets:
    enp3s0f0:
      dhcp4: no
      dhcp6: no
  bridges:
    br0:
      dhcp4: yes
      dhcp6: no
      interfaces: [ enp3s0f0 ]

```

For some reason my server again is not responding anymore to ssh and I have honestly no idea where to look know.
Again I can see **Reset adapter** in the IPMI console. No internet and no local access other than IPMI again
I have physical and IPMI access, so can get every information you might request for further investigation.

Thanks in advance!

---

### Post by LHammonds on 2020-10-06
#1 - Make sure you are referencing the correct name of network card:

```
sudo lshw -class network | grep 'logical name\|product'
```

Example output on my server:
```
       product: VMXNET3 Ethernet Controller
       logical name: ens160
```

---

### Post by andre.friesen on 2020-10-06
Hi,

okay I have checked the logical name:

it really is:

[IMG]https://i.imgur.com/8HyToZY.png[/IMG]


For a few hours it did work again after swapping the ethernet cable.
But suddenly it did not work anymore. I did change the netplan setting to use static ips, but only after a few hours this reset adapter came back:



[IMG]https://i.imgur.com/POIazLp.png[/IMG]

---

### Post by LHammonds on 2020-10-06
Hmmm....if you had problems with network connectivity with the onboard NIC, then installed an add-on board and you are STILL experiencing similar issues (and swapped the cable), I have to wonder if its a bad port on the switch or the switch itself.

Another potential issue could be someone causing a loopback by taking a cable going out from the switch and coming right back to another port on the switch.  Or if a device on the network is beaconing...either of which would affect everything plugged into that switch.

LHammonds

---

### Post by andre.friesen on 2020-10-07
So the onboard nic had a slightly different error and for that particular model is a bug out there still not solved to this day.
I figured buying a 40€ network card will be way cheaper than trying to fix this.

What I read from your post is that you think the config itself is not the problem.

Yesterday I did switch the cable and did put the cable directly into my router instead of the switch.
But I think the switch is not the problem due to following reasons:
- I just a new one because I thought the old one was bad
- the IPMI interface is on that same switch and works like a charm
- other devices use that switch (laptop and desktop)

When switching the cable to the router and waiting a bit and a few restarts suddenly the connection did work again.
I have no idea why because I did to many things. Also update to the kernel 5.8.13.


But still here is my dmesg from that day the connection dropped:
[https://paste.ubuntu.com/p/pHvMNwyptj/](https://paste.ubuntu.com/p/pHvMNwyptj/)

Particular this section worries me, but I can not tell what this means:
```

[52890.038161] ------------[ cut here ]------------
[52890.038175] NETDEV WATCHDOG: enp3s0f0 (igb): transmit queue 0 timed out
[52890.038199] WARNING: CPU: 5 PID: 0 at net/sched/sch_generic.c:442 dev_watchdog+0x25b/0x270
[52890.038200] Modules linked in: xt_nat xt_tcpudp veth xt_conntrack xt_MASQUERADE nf_conntrack_netlink xfrm_user xfrm_algo xt_addrtype iptable_nat nf_nat nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 br_netfilter nf_tables nfnetlink ip6table_filter ip6_tables iptable_filter bpfilter overlay bridge stp llc nls_iso8859_1 dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua intel_rapl_msr intel_rapl_common ipmi_ssif x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm rapl intel_cstate efi_pstore at24 input_leds cdc_acm joydev acpi_ipmi ipmi_si ie31200_edac ipmi_devintf ipmi_msghandler mac_hid sch_fq_codel ip_tables x_tables autofs4 btrfs blake2b_generic crypto_simd glue_helper dm_crypt raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear mgag200 drm_vram_helper drm_ttm_helper ttm drm_kms_helper syscopyarea uas sysfillrect sysimgblt usb_storage fb_sys_fops cec hid_generic rc_core usbhid crct10dif_pclmul i2c_i801 igb
[52890.038240]  crc32_pclmul mpt3sas dca ahci xhci_pci raid_class ghash_clmulni_intel i2c_smbus hid drm i2c_algo_bit e1000e xhci_pci_renesas scsi_transport_sas lpc_ich cryptd libahci video
[52890.038251] CPU: 5 PID: 0 Comm: swapper/5 Not tainted 5.8.9-050809-generic #202009120936
[52890.038252] Hardware name: Supermicro X9SCL/X9SCM/X9SCL/X9SCM, BIOS 2.3 06/12/2018
[52890.038256] RIP: 0010:dev_watchdog+0x25b/0x270
[52890.038259] Code: 85 c0 75 e5 eb 9c 4c 89 ff c6 05 33 09 1d 01 01 e8 2a 90 fa ff 44 89 e9 4c 89 fe 48 c7 c7 48 dd a7 96 48 89 c2 e8 da 5f 64 ff <0f> 0b e9 7a ff ff ff 66 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 0f
[52890.038260] RSP: 0018:ffffb1cd401cce78 EFLAGS: 00010286
[52890.038261] RAX: 0000000000000000 RBX: ffff9ad78c3f38c0 RCX: ffff9ad78fd58cd8
[52890.038262] RDX: 00000000ffffffd8 RSI: 0000000000000027 RDI: ffff9ad78fd58cd0
[52890.038263] RBP: ffffb1cd401ccea8 R08: 0000000000000004 R09: 0000000000002055
[52890.038264] R10: 0000000000000000 R11: 0000000000000001 R12: ffff9ad78c3f3940
[52890.038265] R13: 0000000000000000 R14: ffff9ad77ae9c480 R15: ffff9ad77ae9c000
[52890.038267] FS:  0000000000000000(0000) GS:ffff9ad78fd40000(0000) knlGS:0000000000000000
[52890.038268] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[52890.038269] CR2: 000038b1b4299058 CR3: 000000027f40a004 CR4: 00000000001626e0
[52890.038270] Call Trace:
[52890.038272]  <IRQ>
[52890.038278]  ? pfifo_fast_enqueue+0x150/0x150
[52890.038280]  call_timer_fn+0x32/0x130
[52890.038283]  __run_timers.part.0+0x184/0x280
[52890.038285]  ? lapic_next_deadline+0x26/0x30
[52890.038289]  ? clockevents_program_event+0x8f/0xe0
[52890.038291]  run_timer_softirq+0x2a/0x50
[52890.038294]  __do_softirq+0xd0/0x2a1
[52890.038296]  asm_call_on_stack+0x12/0x20
[52890.038297]  </IRQ>
[52890.038300]  do_softirq_own_stack+0x3f/0x50
[52890.038304]  irq_exit_rcu+0x95/0xd0
[52890.038308]  sysvec_apic_timer_interrupt+0x3b/0x90
[52890.038310]  asm_sysvec_apic_timer_interrupt+0x12/0x20
[52890.038313] RIP: 0010:cpuidle_enter_state+0xb6/0x3f0
[52890.038325] Code: 20 2f 07 6a e8 cb 90 74 ff 48 89 45 d0 0f 1f 44 00 00 31 ff e8 7b 9c 74 ff 80 7d c7 00 0f 85 d1 01 00 00 fb 66 0f 1f 44 00 00 <45> 85 ed 0f 88 dd 01 00 00 49 63 d5 48 8d 04 52 48 8d 0c d5 00 00
[52890.038326] RSP: 0018:ffffb1cd400afe48 EFLAGS: 00000246
[52890.038328] RAX: ffff9ad78fd6c6c0 RBX: ffff9ad78fd77700 RCX: 000000000000001f
[52890.038329] RDX: 0000000000000000 RSI: 0000000025a5cc1b RDI: 0000000000000000
[52890.038330] RBP: ffffb1cd400afe88 R08: 0000301a6bef9b51 R09: 0000000000000001
[52890.038332] R10: 0000000000002bd3 R11: ffff9ad78fd6b364 R12: ffffffff9716d540
[52890.038333] R13: 0000000000000004 R14: 0000000000000004 R15: 0000000000000000
[52890.038337]  ? cpuidle_enter_state+0xa5/0x3f0
[52890.038339]  cpuidle_enter+0x2e/0x40
[52890.038344]  cpuidle_idle_call+0x145/0x200
[52890.038346]  do_idle+0x7a/0xe0
[52890.038349]  cpu_startup_entry+0x20/0x30
[52890.038353]  start_secondary+0xe6/0x100
[52890.038356]  secondary_startup_64+0xb6/0xc0
[52890.038359] ---[ end trace 6ac8b0b27ada2754 ]---



```

---

### Post by andre.friesen on 2020-10-07
For testing purpose I had the ethernet cable in the switch right now for the last couple of hours.

Just now the server got offline again.
Putting the cable back into the router and directly got a new connection.

This is the dmesg from just now:

[https://paste.ubuntu.com/p/TPsfTtsh24/](https://paste.ubuntu.com/p/TPsfTtsh24/)

The switch is used by ipmi from the same machine. How could this be the problem?

---

### Post by LHammonds on 2020-10-07
> **andre.friesen said:**
> What I read from your post is that you think the config itself is not the problem.
Well, I did not explicity say the config was solid.  From what I saw of it, nothing jumped out as being incorrect. I don't use DHCP nor bridges but based on the [examples on netplan](https://netplan.io/examples/) site, it seems ok.  I would imagine if something was wrong with the config, it would not work at all rather than just sometimes.

If you don't think it is a switch/port issue, the next area I would check is the kernel.  I know you just updated it but there have been similar disconnects of NICs in Ubuntu (14.04) that were kernel-related and reverting to a prior kernel was a workaround.

LHammonds

---

