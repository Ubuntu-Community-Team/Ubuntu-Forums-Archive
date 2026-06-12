---
title: "Large Scale Squid Deployment"
date: 2009-06-28
forum: Server Platforms
---

### Post by mudasir on 2009-06-28
[LEFT]Hi,[/LEFT]
 
[LEFT]This is my first post in this forum. I have recently started using Ubuntu, and i kind of like this OS.[/LEFT]
 
[LEFT]I have recently deployed Squid on ubuntu. I have about 6 servers, each with about 1500 clients. And want to configure squid with this load.[/LEFT]
 
[LEFT]I have used Redhat and have configured Squid many times in Redhat, and it has worked great. But as soon as i deploy squid in my Ubuntu Server, browsing at client side just dies, it becomes so slow that a simple page takes about 40 to 45 sec to load...[/LEFT]
 
[LEFT]I am also trying to configure squid with ZPH Hit, but in tcpdump i only see tox 0x0 , nothing else.[/LEFT]
 
[LEFT]I have attached my squid.conf file as squid.txt, please check this, whether i have missed something.[/LEFT]
 
[LEFT]Can any one help me out in this case.[/LEFT]
 
[LEFT]Looking for a quick and positive reply.[/LEFT]

---

### Post by dragos2 on 2009-06-28
Please post the sysctl -a | grep ipv4, also grep ipv6 and most important grep net.core.

Please post these greps for the 2 systems.

---

### Post by mudasir on 2009-06-28
Hi,
 
Thanks for your quick reply.
 
I am attaching files.
 
eth0 = internet
eth1 = network
 
