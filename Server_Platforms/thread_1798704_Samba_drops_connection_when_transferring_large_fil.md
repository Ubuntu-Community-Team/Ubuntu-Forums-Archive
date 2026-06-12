---
title: "Samba drops connection when transferring large file"
date: 2011-07-06
forum: Server Platforms
---

### Post by ordou on 2011-07-06
I'm experiencing connection problem when transferring a large file from Windows 7 (Home Premium) to my Ubuntu 11.04. 

The transfer starts, but after a couple of seconds the connection drops and all the shares are unavailable. I'm also unable to connect to the server over ssh, and the only thing I can do to restore the connection is to reboot the server.

The strange part is that this was never a problem a couple of weeks ago, and I've not done anything to the setup on either machines besides installing security updates.

---

### Post by capscrew on 2011-07-06
> **ordou said:**
> I'm experiencing connection problem when transferring a large file from Windows 7 (Home Premium) to my Ubuntu 11.04. 

The transfer starts, but after a couple of seconds the connection drops and all the shares are unavailable. I'm also unable to connect to the server over ssh, and the only thing I can do to restore the connection is to reboot the server.

The strange part is that this was never a problem a couple of weeks ago, and I've not done anything to the setup on either machines besides installing security updates.

What do you see in the logs?  Samba logs are at ```
/var/log/samba
```Use the **tail **command to view the last few entries.

---

### Post by ordou on 2011-07-13
Thanks for replying. It just happened again, just before I had to restart the server at 2011/07/13 12:44. 

I'm not capable of analyzing the logs, but here they are:

**log.nmbd**
```
[2011/07/04 22:52:40,  0] nmbd/nmbd.c:857(main)
  nmbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/07/04 22:53:03.930772,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server MORDOR is now a local master browser for workgroup MIDGARD on subnet 192.168.1.3
  
  *****
[2011/07/05 07:54:07.847197,  0] nmbd/nmbd.c:132(nmbd_sig_hup_handler)
  Got SIGHUP dumping debug info.
[2011/07/05 07:54:07.847246,  0] nmbd/nmbd_workgroupdb.c:281(dump_workgroups)
  dump_workgroups()
   dump workgroup on subnet     192.168.1.3: netmask=  255.255.255.0:
  	WORKGROUP(2) current master browser = PCH-A200
  	MIDGARD(1) current master browser = MORDOR
  		MORDOR 40849a03 (mordor server (Samba, Ubuntu))
[2011/07/13 12:44:18,  0] nmbd/nmbd.c:857(main)
  nmbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010

```

**log.smbd**
```
[2011/07/10 00:06:39.373047,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/07/10 00:06:59.393064,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/07/10 07:37:33.649697,  1] smbd/process.c:776(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2011/07/10 07:37:33.781825,  0] smbd/server.c:281(remove_child_pid)
  Could not find child 25153 -- ignoring
[2011/07/10 07:37:33.781917,  0] smbd/server.c:281(remove_child_pid)
  Could not find child 25154 -- ignoring
[2011/07/10 21:13:13.072643,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/07/10 21:13:33.090679,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/07/11 12:26:03.092700,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/07/11 12:26:23.112710,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/07/11 15:55:57.394579,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/07/11 15:56:17.414571,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/07/11 23:31:09.822609,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/07/11 23:31:29.842615,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/07/12 12:00:33.272646,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/07/12 12:00:53.290682,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/07/13 12:44:18,  0] smbd/server.c:1123(main)
  smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/07/13 12:44:18.679677,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/07/13 12:44:18.682007,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/07/13 12:44:18.935583,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option

```

