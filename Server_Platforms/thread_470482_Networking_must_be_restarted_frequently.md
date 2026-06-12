---
title: "Networking must be restarted frequently"
date: 2007-06-11
forum: Server Platforms
---

### Post by juantao on 2007-06-11
Hello. I have installed a 7.04 LAMP server and am having a problem that I cannot login to it - or webpages hosted there are unavalialble. This happens frequently (once every day or so). After i do a <sudo /etc/init.d/networking restart> everthing is fine for a while.

This sever is on a DSL connection with a static IP assigned and the odd part is that I can log into a FreeBSD box connected to the same DSL modem with a different IP address (via ssh) and from the FreeBSD box I can ssh into the Ubuntu box and restart the networking, but when the networking is not working I cannot log in directly.

Let me state this a bit differently. When I am at home (away from the servers) and notice my webpages are down, I cannot log into the Ubuntu box via ssh. However, I can log into the FreeBSD box (on the same DSL modem) and from there I can ssh into the Ubuntu box and command the networking restart and at that point I can again log into the Ubuntu box via ssh and the webpages hosted there are again visable.

Here are some things I've tried with the Ubuntu setup:
Replace the NIC
Replace the Eth cable
Replace the computer and the NIC
All with multiple reinstalls of the OS (takes about 13 minutes on a P4)

Is there a bug? Are there logs I could look at that would tell me what's stopping the flow?

Although I started with RedHat 5.1 in '98, I guess I'll always feel like a newbie and the likely cause of my troubles here is that I don't know enough about networking...

Thanks for your assistance, Jon

---

### Post by turinglabs on 2007-06-11
The first place I would look would be in the syslog, kern.log or daemon.log for network errors around the time of your last failure. Is this a PPPOE connection? Can you post your network config?

---

### Post by dbott67 on 2007-06-11
Hi Jon,

This is puzzling.  As turinglabs mentions, check the logs for any sort of indication of network problems.  Aside from that, I have few questions:

1. Does your ISP provide you with multiple static (or DHCP) IP addresses for each server?

2. Are these servers behind a NAT firewall & if so, are you using port forwarding to reach each server?

3. When you SSH from the FreeBSD box to Ubuntu/LAMP are you using a public IP or some sort of private IP ([COLOR=Blue]10.x.y.z[/COLOR] or [COLOR=Blue]172.16-31.x.y[/COLOR] or [COLOR=Blue]192.168.x.y[/COLOR])?

4. Are there multiple NICs in the LAMP server (one public one private)?

Maybe you could provide sort sort of diagram indicating any firewalls & public/private network boundaries.


> **juantao said:**
>  This sever is on a DSL connection with a static IP assigned and the odd part is that I can log into a FreeBSD box connected to the same DSL modem with a different IP address (via ssh) and from the FreeBSD box I can ssh into the Ubuntu box and restart the networking, but when the networking is not working I cannot log in directly.

From this evidence, it appears as though the network is still operating on the LAMP server because you can SSH from a machine on the same subnet, but publicly you can't seem to access it.  

My guess is that _**if**_ you're behind some sort of NAT router then there may be a problem with it:

1. Check the port-forward rules.  Obviously, port 22 can only be forwarded to 1 internal IP address.  You could forward port 1122 to the internal LAMP server (on port 22) and see if SSH still accepts the connection.

2. Update the firmware on the router/modem.

-Dave

---

### Post by juantao on 2007-06-11
Hi. Thanks for the quick assistance. I'll try to answer some of the questions asked.