sysctl-1.txt (for gateway 1)
> 
#### sysctl -a | grep ipv4 ###
net.ipv4.route.gc_thresh = 32768
net.ipv4.route.max_size = 524288
net.ipv4.route.gc_min_interval = 0
net.ipv4.route.gc_min_interval_ms = 500
net.ipv4.route.gc_timeout = 300
net.ipv4.route.gc_interval = 60
net.ipv4.route.redirect_load = 5
net.ipv4.route.redirect_number = 9
net.ipv4.route.redirect_silence = 5120
net.ipv4.route.error_cost = 250
net.ipv4.route.error_burst = 1250
net.ipv4.route.gc_elasticity = 8
net.ipv4.route.mtu_expires = 600
net.ipv4.route.min_pmtu = 552
net.ipv4.route.min_adv_mss = 256
net.ipv4.route.secret_interval = 600
net.ipv4.neigh.default.mcast_solicit = 3
net.ipv4.neigh.default.ucast_solicit = 3
net.ipv4.neigh.default.app_solicit = 0
net.ipv4.neigh.default.retrans_time = 100
net.ipv4.neigh.default.base_reachable_time = 30
net.ipv4.neigh.default.delay_first_probe_time = 5
net.ipv4.neigh.default.gc_stale_time = 60
net.ipv4.neigh.default.unres_qlen = 3
net.ipv4.neigh.default.proxy_qlen = 64
net.ipv4.neigh.default.anycast_delay = 100
net.ipv4.neigh.default.proxy_delay = 80
net.ipv4.neigh.default.locktime = 100
net.ipv4.neigh.default.retrans_time_ms = 1000
net.ipv4.neigh.default.base_reachable_time_ms = 30000
net.ipv4.neigh.default.gc_interval = 30
net.ipv4.neigh.default.gc_thresh1 = 1024
net.ipv4.neigh.default.gc_thresh2 = 2048
net.ipv4.neigh.default.gc_thresh3 = 8192
net.ipv4.neigh.lo.mcast_solicit = 3
net.ipv4.neigh.lo.ucast_solicit = 3
net.ipv4.neigh.lo.app_solicit = 0
net.ipv4.neigh.lo.retrans_time = 100
net.ipv4.neigh.lo.base_reachable_time = 30
net.ipv4.neigh.lo.delay_first_probe_time = 5
net.ipv4.neigh.lo.gc_stale_time = 60
net.ipv4.neigh.lo.unres_qlen = 3
net.ipv4.neigh.lo.proxy_qlen = 64
net.ipv4.neigh.lo.anycast_delay = 100
net.ipv4.neigh.lo.proxy_delay = 80
net.ipv4.neigh.lo.locktime = 100
net.ipv4.neigh.lo.retrans_time_ms = 1000
net.ipv4.neigh.lo.base_reachable_time_ms = 30000
net.ipv4.neigh.eth0.mcast_solicit = 3
net.ipv4.neigh.eth0.ucast_solicit = 3
net.ipv4.neigh.eth0.app_solicit = 0
net.ipv4.neigh.eth0.retrans_time = 100
net.ipv4.neigh.eth0.base_reachable_time = 30
net.ipv4.neigh.eth0.delay_first_probe_time = 5
net.ipv4.neigh.eth0.gc_stale_time = 60
net.ipv4.neigh.eth0.unres_qlen = 3
net.ipv4.neigh.eth0.proxy_qlen = 64
net.ipv4.neigh.eth0.anycast_delay = 100
net.ipv4.neigh.eth0.proxy_delay = 80
net.ipv4.neigh.eth0.locktime = 100
net.ipv4.neigh.eth0.retrans_time_ms = 1000
net.ipv4.neigh.eth0.base_reachable_time_ms = 30000
net.ipv4.neigh.eth1.mcast_solicit = 3
net.ipv4.neigh.eth1.ucast_solicit = 3
net.ipv4.neigh.eth1.app_solicit = 0
net.ipv4.neigh.eth1.retrans_time = 100
net.ipv4.neigh.eth1.base_reachable_time = 30
net.ipv4.neigh.eth1.delay_first_probe_time = 5
net.ipv4.neigh.eth1.gc_stale_time = 60
net.ipv4.neigh.eth1.unres_qlen = 3
net.ipv4.neigh.eth1.proxy_qlen = 64
net.ipv4.neigh.eth1.anycast_delay = 100
net.ipv4.neigh.eth1.proxy_delay = 80
net.ipv4.neigh.eth1.locktime = 100
net.ipv4.neigh.eth1.retrans_time_ms = 1000
net.ipv4.neigh.eth1.base_reachable_time_ms = 30000
net.ipv4.neigh.eth2.mcast_solicit = 3
net.ipv4.neigh.eth2.ucast_solicit = 3
net.ipv4.neigh.eth2.app_solicit = 0
net.ipv4.neigh.eth2.retrans_time = 100
net.ipv4.neigh.eth2.base_reachable_time = 30
net.ipv4.neigh.eth2.delay_first_probe_time = 5
net.ipv4.neigh.eth2.gc_stale_time = 60
net.ipv4.neigh.eth2.unres_qlen = 3
net.ipv4.neigh.eth2.proxy_qlen = 64
net.ipv4.neigh.eth2.anycast_delay = 100
net.ipv4.neigh.eth2.proxy_delay = 80
net.ipv4.neigh.eth2.locktime = 100
net.ipv4.neigh.eth2.retrans_time_ms = 1000
net.ipv4.neigh.eth2.base_reachable_time_ms = 30000
net.ipv4.neigh.pan0.mcast_solicit = 3
net.ipv4.neigh.pan0.ucast_solicit = 3
net.ipv4.neigh.pan0.app_solicit = 0
net.ipv4.neigh.pan0.retrans_time = 100
net.ipv4.neigh.pan0.base_reachable_time = 30
net.ipv4.neigh.pan0.delay_first_probe_time = 5
net.ipv4.neigh.pan0.gc_stale_time = 60
net.ipv4.neigh.pan0.unres_qlen = 3
net.ipv4.neigh.pan0.proxy_qlen = 64
net.ipv4.neigh.pan0.anycast_delay = 100
net.ipv4.neigh.pan0.proxy_delay = 80
net.ipv4.neigh.pan0.locktime = 100
net.ipv4.neigh.pan0.retrans_time_ms = 1000
net.ipv4.neigh.pan0.base_reachable_time_ms = 30000
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_sack = 0
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.ip_default_ttl = 64
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.ip_nonlocal_bind = 0
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_max_orphans = 32768
net.ipv4.tcp_max_tw_buckets = 180000
net.ipv4.ip_dynaddr = 0
net.ipv4.tcp_keepalive_time = 2400
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_max_syn_backlog = 1280
net.ipv4.ip_local_port_range = 32768 61000
net.ipv4.igmp_max_memberships = 20
net.ipv4.igmp_max_msf = 10
net.ipv4.inet_peer_threshold = 65664
net.ipv4.inet_peer_minttl = 120
net.ipv4.inet_peer_maxttl = 600
net.ipv4.inet_peer_gc_mintime = 10
net.ipv4.inet_peer_gc_maxtime = 120
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_ecn = 0
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_mem = 82944 110592 165888
net.ipv4.tcp_wmem = 4096 16384 3538944
net.ipv4.tcp_rmem = 4096 87380 3538944
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_adv_win_scale = 2
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_frto = 2
net.ipv4.tcp_frto_response = 0
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_abc = 0
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_base_mss = 512
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.tcp_dma_copybreak = 4096
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.cipso_cache_enable = 1
net.ipv4.cipso_cache_bucket_size = 10
net.ipv4.cipso_rbm_optfmt = 0
net.ipv4.cipso_rbm_strictvalid = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_max_ssthresh = 0
net.ipv4.udp_mem = 191520 255360 383040
net.ipv4.udp_rmem_min = 4096
net.ipv4.udp_wmem_min = 4096
net.ipv4.netfilter.ip_conntrack_generic_timeout = 600
net.ipv4.netfilter.ip_conntrack_tcp_timeout_syn_sent = 120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_syn_recv = 60
net.ipv4.netfilter.ip_conntrack_tcp_timeout_established = 432000
net.ipv4.netfilter.ip_conntrack_tcp_timeout_fin_wait = 120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_close_wait = 60
net.ipv4.netfilter.ip_conntrack_tcp_timeout_last_ack = 30
net.ipv4.netfilter.ip_conntrack_tcp_timeout_time_wait = 120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_close = 10
net.ipv4.netfilter.ip_conntrack_tcp_timeout_max_retrans = 300
net.ipv4.netfilter.ip_conntrack_tcp_loose = 1
net.ipv4.netfilter.ip_conntrack_tcp_be_liberal = 0
net.ipv4.netfilter.ip_conntrack_tcp_max_retrans = 3
net.ipv4.netfilter.ip_conntrack_udp_timeout = 30
net.ipv4.netfilter.ip_conntrack_udp_timeout_stream = 180
net.ipv4.netfilter.ip_conntrack_icmp_timeout = 30
net.ipv4.netfilter.ip_conntrack_max = 65536
net.ipv4.netfilter.ip_conntrack_count = 33601
net.ipv4.netfilter.ip_conntrack_buckets = 16384
net.ipv4.netfilter.ip_conntrack_checksum = 1
net.ipv4.netfilter.ip_conntrack_log_invalid = 0
net.ipv4.conf.all.forwarding = 1
net.ipv4.conf.all.mc_forwarding = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.all.shared_media = 0
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.all.proxy_arp = 0
net.ipv4.conf.all.medium_id = 0
net.ipv4.conf.all.bootp_relay = 0
net.ipv4.conf.all.log_martians = 0
net.ipv4.conf.all.tag = 0
net.ipv4.conf.all.arp_filter = 0
net.ipv4.conf.all.arp_announce = 0
net.ipv4.conf.all.arp_ignore = 0
net.ipv4.conf.all.arp_accept = 0
net.ipv4.conf.all.disable_xfrm = 0
net.ipv4.conf.all.disable_policy = 0
net.ipv4.conf.all.force_igmp_version = 0
net.ipv4.conf.all.promote_secondaries = 0
net.ipv4.conf.default.forwarding = 1
net.ipv4.conf.default.mc_forwarding = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.conf.default.shared_media = 0
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.conf.default.proxy_arp = 0
net.ipv4.conf.default.medium_id = 0
net.ipv4.conf.default.bootp_relay = 0
net.ipv4.conf.default.log_martians = 0
net.ipv4.conf.default.tag = 0
net.ipv4.conf.default.arp_filter = 0
net.ipv4.conf.default.arp_announce = 0
net.ipv4.conf.default.arp_ignore = 0
net.ipv4.conf.default.arp_accept = 0
net.ipv4.conf.default.disable_xfrm = 0
net.ipv4.conf.default.disable_policy = 0
net.ipv4.conf.default.force_igmp_version = 0
net.ipv4.conf.default.promote_secondaries = 0
net.ipv4.conf.lo.forwarding = 1
net.ipv4.conf.lo.mc_forwarding = 0
net.ipv4.conf.lo.accept_redirects = 0
net.ipv4.conf.lo.secure_redirects = 0
net.ipv4.conf.lo.shared_media = 0
net.ipv4.conf.lo.rp_filter = 0
net.ipv4.conf.lo.send_redirects = 0
net.ipv4.conf.lo.accept_source_route = 0
net.ipv4.conf.lo.proxy_arp = 0
net.ipv4.conf.lo.medium_id = 0
net.ipv4.conf.lo.bootp_relay = 0
net.ipv4.conf.lo.log_martians = 0
net.ipv4.conf.lo.tag = 0
net.ipv4.conf.lo.arp_filter = 0
net.ipv4.conf.lo.arp_announce = 0
net.ipv4.conf.lo.arp_ignore = 0
net.ipv4.conf.lo.arp_accept = 0
net.ipv4.conf.lo.disable_xfrm = 1
net.ipv4.conf.lo.disable_policy = 1
net.ipv4.conf.lo.force_igmp_version = 0
net.ipv4.conf.lo.promote_secondaries = 0
net.ipv4.conf.eth0.forwarding = 1
net.ipv4.conf.eth0.mc_forwarding = 0
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.eth0.secure_redirects = 0
net.ipv4.conf.eth0.shared_media = 0
net.ipv4.conf.eth0.rp_filter = 0
net.ipv4.conf.eth0.send_redirects = 0
net.ipv4.conf.eth0.accept_source_route = 0
net.ipv4.conf.eth0.proxy_arp = 0
net.ipv4.conf.eth0.medium_id = 0
net.ipv4.conf.eth0.bootp_relay = 0
net.ipv4.conf.eth0.log_martians = 0
net.ipv4.conf.eth0.tag = 0
net.ipv4.conf.eth0.arp_filter = 0
net.ipv4.conf.eth0.arp_announce = 0
net.ipv4.conf.eth0.arp_ignore = 0
net.ipv4.conf.eth0.arp_accept = 0
net.ipv4.conf.eth0.disable_xfrm = 0
net.ipv4.conf.eth0.disable_policy = 0
net.ipv4.conf.eth0.force_igmp_version = 0
net.ipv4.conf.eth0.promote_secondaries = 0
net.ipv4.conf.eth1.forwarding = 1
net.ipv4.conf.eth1.mc_forwarding = 0
net.ipv4.conf.eth1.accept_redirects = 0
net.ipv4.conf.eth1.secure_redirects = 0
net.ipv4.conf.eth1.shared_media = 0
net.ipv4.conf.eth1.rp_filter = 0
net.ipv4.conf.eth1.send_redirects = 0
net.ipv4.conf.eth1.accept_source_route = 0
net.ipv4.conf.eth1.proxy_arp = 0
net.ipv4.conf.eth1.medium_id = 0
net.ipv4.conf.eth1.bootp_relay = 0
net.ipv4.conf.eth1.log_martians = 0
net.ipv4.conf.eth1.tag = 0
net.ipv4.conf.eth1.arp_filter = 0
net.ipv4.conf.eth1.arp_announce = 0
net.ipv4.conf.eth1.arp_ignore = 0
net.ipv4.conf.eth1.arp_accept = 0
net.ipv4.conf.eth1.disable_xfrm = 0
net.ipv4.conf.eth1.disable_policy = 0
net.ipv4.conf.eth1.force_igmp_version = 0
net.ipv4.conf.eth1.promote_secondaries = 0
net.ipv4.conf.eth2.forwarding = 1
net.ipv4.conf.eth2.mc_forwarding = 0
net.ipv4.conf.eth2.accept_redirects = 0
net.ipv4.conf.eth2.secure_redirects = 0
net.ipv4.conf.eth2.shared_media = 0
net.ipv4.conf.eth2.rp_filter = 0
net.ipv4.conf.eth2.send_redirects = 0
net.ipv4.conf.eth2.accept_source_route = 0
net.ipv4.conf.eth2.proxy_arp = 0
net.ipv4.conf.eth2.medium_id = 0
net.ipv4.conf.eth2.bootp_relay = 0
net.ipv4.conf.eth2.log_martians = 0
net.ipv4.conf.eth2.tag = 0
net.ipv4.conf.eth2.arp_filter = 0
net.ipv4.conf.eth2.arp_announce = 0
net.ipv4.conf.eth2.arp_ignore = 0
net.ipv4.conf.eth2.arp_accept = 0
net.ipv4.conf.eth2.disable_xfrm = 0
net.ipv4.conf.eth2.disable_policy = 0
net.ipv4.conf.eth2.force_igmp_version = 0
net.ipv4.conf.eth2.promote_secondaries = 0
net.ipv4.conf.pan0.forwarding = 1
net.ipv4.conf.pan0.mc_forwarding = 0
net.ipv4.conf.pan0.accept_redirects = 0
net.ipv4.conf.pan0.secure_redirects = 0
net.ipv4.conf.pan0.shared_media = 0
net.ipv4.conf.pan0.rp_filter = 0
net.ipv4.conf.pan0.send_redirects = 0
net.ipv4.conf.pan0.accept_source_route = 0
net.ipv4.conf.pan0.proxy_arp = 0
net.ipv4.conf.pan0.medium_id = 0
net.ipv4.conf.pan0.bootp_relay = 0
net.ipv4.conf.pan0.log_martians = 0
net.ipv4.conf.pan0.tag = 0
net.ipv4.conf.pan0.arp_filter = 0
net.ipv4.conf.pan0.arp_announce = 0
net.ipv4.conf.pan0.arp_ignore = 0
net.ipv4.conf.pan0.arp_accept = 0
net.ipv4.conf.pan0.disable_xfrm = 0
net.ipv4.conf.pan0.disable_policy = 0
net.ipv4.conf.pan0.force_igmp_version = 0
net.ipv4.conf.pan0.promote_secondaries = 0
net.ipv4.ip_forward = 1
net.ipv4.ipfrag_high_thresh = 262144
net.ipv4.ipfrag_low_thresh = 196608
net.ipv4.ipfrag_time = 30
net.ipv4.icmp_echo_ignore_all = 0
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.icmp_errors_use_inbound_ifaddr = 0
net.ipv4.icmp_ratelimit = 1000
net.ipv4.icmp_ratemask = 6168
net.ipv4.ipfrag_secret_interval = 600
net.ipv4.ipfrag_max_dist = 64
 
