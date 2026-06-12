---
title: "Periodically locked out of headless server"
date: 2008-02-11
forum: Server Platforms
---

### Post by userid on 2008-02-11
I've got a lovely headless server with ubuntu 7.04 at the other end of the world, and every so often (once a month?) it decides to lock itself down entirely, so I cannot access it at all via ssh or vnc and it has to be restarted by my housemates :), but I know its there because its updating the no-ip account so I can ping the router..

Are there any ways of eliminating/troubleshooting the cause for this behaviour? Is anyone acquainted with any related bug reports?

---

### Post by k_grdn on 2008-02-11
Hi,

Monthly ey?

Most likely culprit is syslog, check the scripts in /etc/logrotate.d/ these are run by syslog, run them individually to see which throws up errors, logrotate restarts the program while cleaning out logfiles, possibly a config error somewhere.

Grep /var/log/syslog at the next occurrence to see which prog is causing problems.

Check root mail account for email alerts from cron & syslog.

Check your monthly cron scripts for syntax errors.

Regards,

k_grdn

---

### Post by userid on 2008-02-11
Thanks very much for your quick response.

Monthly was actually a rough guess, I'm not entirely certain there!

There were some superfluous scripts in the directory logrotate.d, can I remove them?

If I execute the scripts, will this not cause the lockdown again?

Thanks again!

---

### Post by k_grdn on 2008-02-11
Check syslog for errors to give you an indication of the frequency of the problem.

If you access the box via ssh your session will not be killed.

Review the logrotate scripts, it's safe to temporally move the scripts to a hold directory.  These scripts just compress your log files but eventually /var will fill up and will cause a system failure of some sort.

Move the scripts one at a time back to logrotate.d until you find the one causing you problems.

This will be long winded, best bet to check syslog for errors give the program what it needs.

Regards,

k_grdn

---

### Post by userid on 2008-02-13
Its actually getting more confusing/worse:

I've just had the problem again (vnc/ssh timeout/unresponsive), and then it resolved itself automagically..

Any ideas what could be causing this erratic behaviour?

Thanks..

---

### Post by k_grdn on 2008-02-13
Hi,

This is a remote box?

Are you connected for long periods of time? could be your ISP dropping the connection.

Is your box firewalled (iptables)? Are you using connection tracking states?

The state could be over written in the state table, states are reliant on RAM and table size.

Could be physical layer, card, cabling.

Packets lost in transition.

Again check your logs and post back.

Regards,

k_grdn

---

### Post by userid on 2008-02-13
Thanks for your quick response again. I think your original idea will have to be discarded in light of the frequency of these incidents.

Its not disconnecting, its temperamental in terms of logging in, e.g. logs in fine all day (several times), then "timeout" on ssh and vnc in the morning..

It's remote as remote gets! I guesstimate 12.000 km at this time.

> Is your box firewalled (iptables)? Are you using connection tracking states?

The state could be over written in the state table, states are reliant on RAM and table size.

As far as linux comes w iptables set, vnc and ssh obviously opened. I do not know what *connection tracking states* are, sorry. My immediate theory would be something with iptables "locking up" or not releasing the port after a session.

After a few hours of timeing out today, it suddenly permitted login again; the normally persistent ssh-session had reset itself however (i.e. fresh gnome desktop). This seems indicative of some sort of software freeze at the remote end.

Regarding the logs, I am relatively noobish with this, would you be so kind as to specify a command to print something useful?

---

### Post by k_grdn on 2008-02-13
Hi,

Not to worry about connection tracking unless you hand coded your iptables script. 

Regarding log checking grep is your friend:

egrep 'ssh[d]|refused|connect|error|cron[tab]|failed' /var/log/auth.log

Try the same on /var/log/syslog, look for common signs of errors.

Next time you get a time out via ssh, add a -vvv to the end of the command to see whats happening.

Regards,

k_grdn

---

### Post by userid on 2008-02-13
Hello k_grdn,

