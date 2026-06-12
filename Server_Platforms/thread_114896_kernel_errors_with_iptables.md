---
title: "kernel errors with iptables"
date: 2006-01-09
forum: Server Platforms
---

### Post by phono2k6 on 2006-01-09
Hi all.

I´m using Ubuntu 5.10 as a firewall with two ISP connections. Also I used shorewall 3.x to configure iptables and the thing I want to do is to get internet load balancing traffic.
Everything works find until I applied the "balance" option on the 2 wan interfaces (the NICs that has the internets connections). After to do that I receive the followings erros:

=================================================
Jan  5 09:27:05 localhost kernel: [4338779.622000]  [pg0+793987925/1069995008] acpi_processor_idle+0x11d/0x29b [processor]

Jan  5 09:27:05 localhost kernel: [4338779.622000]  [cpu_idle+45/66] cpu_idle+0x2d/0x42 
Jan  5 09:27:05 localhost kernel: [4338779.622000]  [start_kernel+374/376] start_kernel+0x176/0x178 
Jan  5 09:27:06 localhost kernel: [4338780.557000] Badness in dst_release at include/net/dst.h:154 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [__kfree_skb+61/218] __kfree_skb+0x3d/0xda 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [arp_process+1077/1088] arp_process+0x435/0x440 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [arp_rcv+241/286] arp_rcv+0xf1/0x11e 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [netif_receive_skb+433/485] netif_receive_skb+0x1b1/0x1e5 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [pg0+793854750/1069995008] e100_poll+0x1d6/0x546 [e100] 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [net_rx_action+110/250] net_rx_action+0x6e/0xfa 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [__do_softirq+52/125] __do_softirq+0x34/0x7d 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [do_softirq+34/38] do_softirq+0x22/0x26 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [do_IRQ+30/36] do_IRQ+0x1e/0x24 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [pg0+793987925/1069995008] acpi_processor_idle+0x11d/0x29b [processor]

Jan  5 09:27:06 localhost kernel: [4338780.557000]  [cpu_idle+45/66] cpu_idle+0x2d/0x42 
Jan  5 09:27:06 localhost kernel: [4338780.557000]  [start_kernel+374/376] start_kernel+0x176/0x178 
Jan  5 09:27:06 localhost kernel: [4338780.764000] Badness in dst_release at include/net/dst.h:154 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [__kfree_skb+61/218] __kfree_skb+0x3d/0xda 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [arp_process+1077/1088] arp_process+0x435/0x440 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [arp_rcv+241/286] arp_rcv+0xf1/0x11e 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [netif_receive_skb+433/485] netif_receive_skb+0x1b1/0x1e5 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [pg0+793854750/1069995008] e100_poll+0x1d6/0x546 [e100] 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [net_rx_action+110/250] net_rx_action+0x6e/0xfa 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [__do_softirq+52/125] __do_softirq+0x34/0x7d 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [do_softirq+34/38] do_softirq+0x22/0x26 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [do_IRQ+30/36] do_IRQ+0x1e/0x24 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [pg0+793987925/1069995008] acpi_processor_idle+0x11d/0x29b [processor]

Jan  5 09:27:06 localhost kernel: [4338780.764000]  [cpu_idle+45/66] cpu_idle+0x2d/0x42 
Jan  5 09:27:06 localhost kernel: [4338780.764000]  [start_kernel+374/376] start_kernel+0x176/0x178 
Jan  5 09:27:14 localhost kernel: [4338788.467000] Badness in dst_release at include/net/dst.h:154 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [__kfree_skb+61/218] __kfree_skb+0x3d/0xda 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [arp_process+1077/1088] arp_process+0x435/0x440 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [arp_rcv+241/286] arp_rcv+0xf1/0x11e 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [netif_receive_skb+433/485] netif_receive_skb+0x1b1/0x1e5 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [pg0+793854750/1069995008] e100_poll+0x1d6/0x546 [e100] 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [net_rx_action+110/250] net_rx_action+0x6e/0xfa 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [__do_softirq+52/125] __do_softirq+0x34/0x7d 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [do_softirq+34/38] do_softirq+0x22/0x26 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [do_IRQ+30/36] do_IRQ+0x1e/0x24 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [pg0+793987925/1069995008] acpi_processor_idle+0x11d/0x29b [processor]

Jan  5 09:27:14 localhost kernel: [4338788.467000]  [cpu_idle+45/66] cpu_idle+0x2d/0x42 
Jan  5 09:27:14 localhost kernel: [4338788.467000]  [start_kernel+374/376] start_kernel+0x176/0x178 
Jan  5 09:27:16 localhost kernel: [4338790.401000] Badness in dst_release at include/net/dst.h:154 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [__kfree_skb+61/218] __kfree_skb+0x3d/0xda 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [arp_process+1077/1088] arp_process+0x435/0x440 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [arp_rcv+241/286] arp_rcv+0xf1/0x11e 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [netif_receive_skb+433/485] netif_receive_skb+0x1b1/0x1e5 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [pg0+793854750/1069995008] e100_poll+0x1d6/0x546 [e100] 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [net_rx_action+110/250] net_rx_action+0x6e/0xfa 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [__do_softirq+52/125] __do_softirq+0x34/0x7d 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [do_softirq+34/38] do_softirq+0x22/0x26 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [do_IRQ+30/36] do_IRQ+0x1e/0x24 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [pg0+793987925/1069995008] acpi_processor_idle+0x11d/0x29b [processor]

Jan  5 09:27:16 localhost kernel: [4338790.401000]  [cpu_idle+45/66] cpu_idle+0x2d/0x42 
Jan  5 09:27:16 localhost kernel: [4338790.401000]  [start_kernel+374/376] start_kernel+0x176/0x178 
Jan  5 09:27:21 localhost kernel: [4338795.955000] Badness in dst_release at include/net/dst.h:154 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [__kfree_skb+61/218] __kfree_skb+0x3d/0xda 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [arp_process+1077/1088] arp_process+0x435/0x440 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [arp_rcv+241/286] arp_rcv+0xf1/0x11e 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [netif_receive_skb+433/485] netif_receive_skb+0x1b1/0x1e5 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [pg0+793854750/1069995008] e100_poll+0x1d6/0x546 [e100] 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [net_rx_action+110/250] net_rx_action+0x6e/0xfa 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [__do_softirq+52/125] __do_softirq+0x34/0x7d 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [do_softirq+34/38] do_softirq+0x22/0x26 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [do_IRQ+30/36] do_IRQ+0x1e/0x24 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20 
Jan  5 09:27:21 localhost kernel: [4338795.955000]  [pg0+793987925/1069995008] acpi_processor_idle+0x11d/0x29b [processor]
=======================================================

My messages log y fully completed whit those messages. After 1 day working in this situation the servers hung up and I have to reboot it.

Please help me.. !!

---

