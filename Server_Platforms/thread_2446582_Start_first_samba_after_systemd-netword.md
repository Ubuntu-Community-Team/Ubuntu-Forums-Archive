---
title: "Start first samba after systemd-netword"
date: 2020-07-03
forum: Server Platforms
---

### Post by badapple7 on 2020-07-03
Hi to all, I new user of forum, always read for resolve my problems but today I write one. I live In Argentina, Yup!!! my english is very bad....

Well, after recived error in samba 

```


Jul  3 03:14:05 XXX samba[815]:   samba: using 'standard' process model
Jul  3 03:14:05 XXX winbindd[1127]: [2020/07/03 03:14:05.000435,  0] ../source3/winbindd/winbindd_cache.c:3170(initialize_winbindd_cache)
Jul  3 03:14:05 XXX winbindd[1127]:   initialize_winbindd_cache: clearing cache and re-creating with version number 2
Jul  3 03:14:05 XXX samba[1126]: [2020/07/03 03:14:05.037981,  0] ../lib/util/util_runcmd.c:327(samba_runcmd_io_handler)
Jul  3 03:14:05 XXX samba[1126]:   /usr/sbin/samba_dnsupdate: interpret_string_addr_internal: getaddrinfo failed for name enp1s0 (flags 32) [Temporary failure in name resolution]
Jul  3 03:14:05 XXX samba[1126]: [2020/07/03 03:14:05.038048,  0] ../lib/util/util_runcmd.c:327(samba_runcmd_io_handler)
Jul  3 03:14:05 XXX samba[1126]:   /usr/sbin/samba_dnsupdate: interpret_interface: Can't find address for enp1s0
Jul  3 03:14:05 XXX smbd[1116]: [2020/07/03 03:14:05.078778,  0] ../lib/util/become_daemon.c:124(daemon_ready)
Jul  3 03:14:05 XXX smbd[1116]:   STATUS=daemon 'smbd' finished starting up and ready to serve connections
Jul  3 03:14:05 XXX systemd[1]: Started Samba AD Daemon.
Jul  3 03:14:05 XXX winbindd[1127]: [2020/07/03 03:14:05.087682,  0] ../lib/util/become_daemon.c:124(daemon_ready)
Jul  3 03:14:05 XXX winbindd[1127]:   STATUS=daemon 'winbindd' finished starting up and ready to serve connections
Jul  3 03:14:06 XXX systemd-networkd[731]: enp1s0: Gained carrier
Jul  3 03:14:06 XXX systemd-timesyncd[728]: Network configuration changed, trying to establish connection.
Jul  3 03:14:06 XXX named[822]: listening on IPv4 interface enp1s0, 192.168.100.5#53
Jul  3 03:14:06 XXX kernel: [    8.390773] r8169 0000:01:00.0 enp1s0: link up
Jul  3 03:14:06 XXX kernel: [    8.390778] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
Jul  3 03:14:08 XXX systemd-networkd[731]: enp1s0: Gained IPv6LL
Jul  3 03:14:08 XXX systemd-networkd[731]: enp1s0: Configured
Jul  3 03:14:08 XXX systemd-timesyncd[728]: Network configuration changed, trying to establish connection.
Jul  3 03:14:08 XXX systemd-networkd-wait-online[756]: managing: enp1s0
Jul  3 03:14:08 XXX systemd-networkd-wait-online[756]: ignoring: lo
Jul  3 03:14:08 XXX systemd[1]: Started Wait for Network to be Configured.
Jul  3 03:14:08 XXX systemd[1]: Reached target Network is Online.

```

only solution; I don't "declare" bind interface in smb.conf, and samba start equal, or restart service.  


After read syslog I watch that samba start first that systemd-networkd, I think that is the problem (Use Ubuntu-server 18.04.4). But in ubuntu 18.04.1 dont problems! first start networkd after samba. I use samba ad, but I installed exact config file and result is always equal.


-------
Other problem, this server "work" with bind, isc-dhcp and samba-ad, the company is family, the software work program on bases *.mdb, other problem, samba worked smb3_11 result? bases corrupt, in 18.04.1 I can forced samba "max protocol NT1" and to work!!! but in 18.04.4 active NT1(smb1) no worked! 

solution?? disable time cache in pc client (win10)


Why smb1? because bases *.mdb work real time, and with cache active(smb2, smb3) no conexion in real time, I said before .. result  *.mdb corrupts.

---------------

repit! sorry for my bad english. i hope help please! Is true, I can solution provisory, I l dont final solution...

---

### Post by TheFu on 2020-07-03
Just a guess, but I'd make certain that the smbd.service "unit file" has a dependency on the networking.service - so networking is always running before samba.  I couldn't find a smbd.service file on my only system running samba (it is 16.04).  However, in the networking.service file, located in /etc/systemd/system/network-online.target.wants, there are "Before=" and "WantedBy=" options which can be used to ensure the correct order. Add the smbd.target to the "Before=" link - that's my guess.

The smbd parts may be "samba" or something else for AD-based Samba stuff. I don't know.

I wasn't able to test. Sorry.

Devices that require NT1 protocol need to be replaced, especially in a business.  That protocol makes taking over a complete domain, all storage and all systems trivial.

---

### Post by badapple7 on 2020-07-03
> **TheFu said:**
> Just a guess, but I'd make certain that the smbd.service "unit file" has a dependency on the networking.service - so networking is always running before samba.  I couldn't find a smbd.service file on my only system running samba (it is 16.04).  However, in the networking.service file, located in /etc/systemd/system/network-online.target.wants, there are "Before=" and "WantedBy=" options which can be used to ensure the correct order. Add the smbd.target to the "Before=" link - that's my guess.

The smbd parts may be "samba" or something else for AD-based Samba stuff. I don't know.

I wasn't able to test. Sorry.

Devices that require NT1 protocol need to be replaced, especially in a business.  That protocol makes taking over a complete domain, all storage and all systems trivial.

Hi, thanks your time...well I find /lib/systemd/system/smbd.service, But all is correct, samba should start after networkd
```

[Unit]
Description=Samba SMB Daemon
Documentation=man:smbd(8) man:samba(7) man:smb.conf(5)
After=network.target nmbd.service winbind.service


[Service]
Type=notify
NotifyAccess=all
PIDFile=/var/run/samba/smbd.pid
LimitNOFILE=16384
EnvironmentFile=-/etc/default/samba
ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS
ExecReload=/bin/kill -HUP $MAINPID
LimitCORE=infinity


[Install]
WantedBy=multi-user.target

```

Sorry but dont much idea about this config (systemd). I want write on network-pre, but it should be in front of the server pysically 

---

yup! very soom I work for migrate bases mdb to sql :-)
[FONT=arial] no samba should start after networkd[/FONT]

---