you've dont this before hey!

/var/log/auth.log

```
Feb 13 15:01:33 server sshd[2855]: (pam_unix) check pass; user unknown
Feb 13 15:01:33 server sshd[2855]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net 
Feb 13 15:01:35 server sshd[2855]: Failed password for invalid user www from 216.110.6.57 port 47679 ssh2
Feb 13 15:01:37 server sshd[2859]: Invalid user www1 from XXXXXXX
Feb 13 15:01:38 server sshd[2859]: (pam_unix) check pass; user unknown
Feb 13 15:01:38 server sshd[2859]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net 
Feb 13 15:01:40 server sshd[2859]: Failed password for invalid user www1 from XXXXXXXX7 port 48860 ssh2
Feb 13 15:01:43 server sshd[2863]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net  user=root
Feb 13 15:01:45 server sshd[2863]: Failed password for root fromXXXXXXX7 port 49974 ssh2
Feb 13 15:01:49 server sshd[2867]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net  user=root
Feb 13 15:01:51 server sshd[2867]: Failed password for root from XXXXXXXXXXx7 port 51119 ssh2
Feb 13 15:01:55 server sshd[2870]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net  user=ftp
Feb 13 15:01:57 server sshd[2870]: Failed password for ftp from XXXXXXXXX7 port 56081 ssh2
Feb 13 15:01:59 server sshd[2874]: Invalid user ftpuser from XXXXXXXXXXX
Feb 13 15:02:00 server sshd[2874]: (pam_unix) check pass; user unknown
Feb 13 15:02:01 server sshd[2874]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net 
Feb 13 15:02:02 server sshd[2874]: Failed password for invalid user ftpuser from XXXXXXXXXXXX port 57296 ssh2
Feb 13 15:02:04 server sshd[2880]: Invalid user data from XXXXXXXXXXXX
Feb 13 15:02:06 server sshd[2880]: (pam_unix) check pass; user unknown
Feb 13 15:02:06 server sshd[2880]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net 
Feb 13 15:02:07 server sshd[2880]: Failed password for invalid user data from XXXXXXXXXXXX port 58424 ssh2
Feb 13 15:02:13 server sshd[2885]: Invalid user oracle from XXXXXXXXXXXX
Feb 13 15:02:13 server sshd[2885]: (pam_unix) check pass; user unknown
Feb 13 15:02:13 server sshd[2885]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net 
Feb 13 15:02:14 server sshd[2885]: Failed password for invalid user oracle from XXXXXXXXXXXX port 59545 ssh2
Feb 13 15:02:20 server sshd[2888]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net  user=root
Feb 13 15:02:22 server sshd[2888]: Failed password for root from XXXXXXXXXXXX port 32839 ssh2
Feb 13 15:02:31 server sshd[2893]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net  user=user
Feb 13 15:02:32 server sshd[2893]: Failed password for user from XXXXXXXXXXXX port 35352 ssh2
Feb 13 15:02:39 server sshd[2899]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net  user=root
Feb 13 15:02:42 server sshd[2899]: Failed password for root from XXXXXXXXXXXX port 37678 ssh2
Feb 13 15:02:49 server sshd[2904]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net  user=root
Feb 13 15:02:51 server sshd[2904]: Failed password for root from XXXXXXXXXXXX port 39718 ssh2
Feb 13 15:03:00 server sshd[2910]: Invalid user install from XXXXXXXXXXXX
Feb 13 15:03:04 server sshd[2910]: (pam_unix) check pass; user unknown
Feb 13 15:03:06 server sshd[2910]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=216-110-6-57.static.twtelecom.net 
Feb 13 15:03:08 server sshd[2910]: Failed password for invalid user install from XXXXXXXXXXXX port 41842 ssh2
Feb 13 15:09:44 server sshd[1300]: (pam_unix) session closed for user user
Feb 13 15:09:57 server sshd[3096]: Accepted password for user from XXXXXXXXXXXX port 58249 ssh2
Feb 13 15:09:57 server sshd[3102]: (pam_unix) session opened for user user by (uid=0)
Feb 13 16:03:07 server sshd[3102]: (pam_unix) session closed for user user
Feb 13 18:58:05 server sshd[14049]: Did not receive identification string from XXXXXXXXXXXX
Feb 13 19:04:03 server sshd[14194]: Invalid user staff from XXXXXXXXXXXX
Feb 13 19:04:23 server sshd[14194]: reverse mapping checking getaddrinfo for host122-244-static.26-213-b.business.telecomitalia.it failed - POSSIBLE BREAK-IN ATTEMPT!
Feb 13 19:04:23 server sshd[14194]: (pam_unix) check pass; user unknown
Feb 13 19:04:23 server sshd[14194]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=XXXXXXXXXXX 
Feb 13 19:04:26 server sshd[14194]: Failed password for invalid user staff from XXXXXXXXXXXX port 44205 ssh2
Feb 14 00:31:19 server sshd[22173]: Did not receive identification string from XXXXXXXXXXXX
Feb 14 00:34:38 server sshd[22254]: Invalid user admin from XXXXXXXXXXXX
Feb 14 00:34:44 server sshd[22254]: (pam_unix) check pass; user unknown
Feb 14 00:34:44 server sshd[22254]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=XXXXXXXXXXXX
Feb 14 00:34:46 server sshd[22254]: Failed password for invalid user admin from XXXXXXXXX port 60217 ssh2
Feb 14 00:40:53 server sshd[22407]: Accepted password for user from XXXXXXXXX port 39443 ssh2
Feb 14 00:40:53 server sshd[22417]: (pam_unix) session opened for user user by (uid=0)

```