#### sysctl -a | grep ipv6 ###
 
net.ipv6.neigh.default.mcast_solicit = 3
net.ipv6.neigh.default.ucast_solicit = 3
net.ipv6.neigh.default.app_solicit = 0
net.ipv6.neigh.default.retrans_time = 250
net.ipv6.neigh.default.base_reachable_time = 30
net.ipv6.neigh.default.delay_first_probe_time = 5
net.ipv6.neigh.default.gc_stale_time = 60
net.ipv6.neigh.default.unres_qlen = 3
net.ipv6.neigh.default.proxy_qlen = 64
net.ipv6.neigh.default.anycast_delay = 100
net.ipv6.neigh.default.proxy_delay = 80
net.ipv6.neigh.default.locktime = 0
net.ipv6.neigh.default.retrans_time_ms = 1000
net.ipv6.neigh.default.base_reachable_time_ms = 30000
net.ipv6.neigh.default.gc_interval = 30
net.ipv6.neigh.default.gc_thresh1 = 128
net.ipv6.neigh.default.gc_thresh2 = 512
net.ipv6.neigh.default.gc_thresh3 = 1024
net.ipv6.neigh.lo.mcast_solicit = 3
net.ipv6.neigh.lo.ucast_solicit = 3
net.ipv6.neigh.lo.app_solicit = 0
net.ipv6.neigh.lo.retrans_time = 250
net.ipv6.neigh.lo.base_reachable_time = 30
net.ipv6.neigh.lo.delay_first_probe_time = 5
net.ipv6.neigh.lo.gc_stale_time = 60
net.ipv6.neigh.lo.unres_qlen = 3
net.ipv6.neigh.lo.proxy_qlen = 64
net.ipv6.neigh.lo.anycast_delay = 100
net.ipv6.neigh.lo.proxy_delay = 80
net.ipv6.neigh.lo.locktime = 0
net.ipv6.neigh.lo.retrans_time_ms = 1000
net.ipv6.neigh.lo.base_reachable_time_ms = 30000
net.ipv6.neigh.eth0.mcast_solicit = 3
net.ipv6.neigh.eth0.ucast_solicit = 3
net.ipv6.neigh.eth0.app_solicit = 0
net.ipv6.neigh.eth0.retrans_time = 250
net.ipv6.neigh.eth0.base_reachable_time = 30
net.ipv6.neigh.eth0.delay_first_probe_time = 5
net.ipv6.neigh.eth0.gc_stale_time = 60
net.ipv6.neigh.eth0.unres_qlen = 3
net.ipv6.neigh.eth0.proxy_qlen = 64
net.ipv6.neigh.eth0.anycast_delay = 100
net.ipv6.neigh.eth0.proxy_delay = 80
net.ipv6.neigh.eth0.locktime = 0
net.ipv6.neigh.eth0.retrans_time_ms = 1000
net.ipv6.neigh.eth0.base_reachable_time_ms = 30000
net.ipv6.neigh.eth1.mcast_solicit = 3
net.ipv6.neigh.eth1.ucast_solicit = 3
net.ipv6.neigh.eth1.app_solicit = 0
net.ipv6.neigh.eth1.retrans_time = 250
net.ipv6.neigh.eth1.base_reachable_time = 30
net.ipv6.neigh.eth1.delay_first_probe_time = 5
net.ipv6.neigh.eth1.gc_stale_time = 60
net.ipv6.neigh.eth1.unres_qlen = 3
net.ipv6.neigh.eth1.proxy_qlen = 64
net.ipv6.neigh.eth1.anycast_delay = 100
net.ipv6.neigh.eth1.proxy_delay = 80
net.ipv6.neigh.eth1.locktime = 0
net.ipv6.neigh.eth1.retrans_time_ms = 1000
net.ipv6.neigh.eth1.base_reachable_time_ms = 30000
net.ipv6.neigh.eth2.mcast_solicit = 3
net.ipv6.neigh.eth2.ucast_solicit = 3
net.ipv6.neigh.eth2.app_solicit = 0
net.ipv6.neigh.eth2.retrans_time = 250
net.ipv6.neigh.eth2.base_reachable_time = 30
net.ipv6.neigh.eth2.delay_first_probe_time = 5
net.ipv6.neigh.eth2.gc_stale_time = 60
net.ipv6.neigh.eth2.unres_qlen = 3
net.ipv6.neigh.eth2.proxy_qlen = 64
net.ipv6.neigh.eth2.anycast_delay = 100
net.ipv6.neigh.eth2.proxy_delay = 80
net.ipv6.neigh.eth2.locktime = 0
net.ipv6.neigh.eth2.retrans_time_ms = 1000
net.ipv6.neigh.eth2.base_reachable_time_ms = 30000
net.ipv6.neigh.pan0.mcast_solicit = 3
net.ipv6.neigh.pan0.ucast_solicit = 3
net.ipv6.neigh.pan0.app_solicit = 0
net.ipv6.neigh.pan0.retrans_time = 250
net.ipv6.neigh.pan0.base_reachable_time = 30
net.ipv6.neigh.pan0.delay_first_probe_time = 5
net.ipv6.neigh.pan0.gc_stale_time = 60
net.ipv6.neigh.pan0.unres_qlen = 3
net.ipv6.neigh.pan0.proxy_qlen = 64
net.ipv6.neigh.pan0.anycast_delay = 100
net.ipv6.neigh.pan0.proxy_delay = 80
net.ipv6.neigh.pan0.locktime = 0
net.ipv6.neigh.pan0.retrans_time_ms = 1000
net.ipv6.neigh.pan0.base_reachable_time_ms = 30000
net.ipv6.conf.all.forwarding = 0
net.ipv6.conf.all.hop_limit = 64
net.ipv6.conf.all.mtu = 1280
net.ipv6.conf.all.accept_ra = 1
net.ipv6.conf.all.accept_redirects = 1
net.ipv6.conf.all.autoconf = 1
net.ipv6.conf.all.dad_transmits = 1
net.ipv6.conf.all.router_solicitations = 3
net.ipv6.conf.all.router_solicitation_interval = 4
net.ipv6.conf.all.router_solicitation_delay = 1
net.ipv6.conf.all.force_mld_version = 0
net.ipv6.conf.all.use_tempaddr = 0
net.ipv6.conf.all.temp_valid_lft = 604800
net.ipv6.conf.all.temp_prefered_lft = 86400
net.ipv6.conf.all.regen_max_retry = 5
net.ipv6.conf.all.max_desync_factor = 600
net.ipv6.conf.all.max_addresses = 16
net.ipv6.conf.all.accept_ra_defrtr = 1
net.ipv6.conf.all.accept_ra_pinfo = 1
net.ipv6.conf.all.proxy_ndp = 0
net.ipv6.conf.all.accept_source_route = 0
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.all.accept_dad = 1
net.ipv6.conf.default.forwarding = 0
net.ipv6.conf.default.hop_limit = 64
net.ipv6.conf.default.mtu = 1280
net.ipv6.conf.default.accept_ra = 1
net.ipv6.conf.default.accept_redirects = 1
net.ipv6.conf.default.autoconf = 1
net.ipv6.conf.default.dad_transmits = 1
net.ipv6.conf.default.router_solicitations = 3
net.ipv6.conf.default.router_solicitation_interval = 4
net.ipv6.conf.default.router_solicitation_delay = 1
net.ipv6.conf.default.force_mld_version = 0
net.ipv6.conf.default.use_tempaddr = 0
net.ipv6.conf.default.temp_valid_lft = 604800
net.ipv6.conf.default.temp_prefered_lft = 86400
net.ipv6.conf.default.regen_max_retry = 5
net.ipv6.conf.default.max_desync_factor = 600
net.ipv6.conf.default.max_addresses = 16
net.ipv6.conf.default.accept_ra_defrtr = 1
net.ipv6.conf.default.accept_ra_pinfo = 1
net.ipv6.conf.default.proxy_ndp = 0
net.ipv6.conf.default.accept_source_route = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.default.accept_dad = 1
net.ipv6.conf.lo.forwarding = 0
net.ipv6.conf.lo.hop_limit = 64
net.ipv6.conf.lo.mtu = 16436
net.ipv6.conf.lo.accept_ra = 1
net.ipv6.conf.lo.accept_redirects = 1
net.ipv6.conf.lo.autoconf = 1
net.ipv6.conf.lo.dad_transmits = 1
net.ipv6.conf.lo.router_solicitations = 3
net.ipv6.conf.lo.router_solicitation_interval = 4
net.ipv6.conf.lo.router_solicitation_delay = 1
net.ipv6.conf.lo.force_mld_version = 0
net.ipv6.conf.lo.use_tempaddr = -1
net.ipv6.conf.lo.temp_valid_lft = 604800
net.ipv6.conf.lo.temp_prefered_lft = 86400
net.ipv6.conf.lo.regen_max_retry = 5
net.ipv6.conf.lo.max_desync_factor = 600
net.ipv6.conf.lo.max_addresses = 16
net.ipv6.conf.lo.accept_ra_defrtr = 1
net.ipv6.conf.lo.accept_ra_pinfo = 1
net.ipv6.conf.lo.proxy_ndp = 0
net.ipv6.conf.lo.accept_source_route = 0
net.ipv6.conf.lo.disable_ipv6 = 0
net.ipv6.conf.lo.accept_dad = -1
net.ipv6.conf.eth0.forwarding = 0
net.ipv6.conf.eth0.hop_limit = 64
net.ipv6.conf.eth0.mtu = 1500
net.ipv6.conf.eth0.accept_ra = 1
net.ipv6.conf.eth0.accept_redirects = 1
net.ipv6.conf.eth0.autoconf = 1
net.ipv6.conf.eth0.dad_transmits = 1
net.ipv6.conf.eth0.router_solicitations = 3
net.ipv6.conf.eth0.router_solicitation_interval = 4
net.ipv6.conf.eth0.router_solicitation_delay = 1
net.ipv6.conf.eth0.force_mld_version = 0
net.ipv6.conf.eth0.use_tempaddr = 0
net.ipv6.conf.eth0.temp_valid_lft = 604800
net.ipv6.conf.eth0.temp_prefered_lft = 86400
net.ipv6.conf.eth0.regen_max_retry = 5
net.ipv6.conf.eth0.max_desync_factor = 600
net.ipv6.conf.eth0.max_addresses = 16
net.ipv6.conf.eth0.accept_ra_defrtr = 1
net.ipv6.conf.eth0.accept_ra_pinfo = 1
net.ipv6.conf.eth0.proxy_ndp = 0
net.ipv6.conf.eth0.accept_source_route = 0
net.ipv6.conf.eth0.disable_ipv6 = 0
net.ipv6.conf.eth0.accept_dad = 1
net.ipv6.conf.eth1.forwarding = 0
net.ipv6.conf.eth1.hop_limit = 64
net.ipv6.conf.eth1.mtu = 1500
net.ipv6.conf.eth1.accept_ra = 1
net.ipv6.conf.eth1.accept_redirects = 1
net.ipv6.conf.eth1.autoconf = 1
net.ipv6.conf.eth1.dad_transmits = 1
net.ipv6.conf.eth1.router_solicitations = 3
net.ipv6.conf.eth1.router_solicitation_interval = 4
net.ipv6.conf.eth1.router_solicitation_delay = 1
net.ipv6.conf.eth1.force_mld_version = 0
net.ipv6.conf.eth1.use_tempaddr = 0
net.ipv6.conf.eth1.temp_valid_lft = 604800
net.ipv6.conf.eth1.temp_prefered_lft = 86400
net.ipv6.conf.eth1.regen_max_retry = 5
net.ipv6.conf.eth1.max_desync_factor = 600
net.ipv6.conf.eth1.max_addresses = 16
net.ipv6.conf.eth1.accept_ra_defrtr = 1
net.ipv6.conf.eth1.accept_ra_pinfo = 1
net.ipv6.conf.eth1.proxy_ndp = 0
net.ipv6.conf.eth1.accept_source_route = 0
net.ipv6.conf.eth1.disable_ipv6 = 0
net.ipv6.conf.eth1.accept_dad = 1
net.ipv6.conf.eth2.forwarding = 0
net.ipv6.conf.eth2.hop_limit = 64
net.ipv6.conf.eth2.mtu = 1500
net.ipv6.conf.eth2.accept_ra = 1
net.ipv6.conf.eth2.accept_redirects = 1
net.ipv6.conf.eth2.autoconf = 1
net.ipv6.conf.eth2.dad_transmits = 1
net.ipv6.conf.eth2.router_solicitations = 3
net.ipv6.conf.eth2.router_solicitation_interval = 4
net.ipv6.conf.eth2.router_solicitation_delay = 1
net.ipv6.conf.eth2.force_mld_version = 0
net.ipv6.conf.eth2.use_tempaddr = 0
net.ipv6.conf.eth2.temp_valid_lft = 604800
net.ipv6.conf.eth2.temp_prefered_lft = 86400
net.ipv6.conf.eth2.regen_max_retry = 5
net.ipv6.conf.eth2.max_desync_factor = 600
net.ipv6.conf.eth2.max_addresses = 16
net.ipv6.conf.eth2.accept_ra_defrtr = 1
net.ipv6.conf.eth2.accept_ra_pinfo = 1
net.ipv6.conf.eth2.proxy_ndp = 0
net.ipv6.conf.eth2.accept_source_route = 0
net.ipv6.conf.eth2.disable_ipv6 = 0
net.ipv6.conf.eth2.accept_dad = 1
net.ipv6.conf.pan0.forwarding = 0
net.ipv6.conf.pan0.hop_limit = 64
net.ipv6.conf.pan0.mtu = 1500
net.ipv6.conf.pan0.accept_ra = 1
net.ipv6.conf.pan0.accept_redirects = 1
net.ipv6.conf.pan0.autoconf = 1
net.ipv6.conf.pan0.dad_transmits = 1
net.ipv6.conf.pan0.router_solicitations = 3
net.ipv6.conf.pan0.router_solicitation_interval = 4
net.ipv6.conf.pan0.router_solicitation_delay = 1
net.ipv6.conf.pan0.force_mld_version = 0
net.ipv6.conf.pan0.use_tempaddr = 0
net.ipv6.conf.pan0.temp_valid_lft = 604800
net.ipv6.conf.pan0.temp_prefered_lft = 86400
net.ipv6.conf.pan0.regen_max_retry = 5
net.ipv6.conf.pan0.max_desync_factor = 600
net.ipv6.conf.pan0.max_addresses = 16
net.ipv6.conf.pan0.accept_ra_defrtr = 1
net.ipv6.conf.pan0.accept_ra_pinfo = 1
net.ipv6.conf.pan0.proxy_ndp = 0
net.ipv6.conf.pan0.accept_source_route = 0
net.ipv6.conf.pan0.disable_ipv6 = 0
net.ipv6.conf.pan0.accept_dad = 1
net.ipv6.ip6frag_high_thresh = 262144
net.ipv6.ip6frag_low_thresh = 196608
net.ipv6.ip6frag_time = 60
net.ipv6.route.gc_thresh = 1024
net.ipv6.route.max_size = 4096
net.ipv6.route.gc_min_interval = 0
net.ipv6.route.gc_timeout = 60
net.ipv6.route.gc_interval = 30
net.ipv6.route.gc_elasticity = 0
net.ipv6.route.mtu_expires = 600
net.ipv6.route.min_adv_mss = 4
net.ipv6.route.gc_min_interval_ms = 500
net.ipv6.icmp.ratelimit = 1000
net.ipv6.bindv6only = 0
net.ipv6.ip6frag_secret_interval = 600
net.ipv6.mld_max_msf = 64
 
