---
title: "ubuntu server 14.04 / plesk 12 server not bootable."
date: 2015-09-21
forum: Server Platforms
---

### Post by derr12 on 2015-09-21
Hello,  My production ubunter server VM wont boot under normal mode anymore. I managed to get some services running in recovery mode for the moment.  Wonder if anyone had any suggestions for this. 
During normal boot it hangs after ""starting configure network virtual devices", forcing me to ctrl/alt/del.

Thinking it may be networking related i turned off networking from booting with the system.  After that it hung after starting system V, forcing me to ctrl/alt/del.

 Here is my bootlog, and yes i have lots of virtual Ethernet adapters on this system;

 ```
* Starting Read required files in advance[74G[ OK ]
 * Starting Mount filesystems on boot[74G[ OK ]
 * Starting Fix-up sensitive /proc filesystem entries[74G[ OK ]
 * Starting Populate /dev filesystem[74G[ OK ]
 * Starting Populate and link to /run filesystem[74G[ OK ]
 * Stopping Fix-up sensitive /proc filesystem entries[74G[ OK ]
 * Stopping Populate /dev filesystem[74G[ OK ]
 * Stopping Populate and link to /run filesystem[74G[ OK ]
 * Stopping Track if upstart is running in a container[74G[ OK ]
 * Starting Fix-up /sys/kernel/debug filesystem[74G[ OK ]
 * Stopping Fix-up /sys/kernel/debug filesystem[74G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[74G[ OK ]
 * Starting Clean /tmp directory[74G[ OK ]
 * Stopping Clean /tmp directory[74G[ OK ]
 * Starting Initialize or finalize resolvconf[74G[ OK ]
 * Starting set console keymap[74G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 * Starting set sysctls from /etc/sysctl.conf[74G[ OK ]
 * Starting Bridge udev events into upstart[74G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[74G[ OK ]
 * Stopping set console keymap[74G[ OK ]
 * Stopping set sysctls from /etc/sysctl.conf[74G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[74G[ OK ]
 * Starting flush early job output to logs[74G[ OK ]
 * Stopping Mount filesystems on boot[74G[ OK ]
 * Starting device node and kernel event manager[74G[ OK ]
 * Stopping flush early job output to logs[74G[ OK ]
 * Starting load modules from /etc/modules[74G[ OK ]
 * Starting cold plug devices[74G[ OK ]
 * Starting log initial device creation[74G[ OK ]
 * Starting Bridge file events into upstart[74G[ OK ]
 * Starting system logging daemon[74G[ OK ]
 * Stopping load modules from /etc/modules[74G[ OK ]
 * Starting D-Bus system message bus[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting Uncomplicated firewall[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting set console font[74G[ OK ]
 * Stopping set console font[74G[ OK ]
 * Starting userspace bootsplash[74G[ OK ]
 * Starting SystemD login management service[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Starting Send an event to indicate plymouth is up[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Stopping userspace bootsplash[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Starting Failsafe Boot Delay[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting SMB/CIFS File Server[74G[ OK ]
 * Stopping Send an event to indicate plymouth is up[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Bridge socket events into upstart[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting NetBIOS name server[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[74G[[31mfail[39;49m]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Stopping Failsafe Boot Delay[74G[ OK ]
 * Starting System V initialisation compatibility[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Starting emergency keypress handling[74G[ OK ]
 * Stopping device node and kernel event manager[74G[ OK ]
 * Stopping Bridge file events into upstart[74G[ OK ]
 * Stopping system logging daemon[74G[ OK ]
 * Stopping SMB/CIFS File Server[74G[ OK ]
 * Stopping Bridge socket events into upstart[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Stopping Initialize or finalize resolvconf[74G[ OK ]
 * Stopping emergency keypress handling[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting save system clock to hardware clock[74G[ OK ]
 * Stopping Bridge udev events into upstart[74G[ OK ]
 * Stopping NetBIOS name server[74G[ OK ]
 * Starting Waiting for state[74G[ OK ]
wait-for-state stop/waiting
 * Asking all remaining processes to terminate...       [100G 
[94G[ OK ]
 * All processes ended within 1 seconds...       [100G 
[94G[ OK ]
 * Deactivating swap...       [100G 
[94G[ OK ]
umount2: Device or resource busy
umount: /var/lib/ureadahead/debugfs busy - remounted read-only
 * Unmounting local filesystems...       [100G 
[94G[ OK ]
mount: / is busy
 * Will now restart
```