looks like someones trying it on.. strange they're not trying the vnc channel. The last successful login is myself btw.

/var/log/syslog

```

Feb 13 12:06:49 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:06:51 server NetworkManager: <information>^IActivation (eth0) failed. 
Feb 13 12:06:52 server avahi-autoipd(eth0)[30395]: fopen() failed: Permission denied
Feb 13 12:06:52 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:06:53 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:06:55 server NetworkManager: <information>^IActivation (eth0) failed. 
Feb 13 12:06:57 server NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Feb 13 12:06:57 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:06:57 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:06:59 server NetworkManager: <information>^IActivation (eth0) failed. 
Feb 13 12:07:00 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:07:00 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:07:01 server avahi-autoipd(eth0)[30395]: fopen() failed: Permission denied
Feb 13 12:07:03 server NetworkManager: <information>^IActivation (eth0) failed. 
Feb 13 12:07:04 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:07:04 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:07:10 server avahi-autoipd(eth0)[30396]: Script execution failed with return value 2
Feb 13 12:18:24 server NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Feb 13 12:18:25 server avahi-autoipd(eth0)[30834]: fopen() failed: Permission denied
Feb 13 12:18:25 server NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Feb 13 12:18:25 server NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Feb 13 12:18:31 server NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Feb 13 12:18:31 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:18:31 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:18:33 server NetworkManager: <information>^IActivation (eth0) failed. 
Feb 13 12:18:34 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:18:34 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:18:35 server avahi-autoipd(eth0)[30834]: fopen() failed: Permission denied
Feb 13 12:18:36 server avahi-autoipd(eth0)[30835]: Script execution failed with return value 2
Feb 13 12:31:51 server NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Feb 13 12:31:51 server avahi-autoipd(eth0)[31278]: fopen() failed: Permission denied
Feb 13 12:31:52 server NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Feb 13 12:31:52 server NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Feb 13 12:32:00 server NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Feb 13 12:32:00 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:32:00 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:32:01 server avahi-autoipd(eth0)[31278]: fopen() failed: Permission denied
Feb 13 12:48:03 server NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Feb 13 12:48:03 server avahi-autoipd(eth0)[31778]: fopen() failed: Permission denied
Feb 13 12:48:04 server NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Feb 13 12:48:04 server NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Feb 13 12:48:09 server NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Feb 13 12:48:09 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:48:09 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:48:11 server NetworkManager: <information>^IActivation (eth0) failed. 
Feb 13 12:48:12 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:48:12 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:48:13 server avahi-autoipd(eth0)[31778]: fopen() failed: Permission denied
Feb 13 12:48:14 server avahi-autoipd(eth0)[31779]: Script execution failed with return value 2
```