**log.shining (client)**
```
[2011/07/11 06:00:30.531155,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service innkommende initially as user nobody (uid=65534, gid=65534) (pid 27780)
[2011/07/11 06:00:30.535015,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service bilder initially as user nobody (uid=65534, gid=65534) (pid 27780)
[2011/07/11 06:00:30.539749,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service musikk initially as user nobody (uid=65534, gid=65534) (pid 27780)
[2011/07/11 06:00:30.544467,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 27780)
[2011/07/11 12:26:03.080691,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/07/11 12:26:03.080780,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
[2011/07/11 12:26:03.080859,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service video
[2011/07/11 12:26:03.080980,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service musikk
[2011/07/11 12:26:03.090720,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service bilder
[2011/07/11 12:26:03.090811,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service innkommende
[2011/07/11 13:55:28.681538,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service bilder initially as user nobody (uid=65534, gid=65534) (pid 28856)
[2011/07/11 13:55:28.683187,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 28856)
[2011/07/11 13:55:28.685180,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service musikk initially as user nobody (uid=65534, gid=65534) (pid 28856)
[2011/07/11 13:55:28.687307,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service innkommende initially as user nobody (uid=65534, gid=65534) (pid 28856)
[2011/07/11 15:55:57.270684,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/07/11 15:55:57.284376,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
[2011/07/11 15:55:57.284577,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service innkommende
[2011/07/11 15:55:57.290760,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service musikk
[2011/07/11 15:55:57.330713,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service video
[2011/07/11 15:55:57.330798,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service bilder
[2011/07/11 23:00:40.770092,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service musikk initially as user nobody (uid=65534, gid=65534) (pid 30490)
[2011/07/11 23:02:19.975056,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service innkommende initially as user nobody (uid=65534, gid=65534) (pid 30490)
[2011/07/11 23:02:19.980076,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service bilder initially as user nobody (uid=65534, gid=65534) (pid 30490)
[2011/07/11 23:02:19.987839,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 30490)
[2011/07/11 23:31:09.720697,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/07/11 23:31:09.720796,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
[2011/07/11 23:31:09.720875,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service video
[2011/07/11 23:31:09.721002,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service bilder
[2011/07/11 23:31:09.721078,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service innkommende
[2011/07/11 23:31:09.721187,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service musikk
[2011/07/12 08:55:03.245909,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service musikk initially as user nobody (uid=65534, gid=65534) (pid 31745)
[2011/07/12 08:56:37.545832,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service bilder initially as user nobody (uid=65534, gid=65534) (pid 31745)
[2011/07/12 08:56:49.131763,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service innkommende initially as user nobody (uid=65534, gid=65534) (pid 31745)
[2011/07/12 08:56:49.136768,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 31745)
[2011/07/12 12:00:32.890695,  0] lib/util_sock.c:474(read_fd_with_timeout)
[2011/07/12 12:00:32.981116,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
[2011/07/12 12:00:32.981198,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service video
[2011/07/12 12:00:33.050694,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service innkommende
[2011/07/12 12:00:33.050795,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service bilder
[2011/07/12 12:00:33.068136,  1] smbd/service.c:1251(close_cnum)
  shining (192.168.1.10) closed connection to service musikk
[2011/07/13 10:46:00.593092,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service musikk initially as user nobody (uid=65534, gid=65534) (pid 2874)
[2011/07/13 10:56:14.623068,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service innkommende initially as user nobody (uid=65534, gid=65534) (pid 2874)
[2011/07/13 10:56:14.629452,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service bilder initially as user nobody (uid=65534, gid=65534) (pid 2874)
[2011/07/13 10:56:14.638219,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 2874)
[2011/07/13 12:45:10.445733,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service innkommende initially as user nobody (uid=65534, gid=65534) (pid 2178)
[2011/07/13 12:45:10.488733,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service bilder initially as user nobody (uid=65534, gid=65534) (pid 2178)
[2011/07/13 12:45:10.494287,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service musikk initially as user nobody (uid=65534, gid=65534) (pid 2178)
[2011/07/13 12:45:10.590856,  1] smbd/service.c:1070(make_connection_snum)
  shining (192.168.1.10) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 2178)

```

---

### Post by capscrew on 2011-07-13
The logs do have interesting information but no conclusive data. See my comments below:
**log.nmbd** # This is the name service for Samba```
**[COLOR="Red"][2011/07/05 07:54:07[/COLOR]**.847197,  0] nmbd/nmbd.c:132(nmbd_sig_hup_handler)
  Got SIGHUP dumping debug info.

[I]# This is not normal.  The [COLOR="Red"]**SIGHUP is a hangup not a # normal terminate[/COLOR]**.  
# No debug info telling us why this happened. Note the time of this event (in red)[/I]
```


**log.smbd** # The Samba server ```

**[COLOR="Red"][2011/07/10 07:37:33[/COLOR]**.649697,  1] smbd/process.c:776(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2011/07/10 07:37:33.781825,  0] smbd/server.c:281(remove_child_pid)
  Could not find child 25153 -- ignoring
[2011/07/10 07:37:33.781917,  0] smbd/server.c:281(remove_child_pid)
  Could not find child 25154 -- ignoring