---

### Post by derr12 on 2015-09-21
here was the last of dmesg;

```
[    9.535677] [drm] width 640
[    9.535691] [drm] height 480
[    9.535704] [drm] bpp 32
[    9.545493] [drm] Fifo max 0x00040000 min 0x00001000 cap 0x0000077f
[    9.566486] fbcon: svgadrmfb (fb0) is primary device
[    9.571739] Console: switching to colour frame buffer device 100x37
[    9.573099] [drm] Initialized vmwgfx 2.5.0 20140228 for 0000:00:0f.0 on minor 0
[    9.684661] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[    9.694302] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.694346] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.265160] init: samba-ad-dc main process (1250) terminated with status 1
[   18.321968] init: failsafe main process (725) killed by TERM signal
```

---

### Post by derr12 on 2015-09-23
I wonder if im not seeing where it's hanging because plymouth is broken;

```
[    2.223961] hid-generic 0003:0E0F:0003.0002: input,hidraw1: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:02.0-1/input1
[    2.813004] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.813221] EXT4-fs (sda1): write access will be enabled during recovery
[    3.507743] random: nonblocking pool is initialized
[    4.006956] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.007251] EXT4-fs (sda1): 2 orphan inodes deleted
[    4.007435] EXT4-fs (sda1): recovery complete
[    4.013452] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.999851] init: plymouth-upstart-bridge main process (200) terminated with status 1
[    6.000501] init: plymouth-upstart-bridge main process ended, respawning
[    6.005633] init: plymouth-upstart-bridge main process (208) terminated with status 1
[    6.006176] init: plymouth-upstart-bridge main process ended, respawning
[    6.010800] init: plymouth-upstart-bridge main process (210) terminated with status 1
[    6.011135] init: plymouth-upstart-bridge main process ended, respawning
[    6.014467] init: plymouth-upstart-bridge main process (213) terminated with status 1
[    6.014917] init: plymouth-upstart-bridge main process ended, respawning
[    6.018312] init: plymouth-upstart-bridge main process (214) terminated with status 1
[    6.018763] init: plymouth-upstart-bridge main process ended, respawning
[    6.025280] init: plymouth-upstart-bridge main process (215) terminated with status 1
[    6.025827] init: plymouth-upstart-bridge main process ended, respawning
[    6.030875] init: plymouth-upstart-bridge main process (217) terminated with status 1
[    6.031385] init: plymouth-upstart-bridge main process ended, respawning
[    6.034561] init: plymouth-upstart-bridge main process (219) terminated with status 1
[    6.035066] init: plymouth-upstart-bridge main process ended, respawning
[    6.039887] init: plymouth-upstart-bridge main process (220) terminated with status 1
[    6.040207] init: plymouth-upstart-bridge main process ended, respawning
[    6.044509] init: plymouth-upstart-bridge main process (222) terminated with status 1
[    6.044823] init: plymouth-upstart-bridge main process ended, respawning
[    6.047337] init: plymouth-upstart-bridge main process (224) terminated with status 1
[    6.047669] init: plymouth-upstart-bridge respawning too fast, stopped
```

---

### Post by derr12 on 2015-09-23
Well plymouth is sometimes working again.  

what i did find in syslog is that the NTP daemon is whats causing my problem, It just fails on error code 15 and then loops infinitely; check it;

