---
title: "Intermittent network connection issue with OVS 1.10.2"
date: 2014-04-24
forum: Virtualisation
---

### Post by vivekraghuwanshi on 2014-04-24
Hi All,
    
    I have deployed OpenStack Multi node Havana for provisioning VMs     using ESXi as hypervisor.
    However, OpenStack instances looses network connectivity every so     often.
    
    [COLOR=#000000]We could         see the ARP reply on the GRE tunnel on the network node, but we         don't see it in the tcpdump 
        on the 'qr-xxx' interface of the qrouter namespace.For some         strange reason, br-tun does not 
        pass ARP reply to qr-xxx on network node.
        
        Please find more details below.
        
        ESXi version : 5.5.0
        OVS version : 1.10.2
        
        compute1 : 172.16.39.156
        compute2 : 172.16.39.155
        neutron node : 172.16.39.200
        
        Please find below packet flow when we ping VM from external         world and VM is not reachable.
        
        10.230.39.163 is floating and 10.10.10.2 is private IP of VM. 
        
        C:\> ping 10.230.39.163 -t
        
        Pinging 10.230.39.163 with 32 bytes of data:
        
        Reply from [10.230.39.163]("http://10.230.39.163"): Destination host unreachable.
        Reply from [10.230.39.163]("http://10.230.39.163"): Destination host unreachable.
        
        root@compute1:~#tcpdump -n -i eth0 proto gre
        17:07:57.541440 IP 172.16.39.155 > [172.16.39.156]("http://172.16.39.156"): GREv0,         key=0x1, length 54: ARP, Request who-has 10.10.10.2 tell         10.10.10.1, length 28
        17:07:57.541457 IP 172.16.39.156 > [172.16.39.200]("http://172.16.39.200"): GREv0,         key=0x1, length 54: ARP, Request who-has 10.10.10.2 tell         10.10.10.1, length 28
        17:07:57.541465 IP 172.16.39.156 > [172.16.39.200]("http://172.16.39.200"): GREv0,         key=0x1, length 72: ARP, Reply 10.10.10.2 is-at         fa:16:3e:ba:22:ff, length 46
        17:07:57.541486 IP 172.16.39.156 > [172.16.39.200]("http://172.16.39.200"): GREv0,         key=0x1, length 72: ARP, Reply 10.10.10.2 is-at         fa:16:3e:ba:22:ff, length 46
        
        Here we can see compute node is sending ARP reply to network         node over gre tunnel.
        
        root@neutron:~#tcpdump -n -i eth0 proto gre
        17:08:55.281644 IP 172.16.39.156 > [172.16.39.200]("http://172.16.39.200"): GREv0,         key=0x1, length 54: ARP, Request who-has 10.10.10.2 tell         10.10.10.1, length 28
        17:08:55.281663 IP 172.16.39.155 > [172.16.39.200]("http://172.16.39.200"): GREv0,         key=0x1, length 54: ARP, Request who-has 10.10.10.2 tell         10.10.10.1, length 28
        17:08:55.281669 IP 172.16.39.156 > [172.16.39.200]("http://172.16.39.200"): GREv0,         key=0x1, length 72: ARP, Reply 10.10.10.2 is-at         fa:16:3e:ba:22:ff, length 46
        
        Here we can see network node is receiving ARP reply from compute         node over gre tunnel.
        
        root@neutron:~# tcpdump -i br-int 
        tcpdump: WARNING: br-int: no IPv4 address assigned
        tcpdump: verbose output suppressed, use -v or -vv for full         protocol decode
        listening on br-int, link-type EN10MB (Ethernet), capture size         65535 bytes
        17:23:45.344970 ARP, Request who-has 10.10.10.2 tell 10.10.10.1,         length 28
        17:23:45.345121 ARP, Request who-has 10.10.10.2 tell 10.10.10.1,         length 28
        
        We can see only ARP request on br-int of network node. There is         no ARP reply on br-int.
        
        root@neutron:~# ip netns exec         qrouter-905087ce-b1e2-4038-beae-32865fa7924b tcpdump -i         qr-8d3a43d5-f5
        tcpdump: verbose output suppressed, use -v or -vv for full         protocol decode
        listening on qr-8d3a43d5-f5, link-type EN10MB (Ethernet),         capture size 65535 bytes
        ^C23:21:20.950674 ARP, Request who-has 10.10.10.6 tell         headnode.hpc.hpc, length 28
        23:21:20.951224 ARP, Request who-has 10.10.10.6 tell         headnode.hpc.hpc, length 28
        23:21:20.951237 ARP, Request who-has 10.10.10.6 tell         headnode.hpc.hpc, length 28
        23:21:21.949476 ARP, Request who-has 10.10.10.6 tell         headnode.hpc.hpc, length 28
        23:21:21.949622 ARP, Request who-has 10.10.10.6 tell         headnode.hpc.hpc, length 28
        
        Here we could not see any ARP reply on qr-xxx.
        
        root@neutron:~# ovs-vsctl show
        1f793d03-8ab1-495c-877e-e6002dda9912
        Bridge br-ex
        Port br-ex
        Interface br-ex
        type: internal
        Port "eth2"
        Interface "eth2"
        Port "qg-ac77add8-f6"
        Interface "qg-ac77add8-f6"
        type: internal
        Bridge br-tun
        Port "gre-1"
        Interface "gre-1"
        type: gre
        options: {in_key=flow, local_ip="172.16.39.200", out_key=flow,         remote_ip="172.16.39.155"}
        Port br-tun
        Interface br-tun
        type: internal
        Port "gre-2"
        Interface "gre-2"
        type: gre
        options: {in_key=flow, local_ip="172.16.39.200", out_key=flow,         remote_ip="172.16.39.156"}
        Port patch-int
        Interface patch-int
        type: patch
        options: {peer=patch-tun}
        Bridge br-int
        Port "tapfc47451e-6e"
        tag: 2
        Interface "tapfc47451e-6e"
        type: internal
        Port patch-tun
        Interface patch-tun
        type: patch
        options: {peer=patch-int}
        Port br-int
        Interface br-int
        type: internal
        Port "qr-9362c080-49"
        tag: 1
        Interface "qr-9362c080-49"
        type: internal
        Port "tap494d9d45-de"
        tag: 1
        Interface "tap494d9d45-de"
        type: internal
        ovs_version: "1.10.2"
        root@neutron:~# 
        
        root@neutron:~# ovs-ofctl show br-tun
        OFPT_FEATURES_REPLY (xid=0x2): dpid:0000826b075fdc46
        n_tables:254, n_buffers:256
        capabilities: FLOW_STATS TABLE_STATS PORT_STATS QUEUE_STATS         ARP_MATCH_IP
        actions: OUTPUT SET_VLAN_VID SET_VLAN_PCP STRIP_VLAN SET_DL_SRC         SET_DL_DST SET_NW_SRC SET_NW_DST SET_NW_TOS SET_TP_SRC         SET_TP_DST ENQUEUE
        1(patch-int): addr:76:05:50:ec:29:d2
        config: 0
        state: 0
        speed: 0 Mbps now, 0 Mbps max
        2(gre-1): addr:32:1d:80:12:a0:c1
        config: 0
        state: 0
        speed: 0 Mbps now, 0 Mbps max
        3(gre-2): addr:22:a5:5c:84:bf:66
        config: 0
        state: 0
        speed: 0 Mbps now, 0 Mbps max
        LOCAL(br-tun): addr:82:6b:07:5f:dc:46
        config: 0
        state: 0
        speed: 0 Mbps now, 0 Mbps max
        OFPT_GET_CONFIG_REPLY (xid=0x4): frags=normal miss_send_len=0
        root@neutron:~# 
        
        root@neutron:~# ovs-appctl fdb/show br-int 
        port VLAN MAC Age
        -1 1 fa:16:3e:94:4c:19 0
        -1 1 fa:16:3e:ba:22:ff 0
        root@neutron:~# 
        
        root@neutron:~# ovs-ofctl dump-flows br-tun
        NXST_FLOW reply (xid=0x4):
        cookie=0x0, duration=50535.216s, table=0, n_packets=34524,         n_bytes=2156153, idle_age=1, priority=1,in_port=3         actions=resubmit(,2)
        cookie=0x0, duration=50536.204s, table=0, n_packets=31063,         n_bytes=1773195, idle_age=1, priority=1,in_port=1         actions=resubmit(,1)
        cookie=0x0, duration=50535.506s, table=0, n_packets=34472,         n_bytes=2188954, idle_age=1, priority=1,in_port=2         actions=resubmit(,2)
        cookie=0x0, duration=50536.169s, table=0, n_packets=4,         n_bytes=300, idle_age=50527, priority=0 actions=drop
        cookie=0x0, duration=50536.099s, table=1, n_packets=1880,         n_bytes=78960, idle_age=1,         priority=0,dl_dst=01:00:00:00:00:00/01:00:00:00:00:00         actions=resubmit(,21)
        cookie=0x0, duration=50536.134s, table=1, n_packets=29183,         n_bytes=1694235, idle_age=1016,         priority=0,dl_dst=00:00:00:00:00:00/01:00:00:00:00:00         actions=resubmit(,20)
        cookie=0x0, duration=50534.872s, table=2, n_packets=68996,         n_bytes=4345107, idle_age=1, priority=1,tun_id=0x1         actions=mod_vlan_vid:1,resubmit(,10)
        cookie=0x0, duration=50534.678s, table=2, n_packets=0,         n_bytes=0, idle_age=50534, priority=1,tun_id=0x2         actions=mod_vlan_vid:2,resubmit(,10)
        cookie=0x0, duration=50536.065s, table=2, n_packets=0,         n_bytes=0, idle_age=50536, priority=0 actions=drop
        cookie=0x0, duration=50536.03s, table=3, n_packets=0, n_bytes=0,         idle_age=50536, priority=0 actions=drop
        
        cookie=0x0, duration=50535.995s, table=10, n_packets=68996,         n_bytes=4345107, idle_age=1, priority=1 actions=learn(table=20,hard_timeout=300,priority=1,NXM_OF_VLAN_TCI[0..11],NXM_OF_ETH_DST[]=NXM_OF_ETH_SRC[],load:0->NXM_OF_VLAN_TCI[],load:NXM_NX_TUN_ID[]->NXM_NX_TUN_ID[],output:NXM_OF_IN_PORT[]),output:1
        
        This rule gets hit as number of packets increases. Its output         port is 1, it means packet should pass to patch-int and then to         qr-xxx. However we can not see any ARP reply on qr-xxx.
         
        cookie=0x0, duration=1113.575s, table=20, n_packets=5,         n_bytes=249, hard_timeout=300, idle_age=1106, hard_age=0,         priority=1,vlan_tci=0x0001/0x0fff,dl_dst=fa:16:3e:ba:22:ff actions=load:0->NXM_OF_VLAN_TCI[],load:0x1->NXM_NX_TUN_ID[],output:3
        cookie=0x0, duration=1113.575s, table=20, n_packets=0,         n_bytes=0, hard_timeout=300, idle_age=1113, hard_age=0,         priority=1,vlan_tci=0x0001/0x0fff,dl_dst=fa:16:3e:94:4c:19 actions=load:0->NXM_OF_VLAN_TCI[],load:0x1->NXM_NX_TUN_ID[],output:2
        cookie=0x0, duration=50535.961s, table=20, n_packets=0,         n_bytes=0, idle_age=50535, priority=0 actions=resubmit(,21)
        cookie=0x0, duration=50534.907s, table=21, n_packets=1880,         n_bytes=78960, idle_age=1, priority=1,dl_vlan=1         actions=strip_vlan,set_tunnel:0x1,output:2,output:3
        cookie=0x0, duration=50534.713s, table=21, n_packets=0,         n_bytes=0, idle_age=50534, priority=1,dl_vlan=2         actions=strip_vlan,set_tunnel:0x2,output:2,output:3
        cookie=0x0, duration=50535.926s, table=21, n_packets=0,         n_bytes=0, idle_age=50535, priority=0 actions=drop
        
        Does anyone have any idea? Why flows on br-tun could not pass         ARP reply packets to qr-xxx.
        
        Any assistance you can provide would be greatly appreciated. 
[/COLOR]

---

