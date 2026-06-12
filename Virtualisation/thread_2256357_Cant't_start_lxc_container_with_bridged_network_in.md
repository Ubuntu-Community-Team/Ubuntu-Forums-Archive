---
title: "Cant't start lxc container with bridged network interface"
date: 2014-12-11
forum: Virtualisation
---

### Post by stanley-bagshaw on 2014-12-11
Basically I have a 14.10 ubuntu server install, with the physical ethernet adaptor bound to a bridge (br0), and some unprivileged lxc containers (all running as the same user).

I can start any four of the lxc containers and they behave as expected, bridged network interface  (br0) is fine etc.

When I start the fifth lxc container it fails because it cant start the network.

If I change the lxc.network.link to lxcbr0 instead of br0 the fifth lxc container starts fine, so It seems to be an issue with br0.

If I start the containers in a different order, the first four start fine, but the fifth (a different container this time) fails on network, while the one that failed before starts fine.

If anyone has any ideas I would be grateful.

lxc-start debug log of machine failing to start
```
lxc-start 1418331352.710 INFO     lxc_start_ui - lxc_start.c:main:265 - using rcfile /lxc/.local/share/lxc/twister-ubuntu/config      lxc-start 1418331352.710 WARN     lxc_confile - confile.c:config_pivotdir:1685 - lxc.pivotdir is ignored.  It will soon become an error.
      lxc-start 1418331352.710 INFO     lxc_confile - confile.c:config_idmap:1375 - read uid map: type u nsid 0 hostid 100000 range 65536
      lxc-start 1418331352.710 INFO     lxc_confile - confile.c:config_idmap:1375 - read uid map: type g nsid 0 hostid 100000 range 65536
      lxc-start 1418331352.711 WARN     lxc_log - log.c:lxc_log_init:316 - lxc_log_init called with log already initialized
      lxc-start 1418331352.711 INFO     lxc_start - start.c:lxc_check_inherited:209 - closed inherited fd 4
      lxc-start 1418331352.718 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
      lxc-start 1418331352.719 INFO     lxc_start - start.c:lxc_check_inherited:209 - closed inherited fd 4
      lxc-start 1418331352.719 DEBUG    lxc_conf - conf.c:lxc_create_tty:3504 - allocated pty '/dev/pts/26' (5/6)
      lxc-start 1418331352.719 DEBUG    lxc_conf - conf.c:lxc_create_tty:3504 - allocated pty '/dev/pts/27' (7/8)
      lxc-start 1418331352.719 DEBUG    lxc_conf - conf.c:lxc_create_tty:3504 - allocated pty '/dev/pts/28' (9/10)
      lxc-start 1418331352.719 DEBUG    lxc_conf - conf.c:lxc_create_tty:3504 - allocated pty '/dev/pts/29' (11/12)
      lxc-start 1418331352.719 INFO     lxc_conf - conf.c:lxc_create_tty:3515 - tty's configured
      lxc-start 1418331352.719 DEBUG    lxc_start - start.c:setup_signal_fd:247 - sigchild handler set
      lxc-start 1418331352.720 DEBUG    lxc_console - console.c:lxc_console_peer_default:536 - no console peer
      lxc-start 1418331352.724 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:177 - using monitor sock name lxc/59f36eb00b757df3//lxc/.local/share/lxc
      lxc-start 1418331352.939 INFO     lxc_start - start.c:lxc_init:443 - 'twister-ubuntu' is initialized
      lxc-start 1418331352.939 DEBUG    lxc_start - start.c:__lxc_start:1061 - Not dropping cap_sys_boot or watching utmp
      lxc-start 1418331352.939 INFO     lxc_start - start.c:lxc_spawn:805 - Cloning a new user namespace
      lxc-start 1418331352.939 INFO     lxc_cgroup - cgroup.c:cgroup_init:62 - cgroup driver cgmanager initing for twister-ubuntu
      lxc-start 1418331361.015 ERROR    lxc_start - start.c:lxc_spawn:930 - failed to create the configured network
      lxc-start 1418331361.042 ERROR    lxc_start - start.c:__lxc_start:1087 - failed to spawn 'twister-ubuntu'
      lxc-start 1418331361.042 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
      lxc-start 1418331361.043 WARN     lxc_cgmanager - cgmanager.c:cgm_get:946 - do_cgm_get exited with error
      lxc-start 1418331366.048 ERROR    lxc_start_ui - lxc_start.c:main:337 - The container failed to start.
      lxc-start 1418331366.049 ERROR    lxc_start_ui - lxc_start.c:main:339 - To get more details, run the container in foreground mode.
      lxc-start 1418331366.049 ERROR    lxc_start_ui - lxc_start.c:main:341 - Additional information can be obtained by setting the --logfile and --logpriority options.
```