#### sysctl -a | grep ipv6 ###
 
net.core.wmem_max = 131071
net.core.rmem_max = 131071
net.core.wmem_default = 112640
net.core.rmem_default = 112640
net.core.dev_weight = 64
net.core.netdev_max_backlog = 1000
net.core.message_cost = 5
net.core.message_burst = 10
net.core.optmem_max = 10240
net.core.xfrm_aevent_etime = 10
net.core.xfrm_aevent_rseqth = 2
net.core.xfrm_larval_drop = 0
net.core.xfrm_acq_expires = 30
net.core.netdev_budget = 300
net.core.warnings = 1
net.core.somaxconn = 128
 

 
 
sysctl-6.txt (for gateway 6)
 
> 
### sysctl -a | grep ipv4 ###
 
net.ipv4.route.gc_thresh = 32768
net.ipv4.route.max_size = 524288
net.ipv4.route.gc_min_interval = 0
net.ipv4.route.gc_min_interval_ms = 500
net.ipv4.route.gc_timeout = 300
net.ipv4.route.gc_interval = 60
net.ipv4.route.redirect_load = 5
net.ipv4.route.redirect_number = 9
net.ipv4.route.redirect_silence = 5120
net.ipv4.route.error_cost = 250
net.ipv4.route.error_burst = 1250
net.ipv4.route.gc_elasticity = 8
net.ipv4.route.mtu_expires = 600
net.ipv4.route.min_pmtu = 552
net.ipv4.route.min_adv_mss = 256
net.ipv4.route.secret_interval = 600
net.ipv4.neigh.default.mcast_solicit = 3
net.ipv4.neigh.default.ucast_solicit = 3
net.ipv4.neigh.default.app_solicit = 0
net.ipv4.neigh.default.retrans_time = 100
net.ipv4.neigh.default.base_reachable_time = 30
net.ipv4.neigh.default.delay_first_probe_time = 5
net.ipv4.neigh.default.gc_stale_time = 60
net.ipv4.neigh.default.unres_qlen = 3
net.ipv4.neigh.default.proxy_qlen = 64
net.ipv4.neigh.default.anycast_delay = 100
net.ipv4.neigh.default.proxy_delay = 80
net.ipv4.neigh.default.locktime = 100
net.ipv4.neigh.default.retrans_time_ms = 1000
net.ipv4.neigh.default.base_reachable_time_ms = 30000
net.ipv4.neigh.default.gc_interval = 30
net.ipv4.neigh.default.gc_thresh1 = 1024
net.ipv4.neigh.default.gc_thresh2 = 2048
net.ipv4.neigh.default.gc_thresh3 = 8192
net.ipv4.neigh.lo.mcast_solicit = 3
net.ipv4.neigh.lo.ucast_solicit = 3
net.ipv4.neigh.lo.app_solicit = 0
net.ipv4.neigh.lo.retrans_time = 100
net.ipv4.neigh.lo.base_reachable_time = 30
net.ipv4.neigh.lo.delay_first_probe_time = 5
net.ipv4.neigh.lo.gc_stale_time = 60
net.ipv4.neigh.lo.unres_qlen = 3
net.ipv4.neigh.lo.proxy_qlen = 64
net.ipv4.neigh.lo.anycast_delay = 100
net.ipv4.neigh.lo.proxy_delay = 80
net.ipv4.neigh.lo.locktime = 100
net.ipv4.neigh.lo.retrans_time_ms = 1000
net.ipv4.neigh.lo.base_reachable_time_ms = 30000
net.ipv4.neigh.eth0.mcast_solicit = 3
net.ipv4.neigh.eth0.ucast_solicit = 3
net.ipv4.neigh.eth0.app_solicit = 0
net.ipv4.neigh.eth0.retrans_time = 100
net.ipv4.neigh.eth0.base_reachable_time = 30
net.ipv4.neigh.eth0.delay_first_probe_time = 5
net.ipv4.neigh.eth0.gc_stale_time = 60
net.ipv4.neigh.eth0.unres_qlen = 3
net.ipv4.neigh.eth0.proxy_qlen = 64
net.ipv4.neigh.eth0.anycast_delay = 100
net.ipv4.neigh.eth0.proxy_delay = 80
net.ipv4.neigh.eth0.locktime = 100
net.ipv4.neigh.eth0.retrans_time_ms = 1000
net.ipv4.neigh.eth0.base_reachable_time_ms = 30000
net.ipv4.neigh.eth1.mcast_solicit = 3
net.ipv4.neigh.eth1.ucast_solicit = 3
net.ipv4.neigh.eth1.app_solicit = 0
net.ipv4.neigh.eth1.retrans_time = 100
net.ipv4.neigh.eth1.base_reachable_time = 30
net.ipv4.neigh.eth1.delay_first_probe_time = 5
net.ipv4.neigh.eth1.gc_stale_time = 60
net.ipv4.neigh.eth1.unres_qlen = 3
net.ipv4.neigh.eth1.proxy_qlen = 64
net.ipv4.neigh.eth1.anycast_delay = 100
net.ipv4.neigh.eth1.proxy_delay = 80
net.ipv4.neigh.eth1.locktime = 100
net.ipv4.neigh.eth1.retrans_time_ms = 1000
net.ipv4.neigh.eth1.base_reachable_time_ms = 30000
net.ipv4.neigh.pan0.mcast_solicit = 3
net.ipv4.neigh.pan0.ucast_solicit = 3
net.ipv4.neigh.pan0.app_solicit = 0
net.ipv4.neigh.pan0.retrans_time = 100
net.ipv4.neigh.pan0.base_reachable_time = 30
net.ipv4.neigh.pan0.delay_first_probe_time = 5
net.ipv4.neigh.pan0.gc_stale_time = 60
net.ipv4.neigh.pan0.unres_qlen = 3
net.ipv4.neigh.pan0.proxy_qlen = 64
net.ipv4.neigh.pan0.anycast_delay = 100
net.ipv4.neigh.pan0.proxy_delay = 80
net.ipv4.neigh.pan0.locktime = 100
net.ipv4.neigh.pan0.retrans_time_ms = 1000
net.ipv4.neigh.pan0.base_reachable_time_ms = 30000
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_sack = 0
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.ip_default_ttl = 64
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.ip_nonlocal_bind = 0
net.ipv4.tcp_syn_retries = 5
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_max_orphans = 32768
net.ipv4.tcp_max_tw_buckets = 180000
net.ipv4.ip_dynaddr = 0
net.ipv4.tcp_keepalive_time = 2400
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_max_syn_backlog = 1280
net.ipv4.ip_local_port_range = 32768 61000
net.ipv4.igmp_max_memberships = 20
net.ipv4.igmp_max_msf = 10
net.ipv4.inet_peer_threshold = 65664
net.ipv4.inet_peer_minttl = 120
net.ipv4.inet_peer_maxttl = 600
net.ipv4.inet_peer_gc_mintime = 10
net.ipv4.inet_peer_gc_maxtime = 120
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_ecn = 0
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_mem = 82080 109440 164160
net.ipv4.tcp_wmem = 4096 16384 3502080
net.ipv4.tcp_rmem = 4096 87380 3502080
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_adv_win_scale = 2
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_frto = 2
net.ipv4.tcp_frto_response = 0
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_abc = 0
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_base_mss = 512
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.tcp_dma_copybreak = 4096
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.cipso_cache_enable = 1
net.ipv4.cipso_cache_bucket_size = 10
net.ipv4.cipso_rbm_optfmt = 0
net.ipv4.cipso_rbm_strictvalid = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_max_ssthresh = 0
net.ipv4.udp_mem = 291936 389248 583872
net.ipv4.udp_rmem_min = 4096
net.ipv4.udp_wmem_min = 4096
net.ipv4.netfilter.ip_conntrack_generic_timeout = 600
net.ipv4.netfilter.ip_conntrack_tcp_timeout_syn_sent = 120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_syn_recv = 60
net.ipv4.netfilter.ip_conntrack_tcp_timeout_established = 432000
net.ipv4.netfilter.ip_conntrack_tcp_timeout_fin_wait = 120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_close_wait = 60
net.ipv4.netfilter.ip_conntrack_tcp_timeout_last_ack = 30
net.ipv4.netfilter.ip_conntrack_tcp_timeout_time_wait = 120
net.ipv4.netfilter.ip_conntrack_tcp_timeout_close = 10
net.ipv4.netfilter.ip_conntrack_tcp_timeout_max_retrans = 300
net.ipv4.netfilter.ip_conntrack_tcp_loose = 1
net.ipv4.netfilter.ip_conntrack_tcp_be_liberal = 0
net.ipv4.netfilter.ip_conntrack_tcp_max_retrans = 3
net.ipv4.netfilter.ip_conntrack_udp_timeout = 30
net.ipv4.netfilter.ip_conntrack_udp_timeout_stream = 180
net.ipv4.netfilter.ip_conntrack_icmp_timeout = 30
net.ipv4.netfilter.ip_conntrack_max = 65536
net.ipv4.netfilter.ip_conntrack_count = 23
net.ipv4.netfilter.ip_conntrack_buckets = 16384
net.ipv4.netfilter.ip_conntrack_checksum = 1
net.ipv4.netfilter.ip_conntrack_log_invalid = 0
net.ipv4.conf.all.forwarding = 1
net.ipv4.conf.all.mc_forwarding = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.all.shared_media = 0
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.all.proxy_arp = 0
net.ipv4.conf.all.medium_id = 0
net.ipv4.conf.all.bootp_relay = 0
net.ipv4.conf.all.log_martians = 0
net.ipv4.conf.all.tag = 0
net.ipv4.conf.all.arp_filter = 0
net.ipv4.conf.all.arp_announce = 0
net.ipv4.conf.all.arp_ignore = 0
net.ipv4.conf.all.arp_accept = 0
net.ipv4.conf.all.disable_xfrm = 0
net.ipv4.conf.all.disable_policy = 0
net.ipv4.conf.all.force_igmp_version = 0
net.ipv4.conf.all.promote_secondaries = 0
net.ipv4.conf.default.forwarding = 1
net.ipv4.conf.default.mc_forwarding = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.conf.default.shared_media = 0
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.conf.default.proxy_arp = 0
net.ipv4.conf.default.medium_id = 0
net.ipv4.conf.default.bootp_relay = 0
net.ipv4.conf.default.log_martians = 0
net.ipv4.conf.default.tag = 0
net.ipv4.conf.default.arp_filter = 0
net.ipv4.conf.default.arp_announce = 0
net.ipv4.conf.default.arp_ignore = 0
net.ipv4.conf.default.arp_accept = 0
net.ipv4.conf.default.disable_xfrm = 0
net.ipv4.conf.default.disable_policy = 0
net.ipv4.conf.default.force_igmp_version = 0
net.ipv4.conf.default.promote_secondaries = 0
net.ipv4.conf.lo.forwarding = 1
net.ipv4.conf.lo.mc_forwarding = 0
net.ipv4.conf.lo.accept_redirects = 0
net.ipv4.conf.lo.secure_redirects = 0
net.ipv4.conf.lo.shared_media = 0
net.ipv4.conf.lo.rp_filter = 0
net.ipv4.conf.lo.send_redirects = 0
net.ipv4.conf.lo.accept_source_route = 0
net.ipv4.conf.lo.proxy_arp = 0
net.ipv4.conf.lo.medium_id = 0
net.ipv4.conf.lo.bootp_relay = 0
net.ipv4.conf.lo.log_martians = 0
net.ipv4.conf.lo.tag = 0
net.ipv4.conf.lo.arp_filter = 0
net.ipv4.conf.lo.arp_announce = 0
net.ipv4.conf.lo.arp_ignore = 0
net.ipv4.conf.lo.arp_accept = 0
net.ipv4.conf.lo.disable_xfrm = 1
net.ipv4.conf.lo.disable_policy = 1
net.ipv4.conf.lo.force_igmp_version = 0
net.ipv4.conf.lo.promote_secondaries = 0
net.ipv4.conf.eth0.forwarding = 1
net.ipv4.conf.eth0.mc_forwarding = 0
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.eth0.secure_redirects = 0
net.ipv4.conf.eth0.shared_media = 0
net.ipv4.conf.eth0.rp_filter = 0
net.ipv4.conf.eth0.send_redirects = 0
net.ipv4.conf.eth0.accept_source_route = 0
net.ipv4.conf.eth0.proxy_arp = 0
net.ipv4.conf.eth0.medium_id = 0
net.ipv4.conf.eth0.bootp_relay = 0
net.ipv4.conf.eth0.log_martians = 0
net.ipv4.conf.eth0.tag = 0
net.ipv4.conf.eth0.arp_filter = 0
net.ipv4.conf.eth0.arp_announce = 0
net.ipv4.conf.eth0.arp_ignore = 0
net.ipv4.conf.eth0.arp_accept = 0
net.ipv4.conf.eth0.disable_xfrm = 0
net.ipv4.conf.eth0.disable_policy = 0
net.ipv4.conf.eth0.force_igmp_version = 0
net.ipv4.conf.eth0.promote_secondaries = 0
net.ipv4.conf.eth1.forwarding = 1
net.ipv4.conf.eth1.mc_forwarding = 0
net.ipv4.conf.eth1.accept_redirects = 0
net.ipv4.conf.eth1.secure_redirects = 0
net.ipv4.conf.eth1.shared_media = 0
net.ipv4.conf.eth1.rp_filter = 0
net.ipv4.conf.eth1.send_redirects = 0
net.ipv4.conf.eth1.accept_source_route = 0
net.ipv4.conf.eth1.proxy_arp = 0
net.ipv4.conf.eth1.medium_id = 0
net.ipv4.conf.eth1.bootp_relay = 0
net.ipv4.conf.eth1.log_martians = 0
net.ipv4.conf.eth1.tag = 0
net.ipv4.conf.eth1.arp_filter = 0
net.ipv4.conf.eth1.arp_announce = 0
net.ipv4.conf.eth1.arp_ignore = 0
net.ipv4.conf.eth1.arp_accept = 0
net.ipv4.conf.eth1.disable_xfrm = 0
net.ipv4.conf.eth1.disable_policy = 0
net.ipv4.conf.eth1.force_igmp_version = 0
net.ipv4.conf.eth1.promote_secondaries = 0
net.ipv4.conf.pan0.forwarding = 1
net.ipv4.conf.pan0.mc_forwarding = 0
net.ipv4.conf.pan0.accept_redirects = 0
net.ipv4.conf.pan0.secure_redirects = 0
net.ipv4.conf.pan0.shared_media = 0
net.ipv4.conf.pan0.rp_filter = 0
net.ipv4.conf.pan0.send_redirects = 0
net.ipv4.conf.pan0.accept_source_route = 0
net.ipv4.conf.pan0.proxy_arp = 0
net.ipv4.conf.pan0.medium_id = 0
net.ipv4.conf.pan0.bootp_relay = 0
net.ipv4.conf.pan0.log_martians = 0
net.ipv4.conf.pan0.tag = 0
net.ipv4.conf.pan0.arp_filter = 0
net.ipv4.conf.pan0.arp_announce = 0
net.ipv4.conf.pan0.arp_ignore = 0
net.ipv4.conf.pan0.arp_accept = 0
net.ipv4.conf.pan0.disable_xfrm = 0
net.ipv4.conf.pan0.disable_policy = 0
net.ipv4.conf.pan0.force_igmp_version = 0
net.ipv4.conf.pan0.promote_secondaries = 0
net.ipv4.ip_forward = 1
net.ipv4.ipfrag_high_thresh = 262144
net.ipv4.ipfrag_low_thresh = 196608
net.ipv4.ipfrag_time = 30
net.ipv4.icmp_echo_ignore_all = 0
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.icmp_errors_use_inbound_ifaddr = 0
net.ipv4.icmp_ratelimit = 1000
net.ipv4.icmp_ratemask = 6168
net.ipv4.ipfrag_secret_interval = 600
net.ipv4.ipfrag_max_dist = 64
 