My ISP provides two separate static IP addresses from the DSL modem. The Eth out of the modem goes to a little 100mbs switch and from that switch there are two Eth cables running to the two boxes, a 7.04 LAMP server (that needs it's networking restarted [again this morning] and a FreeBSD box which stays up. Both run httpd, sshd, etc. The FreeBSD box runs NAT and provides for my LAN, but here's where my trouble started, I'm trying to migrate away from the FreeBSD box and do all my services from Ubuntu)

It is possible that my troubles lie here - in the DSL modem, cabling or switch? Maybe it's not the Linux OS, but something prior to the Linux machine - but whatever the problem is, a command to restart networking on the Linux box restores service.  

Hm... Maybe it's just routing or DNS because when I can't see my pages or ssh from home I can from the FreeBSD box - Like this:
LAMP server  69.9.146.90
FreeBSD box 69.9.146.28
Home box      69.9.151.186 (same ISP)

When I can't log into the LAMP server from home (ssh hangs or web pages 'not available') I ssh into the other box on that DSL modem and just by logging in from there restores my ability to see my pages and ssh in to the LAMP box. I discovered this morning that I don't actually have to restart networking, just give it a nudge from the other box at that location. As soon as I 'wake up' the LAMP server with a ssh request from the FreeBSD box, all is well and then the world can see my pages...

There is no firewall on the LAMP server (when I try to add one, I break the network)
The LAMP server has two NICs and does DHCP on Eth1, but not NAT (yet) as I break stuff when I try.
Here is the /etc/network/interfaces of the LAMP:

======================
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 69.9.146.90
        netmask 255.255.255.0
        gateway 69.9.146.1

# The LAN network interface
auto eth1
iface eth1 inet static
        address 192.168.4.2
        netmask 255.255.255.0
        gateway 192.168.4.1
======================
Here's the recent syslog
======================

root@CDOserver:/etc# tail -50 /var/log/syslog
Jun 11 06:25:25 CDOserver syslogd 1.4.1#20ubuntu4: restart.
Jun 11 06:39:01 CDOserver /USR/SBIN/CRON[4563]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 11 07:00:57 CDOserver -- MARK --
Jun 11 07:09:01 CDOserver /USR/SBIN/CRON[4570]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 11 07:17:01 CDOserver /USR/SBIN/CRON[4577]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 11 07:39:01 CDOserver /USR/SBIN/CRON[4580]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 11 08:00:58 CDOserver -- MARK --
Jun 11 08:09:02 CDOserver /USR/SBIN/CRON[4587]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 11 08:17:01 CDOserver /USR/SBIN/CRON[4594]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 11 08:39:01 CDOserver /USR/SBIN/CRON[4646]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
root@CDOserver:/etc#
======================
Here's the recent kern.log
======================
root@CDOserver:/var/log# tail -50 /var/log/kern.log
Jun 10 14:00:20 CDOserver kernel: [    5.080000] hda: 30064608 sectors (15393 MB) w/2048KiB Cache, CHS=29826/16/63, UDMA(66)
Jun 10 14:00:20 CDOserver kernel: [    5.080000] hda: cache flushes not supported
Jun 10 14:00:20 CDOserver kernel: [    5.080000]  hda: hda1 hda2
Jun 10 14:00:20 CDOserver kernel: [    5.110000] hdc: max request size: 512KiB
Jun 10 14:00:20 CDOserver kernel: [    5.110000] hdc: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
Jun 10 14:00:20 CDOserver kernel: [    5.120000] hdc: cache flushes supported
Jun 10 14:00:20 CDOserver kernel: [    5.120000]  hdc: hdc1
Jun 10 14:00:20 CDOserver kernel: [    5.190000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
Jun 10 14:00:20 CDOserver kernel: [    5.190000] uhci_hcd 0000:00:11.3: UHCI Host Controller
Jun 10 14:00:20 CDOserver kernel: [    5.190000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
Jun 10 14:00:20 CDOserver kernel: [    5.190000] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000e400
Jun 10 14:00:20 CDOserver kernel: [    5.190000] usb usb2: configuration #1 chosen from 1 choice
Jun 10 14:00:20 CDOserver kernel: [    5.190000] hub 2-0:1.0: USB hub found
Jun 10 14:00:20 CDOserver kernel: [    5.190000] hub 2-0:1.0: 2 ports detected
Jun 10 14:00:20 CDOserver kernel: [    5.300000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
Jun 10 14:00:20 CDOserver kernel: [    5.300000] PCI: setting IRQ 12 as level-triggered
Jun 10 14:00:20 CDOserver kernel: [    5.300000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
Jun 10 14:00:20 CDOserver kernel: [    5.560000] e1000: 0000:00:0a.0: e1000_probe: (PCI:33MHz:32-bit) 00:07:e9:09:38:e0
Jun 10 14:00:20 CDOserver kernel: [    5.590000] Attempting manual resume
Jun 10 14:00:20 CDOserver kernel: [    5.590000] swsusp: Resume From Partition 3:2
Jun 10 14:00:20 CDOserver kernel: [    5.590000] PM: Checking swsusp image.
Jun 10 14:00:20 CDOserver kernel: [    5.590000] PM: Resume from disk failed.
Jun 10 14:00:20 CDOserver kernel: [    5.600000] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 10 14:00:20 CDOserver kernel: [    5.630000] kjournald starting.  Commit interval 5 seconds
Jun 10 14:00:20 CDOserver kernel: [    5.630000] EXT3-fs: mounted filesystem with ordered data mode.
Jun 10 14:00:20 CDOserver kernel: [    8.730000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
Jun 10 14:00:20 CDOserver kernel: [    9.660000] NET: Registered protocol family 10
Jun 10 14:00:20 CDOserver kernel: [    9.660000] lo: Disabled Privacy Extensions
Jun 10 14:00:20 CDOserver kernel: [    9.660000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 10 14:00:20 CDOserver kernel: [   10.400000] Linux agpgart interface v0.102 (c) Dave Jones
Jun 10 14:00:20 CDOserver kernel: [   10.450000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 14:00:20 CDOserver kernel: [   10.790000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 10 14:00:20 CDOserver kernel: [   10.810000] agpgart: Detected VIA P4M266x/P4N266 chipset
Jun 10 14:00:20 CDOserver kernel: [   10.820000] agpgart: AGP aperture is 64M @ 0xe8000000
Jun 10 14:00:20 CDOserver kernel: [   10.940000] input: PC Speaker as /class/input/input1
Jun 10 14:00:20 CDOserver kernel: [   11.190000] irda_init()
Jun 10 14:00:20 CDOserver kernel: [   11.190000] NET: Registered protocol family 23
Jun 10 14:00:20 CDOserver kernel: [   11.220000] parport: PnPBIOS parport detected.
Jun 10 14:00:20 CDOserver kernel: [   11.220000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jun 10 14:00:20 CDOserver kernel: [   11.960000] lp0: using parport0 (interrupt-driven).
Jun 10 14:00:20 CDOserver kernel: [   12.160000] Adding 184736k swap on /dev/disk/by-uuid/4b20a514-53ef-4b50-a08f-6a8cc962fd61.  Priority:-1 extents:1 across:184736k
Jun 10 14:00:20 CDOserver kernel: [   12.380000] EXT3 FS on hda1, internal journal
Jun 10 14:00:20 CDOserver kernel: [   12.750000] kjournald starting.  Commit interval 5 seconds
Jun 10 14:00:20 CDOserver kernel: [   12.750000] EXT3 FS on hdc1, internal journal
Jun 10 14:00:20 CDOserver kernel: [   12.750000] EXT3-fs: mounted filesystem with ordered data mode.
Jun 10 14:00:25 CDOserver kernel: [   19.740000] eth0: no IPv6 routers present
Jun 10 14:00:27 CDOserver kernel: [   21.930000] NET: Registered protocol family 17
Jun 10 22:34:55 CDOserver kernel: [30890.250000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
Jun 10 22:34:55 CDOserver kernel: [30890.300000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 10 22:35:23 CDOserver kernel: [30901.170000] eth0: no IPv6 routers present
root@CDOserver:/var/log#
======================
Here's the recent daemon.log
======================
root@CDOserver:/var/log# tail -50 /var/log/daemon.log
Jun 10 13:21:12 CDOserver dhcpd: All rights reserved.
Jun 10 13:21:12 CDOserver dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 10 13:21:12 CDOserver /etc/mysql/debian-start[3927]: Checking for crashed MySQL tables.
Jun 10 13:59:11 CDOserver init: tty4 main process (3635) killed by TERM signal
Jun 10 13:59:11 CDOserver init: tty5 main process (3636) killed by TERM signal
Jun 10 13:59:11 CDOserver init: tty2 main process (3639) killed by TERM signal
Jun 10 13:59:11 CDOserver init: tty3 main process (3644) killed by TERM signal
Jun 10 13:59:11 CDOserver init: tty1 main process (3647) killed by TERM signal
Jun 10 13:59:11 CDOserver init: tty6 main process (3648) killed by TERM signal
Jun 10 13:59:12 CDOserver mysqld[3816]: 070610 13:59:12 [Note] /usr/sbin/mysqld: Normal shutdown
Jun 10 13:59:12 CDOserver mysqld[3816]:
Jun 10 13:59:12 CDOserver mysqld[3816]: 070610 13:59:12  InnoDB: Starting shutdown...
Jun 10 13:59:14 CDOserver mysqld[3816]: 070610 13:59:14  InnoDB: Shutdown completed; log sequence number 0 43655
Jun 10 13:59:14 CDOserver mysqld[3816]: 070610 13:59:14 [Note] /usr/sbin/mysqld: Shutdown complete
Jun 10 13:59:14 CDOserver mysqld[3816]:
Jun 10 13:59:14 CDOserver mysqld_safe[4177]: ended
Jun 10 13:59:16 CDOserver named[3712]: shutting down: flushing changes
Jun 10 13:59:16 CDOserver named[3712]: stopping command channel on 127.0.0.1#953
Jun 10 13:59:16 CDOserver named[3712]: stopping command channel on ::1#953
Jun 10 13:59:16 CDOserver named[3712]: no longer listening on ::#53
Jun 10 13:59:16 CDOserver named[3712]: no longer listening on 127.0.0.1#53
Jun 10 13:59:16 CDOserver named[3712]: no longer listening on 192.168.4.2#53
Jun 10 13:59:16 CDOserver named[3712]: no longer listening on 69.9.146.90#53
Jun 10 13:59:16 CDOserver named[3712]: exiting
Jun 10 14:00:22 CDOserver named[3704]: starting BIND 9.3.4 -u bind
Jun 10 14:00:22 CDOserver named[3704]: found 1 CPU, using 1 worker thread
Jun 10 14:00:22 CDOserver named[3704]: loading configuration from '/etc/bind/named.conf'
Jun 10 14:00:22 CDOserver named[3704]: listening on IPv6 interfaces, port 53
Jun 10 14:00:22 CDOserver named[3704]: listening on IPv4 interface lo, 127.0.0.1#53
Jun 10 14:00:22 CDOserver named[3704]: listening on IPv4 interface eth0, 69.9.146.90#53
Jun 10 14:00:22 CDOserver named[3704]: listening on IPv4 interface eth1, 192.168.4.2#53
Jun 10 14:00:22 CDOserver named[3704]: command channel listening on 127.0.0.1#953
Jun 10 14:00:22 CDOserver named[3704]: command channel listening on ::1#953
Jun 10 14:00:22 CDOserver named[3704]: zone 0.in-addr.arpa/IN: loaded serial 1
Jun 10 14:00:22 CDOserver named[3704]: zone 127.in-addr.arpa/IN: loaded serial 1
Jun 10 14:00:22 CDOserver named[3704]: zone 255.in-addr.arpa/IN: loaded serial 1
Jun 10 14:00:22 CDOserver named[3704]: zone localhost/IN: loaded serial 1
Jun 10 14:00:22 CDOserver named[3704]: running
Jun 10 14:00:24 CDOserver mysqld_safe[3804]: started
Jun 10 14:00:25 CDOserver mysqld[3808]: 070610 14:00:25  InnoDB: Started; log sequence number 0 43655
Jun 10 14:00:25 CDOserver mysqld[3808]: 070610 14:00:25 [Note] /usr/sbin/mysqld: ready for connections.
Jun 10 14:00:25 CDOserver mysqld[3808]: Version: '5.0.38-Ubuntu_0ubuntu1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Jun 10 14:00:25 CDOserver /etc/mysql/debian-start[3844]: Upgrading MySQL tables if necessary.
Jun 10 14:00:26 CDOserver dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Jun 10 14:00:26 CDOserver dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Jun 10 14:00:26 CDOserver dhcpd: All rights reserved.
Jun 10 14:00:26 CDOserver dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 10 14:00:27 CDOserver /etc/mysql/debian-start[3912]: Checking for crashed MySQL tables.
Jun 10 22:35:14 CDOserver ntpdate[4302]: step time server 82.211.81.145 offset 17.191427 sec
Jun 10 22:35:15 CDOserver ntpdate[4280]: step time server 82.211.81.145 offset -0.000638 sec
root@CDOserver:/var/log#
======================
Thanks again for your help, Jon

---

### Post by juantao on 2007-06-11
Oops. I was looking at some cached pages... Actually networking does need to be restarted before the world can see my pages.
======================
kern.log from a few minutes ago
======================
Jun 10 22:35:23 CDOserver kernel: [30901.170000] eth0: no IPv6 routers present
Jun 11 09:29:14 CDOserver kernel: [70131.610000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
Jun 11 09:29:14 CDOserver kernel: [70131.660000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 11 09:29:28 CDOserver kernel: [70141.880000] eth0: no IPv6 routers present
root@CDOserver:/var/log#
=====================
and syslog
=====================
Jun 11 09:17:01 CDOserver /USR/SBIN/CRON[4701]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 11 09:29:14 CDOserver dhcpd: receive_packet failed on eth1: Network is down
Jun 11 09:29:14 CDOserver kernel: [70131.610000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
Jun 11 09:29:14 CDOserver kernel: [70131.660000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 11 09:29:20 CDOserver ntpdate[4784]: step time server 82.211.81.145 offset 3.661972 sec
Jun 11 09:29:21 CDOserver ntpdate[4762]: step time server 82.211.81.145 offset -0.000622 sec
Jun 11 09:29:28 CDOserver kernel: [70141.880000] eth0: no IPv6 routers present
root@CDOserver:/var/log#
=====================
Is this my problem? "eth0: no IPv6 routers present"

Jon

---

### Post by dbott67 on 2007-06-11
Hi Jon,

I don't think it's the IPv6 message.  As IPv6 is not utilized much (yet) it's quite likely that your ISP does not support it yet.

It makes sense that to me that you can SSH over to your LAMP box from FreeBSD *if you're connecting to the internal address* of the LAMP server ([COLOR=Blue]192.168.4.2[/COLOR]).  I'm guessing that the FreeBSD box also has 2 NICs (one public: [COLOR=Purple]69.9.146.28[/COLOR] and one private: [COLOR=Blue]192.168.4.x[/COLOR]).  But, if you're connecting to the public IP of the LAMP box ([COLOR=Purple]69.9.146.90[/COLOR]) I'm stumped.

For example, when the LAMP server network stalls, do you:

1. SSH remotely to FreeBSD on [COLOR=Purple]69.9.146.28[/COLOR].
2. And then (from FreeBSD), SSH to [COLOR=Blue]192.168.4.2

[/COLOR]If this is the case, then eth1 is staying active and the problem lies with one of the following:

1. Routing table
2. eth0 (public NIC)
3. DSL router

My instinct is telling me that it's the routing table.  Can you post the output of the following 2 commands:

```
dbott@feisty:~$ [COLOR=Red]**route -n**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.177.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.62.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```and
```
dbott@feisty:~$ [COLOR=Red]**cat /etc/resolv.conf **[/COLOR]
nameserver 192.168.1.1

```_**Here's the catch:**_  I need you to post _TWICE_.  Once while the network is *[COLOR=Red]working[/COLOR]* and then again when it [COLOR=Red]*stalls*[/COLOR].  I'm wondering if the public default gateway (69.9.146.1) is getting overwritten/removed at some point during the day, but when you restart the network, it's getting re-written.  Same thing for the DNS settings in /etc/resolv.conf.  Any difference in those 2 files would indicate that something is happening.

If so, it may be due to a DHCP setting in the **/etc/dhcp3/dhclient.conf **file that requests the network settings (such as gateways, DNS servers, etc.)

```
dbott@feisty:~$ cat /etc/dhcp3/dhclient.conf 
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, [COLOR=Red]routers[/COLOR],
        domain-name, [COLOR=Red]domain-name-servers[/COLOR], host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```If there is a difference between the 'working' and 'not working' versions of the above output, we may be able to prevent the system from overwriting the route or resolv.conf file (whatever the case may be).

-Dave

---

### Post by dbott67 on 2007-06-11
One other command you can post the output of before and after: traceroute.

You'll need to install it on the LAMP server:
```
sudo apt-get install traceroute
```An then run it against a known site (google.com) while your network is functional:
```
dbott@feisty:~$ traceroute www.google.com
traceroute: Warning: www.google.com has multiple addresses; using 216.239.51.104
traceroute to www.l.google.com (216.239.51.104), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  4.689 ms  0.580 ms  0.713 ms
 2  w.x.y.z (w.x.y.z)  16.209 ms  14.166 ms  15.041 ms
 3  sprint.someone.com (xx.yy.32.1)  15.884 ms  15.166 ms  15.055 ms
 4  f0-10.na01.b011027-0.yyz01.atlas.cogentco.com (38.112.21.193)  14.884 ms  15.239 ms  17.183 ms
 5  g9-0-3503.core01.yyz02.atlas.cogentco.com (38.20.32.105)  17.017 ms *  15.592 ms
 6  v3492.mpd01.yyz01.atlas.cogentco.com (154.54.5.81)  17.289 ms  14.431 ms  16.394 ms
 7  t7-4.mpd01.ord01.atlas.cogentco.com (154.54.7.73)  30.597 ms  30.876 ms  29.977 ms
 8  v3488.mpd01.ord03.atlas.cogentco.com (154.54.5.26)  34.844 ms  29.273 ms  28.223 ms
 9  google.ord03.atlas.cogentco.com (154.54.11.186)  33.108 ms  31.521 ms  29.214 ms
10  66.249.95.253 (66.249.95.253)  32.500 ms  30.208 ms  29.161 ms
11  72.14.236.26 (72.14.236.26)  56.289 ms  49.084 ms  49.219 ms
12  72.14.232.149 (72.14.232.149)  57.616 ms  58.789 ms 72.14.238.157 (72.14.238.157)  68.672 ms
13  216.239.46.130 (216.239.46.130)  51.409 ms 72.14.236.82 (72.14.236.82)  62.395 ms 72.14.236.117 (72.14.236.117)  55.249 ms
14  209.85.177.46 (209.85.177.46)  64.144 ms 209.85.177.174 (209.85.177.174)  64.481 ms 209.85.176.46 (209.85.176.46)  62.042 ms
15  kc-in-f104.google.com (216.239.51.104)  55.953 ms  52.712 ms  51.164 ms

```and then again when it fails.  It should give us a good indication of where the problem lies.

Also, there are a couple of hacks you can try (not all at the same time, though).  These won't fix the problem, although they may help pinpoint where the problem is:

1. Write a little script that pings a public IP address (such as [www.google.com]("http://www.google.com")) and redirects it to a file:
```

dbott@feisty:~$ [COLOR=Red]**ping www.google.com > ping-test.txt**[/COLOR]
```Then when you get home, you can check the output to see at what point it fails (if at all):
```
dbott@feisty:~$ [COLOR=Red]**cat ping-test.txt**[/COLOR]
PING www.l.google.com (216.239.51.99) 56(84) bytes of data.
64 bytes from kc-in-f99.google.com (216.239.51.99): icmp_seq=1 ttl=232 time=52.1 ms
64 bytes from kc-in-f99.google.com (216.239.51.99): icmp_seq=2 ttl=232 time=53.0 ms
64 bytes from kc-in-f99.google.com (216.239.51.99): icmp_seq=3 ttl=232 time=52.6 ms
64 bytes from kc-in-f99.google.com (216.239.51.99): icmp_seq=4 ttl=232 time=52.3 ms
64 bytes from kc-in-f99.google.com (216.239.51.99): icmp_seq=5 ttl=232 time=50.6 ms
64 bytes from kc-in-f99.google.com (216.239.51.99): icmp_seq=6 ttl=232 time=54.4 ms
64 bytes from kc-in-f99.google.com (216.239.51.99): icmp_seq=7 ttl=232 time=54.2 ms

--- www.l.google.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6002ms
rtt min/avg/max/mdev = 50.676/52.785/54.461/1.208 ms

```If it doesn't fail, then it may have to do with lack of traffic (perhaps the NIC has some power saving/sleep mode?).

2. Create a cron job that automatically restarts the network every X minutes/hours.

3. Create a batch file or script on your remote PC that pings your LAMP server every 5 seconds to see if it stays up (or when it fails).

---

### Post by juantao on 2007-06-11
One thing I wasn't clear on (maybe one of many...)

When I can't login to my LAMP server from home, I login to the FreeBSD box, but I don't restart the LAMP server via a private network (the LAMP's eth1 range is 192.168.4.0/24 and the FreeBSD box has a internal range of 192.168.6.0/24) - I succeed at restarting my network by doing ssh to 69.9.146.28 (the FreeBSD box) and after I'm there, I do a ssh to 69.9.146.90 (the LAMP server's public address) and do a /etc/init.d/networking restart. After the restart I can then login from home, webpages are up, etc...

That's what's weird... when it goes down, I can't ssh from home 69.9.151.x (dynamic) but I can from the same class C or 69.9.146.28...

I'll set up the ping tests (numbers one and three - 1. Write a little script that pings a public IP address (such as [www.google.com](www.google.com)) and redirects it to a file:
Code:

3. Create a batch file or script on your remote PC that pings your LAMP server every 5 seconds to see if it stays up (or when it fails).
6 Hours Ago 11:22 AM

And let you know what I see. Seems to go down overnight... Thanks a million!

---

### Post by Mr. C. on 2007-06-12
Why are you getting 10Mbps and half-duplex?

```
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
```

This seems more like a hub than a switch.

Where does your eth1 on the LAMP server go ?

You say your FreeBSD is proving NAT for the rest of the network (for your LAMP box too ?)

I'm sensing ARP problems here...

MrC

---

### Post by juantao on 2007-06-12
I pingged the LAMP server from home overnight and the network is down, so constant activity didn't keep the connection 'awake'... 

For Mr. C...

Eth1 on the LAMP server goes nowhere at this time. I hope to do my LAN from it eventually.
The FreeBSD's Eth1 (sic) provides NAT for my LAN but the LAMP server is not connected to it. The LAMP server gets it's Internet connection from the same DSL modem using a second static IP given by my ISP.

Bear in mind, I can connect to it via 'ssh -l <username> 69.9.146.90' from the FreeBSD box, but not issuing the same command from my home computer when it is down (like now)

I'm going to initiate a cron job to restart the network hourly and see what that does, if it helps, it will only be a workaround masking some other unknown problem though.
More later - thanks.

---

### Post by dbott67 on 2007-06-12
I just had a bit of an epiphany regarding the IP address ranges.  I didn't notice that the home connection was on a different subnet than the other 2 servers.

Both the LAMP & BSD servers are on 69.9.[COLOR=Red]146[/COLOR].xxx / 255.255.255.0; whereas the home computer is on 69.9.[COLOR=Red]151[/COLOR].xxx.  This would explain why the FreeBSD box can still connect to the LAMP server (no routing involved as both are on the same subnet), but does not explain why you can connect to FreeBSD remotely but not LAMP.

I'm not sure why restarting the network gets things working again, unless the problem is related to the default route somehow getting mangled/changed on the LAMP server.

Can you post the current **routing table** & **resolv.conf** as per post #6 (while everything is working) and then post it again just after it fails.

Maybe also post your arp table before & after failure:
```
dbott@feisty:~$ [COLOR=Red]**arp -vn**[/COLOR]
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.105            ether   00:16:CE:31:88:6F   C                     eth0
192.168.1.2              ether   00:01:D2:00:00:ED   C                     eth0
192.168.1.1              ether   00:40:05:B2:AF:45   C                     eth0
Entries: 3      Skipped: 0      Found: 3

```

---

### Post by Mr. C. on 2007-06-12
You didn't respond to my hub/switch 10Mbps question.  I see a problem here with ICMP redirects.

dbott67,
  - routing is ALWAYS involved.  All IP packets are routed to the interface specified in the routing table.
  - unless the OP is running a routing protocol besides RIP, etc. the routing table will not change magically, except if there is an ICMP redirect.

MrC

---

### Post by dbott67 on 2007-06-12
> **Mr. C. said:**
> dbott67,
  - routing is ALWAYS involved.  All IP packets are routed to the interface specified in the routing table.

I probably phrased that poorly.  I should have said *'no routing to another subnet'* (meaning that the FreeBSD box could initiate communications directly to the LAMP server, without having to pass through a router).  Of course, I may be totally out in left field... I'm just trying to think out loud as to why the LAMP NIC accepts local traffic, but not traffic from an external subnet (or so it appears).
[B]
More thinking out loud:[/B]

I've read through a number of posts from users with mulitiple interfaces (wireless & LAN) that have had problems when both interfaces are active and connected.

Try disabling eth1 (or unplugging the cable) and let it run for a while just using eth0:
```
sudo ifdown eth1
```

-Dave

---

### Post by juantao on 2007-06-13
I set up a cron job to restart the network every two hours and that has solved the problem, but I still don't know the cause. Oh Well... Now I learn about IP tables... (which means 'I'll be Bach').

---

### Post by JGJones on 2007-06-30
Hey there...I have the same problem as you somewhat...

In my case I run an eBox-Platform server with two NIC's...one is a onboard Broadcom NIC and the other is an Intel NIC (same as yours)..

They both are set to static in ebox settings, but after a while, I have to restart network (command line - ebox network restart) and all is well.

It appears that only the Intel NIC is affected - it have a static IP of 10.4.0.3 but when it fails, it seems to somehow have picked up an IP from DHCP even though it's not configured to do so, but use a static IP. It picks up an IP from the DHCP and become 10.4.1.x.

Restarting resets it to start using the default static IP that it's supposed to have.

I've not found any mention of this being a bug with eBox - and I'm not certain if it is (if it was, surely it would have gotten reported...but wanted to be sure before I report it).

So just a thought...

When your network fails, do an ifconfig after it fails and see if it still have the same IP or not. If not, then it's probably picking up from DHCP.

Cheers

---

### Post by NotRoot:-) on 2007-06-30
Maybe I can help to explain networking.

For connections to work, there must be two way traffic.
 1. From end_user to the server
 2. From the server back to the end_user

You are able to connect to one of the two servers on the same subnet from
a different network.   So this tells us that routing is in place to and back from
the servers subnet.  This also tell us that the default gateway is correct on the 
one server that works.  I strongly suspect, as others have stated,
 that the default gateway is changing
on the Lamp Server that looses its connection to other networks.

The reason that you can connect to the Lamp Server from your other server
is that they are on the same network.   The two servers can access each other
by arping on layer2.   You do not need a router to access other devices on the
same subnet.

To connect to anything on a different network, devices must be routed ( layer 3) 
to  the other network.   The default gateway is what specifies the router to use.

---

