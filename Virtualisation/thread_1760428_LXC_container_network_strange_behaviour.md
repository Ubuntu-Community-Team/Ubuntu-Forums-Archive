---
title: "LXC container network strange behaviour"
date: 2011-05-16
forum: Virtualisation
---

### Post by aXe1 on 2011-05-16
**[SIZE="3"]Hi, people.[/SIZE]**
I'm trying to setup some LXC containers, which would have their own IP on network, obtaining it from home router DHCP. I have installed Ubuntu 11.04 Server x86 minimal virtual configuration on my virtual computer with bridge-utils and lxc packages. Everything works as expected, except network. When I'm starting container it has no IP address, but after "**ifdown eth0 && ifup eth0**" (or network service restart of course) it successfully obtain IP, and all is ok until next reboot.

**[SIZE="3"]Briefly I did this:[/SIZE]**
[LIST=1]
[*]Created **cgroups** mount in **/etc/fstab**.
[*]Edited **/etc/network/interfaces** to setup bridge.
[*]Edited **/etc/sysctl.conf** to enable ipv4 forwarding.
[*]**sudo lxc-create -n test1 -t natty**
[*]Added to **/var/lib/lxc/test1/config** network parameters.
[*]Make symlink **/var/lib/lxc/test1/config** to **/etc/lxc/test1.conf**
[*]Enabled **lxc** service in **/etc/defaults/lxc** and make it to autostart "test1" container.
[/LIST]

**[SIZE="3"]And got this:[/SIZE]**
on guest:
```

root@test1:~# ifconfig
[COLOR="Red"]eth0      Link encap:Ethernet  HWaddr 00:0c:29:bd:cc:75
          inet6 addr: fe80::20c:29ff:febd:cc75/64 Scope:Link[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8768 (8.7 KB)  TX bytes:652 (652.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[COLOR="Red"]root@test1:~# /etc/init.d/networking restart[/COLOR]
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                                  ssh stop/waiting
ssh start/running, process 377
                                                                                                                                                                 [ OK ]
root@test1:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:bd:cc:75
          [COLOR="Red"]inet addr:192.168.1.166 Bcast:192.168.1.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::20c:29ff:febd:cc75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13209 (13.2 KB)  TX bytes:1884 (1.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**/var/log/syslog** (on host)
```