### sysctl -a | grep ipv6 ###
 
net.ipv6.neigh.default.mcast_solicit = 3
net.ipv6.neigh.default.ucast_solicit = 3
net.ipv6.neigh.default.app_solicit = 0
net.ipv6.neigh.default.retrans_time = 250
net.ipv6.neigh.default.base_reachable_time = 30
net.ipv6.neigh.default.delay_first_probe_time = 5
net.ipv6.neigh.default.gc_stale_time = 60
net.ipv6.neigh.default.unres_qlen = 3
net.ipv6.neigh.default.proxy_qlen = 64
net.ipv6.neigh.default.anycast_delay = 100
net.ipv6.neigh.default.proxy_delay = 80
net.ipv6.neigh.default.locktime = 0
net.ipv6.neigh.default.retrans_time_ms = 1000
net.ipv6.neigh.default.base_reachable_time_ms = 30000
net.ipv6.neigh.default.gc_interval = 30
net.ipv6.neigh.default.gc_thresh1 = 128
net.ipv6.neigh.default.gc_thresh2 = 512
net.ipv6.neigh.default.gc_thresh3 = 1024
net.ipv6.neigh.lo.mcast_solicit = 3
net.ipv6.neigh.lo.ucast_solicit = 3
net.ipv6.neigh.lo.app_solicit = 0
net.ipv6.neigh.lo.retrans_time = 250
net.ipv6.neigh.lo.base_reachable_time = 30
net.ipv6.neigh.lo.delay_first_probe_time = 5
net.ipv6.neigh.lo.gc_stale_time = 60
net.ipv6.neigh.lo.unres_qlen = 3
net.ipv6.neigh.lo.proxy_qlen = 64
net.ipv6.neigh.lo.anycast_delay = 100
net.ipv6.neigh.lo.proxy_delay = 80
net.ipv6.neigh.lo.locktime = 0
net.ipv6.neigh.lo.retrans_time_ms = 1000
net.ipv6.neigh.lo.base_reachable_time_ms = 30000
net.ipv6.neigh.eth0.mcast_solicit = 3
net.ipv6.neigh.eth0.ucast_solicit = 3
net.ipv6.neigh.eth0.app_solicit = 0
net.ipv6.neigh.eth0.retrans_time = 250
net.ipv6.neigh.eth0.base_reachable_time = 30
net.ipv6.neigh.eth0.delay_first_probe_time = 5
net.ipv6.neigh.eth0.gc_stale_time = 60
net.ipv6.neigh.eth0.unres_qlen = 3
net.ipv6.neigh.eth0.proxy_qlen = 64
net.ipv6.neigh.eth0.anycast_delay = 100
net.ipv6.neigh.eth0.proxy_delay = 80
net.ipv6.neigh.eth0.locktime = 0
net.ipv6.neigh.eth0.retrans_time_ms = 1000
net.ipv6.neigh.eth0.base_reachable_time_ms = 30000
net.ipv6.neigh.eth1.mcast_solicit = 3
net.ipv6.neigh.eth1.ucast_solicit = 3
net.ipv6.neigh.eth1.app_solicit = 0
net.ipv6.neigh.eth1.retrans_time = 250
net.ipv6.neigh.eth1.base_reachable_time = 30
net.ipv6.neigh.eth1.delay_first_probe_time = 5
net.ipv6.neigh.eth1.gc_stale_time = 60
net.ipv6.neigh.eth1.unres_qlen = 3
net.ipv6.neigh.eth1.proxy_qlen = 64
net.ipv6.neigh.eth1.anycast_delay = 100
net.ipv6.neigh.eth1.proxy_delay = 80
net.ipv6.neigh.eth1.locktime = 0
net.ipv6.neigh.eth1.retrans_time_ms = 1000
net.ipv6.neigh.eth1.base_reachable_time_ms = 30000
net.ipv6.neigh.pan0.mcast_solicit = 3
net.ipv6.neigh.pan0.ucast_solicit = 3
net.ipv6.neigh.pan0.app_solicit = 0
net.ipv6.neigh.pan0.retrans_time = 250
net.ipv6.neigh.pan0.base_reachable_time = 30
net.ipv6.neigh.pan0.delay_first_probe_time = 5
net.ipv6.neigh.pan0.gc_stale_time = 60
net.ipv6.neigh.pan0.unres_qlen = 3
net.ipv6.neigh.pan0.proxy_qlen = 64
net.ipv6.neigh.pan0.anycast_delay = 100
net.ipv6.neigh.pan0.proxy_delay = 80
net.ipv6.neigh.pan0.locktime = 0
net.ipv6.neigh.pan0.retrans_time_ms = 1000
net.ipv6.neigh.pan0.base_reachable_time_ms = 30000
net.ipv6.conf.all.forwarding = 0
net.ipv6.conf.all.hop_limit = 64
net.ipv6.conf.all.mtu = 1280
net.ipv6.conf.all.accept_ra = 1
net.ipv6.conf.all.accept_redirects = 1
net.ipv6.conf.all.autoconf = 1
net.ipv6.conf.all.dad_transmits = 1
net.ipv6.conf.all.router_solicitations = 3
net.ipv6.conf.all.router_solicitation_interval = 4
net.ipv6.conf.all.router_solicitation_delay = 1
net.ipv6.conf.all.force_mld_version = 0
net.ipv6.conf.all.use_tempaddr = 0
net.ipv6.conf.all.temp_valid_lft = 604800
net.ipv6.conf.all.temp_prefered_lft = 86400
net.ipv6.conf.all.regen_max_retry = 5
net.ipv6.conf.all.max_desync_factor = 600
net.ipv6.conf.all.max_addresses = 16
net.ipv6.conf.all.accept_ra_defrtr = 1
net.ipv6.conf.all.accept_ra_pinfo = 1
net.ipv6.conf.all.proxy_ndp = 0
net.ipv6.conf.all.accept_source_route = 0
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.all.accept_dad = 1
net.ipv6.conf.default.forwarding = 0
net.ipv6.conf.default.hop_limit = 64
net.ipv6.conf.default.mtu = 1280
net.ipv6.conf.default.accept_ra = 1
net.ipv6.conf.default.accept_redirects = 1
net.ipv6.conf.default.autoconf = 1
net.ipv6.conf.default.dad_transmits = 1
net.ipv6.conf.default.router_solicitations = 3
net.ipv6.conf.default.router_solicitation_interval = 4
net.ipv6.conf.default.router_solicitation_delay = 1
net.ipv6.conf.default.force_mld_version = 0
net.ipv6.conf.default.use_tempaddr = 0
net.ipv6.conf.default.temp_valid_lft = 604800
net.ipv6.conf.default.temp_prefered_lft = 86400
net.ipv6.conf.default.regen_max_retry = 5
net.ipv6.conf.default.max_desync_factor = 600
net.ipv6.conf.default.max_addresses = 16
net.ipv6.conf.default.accept_ra_defrtr = 1
net.ipv6.conf.default.accept_ra_pinfo = 1
net.ipv6.conf.default.proxy_ndp = 0
net.ipv6.conf.default.accept_source_route = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.default.accept_dad = 1
net.ipv6.conf.lo.forwarding = 0
net.ipv6.conf.lo.hop_limit = 64
net.ipv6.conf.lo.mtu = 16436
net.ipv6.conf.lo.accept_ra = 1
net.ipv6.conf.lo.accept_redirects = 1
net.ipv6.conf.lo.autoconf = 1
net.ipv6.conf.lo.dad_transmits = 1
net.ipv6.conf.lo.router_solicitations = 3
net.ipv6.conf.lo.router_solicitation_interval = 4
net.ipv6.conf.lo.router_solicitation_delay = 1
net.ipv6.conf.lo.force_mld_version = 0
net.ipv6.conf.lo.use_tempaddr = -1
net.ipv6.conf.lo.temp_valid_lft = 604800
net.ipv6.conf.lo.temp_prefered_lft = 86400
net.ipv6.conf.lo.regen_max_retry = 5
net.ipv6.conf.lo.max_desync_factor = 600
net.ipv6.conf.lo.max_addresses = 16
net.ipv6.conf.lo.accept_ra_defrtr = 1
net.ipv6.conf.lo.accept_ra_pinfo = 1
net.ipv6.conf.lo.proxy_ndp = 0
net.ipv6.conf.lo.accept_source_route = 0
net.ipv6.conf.lo.disable_ipv6 = 0
net.ipv6.conf.lo.accept_dad = -1
net.ipv6.conf.eth0.forwarding = 0
net.ipv6.conf.eth0.hop_limit = 64
net.ipv6.conf.eth0.mtu = 1500
net.ipv6.conf.eth0.accept_ra = 1
net.ipv6.conf.eth0.accept_redirects = 1
net.ipv6.conf.eth0.autoconf = 1
net.ipv6.conf.eth0.dad_transmits = 1
net.ipv6.conf.eth0.router_solicitations = 3
net.ipv6.conf.eth0.router_solicitation_interval = 4
net.ipv6.conf.eth0.router_solicitation_delay = 1
net.ipv6.conf.eth0.force_mld_version = 0
net.ipv6.conf.eth0.use_tempaddr = 0
net.ipv6.conf.eth0.temp_valid_lft = 604800
net.ipv6.conf.eth0.temp_prefered_lft = 86400
net.ipv6.conf.eth0.regen_max_retry = 5
net.ipv6.conf.eth0.max_desync_factor = 600
net.ipv6.conf.eth0.max_addresses = 16
net.ipv6.conf.eth0.accept_ra_defrtr = 1
net.ipv6.conf.eth0.accept_ra_pinfo = 1
net.ipv6.conf.eth0.proxy_ndp = 0
net.ipv6.conf.eth0.accept_source_route = 0
net.ipv6.conf.eth0.disable_ipv6 = 0
net.ipv6.conf.eth0.accept_dad = 1
net.ipv6.conf.eth1.forwarding = 0
net.ipv6.conf.eth1.hop_limit = 64
net.ipv6.conf.eth1.mtu = 1500
net.ipv6.conf.eth1.accept_ra = 1
net.ipv6.conf.eth1.accept_redirects = 1
net.ipv6.conf.eth1.autoconf = 1
net.ipv6.conf.eth1.dad_transmits = 1
net.ipv6.conf.eth1.router_solicitations = 3
net.ipv6.conf.eth1.router_solicitation_interval = 4
net.ipv6.conf.eth1.router_solicitation_delay = 1
net.ipv6.conf.eth1.force_mld_version = 0
net.ipv6.conf.eth1.use_tempaddr = 0
net.ipv6.conf.eth1.temp_valid_lft = 604800
net.ipv6.conf.eth1.temp_prefered_lft = 86400
net.ipv6.conf.eth1.regen_max_retry = 5
net.ipv6.conf.eth1.max_desync_factor = 600
net.ipv6.conf.eth1.max_addresses = 16
net.ipv6.conf.eth1.accept_ra_defrtr = 1
net.ipv6.conf.eth1.accept_ra_pinfo = 1
net.ipv6.conf.eth1.proxy_ndp = 0
net.ipv6.conf.eth1.accept_source_route = 0
net.ipv6.conf.eth1.disable_ipv6 = 0
net.ipv6.conf.eth1.accept_dad = 1
net.ipv6.conf.pan0.forwarding = 0
net.ipv6.conf.pan0.hop_limit = 64
net.ipv6.conf.pan0.mtu = 1500
net.ipv6.conf.pan0.accept_ra = 1
net.ipv6.conf.pan0.accept_redirects = 1
net.ipv6.conf.pan0.autoconf = 1
net.ipv6.conf.pan0.dad_transmits = 1
net.ipv6.conf.pan0.router_solicitations = 3
net.ipv6.conf.pan0.router_solicitation_interval = 4
net.ipv6.conf.pan0.router_solicitation_delay = 1
net.ipv6.conf.pan0.force_mld_version = 0
net.ipv6.conf.pan0.use_tempaddr = 0
net.ipv6.conf.pan0.temp_valid_lft = 604800
net.ipv6.conf.pan0.temp_prefered_lft = 86400
net.ipv6.conf.pan0.regen_max_retry = 5
net.ipv6.conf.pan0.max_desync_factor = 600
net.ipv6.conf.pan0.max_addresses = 16
net.ipv6.conf.pan0.accept_ra_defrtr = 1
net.ipv6.conf.pan0.accept_ra_pinfo = 1
net.ipv6.conf.pan0.proxy_ndp = 0
net.ipv6.conf.pan0.accept_source_route = 0
net.ipv6.conf.pan0.disable_ipv6 = 0
net.ipv6.conf.pan0.accept_dad = 1
net.ipv6.ip6frag_high_thresh = 262144
net.ipv6.ip6frag_low_thresh = 196608
net.ipv6.ip6frag_time = 60
net.ipv6.route.gc_thresh = 1024
net.ipv6.route.max_size = 4096
net.ipv6.route.gc_min_interval = 0
net.ipv6.route.gc_timeout = 60
net.ipv6.route.gc_interval = 30
net.ipv6.route.gc_elasticity = 0
net.ipv6.route.mtu_expires = 600
net.ipv6.route.min_adv_mss = 4
net.ipv6.route.gc_min_interval_ms = 500
net.ipv6.icmp.ratelimit = 1000
net.ipv6.bindv6only = 0
net.ipv6.ip6frag_secret_interval = 600
net.ipv6.mld_max_msf = 64
 
 
### sysctl -a | gre net.core ###
 