Could this be the problem?

---

### Post by k_grdn on 2008-02-14
Hi,

I would base my suspicions on this:

> Feb 13 12:48:03 server NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Feb 13 12:48:03 server avahi-autoipd(eth0)[31778]: fopen() failed: Permission denied
Feb 13 12:48:04 server NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Feb 13 12:48:04 server NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Feb 13 12:48:09 server NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Feb 13 12:48:09 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:48:09 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:48:11 server NetworkManager: <information>^IActivation (eth0) failed. 
Feb 13 12:48:12 server NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Feb 13 12:48:12 server NetworkManager: <information>^IWill activate connection 'eth0'. 
Feb 13 12:48:13 server avahi-autoipd(eth0)[31778]: fopen() failed: Permission denied
Feb 13 12:48:14 server avahi-autoipd(eth0)[31779]: Script execution failed with return value 2

As for the dictionary attacks install denyhosts or failtoban, implement tcp wrappers to only allow your subnets/hosts, enforce ssh ver2, no root login, pam_listfile etc....

Regards,

k_grdn

---

### Post by k_grdn on 2008-02-14
Hi,

Looks like NetworkManager is killing eth0,  stating 'terminating current connection 'eth0' because it's no longer valid'.  Then when dhcp reassigns address your connection comes back up.

Regards,

k_grdn

---

### Post by k_grdn on 2008-02-14
Grep syslog for messages related to eth0.

grep eth0 /var/log/syslog

Also run ifconfig eth0, look for high amount of errors for TX RX., could be related to your ethernet card, possibly drivers or hardware.

Regards,

k_grdn

---

### Post by userid on 2008-02-14
Thanks again.

Not too worried about the brute force, got noroot and ssh2 activated. More worried someone may try this on vncserver, seems a lot less secure (no trylogin delay etc)

The underlying problem could indeed be this eth0/avahi business; although the network seems to come back after just a few seconds. in the actual scenario on the other hand, the server is seemingly disconnected from the network for hours/until reboot, although it's still sending no-ip updates


ifconfig fine:

          RX packets:14015021 errors:0 dropped:0 overruns:0 frame:1
          TX packets:12881153 errors:0 dropped:0 overruns:0 carrier:0

syslog only yields this:

Feb 14 07:50:24 server kernel: [208380.793255] Inbound IN=eth0 OUT= MAC=00:0d:87:24:16:50:00:15:e9:16:4e:0c:08:00 SRC=XXXXXXXXXX DST=XXXXXXXXXX LEN=73 TOS=0x00 PREC=0x00 TTL=58 ID=43826 PROTO=UDP SPT=53 DPT=1941 LEN=53 
Feb 14 11:35:52 server kernel: [221887.024054] Inbound IN=eth0 OUT= MAC=00:0d:87:24:16:50:00:15:e9:16:4e:0c:08:00 SRC=XXXXXXX DST=XXXXXXXXX LEN=74 TOS=0x00 PREC=0x00 TTL=58 ID=2610 PROTO=UDP SPT=53 DPT=1945 LEN=54

---

### Post by k_grdn on 2008-02-14
Hi,

Do you actully need th avahi daemon running?

Description: Avahi mDNS/DNS-SD daemon
 Avahi is a fully LGPL framework for Multicast DNS Service Discovery.
 It allows programs to publish and discover services and hosts
 running on a local network with no specific configuration.  For
 example you can plug into a network and instantly find printers to
 print to, files to look at and people to talk to.
 .
 This package contains the Avahi Daemon which represents your machine
 on the network and allows other applications to publish and resolve
 mDNS/DNS-SD records.