Sample container config file (there all similar to this with different names/paths)
```
# Template used to create this container: /usr/share/lxc/templates/lxc-download# Parameters passed to the template:
# For additional config options, please look at lxc.container.conf(5)


# Distribution configuration
lxc.include = /usr/share/lxc/config/ubuntu.common.conf
lxc.include = /usr/share/lxc/config/ubuntu.userns.conf
lxc.arch = x86_64


# Container specific configuration
lxc.id_map = u 0 100000 65536
lxc.id_map = g 0 100000 65536
lxc.rootfs = /lxc/.local/share/lxc/twister-ubuntu/rootfs
lxc.utsname = twister-ubuntu


# Network configuration
lxc.network.type = veth
#lxc.network.link = lxcbr0
lxc.network.link = br0
lxc.network.flags = up
lxc.network.hwaddr = 00:16:3e:xx:xx:xx



```

Output of ifconfig on host
```
br0       Link encap:Ethernet  HWaddr b8:97:5a:5f:d8:68            inet addr:10.45.45.250  Bcast:10.45.45.255  Mask:255.255.255.0
          inet6 addr: fe80::ba97:5aff:fe5f:d868/64 Scope:Link
          inet6 addr: fda3:6672:3c2d:0:ba97:5aff:fe5f:d868/64 Scope:Global
          inet6 addr: fda3:6672:3c2d:0:8163:4fd3:c169:51f6/64 Scope:Global
          inet6 addr: fda3:6672:3c2d:0:ed83:8c24:330d:5283/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75814221 (75.8 MB)  TX bytes:12957514 (12.9 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:135677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22821196 (22.8 MB)  TX bytes:22821196 (22.8 MB)


lxcbr0    Link encap:Ethernet  HWaddr 36:d3:51:15:35:8b  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::34d3:51ff:fe15:358b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:73762 (73.7 KB)


p1p1      Link encap:Ethernet  HWaddr b8:97:5a:5f:d8:68  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:374090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:711293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144700611 (144.7 MB)  TX bytes:97978777 (97.9 MB)


vethB5657S Link encap:Ethernet  HWaddr fe:4e:8c:df:01:1d  
          inet6 addr: fe80::fc4e:8cff:fedf:11d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3014078 (3.0 MB)  TX bytes:2148518 (2.1 MB)


vethKWOUHK Link encap:Ethernet  HWaddr fe:7a:b9:1b:04:42  
          inet6 addr: fe80::fc7a:b9ff:fe1b:442/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1217210 (1.2 MB)  TX bytes:1769144 (1.7 MB)


vethO5F7KP Link encap:Ethernet  HWaddr fe:e4:bb:75:98:07  
          inet6 addr: fe80::fce4:bbff:fe75:9807/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:528782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55443928 (55.4 MB)  TX bytes:28394310 (28.3 MB)


vethPERNAB Link encap:Ethernet  HWaddr fe:2f:4b:8e:eb:28  
          inet6 addr: fe80::fc2f:4bff:fe8e:eb28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24389658 (24.3 MB)  TX bytes:36967893 (36.9 MB)



```

---

### Post by stanley-bagshaw on 2014-12-14
Found my problem this morning, it was a configuration error on my part.

Basically when I was setting up unprivileged lxc I copy pasted the following config and forgot about it

/etc/lxc/lxc-usernet
[CODE
]# USERNAME TYPE BRIDGE COUNT
lxcd veth lxcbr0 4
lxcd veth br0 4[/CODE]

after changing the bridge count to a higher number everything works as expected.

---

### Post by TheFu on 2014-12-14
Thank you very much for posting the solution!

---