net.core.wmem_max = 131071
net.core.rmem_max = 131071
net.core.wmem_default = 112640
net.core.rmem_default = 112640
net.core.dev_weight = 64
net.core.netdev_max_backlog = 1000
net.core.message_cost = 5
net.core.message_burst = 10
net.core.optmem_max = 10240
net.core.xfrm_aevent_etime = 10
net.core.xfrm_aevent_rseqth = 2
net.core.xfrm_larval_drop = 0
net.core.xfrm_acq_expires = 30
net.core.netdev_budget = 300
net.core.warnings = 1
net.core.somaxconn = 128
 

 
Both running Ubuntu.
 
Please let me know how will i be able to configure squid at this scale.

---

### Post by dragos2 on 2009-06-28
Try change somaxconn to 8192 or higher (this implies another option-I will get back later with the name), also increase the socket IO buffers and let me know if anything changes.

---

### Post by mudasir on 2009-06-28
Hi,
 
Everything was working fine, just by changing somaxcon to 8192, my support phones started to ring, becasue the browsing become dead slow, and i was even unable to connect to the server remotely. There must be something wrong with this.

---

### Post by dragos2 on 2009-06-29
net.core.netdev_max_backlog = 1000 should have been changed too 
try something a little bigger than somaxconn like 
netdev_max_backlog = 32000