Description: Avahi IPv4LL network address configuration daemon
 Avahi is a fully LGPL framework for Multicast DNS Service Discovery.
 It allows programs to publish and discover services and hosts
 running on a local network with no specific configuration.  For
 example you can plug into a network and instantly find printers to
 print to, files to look at and people to talk to.
 .
 This tool implements IPv4LL, "Dynamic Configuration of IPv4 Link-Local
 Addresses" (IETF RFC3927), a protocol for automatic IP address
 configuration from the link-local 169.254.0.0/16 range without the
 need for a central server. It is primarily intended to be used in
 ad-hoc networks which lack a DHCP server.


Edit: /etc/default/avahi-daemon

Change:
AVAHI_DAEMON_START=1

To:
AVAHI_DAEMON_START=0

Regards,

k_grdn

---

### Post by userid on 2008-02-14
Indeed.. router should be providing dhcp.. disabled, killed, praying it helps ;) 

Best regards from brazil

---

### Post by userid on 2008-02-16
debug2: ssh_connect: needpriv 0
debug1: Connecting to XXXXXXXXg [XXXXXXXXX] port 22.
debug1: connect to address XXXXXXXXX port 22: Connection timed out
ssh: connect to host  XXXXXXXXX port 22: Connection timed out

hm.. locked out again.. ahavi is off.. :(

new variation on theme:

debug1: Connecting to XXXXXXXXg [XXXXXXXXX] port 22.
debug1: connect to address  XXXXXXXXX port 22: Connection refused
ssh: connect to host  XXXXXXXXX port 22: Connection refused

---

### Post by JonathanRRogers on 2008-02-17
You might want to disable NetworkManager, as it's designed primarily for mobile machines with transient network connections. It offers no benefits for the type of server setup described AFAIK and it might even be causing trouble. I think /etc/network/interfaces is the best place to configure the interface.

---

### Post by userid on 2008-02-18
Thanks for your response.. I suppose this could be causing network hickups, although it may be worth considering that no-ip is still receiving ip address updates

---

### Post by JonathanRRogers on 2008-02-18
> **userid said:**
> Thanks for your response.. I suppose this could be causing network hickups, although it may be worth considering that no-ip is still receiving ip address updates

That would seem to indicate that the machine has a usable Internet connection. Maybe it's a firewall or routing issue on or near the machine. Are there any NATs or firewalls between the machine and the Internet? Does a traceroute or tracepath seem to get close to the machine even when SSH connections fail?

---

### Post by userid on 2008-02-18
there is actually a d-link household router in there, but I also got the lockouts on the internal network, restarting the router didnt help; hence I assume its in the server..

---

### Post by userid on 2008-02-25
Any ideas regarding analisys of iptables for this?

---

### Post by JonathanRRogers on 2008-02-25
An iptables rule that would cause incoming connections to be refused would probably be in the INPUT chain. You can see the rules there by typing "sudo iptables -L INPUT". The command "sudo iptables -L" shows you all rules in the main "filter" table. For instance, on my desktop, I see this the following, which shows I have an empty filter table and IP datagrams are accepted everywhere by default:
```
jrogers@zaphod:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
jrogers@zaphod:~$
```Other tables that could be playing a role are "nat" and "mangle". You can select the table to view with iptable's -t option. For more info, see the [iptables man page]("http://linux.die.net/man/8/iptables") and this [HOWTO]("https://help.ubuntu.com/community/IptablesHowTo").

---

### Post by userid on 2008-02-25
```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.0.1          anywhere
ACCEPT     0    --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       0    --  anywhere             255.255.255.255
DROP       0    --  anywhere             192.168.0.255
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.104        192.168.0.1         tcp dpt:domain
ACCEPT     udp  --  192.168.0.104        192.168.0.1         udp dpt:domain
ACCEPT     0    --  anywhere             anywhere
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       0    --  255.255.255.255      anywhere
DROP       0    --  anywhere             0.0.0.0
DROP       0    --  anywhere             anywhere            state INVALID
OUTBOUND   0    --  anywhere             anywhere
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:5900:5901
ACCEPT     udp  --  anywhere             anywhere            udp dpts:5900:5901
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4672
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4672
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4671
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4671
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:32461
ACCEPT     udp  --  anywhere             anywhere            udp dpt:32461
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:32462
ACCEPT     udp  --  anywhere             anywhere            udp dpt:32462
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:32464
ACCEPT     udp  --  anywhere             anywhere            udp dpt:32464
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4674
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4674
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:32463
ACCEPT     udp  --  anywhere             anywhere            udp dpt:32463
LSI        0    --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       0    --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  0    --  anywhere             anywhere
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     0    --  anywhere             anywhere
```

Thanks v much.. 

This is the output for -L, -t nat / -t mangle show empty files

Theres quite a lot going on. A few ports are open for bittorrent/emule etc (principal use of this machine); I added these using firestarter

I just dont get how/why iptables could/would lock up randomly, sometimes even to open up again at a later time (mostly not).

---

### Post by JonathanRRogers on 2008-02-25
I find the CODE tags useful on this forum, since they format the text inside with a fixed-width font, making tables output by commands like iptables easier to read than a variable-width font like the QUOTE tags generate.

Well, as it doesn't sound like you wrote those iptables rules yourself, I assume they're being automatically generated by some firewall script or manager. Do you know what you're running that's generating those rules? Whatever it is could be changing rules periodically or when some state changes. Don't change iptables rules directly, but rather try to configure the program that's generating them. Either configure it to allow connections to SSH (TCP port 22) from the Internet at large or turn the program off for now to see what happens.

Of course, if it's off, there's a greater chance of a successful attack from someone else against one of the many services that could be running on the machine. Turn off or uninstall any services (like samba, apache, bind, nfs, etc) that you aren't using. As has already been pointed out, you probably don't need Avahi and network-manager on that machine. Make sure the firewall between the machine in question and the Internet is set up to allow a minimum of access to the machine, probably just TCP port 22 in your case. It's also a good idea to set up public key authentication and then turn off password authentication in /etc/ssh/sshd_config, since brute forcing or guessing keys is almost impossible, but doing the same against a weak or common password might not take long.

---

### Post by userid on 2008-02-25
A few ports are open for bittorrent/emule etc (principal use of this machine); I added these using firestarter..

SSH is open for the internet as large, theres usually an ongoing brute force attack, am planning to introduce a retry-failure-ban script of some sort

I don't think firestarter could be causing the lockup.. you were suggesting killing networkmanager at some stage, problem is I only have remote access to the machine and I dont want to permanently kill its network connection..

There appears to be nothing further in the logs, Ive looked through them a few times after each occurence

---

### Post by JonathanRRogers on 2008-02-25
Yeah, that iptables output is  a lot easier to read now. Now that I look more closely, I see that there is a rule allowing SSH incoming connections in the INBOUND chain, which must have been created by firestarter.

If I understand correctly, NetworkManger is running on the machine, but I'm not sure how it's configured. If you have put it in Manual Configuration mode, using either DHCP or static IP configuration, it's probably not interfering with anything. I'd be more suspicious of it if it's in roaming mode.

If you don't currently have physical access to the machine, I'd agree that it would be better not to change any more in the network configuration than necessary. However, when you do have physical access to the machine, I still think it would be a good idea to uninstall NetworkManger and configure the interfaces in /etc/network/interfaces.

I also asked how close traceroute or tracepath seems to get to the machine when SSH connections are refused. You should at least be able to determine if any IP datagrams are reaching the router in the house. You can compare output from traceroute when you can connect to SSH vs. when you can't. That can help you rule out problems with the ISP or router.

---

### Post by userid on 2008-02-25
Thx again, will conduct the traceroute experiment.

```
Feb 25 21:35:48 server kernel: [16508.733356] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:36:48 server kernel: [16568.757264] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:37:48 server kernel: [16628.719988] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:38:49 server kernel: [16689.501795] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:39:57 server kernel: [16757.224644] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:40:57 server kernel: [16817.214813] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:41:57 server kernel: [16877.725844] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:42:58 server kernel: [16937.875442] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:43:58 server kernel: [16997.994361] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:44:58 server kernel: [17058.620023] possible SYN flooding on port 4671. Sending cookies.
Feb 25 21:45:59 server kernel: [17118.643743] possible SYN flooding on port 4671. Sending cookies.
```

I've actually found these in syslog. They seem to originate from a DNS server. not sure what that means. amule is running on port 4671.

---

### Post by k_grdn on 2008-02-25
Hi,

If your connection was down ssh conn attempt would normally output:

ssh: connect to host XXXXXXXXX port 22: No route to host


If the ssh daemon is not running or your host is being blocked then you'll get the following:

ssh: connect to host XXXXXXXXX port 22: Connection refused

How do you normally resolve the problem?

Is there a way you can check if the ssh daemon is running when you get locked out?

Regards,

k_grdn

---

### Post by k_grdn on 2008-02-25
Hi,

Do you have a socket listening on port: 4671?

Syn flooding is lots of initial syn packets hitting that port, this is quite common on mail ports etc..as they sometimes recieve lots of traffic.

Regards,

k_grdn

---

### Post by userid on 2008-02-25
> If the ssh daemon is not running or your host is being blocked then you'll get the following:

ssh: connect to host XXXXXXXXX port 22: Connection refused

Varies, it may give output refused or timeout, sometimes it actually returns to normal after this. It appears to be always sending no-ip packets in this state nonetheless

> How do you normally resolve the problem?

I resolve the problem by asking my cohabitants to restart the computer manually. This used to be once in a while (appears to be getting worse, every few days?)

> Is there a way you can check if the ssh daemon is running when you get locked out?

Unfortunately the server goes into a totally unresponsive state (both vnc and ssh ports).

---

### Post by k_grdn on 2008-02-25
Hi,

Do you have any ssh dictionary attack software setup? denyhosts, failtoban etc..?

How do you start ssh, xinetd or ssh script?

Edit /etc/hosts.allow, add:

ssh: your ip address or network

i.e

ssh: 192.168.

Regards,

k_grdn

---

### Post by k_grdn on 2008-02-25
Hi,

hmmm, 

As a short term fix why not set a cron job to restart networking services, or knock up a script to ping your private address if no responce then restart networking.

Regards,

k_grdn

---

### Post by userid on 2008-02-25
Thanks for your time

sshd starts with ubuntu as apt sets it up, no idea..

I access this server over the internet (various locations), so cannot implement allowhosts. I may implement fail2ban or so. 

Theres often a dictionary attack running + "syn flooding" as above, but as far as I can tell, system has not been compromised.

Maybe the brute force attacks cause the network interface to lock up eventually (as is usually fine for a certain period of time?)

> As a short term fix why not set a cron job to restart networking services, or knock up a script to ping your private address if no responce then restart networking.

This is the cleverest thing I've read in while regarding this annoying issue ;-) will google for this sort of solution..

Best regards

---

### Post by JonathanRRogers on 2008-02-25
That looks like a possible attack. A [SYN flood]("http://en.wikipedia.org/wiki/SYN_flood") is when the attacker sends many packets starting TCP connections, but doesn't ever complete the setup for any of them. Linux has a feature called SYN cookies that can mitigate to impact of a SYN flood attack, but not eliminate the threat completely. If the log times about SYN flooding correspond to the periods when you can't connect, that's probably the culprit.

I installed mldonkey a number of years ago and was soon hit by a huge amount of traffic. I wasn't sure whether it was an attack or misconfigured nodes or what, but I turned it off and have never tried it since.

---

### Post by JonathanRRogers on 2008-02-25
If you're seeing dictionary attacks against sshd, I'd even more strongly recommend turning off password authentication and always use public key authentication. However, that's probably not directly related to the connections being refused.

---

### Post by k_grdn on 2008-02-25
Hi,

echo 1 > /proc/sys/net/ipv4/tcp_syncookies

What is your networking setup is there a reason for using network manager?

I suggest you kill it, and create static configs via:
/etc/network/interfaces

To resolve any problems and to prevent getting locked out reset back to original config with cron until you achieve your desired setup.

If you still get locked out we can then elimate network manager and focus attention elsewhere.

Regards,

k_grdn

---

### Post by userid on 2008-02-25
cat /proc/sys/net/ipv4/tcp_syncookies
1

think it is sending syncookies already... it may just be panicking about the amule traffic though as per JonathanR I suppose

The networkmanager icon is flickering sometimes, not sure if that means anything. Bit scared removing it, won't killing networkmanager lock me out for good?

---

### Post by k_grdn on 2008-02-25
Hi,

Basic, not tested!

#!/bin/bash

PING=`/bin/ping -c1`

$PING XXXXXXXX

if [[ $? -ne 0 ]]; then
        /etc/init.d/networking restart
        exit $?
fi

exit0

Regards,

k_grdn

---

### Post by k_grdn on 2008-02-25
Hi,

Not kill figure of speech!

I mean statically configure your network settings then stop/overide network manger, as a failsafe use cron to re-apply your original setup to stop you getting locked out.

What are you network requirements?

> Never used network manager, allways used the shell

Regards,

k_grdn

---

### Post by userid on 2008-02-25
Thanks very much for the script, where would I put it?

It may be better just to enforce a periodic networking restart, as the server (probably the router actually) is on a variable IP BUT does still respond to ping on its no-ip domain name after lockup..

> Never used network manager, allways used the shell

I'm a newschool ubuntu noob!

> What are you network requirements?

eth0 only! requirements? erm.. to have it working continuously

---

### Post by k_grdn on 2008-02-25
Hi,

Place your script is /usr/local/bin/

crontab -e

*/5 * * * * /usr/local/bin/restart-net.sh > /dev/null 2>&1

Above cron entry will run the script every 5 mins, don't forget to chmod 755 script.

May be worth reviewing the script as it's just a quickie, it's allways worth adding some error checking/notifies etc.. like send an email when a restart occurs, so you can get the exact time of occurance and pin point the issue.

5 mins may be overkill.

Regards,

k_grdn

---

### Post by k_grdn on 2008-02-25
Hi,

As peace of mind the script works......as quick fix yes but think you need to route out the problem.

Regards,

k_grdn

---

### Post by userid on 2008-02-25
Thanks a lot for your time

Could I not just restart networking every 5 minutes without the ping checks? The address still pings when the server is locked, as its updating no-ip and I think the router is responding to the pings

---

### Post by k_grdn on 2008-02-25
Hi,

Yes you could but every 5 mins is overkill, and you increase the risk of lockouts if there's a problem restarting.

Does the interface actually loose it's address?

You could grep the output of ifconfig if no address or no match then restart.

Up to you! but the best solution is to resolve the problem.

Regards,

k_grdn

---

### Post by userid on 2008-02-25
> Up to you! but the best solution is to resolve the problem.

I'd love to ;-)

I would probably set it to restart only once or twice a day, that way I wouldnt have to bother people at the server location so often (could just wait to server to come back up). Provided that the networking restart actually gets computer out of catatonic state!

---

### Post by k_grdn on 2008-02-25
Hi,

I think a means to a solution would be to use /etc/network/interfaces to configure networking.

Good Luck.

Regards,

k_grdn

---