May 17 06:26:31 lxc-server1 kernel: [    6.177577] device veth1dZwKs entered promiscuous mode
May 17 06:26:31 lxc-server1 kernel: [    6.177607] ADDRCONF(NETDEV_UP): veth1dZwKs: link is not ready
May 17 06:26:31 lxc-server1 kernel: [    6.228534] ADDRCONF(NETDEV_CHANGE): veth1dZwKs: link becomes ready
May 17 06:26:31 lxc-server1 kernel: [    6.496101] br0: port 2(veth1dZwKs) entering forwarding state
May 17 06:26:31 lxc-server1 kernel: [    6.496144] br0: port 2(veth1dZwKs) entering forwarding state
May 17 06:26:31 lxc-server1 kernel: [    6.496186] br0: port 1(eth0) entering forwarding state
May 17 06:26:31 lxc-server1 kernel: [    6.496191] br0: port 1(eth0) entering forwarding state
May 17 06:26:31 lxc-server1 dhclient: can't create /var/lib/dhcp3/dhclient.br0.leases: No such file or directory
May 17 06:26:31 lxc-server1 dhclient: DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 3
May 17 06:26:31 lxc-server1 dhclient: DHCPOFFER of 192.168.1.165 from 192.168.1.1
May 17 06:26:31 lxc-server1 dhclient: DHCPREQUEST of 192.168.1.165 on br0 to 255.255.255.255 port 67
May 17 06:26:31 lxc-server1 dhclient: DHCPACK of 192.168.1.165 from 192.168.1.1
May 17 06:26:31 lxc-server1 dhclient: can't create /var/lib/dhcp3/dhclient.br0.leases: No such file or directory
May 17 06:26:31 lxc-server1 dhclient: bound to 192.168.1.165 -- renewal in 37494 seconds.
May 17 06:26:32 lxc-server1 init: ssh main process (354) terminated with status 255
May 17 06:26:32 lxc-server1 kernel: [    7.504064] vesafb: framebuffer at 0xd0000000, mapped to 0xe0980000, using 1216k, total 1216k
May 17 06:26:32 lxc-server1 kernel: [    7.504111] vesafb: mode is 640x480x32, linelength=2560, pages=0
May 17 06:26:32 lxc-server1 kernel: [    7.504158] vesafb: scrolling: redraw
May 17 06:26:32 lxc-server1 kernel: [    7.504205] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
May 17 06:26:32 lxc-server1 kernel: [    7.516129] Console: switching to colour frame buffer device 80x30
May 17 06:26:32 lxc-server1 kernel: [    7.520064] fb0: VESA VGA frame buffer device
May 17 06:26:32 lxc-server1 init: plymouth-splash main process (918) terminated with status 1
May 17 06:26:48 lxc-server1 ntpdate[735]: step time server 91.189.94.4 offset 7.935507 sec
May 17 06:26:49 lxc-server1 kernel: [   16.128195] eth0: no IPv6 routers present
May 17 06:26:50 lxc-server1 kernel: [   16.672083] veth1dZwKs: no IPv6 routers present
May 17 06:26:50 lxc-server1 kernel: [   17.016784] br0: no IPv6 routers present
May 17 06:26:50 lxc-server1 kernel: [   17.184776] eth0: no IPv6 routers present
May 17 06:28:05 lxc-server1 kernel: [   91.965394] br0: port 2(veth1dZwKs) entering forwarding state
May 17 06:28:05 lxc-server1 kernel: [   92.036127] br0: port 2(veth1dZwKs) entering forwarding state
May 17 06:28:05 lxc-server1 kernel: [   92.036135] br0: port 2(veth1dZwKs) entering forwarding state
May 17 06:28:15 lxc-server1 kernel: [  102.080655] eth0: no IPv6 routers present

```

**[SIZE="3"]My configs:[/SIZE]**
**/etc/network/interfaces** (on host)
```
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_hello 0
        bridge_maxwait 0
```

**/var/lib/lxc/test1/config** (on host)
```
lxc.network.type=veth
lxc.network.link=br0
lxc.network.flags=up
lxc.network.hwaddr=00:0c:29:bd:cc:75
lxc.utsname = test1

lxc.tty = 4
lxc.pts = 1024
lxc.rootfs = /var/lib/lxc/test1/rootfs
lxc.mount  = /var/lib/lxc/test1/fstab

lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
#lxc.cgroup.devices.allow = c 4:0 rwm
#lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm
```

**/etc/network/interfaces** (on guest)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

[SIZE="4"]Any hint will be helpful.[/SIZE]

---

### Post by sgiebels on 2011-06-11
Try using 
0.0.0.0
as the IPV4 address for this device.
[http://www.techrepublic.com/blog/opensource/how-to-create-lxc-system-containers-to-isolate-services/1299](http://www.techrepublic.com/blog/opensource/how-to-create-lxc-system-containers-to-isolate-services/1299)

---

### Post by aXe1 on 2011-06-11
Already tried it - no change :(

Also I tried to install some other templates as guest (maverick, debian, fedora), and debian works as expected! Other two has the same bug as natty template. Debian template has the same default /etc/interfaces as natty, and I configured containers identically.

Can anybody give me a hint, where to dig?

---

### Post by FlappySocks on 2011-07-02
Any updates to this? I have the same problem. :(

---

### Post by aXe1 on 2011-07-02
No:( Unfortunately now I have no time to dig into it. I have posted about this problem on some other ubuntu and *nix related forums and people there give me some hints, but all the same problem remained.

some hints from there:
[LIST=1]
[*]Check runlevel in container as soon as it started. Was normal = 2.
[*]Install rsyslog at guest and look there. Was uninteresting, only plymouth crash (splash screen).
[*]Add ```
lxc.network.ipv4 = 0.0.0.0
``` line to container config. No difference I saw.
[*]"Play" with interface settings in /etc/interfaces on container. No progress at all(
[*] Try other templates, that are available in natty. Debian works much better, but not ideally at all. Fedora doesn't work normal at all. Maverick has the same problem as natty.
[/LIST]

I hope someone will solve it, cause I'll not have more time soon :(

(warning: russian language!)
Here are links to that forums:
[http://www.linux.org.ru/forum/admin/6276013](http://www.linux.org.ru/forum/admin/6276013)
[http://forum.sysadmins.su/index.php?showtopic=40247540](http://forum.sysadmins.su/index.php?showtopic=40247540)
[http://forum.ubuntu.ru/index.php?topic=152560.0](http://forum.ubuntu.ru/index.php?topic=152560.0)

---

### Post by FlappySocks on 2011-07-02
I found the answer to my problem on the LXC group. I have a static IP address, but the gateway would not get added into the route table until I did a ifdown/ifup


```
$ cat /etc/init/lxclo.conf
# description "LXC vs. Upstart workarounds"
start on startup
task
console output

     script
      # As lxc 0.7's halt/reboot detection hack needs /var/run to NOT be a
      # tmpfs, we need to manually clean it -- esp. the ifstate file that
      # tells falsely tells ifupdown "lo is up".
      #
      # To debug, add -printf "Deleting stale file %p\n" before -delete.
      find /var/run/ -xdev -not -path /var/run/ -delete
      initctl emit -n stopped JOB=udevtrigger
      initctl emit -n started JOB=udev
      # This one is needed for broken ifupdown NMU 0.6.8ubuntu29.1
      initctl emit -n net-device-up IFACE=lo LOGICAL=lo ADDRFAM=inet 
METHOD=loopback
     end script

```

---

### Post by agent8131 on 2011-08-12
I ran into this today.  This is specific to Ubuntu containers as Ubuntu uses upstart which relies on udev and udev does not function inside the container.  So Ubuntu will fail to start many services by default.  Something to be aware of.

---

### Post by aXe1 on 2011-08-29
> **FlappySocks said:**
> I found the answer to my problem on the LXC group. I have a static IP address, but the gateway would not get added into the route table until I did a ifdown/ifup


```
$ cat /etc/init/lxclo.conf
# description "LXC vs. Upstart workarounds"
start on startup
task
console output

     script
      # As lxc 0.7's halt/reboot detection hack needs /var/run to NOT be a
      # tmpfs, we need to manually clean it -- esp. the ifstate file that
      # tells falsely tells ifupdown "lo is up".
      #
      # To debug, add -printf "Deleting stale file %p\n" before -delete.
      find /var/run/ -xdev -not -path /var/run/ -delete
      initctl emit -n stopped JOB=udevtrigger
      initctl emit -n started JOB=udev
      # This one is needed for broken ifupdown NMU 0.6.8ubuntu29.1
      initctl emit -n net-device-up IFACE=lo LOGICAL=lo ADDRFAM=inet 
METHOD=loopback
     end script

```

Thank you, man!! This solve my problem too! Now container works like a swiss watches =) I'll repost it to topics on other forums that I started.

---

### Post by beeltejuice on 2011-11-14
I'm running into what appears to be a very similar issue, except restarting networking does not fix.  Mine may be caused by UFW -- here's what I see:

```

Nov 14 13:24:23 cro kernel: [1024678.584227] [UFW BLOCK] IN=br0 OUT=br0 PHYSIN=vethFtPdZX PHYSOUT=eth0 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x10 PREC=0x00 TTL=128 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308 
Nov 14 13:26:56 cro kernel: [1024831.663947] [UFW BLOCK] IN=br0 OUT=br0 PHYSIN=vethFtPdZX PHYSOUT=eth0 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x10 PREC=0x00 TTL=128 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308 

```

My lxc config:
```

lxc.network.type = veth
lxc.network.flags = up
lxc.network.name = eth0
lxc.network.link = br0
lxc.network.ipv4 = 0.0.0.0

```

My UFW:
```

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
22                         ALLOW       Anywhere

```

Any ideas what I need to allow to make this work?  If i disable UFW everything works fine.

---