[I]# Why did the SIGUP happen?  When this service is shut down normally there is no SIGHUP. 
# The time of this event (in red) is not the same time as the nmbd log (???).
# Still, we have random SIGHUP's.[/I]
```

**log.shining (client)**

```
[2011/07/11 12:26:03.080780,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.

[I]# Again, the time is not the same. 
# This appears to be a network problem and _could_ cause SIGHUP's.  
# The share is not connected due to a routing error. 
[/I]

```
Can you also post the log for the server?

You seem to have random SIGHUP (disconnects) and routing errors.  Unfortunately, there is no one specific thing that is showing up that can show what the is problem yet.

---

### Post by ordou on 2011-07-13
Which log do you mean?

---

### Post by capscrew on 2011-07-13
> **ordou said:**
> Which log do you mean?
log.<server_name>

---

### Post by ordou on 2011-07-13
The log is empty.

```
kjetil@mordor:512:13:/var/log/samba$ cat log.mordor
Wed Jul 13@19:04:55
kjetil@mordor:513:14:/var/log/samba$ ls -al log.mordor
-rw-r--r-- 1 root root 0 2011-07-05 19:58 log.mordor
Wed Jul 13@19:05:42
kjetil@mordor:514:15:/var/log/samba$

```

---

### Post by capscrew on 2011-07-13
At this point I still feel this is a networking problem not a Samba problem.  Are you using a wireless card on either the client or the server?  Are either of the hosts using DHCP.  More importantly is the Samba server using DHCP?

I have to leave for a few hours.  I will reply when I get back.

---

### Post by ordou on 2011-07-13
> **capscrew said:**
> At this point I still feel this is a networking problem not a Samba problem.  Are you using a wireless card on either the client or the server?  Are either of the hosts using DHCP.  More importantly is the Samba server using DHCP?

I have to leave for a few hours.  I will reply when I get back.

Not using wireless at all.

I'm not sure how to be sure that Samba server is not using DHCP, but the /etc/network/interfaces shows:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        pre-up iptables-restore < /etc/iptables.up.rules
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 195.159.0.100

```

The host (Win7 client) is also on a static ip.

---

### Post by capscrew on 2011-07-13
> **ordou said:**
> Not using wireless at all.

I'm not sure how to be sure that Samba server is not using DHCP, but the /etc/network/interfaces shows:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        pre-up iptables-restore < /etc/iptables.up.rules
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 195.159.0.100

```

The host (Win7 client) is also on a static ip.

It appears that the system uses a statically configured IP address.  Is this a desktop environment (DE) or is it Ubuntu server?  Did you set the system up?  

I notice that the system has a firewall using IPtables directly.  Also the line dns-nameservers 195.159.0.100 is indicative of a DHCP setup at one time.

I think there is a real possibility that the networking is misconfigured.  It could be the firewall with the way TCP/IP is being handled.  

Can you try a transfer with the IPtables firewall disabled?

Can you ping between the all the hosts?  Can you do it by hostname?

---

### Post by ordou on 2011-07-13
> **capscrew said:**
> It appears that the system uses a statically configured IP address.  Is this a desktop environment (DE) or is it Ubuntu server?  Did you set the system up?  

I notice that the system has a firewall using IPtables directly.  Also the line dns-nameservers 195.159.0.100 is indicative of a DHCP setup at one time.

I think there is a real possibility that the networking is misconfigured.  It could be the firewall with the way TCP/IP is being handled.  

Can you try a transfer with the IPtables firewall disabled?

Can you ping between the all the hosts?  Can you do it by hostname?

Thanks! I commented out some duplicated rules in the IPtables list that was probably inserted automatically by Deluge when I upgraded to Natty. Now transfer works!

The dns-nameservers 195.159.0.100 was put there by me because I had trouble connecting to Internet hosts by means of domain names when using the IP address of my home gateway. Now, however for some strange reason, I'm unable to connect to e.g. google.com. Pinging the IP address works though. Flushing IPtables rules rectifies this. 

Here's the IPtables filter list:
```
# Generated by iptables-save v1.3.3 on Thu Feb 15 16:40:09 2007
*filter

# HTTP
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 6543 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 6544 -j ACCEPT

# UPnP
-A INPUT -p udp -m udp --dport 1900 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 2869 -j ACCEPT

# NFS
-A INPUT -p tcp -m tcp --dport 111 -j ACCEPT
-A INPUT -p udp -m udp --dport 111 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 2049 -j ACCEPT
-A INPUT -p udp -m udp --dport 2049 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 32765:32769 -j ACCEPT
-A INPUT -p udp -m udp --dport 32765:32769 -j ACCEPT

# Samba
-A INPUT -p tcp -m multiport --dports 135,139,445 -j ACCEPT 
-A INPUT -p udp -m multiport --dports 135,137,138,139,445 -j ACCEPT 
-A INPUT -p udp --sport 137 -s 192.168.1.0/24 -j ACCEPT

# BitTorrent
-A INPUT -p tcp -m tcp --dport 8112 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 58846 -j ACCEPT
-A INPUT -p udp -m udp --dport 58846 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 49160:49300 -j ACCEPT
-A INPUT -p udp -m udp --dport 49160:49300 -j ACCEPT

# VNC
-A INPUT -p tcp -m tcp --dport 5900 -j ACCEPT
-A INPUT -p udp -m udp --dport 5900 -j ACCEPT

# Rsync
-A INPUT -p tcp -m tcp --dport 873 -j ACCEPT
-A INPUT -p udp -m udp --dport 873 -j ACCEPT

# Ping
-A INPUT -i lo -j ACCEPT 
-A INPUT -p icmp -j ACCEPT 

# The rest..
-A INPUT -j DROP 
-A OUTPUT -j ACCEPT 
COMMIT

```

I reckon there's a missing rule somewhere. Any suggestions? Thanks again for all your help.

---

### Post by capscrew on 2011-07-13
> **ordou said:**
> Thanks! I commented out some duplicated rules in the IPtables list that was probably inserted automatically by Deluge when I upgraded to Natty. Now transfer works!

The dns-nameservers 195.159.0.100 was put there by me because I had trouble connecting to Internet hosts by means of domain names when using the IP address of my home gateway. Now, however for some strange reason, I'm unable to connect to e.g. google.com. Pinging the IP address works though. Flushing IPtables rules rectifies this. 

Here's the IPtables filter list:
```
# Generated by iptables-save v1.3.3 on Thu Feb 15 16:40:09 2007
*filter

# HTTP
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 6543 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 6544 -j ACCEPT

# UPnP
-A INPUT -p udp -m udp --dport 1900 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 2869 -j ACCEPT

# NFS
-A INPUT -p tcp -m tcp --dport 111 -j ACCEPT
-A INPUT -p udp -m udp --dport 111 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 2049 -j ACCEPT
-A INPUT -p udp -m udp --dport 2049 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 32765:32769 -j ACCEPT
-A INPUT -p udp -m udp --dport 32765:32769 -j ACCEPT

# Samba
-A INPUT -p tcp -m multiport --dports 135,139,445 -j ACCEPT 
-A INPUT -p udp -m multiport --dports 135,137,138,139,445 -j ACCEPT 
-A INPUT -p udp --sport 137 -s 192.168.1.0/24 -j ACCEPT

# BitTorrent
-A INPUT -p tcp -m tcp --dport 8112 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 58846 -j ACCEPT
-A INPUT -p udp -m udp --dport 58846 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 49160:49300 -j ACCEPT
-A INPUT -p udp -m udp --dport 49160:49300 -j ACCEPT

# VNC
-A INPUT -p tcp -m tcp --dport 5900 -j ACCEPT
-A INPUT -p udp -m udp --dport 5900 -j ACCEPT

# Rsync
-A INPUT -p tcp -m tcp --dport 873 -j ACCEPT
-A INPUT -p udp -m udp --dport 873 -j ACCEPT

# Ping
-A INPUT -i lo -j ACCEPT 
-A INPUT -p icmp -j ACCEPT 

# The rest..
-A INPUT -j DROP 
-A OUTPUT -j ACCEPT 
COMMIT

```

I reckon there's a missing rule somewhere. Any suggestions? Thanks again for all your help.

First off the dns-nameservers entry is wrong.  The only way that works is with an automated application.  If you just want to name a couple of Internet DNS servers you use the /etc/resolv.conf file.  For more info use```
man resolv.conf
```

I don't use IPtables so I can't advise you on that.  I would start another thread with this IPtables problem in the title.

---

### Post by Kezspez on 2011-08-09
I too am experiencing drop outs with files of anything over about 18mb.  I however have wireless connections from both the client and server, but both are able to download files larger than this individually, it seems only when uploading to the server that these drop outs occur..

Please, any help is welcome!

---

