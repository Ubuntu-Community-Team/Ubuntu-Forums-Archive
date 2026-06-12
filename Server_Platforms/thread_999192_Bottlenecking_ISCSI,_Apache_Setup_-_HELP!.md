---
title: "Bottlenecking ISCSI, Apache Setup - HELP!"
date: 2008-12-01
forum: Server Platforms
---

### Post by Biker803 on 2008-12-01
Hey guys,

Bare with me as I've been on and off using Linux/BSD the past few years and don't have a full grip on things yet...

So here's my situation:

I've got a box running Ubuntu Server 8.10 that I've been trying to setup as an ISCSI Initiator to connect to a 14TB SAN (target) I have via direct ethernet. This box (the ubuntu server) has two ethernet cards so one line goes out to the public internet and the other to the SAN (as I mentioned).

I've had quite a few problems getting up and running, some due to my ignorance but have ironed out most of everything except:

1.) My main gripe is that when I perform a 'sudo reboot' to restart the server, it never actually restarts. I get disconnected from my SSH session and am unable to reconnect, or access the web interface (apache) or connect remotely in any way -- but the server never reboots. I have to remotely pull the power to it and plug it back in, then I'm able to get it to boot up again. This happens everytime!

2.) Sparing the details of the setup, I've been able to get the Ubuntu box to act as an intitiator (open-iscsi, the version that apt-get gave me) and get it to connect to the target san, however when I first attempted to mount the san (/dev/sdb2) to my own folder (/san) I got an error about the drive being in use (or something to that effect) and was given an option to force mount (-o force) -- and by doing so I was able to mount, but not without forcing.

3.) Once everything is mounted, and working (maybe not properly, but can access SAN from /san) if I restart the server the SAN is not auto-mounted (even though I've set it to be an automatic startup in the config) and I have to reset the open-iscsi service when I log back into SSH and then it finds it again, however I end up having to remount AGAIN (-o force, again) after resetting the open-iscsi service.

4.) When doing '/etc/init.d/open-iscsi status' I get this output when everything is mounted and "seemingly" working:

```
Current active iSCSI sessions:
iscsiadm: Could not get host for sid 1.
iscsiadm: could not get host_no for session 6.
iscsiadm: could not find session info for session1
iscsiadm: Can not get list of active sessions (6)
```

5.) I'm running apache2 to allow public access to files on the SAN. I have an alias in the server config to go from [http://server/san](http://server/san) to /san on the computer. This of course, works regardless of all these other issues I'm having. The issue here (and I don't know if this is apache related) is that I can't seem to withstand more than 100mb throughput or as in apache's server-status page, 250-300 connections, because then it gets more difficult to access files. My settings for apache2 prefork are:


```
<IfModule mpm_prefork_module>
    ServerLimit         500
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients         2000
    MaxRequestsPerChild   0
</IfModule>
```

I don't know if these settings are optimal, but I think around 2000 maxclients is about what I need for this box, maybe a little less. I'm not sure if any of these other values are optimal, however. This machine currently only has 2GB of memory but will be upgraded to 4GB in a few days. I'm also serving only static content, not dynamic (with PHP or anything) currently.

Both ethernet adapters are 10/100/1000 and I have checked that they are transmitting in 1000 full duplex already, but I'm still getting a bottleneck SOMEWHERE, either in ISCSI or Apache (my guess it's one of those)... after too many connections trying to download files is very slow. I have an HTML page that I test to make sure the connection to the SAN is still working and under very low load, that file refreshes instantly (as it should being a 1/2 KB .htm file). However, when I get too many connections (haven't hit maxclients setting in apache of course) -- I get a "connecting..." and "waiting..." status in my browser bar and then sometimes 1 second, sometimes 7 seconds later I finally get the HTML file.

So something is bottlenecking. I have a similar setup on a Windows Server 2003 machine and it handles everything by itself right now (identical hardware, by the way) -- so I know the box is capable of handling this load. I'm also not running a firewall on the Ubuntu box right now. Hopefully someone has some helpful suggestions. I would much rather be moving over to Ubuntu versus Windows. I do plan to split the load between 2 or 3 boxes, but I need to get this first one working properly before I can do anything else.

Any help is greatly appreciated!

Here's the ISCSI settings:

```
winsys:raid.** --portal 192.**:3260
node.name = iqn.**
node.tpgt = 1
node.startup = automatic
iface.hwaddress = default
iface.iscsi_ifacename = default
iface.net_ifacename = default
iface.transport_name = tcp
node.discovery_address = 192.**
node.discovery_port = 3260
node.discovery_type = send_targets
node.session.initial_cmdsn = 0
node.session.initial_login_retry_max = 4
node.session.cmds_max = 128
node.session.queue_depth = 32
node.session.auth.authmethod = None
node.session.auth.username = <empty>
node.session.auth.password = <empty>
node.session.auth.username_in = <empty>
node.session.auth.password_in = <empty>
node.session.timeo.replacement_timeout = 120
node.session.err_timeo.abort_timeout = 10
node.session.err_timeo.reset_timeout = 30
node.session.iscsi.InitialR2T = No
node.session.iscsi.ImmediateData = Yes
node.session.iscsi.FirstBurstLength = 262144
node.session.iscsi.MaxBurstLength = 16776192
node.session.iscsi.DefaultTime2Retain = 0
node.session.iscsi.DefaultTime2Wait = 0
node.session.iscsi.MaxConnections = 1
node.session.iscsi.MaxOutstandingR2T = 1
node.session.iscsi.ERL = 0
node.conn[0].address = 192.**
node.conn[0].port = 3260
node.conn[0].startup = manual
node.conn[0].tcp.window_size = 524288
node.conn[0].tcp.type_of_service = 0
node.conn[0].timeo.logout_timeout = 15
node.conn[0].timeo.login_timeout = 15
node.conn[0].timeo.auth_timeout = 45
node.conn[0].timeo.active_timeout = 5
node.conn[0].timeo.idle_timeout = 60
node.conn[0].timeo.ping_timeout = 5
node.conn[0].timeo.noop_out_interval = 10
node.conn[0].timeo.noop_out_timeout = 15
node.conn[0].iscsi.MaxRecvDataSegmentLength = 131072
node.conn[0].iscsi.HeaderDigest = None,CRC32C
node.conn[0].iscsi.DataDigest = None
node.conn[0].iscsi.IFMarker = No
node.conn[0].iscsi.OFMarker = No
```

---

### Post by Biker803 on 2008-12-01
I should probably mention that this is the 64-bit version of Ubuntu 8.10...

---