```
Sep 23 10:39:11 redacted ntpdate[3948]: step time server 206.108.0.132 offset -0.000010 sec
Sep 23 10:39:11 redacted ntpd[3979]: ntpd 4.2.6p5@1.2349-o Mon Apr 13 13:39:46 UTC 2015 (1)
Sep 23 10:39:11 redacted ntpd[3980]: proto: precision = 0.218 usec
Sep 23 10:39:11 redacted ntpd[3980]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Sep 23 10:39:11 redacted ntpd[3980]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen and drop on 1 v6wildcard :: UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 2 lo 127.0.0.1 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 3 eth0 x.x.x.166 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 4 eth0:5 x.x.x.17 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 5 eth0:6 x.x.x.42 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 6 eth0:17 x.x.x.34 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 7 eth0:23 x.x.x.150 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 8 eth0:24 x.x.x.151 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 9 eth0:25 x.x.x.152 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 10 eth0:26 x.x.x.153 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 11 eth0:27 x.x.x.154 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 12 eth0:29 x.x.x.8 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 13 eth0:30 x.x.x.15 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 14 eth0:31 x.x.x.13 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 15 eth0:32 x.x.x.7 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 16 eth0:33 x.x.x.154 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 17 eth0:34 x.x.x.27 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 18 eth0:35 x.x.x.152 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 19 eth0:36 x.x.x.25 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 20 eth0:37 x.x.x.30 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 21 eth0:38 x.x.x.28 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 22 eth0:39 x.x.x.29 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 23 eth0:40 x.x.x.18 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 24 eth0:41 x.x.x.19 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 25 eth0:42 x.x.x.17 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 26 eth0:43 x.x.x.150 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 27 eth0:44 x.x.x.23 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 28 eth0:45 x.x.x.20 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 29 eth0:46 x.x.x.21 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 30 eth0:47 x.x.x.46 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 31 eth0:48 x.x.x.37 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 32 eth0:49 x.x.x.34 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 33 eth0:50 x.x.x.35 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 34 eth0:51 x.x.x.33 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 35 eth0:52 x.x.x.36 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 36 eth0:53 x.x.x.151 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 37 eth0:54 x.x.x.48 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 38 eth0:55 x.x.x.49 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 39 eth0:56 x.x.x.52 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 40 eth0:57 x.x.x.153 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 41 eth0:1 x.x.x.50 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 42 eth0:2 x.x.x.22 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 43 eth0:3 x.x.x.160 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: Listen normally on 44 eth0:4 x.x.x.162 UDP 123
Sep 23 10:39:11 redacted ntpd[3980]: peers refreshed
Sep 23 10:39:11 redacted ntpd[3980]: Listening on routing socket on fd #61 for interface updates
Sep 23 10:39:24 redacted rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="401" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

Gonna try uninstalling ntp later today and see how that goes.

---

### Post by derr12 on 2015-09-24
now with ntpd uninstalled, im not puking errors or looping.  no boot either, all i get is;

```
Sep 24 07:49:44 cableweb3 kernel: [   10.522435] vmxnet3 0000:03:00.0 eth0: NIC Link is Up 10000 Mbps
Sep 24 07:49:49 cableweb3 ntpdate[1025]: 142.137.247.109 rate limit response from server.
Sep 24 07:49:55 cableweb3 ntpdate[1025]: step time server 206.108.0.131 offset -0.297181 sec
Sep 24 07:50:09 cableweb3 ntpdate[3193]: step time server 206.108.0.131 offset -0.000635 sec
Sep 24 07:50:24 cableweb3 ntpdate[3240]: step time server 206.108.0.131 offset -0.000751 sec
Sep 24 07:50:44 cableweb3 ntpdate[3287]: step time server 206.108.0.131 offset -0.000859 sec
Sep 24 07:51:09 cableweb3 ntpdate[3335]: step time server 206.108.0.131 offset -0.001002 sec
Sep 24 07:51:39 cableweb3 ntpdate[3382]: step time server 206.108.0.131 offset -0.001197 sec
Sep 24 07:52:14 cableweb3 ntpdate[3430]: step time server 206.108.0.131 offset -0.001487 sec
Sep 24 07:52:56 cableweb3 ntpdate[3477]: step time server 129.128.5.210 offset -0.000621 sec
```



Im at a loss here, anyone have any suggestions?

---

### Post by kosmokramer314 on 2015-09-25
may be related?  
[http://ubuntuforums.org/showthread.php?t=2218100](http://ubuntuforums.org/showthread.php?t=2218100)

---

### Post by cariboo on 2015-09-25
Please use [noparse]```

```[/noparse] tags when posting terminal output.

---