Please tell me if its working now. If not I will think more.

---

### Post by mudasir on 2009-06-29
Hi, 
 
Can you tell me what these parameters do, so that it will become more clear to me what i am doing.

---

### Post by mudasir on 2009-06-29
Hi,
 
By the way i have never changed these value in RedHat, still it used to perfect great.
And as these are kernel parameters, it should be similar or same in both.

---

### Post by dragos2 on 2009-06-29
> **mudasir said:**
> Hi, 
 
Can you tell me what these parameters do, so that it will become more clear to me what i am doing.

Yes, the somaxconn can be increased but is of no effect if the devlog is not increased too
as I stated in the previous post. It should get you some performance hit this way.

Did you tried varnish ? It is said to be faster than squid, and better.

---

### Post by dragos2 on 2009-06-29
> **mudasir said:**
> Hi,
 
By the way i have never changed these value in RedHat, still it used to perfect great.
And as these are kernel parameters, it should be similar or same in both.

Read this please, the linux section

[http://varnish.projects.linpro.no/wiki/Performance](http://varnish.projects.linpro.no/wiki/Performance)

---

### Post by mudasir on 2009-06-29
Dear thanks for your quick reply.
 
The only thing i dont understand is why it is creating problems in ubuntu, as i dont have any issue in configuring it in RedHat.
 
Right now i have 1 Server running CentOS, and it is working great, having no problem at all.
 
I also tried to copy the squid.conf file from that server, as that is also running squid2.7. Still it did not work great.

---

### Post by dragos2 on 2009-06-30
It is hard to tell. Can you try to find the bottleneck ?
Useful commands: top, vmstat, iostat, sar, pmap, iptraf, etc.

Somewhere should be a bottlneck.

---

### Post by mudasir on 2009-06-30
Hi,
 
Dear the thing is, when i allow my clients direct connection to internet without squid, everything works great, as soon as i deploy squid in between, the browsing dies.
 
So i can say this for sure, that there is something wrong with squid.
 
One more thing, right now i am using Ubuntu Desktop Version. Can this also affect.

---

### Post by dragos2 on 2009-06-30
> **mudasir said:**
> Hi,
 
Dear the thing is, when i allow my clients direct connection to internet without squid, everything works great, as soon as i deploy squid in between, the browsing dies.
 
So i can say this for sure, that there is something wrong with squid.
 
One more thing, right now i am using Ubuntu Desktop Version. Can this also affect.

Desktop version.. I am sorry but this is a major problem.

---

### Post by mudasir on 2009-06-30
Should i install Server Version, as i have it with me.

---

### Post by dragos2 on 2009-06-30
Highly recommended.

---

### Post by mudasir on 2009-06-30
Which version would you recommend...i have version 8

---

