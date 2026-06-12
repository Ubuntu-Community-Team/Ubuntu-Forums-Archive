---
title: "keepalived and ipvsadm"
date: 2010-01-18
forum: Server Platforms
---

### Post by lexo on 2010-01-18
hello,

i've a problem with keepalived and ipvsadm.
With keepalived, i could not Direct Routing port 80 but with ipvsadm, that's work :(

ubuntu server 9.10 64 bits on Dell PowerEdge R410

HA balancer : 10.1.6.248
Virtual IP : 10.1.6.70
Real HTTP server IP : 10.1.6.71

```
/etc/keepalived/keepalived.conf
global_defs {
        lvs_id LVSWEB1
        router_id arf1
}

vrrp_instance VI_L {
        state MASTER
        interface eth0
        virtual_router_id 5
        priority 100
        advert_int 1
        lvs_sync_daemon_interface eth0

        authentication {
                auth_type PASS
                auth_pass AAAA
        }

        virtual_ipaddress {
                10.1.6.70/24
        }
}

virtual_server 10.1.6.70 80 {
        delay_loop 6
        lb_algo wrr
        lb_kind DR
        protocol TCP

        real_server 10.1.6.71 80 {
                weight 1
        }
}

``````

/etc/init.d/keepalived restart

Jan 18 13:44:26 localhost Keepalived: Starting Keepalived v1.1.17 (05/14,2009)
Jan 18 13:44:26 localhost Keepalived_vrrp: Using MII-BMSR NIC polling thread...
Jan 18 13:44:26 localhost Keepalived_vrrp: Registering Kernel netlink reflector
Jan 18 13:44:26 localhost Keepalived_vrrp: Registering Kernel netlink command channel
Jan 18 13:44:26 localhost Keepalived_vrrp: Registering gratutious ARP shared channel
Jan 18 13:44:26 localhost Keepalived_vrrp: Opening file '/etc/keepalived/keepalived.conf'.
Jan 18 13:44:26 localhost Keepalived_vrrp: Configuration is using : 64850 Bytes
Jan 18 13:44:26 localhost Keepalived: Starting VRRP child process, pid=1653
Jan 18 13:44:27 localhost Keepalived_vrrp: VRRP_Instance(VI_L) Transition to MASTER STATE
Jan 18 13:44:28 localhost Keepalived_vrrp: VRRP_Instance(VI_L) Entering MASTER STATE
Jan 18 13:44:28 localhost Keepalived_vrrp: VRRP_Group(G2) Syncing instances to MASTER state
Jan 18 13:44:28 localhost Keepalived_vrrp: Netlink: skipping nl_cmd msg...
```Ping on virtual IP 10.1.6.70 work but not redirection :(

But, if i had this ipvsadm commands, redirection on port 80 work !!! 

```

# ipvsadm -A -t 10.1.6.70:80 -s rr
# ipvsadm -a -t 10.1.6.70:80 -r 10.1.6.71:80 -g

# ipvsadm -l
IP Virtual Server version 1.2.1 (size=4096)
Prot LocalAddress:Port Scheduler Flags
  -> RemoteAddress:Port           Forward Weight ActiveConn InActConn
TCP  10.1.6.70:www rr
  -> 10.1.6.71:www                Route   1      0          0

```That's work very fine. Why with keepalived only, that don't work.

Very thanks

---

### Post by lexo on 2010-01-19
Nobody could help me :( ?

---

### Post by lexo on 2010-01-19
i've found the solution :(

[https://bugs.launchpad.net/ubuntu/+source/keepalived/+bug/496932](https://bugs.launchpad.net/ubuntu/+source/keepalived/+bug/496932)

---

