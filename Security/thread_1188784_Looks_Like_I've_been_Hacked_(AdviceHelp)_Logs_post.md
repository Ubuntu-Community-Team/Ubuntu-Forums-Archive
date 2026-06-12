---
title: "Looks Like I've been Hacked (Advice/Help) Logs posted"
date: 2009-06-16
forum: Security
---

### Post by Ashocka on 2009-06-16
I've posted one session here [http://pastebin.com/d662e4bbe](http://pastebin.com/d662e4bbe)

Anyone have any suggestions or advice, it would be much appreciated.  I'm not up to date with linux logs, but there's stuff going on here that doesn't look good or attributed to me.  Firestarter sees none of this.  My machine is crashing a lot too.

G.

---

### Post by brian_p on 2009-06-16
> **Ashocka said:**
> 

I'm not up to date with linux logs, but there's stuff going on here that doesn't look good or attributed to me.  Firestarter sees none of this.  My machine is crashing a lot too.

```
Jun 16 10:44:59 my-desktop kernel: Cannot find map file.
```

doesn't look good but is hardly security related. Posting your problem (which is nothing to do with being hacked) in another forum might bring a better response.

---

### Post by Ashocka on 2009-06-16
Hi Brian,

Yes, I have to agree with you on that.

Here's where I think there are security compromises

> Jun 16 10:44:59 my-desktop chat[3271]: expect (OK)
Jun 16 10:45:00 my-desktop mysqld_safe[3433]: started
Jun 16 10:45:00 my-desktop mysqld[3436]: 090616 10:45:00  InnoDB: Started; log sequence number 0 43655
Jun 16 10:45:00 my-desktop mysqld[3436]: 090616 10:45:00 [Note] /usr/sbin/mysqld: ready for connections.
Jun 16 10:45:00 my-desktop mysqld[3436]: Version: '5.0.75-0ubuntu10.2'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Jun 16 10:45:01 my-desktop /etc/mysql/debian-start[3475]: Upgrading MySQL tables if necessary.
Jun 16 10:45:01 my-desktop /etc/mysql/debian-start[3481]: Looking for 'mysql' as: /usr/bin/mysql
Jun 16 10:45:01 my-desktop /etc/mysql/debian-start[3481]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jun 16 10:45:01 my-desktop /etc/mysql/debian-start[3481]: This installation of MySQL is already upgraded to 5.0.75, use --force if you still need to run mysql_upgrade
Jun 16 10:45:01 my-desktop /etc/mysql/debian-start[3566]: Checking for insecure root accounts.

and 

> un 16 10:45:26 my-desktop NetworkManager: <info>  starting... 
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Successfully dropped root privileges.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: avahi-daemon 0.6.23 starting up.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Successfully called chroot().
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Successfully dropped remaining capabilities.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: No service file found in /etc/avahi/services.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Joining mDNS multicast group on interface virbr0.IPv4 with address 192.168.122.1.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: New relevant interface virbr0.IPv4 for mDNS.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.29.45.18.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Network interface enumeration completed.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Registering new address record for fe80::ac10:2dff:fed8:bdab on virbr0.*.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Registering new address record for 192.168.122.1 on virbr0.IPv4.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Registering new address record for fe80::219:d1ff:fe9d:a1a8 on eth0.*.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Registering new address record for 10.29.45.18 on eth0.IPv4.
Jun 16 10:45:26 my-desktop avahi-daemon[4412]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 16 10:45:27 my-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000e') 
Jun 16 10:45:27 my-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_19_d1_9d_a1_a8 
Jun 16 10:45:27 my-desktop NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Jun 16 10:45:27 my-desktop NetworkManager: <info>  (ttyS1): ignoring due to lack of mobile broadband capabilties 
Jun 16 10:45:27 my-desktop NetworkManager: <info>  Trying to start the supplicant... 
Jun 16 10:45:27 my-desktop NetworkManager: <info>  Trying to start the system settings daemon... 
Jun 16 10:45:27 my-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Jun 16 10:45:27 my-desktop hal_lpadmin: Running hal_lpadmin

and

> Jun 16 10:45:59 my-desktop chat[3271]: alarm
Jun 16 10:45:59 my-desktop chat[3271]: send (AT^M)
Jun 16 10:45:59 my-desktop chat[3271]: expect (OK)
Jun 16 10:46:38 my-desktop kernel: [  142.207826] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=192.168.122.255 LEN=268 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=248 
Jun 16 10:46:59 my-desktop chat[3271]: alarm
Jun 16 10:46:59 my-desktop chat[3271]: Failed
Jun 16 10:46:59 my-desktop pppd[2716]: Connect script failed
Jun 16 10:47:00 my-desktop pppd[2716]: Exit.

Is there anything to worry about here?

---

### Post by rookcifer on 2009-06-16
virbr0 is for bridging (sometimes used in virtualization for the VM to connect to the "real" physical device).  Are you running a VM like VirtualBox?  If not, have you tried to bridge your interfaces for any reason?

At any rate, it doesn't look to be a security issue, as the IP addresses listed in that log are all local NAT'ed addresses.  192.xx and 10.xxx are local addresses.  Nothing remote here.

---

### Post by HermanAB on 2009-06-16
Avahi is used by an iPod or similar device to get an IP address.  So it looks to me like you plugged your iPod in.

---

### Post by Ashocka on 2009-06-16
Thanks very much for the feedback.

I've shutdown none essential services.  Will have to fix the problem at boot and get a better handle on understanding my system in more depth.

Once again, thanks.

(I really did think I saw an intrusion but I can't find it now... could have just been seeing ghosts in the machine).

---

### Post by Agent ME on 2009-06-16
> **HermanAB said:**
> Avahi is used by an iPod or similar device to get an IP address.  So it looks to me like you plugged your iPod in.
Avahi has nothing to do with ipods, besides it being an implementation of a protocol made by Apple. It's a service discovery protocol enabled in Ubuntu by default.

Nothing in the logs posted here makes it look like you've been hacked. Everything besides the kernel error messages is pretty normal for someone with MySQL and a vm.

---

