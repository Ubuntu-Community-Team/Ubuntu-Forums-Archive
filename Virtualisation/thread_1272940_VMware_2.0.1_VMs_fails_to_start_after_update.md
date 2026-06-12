---
title: "VMware 2.0.1 VMs fails to start after update"
date: 2009-09-22
forum: Virtualisation
---

### Post by CalleJ on 2009-09-22
Edit: Downgrading the kernel from 2.6.24-24.60 to 2.6.24-24.59 did the trick.

Hi everyone! :)

My VMware Server 2.0.1 running upon a 8.04 Server;
> root@visionserver:/usr/lib/vmware# uname -a
Linux visionserver 2.6.24-24-server #1 SMP Sat Aug 22 00:59:57 UTC 2009 x86_64 GNU/Linux

Was fully functioning and working until i updated the kernel (as seen above), after the update I ran the usual; > sudo apt-get install build-essential linux-headers-`uname -r` xinetd

I also upgraded the existing RAM from 1GB to 8, but that shouldn't make any changes? :confused:

and re-configured VMware, which in turn gave me all green lights and a "go". However, running a quick top showed that none of the VMware-processes were infact running... Trying to access the webconsole and/or the machines is not working.

Netstat -l shows me that it however is listening for connections;
> root@visionserver:/usr/lib/vmware# netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State 
tcp 0 0 *:902 : LISTEN 
tcp 0 0 *:8333 : LISTEN 
tcp 0 0 localhost:8307 : LISTEN 
tcp 0 0 *:8222 : LISTEN 
tcp6 0 0 localhost:8005 :::* LISTEN 
tcp6 0 0 :::8009 :::* LISTEN 
tcp6 0 0 :::8308 :::* LISTEN 
tcp6 0 0 :::ssh :::* LISTEN 
udp 0 0 *:bootpc : 
udp 0 0 192.168.17.1:ntp : 
udp 0 0 172.16.130.1:ntp : 
udp 0 0 visionserver.vision:ntp : 
udp 0 0 localhost:ntp : 
udp 0 0 *:ntp : 
udp6 0 0 fe80::250:56ff:fec0:ntp :::* 
udp6 0 0 fe80::250:56ff:fec0:ntp :::* 
udp6 0 0 fe80::214:5eff:fef8:ntp :::* 
udp6 0 0 ip6-localhost:ntp :::* 
udp6 0 0 :::ntp :::* 
raw 0 0 *:icmp : 7 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags Type State I-Node Path
unix 2 ACC STREAM LISTENING 17007 /var/run/vmware/root_0/1253661581394001_8906/ha-nfc-fd
unix 2 ACC STREAM LISTENING 17014 /var/run/vmware/root_0/1253661581394001_8906/ha-nfcssl-fd
unix 2 ACC STREAM LISTENING 17016 /var/run/vmware/proxy-webserver
unix 2 ACC STREAM LISTENING 17065 /var/run/vmware/root_0/1253661581394001_8906/hostd-vmdb-fd
unix 2 ACC STREAM LISTENING 17067 /var/run/vmware/proxy-mob
unix 2 ACC STREAM LISTENING 17901 /var/run/vmnat.9485

and;

> root@visionserver:/usr/lib/vmware# /etc/init.d/vmware-core start
Starting VMware services:
Virtual machine monitor done
Virtual machine communication interface done
VM communication interface socket family: done
Virtual ethernet done
Bridged networking on /dev/vmnet0 done
Host-only networking on /dev/vmnet1 (background) done
DHCP server on /dev/vmnet1 done
Host-only networking on /dev/vmnet8 (background) done
DHCP server on /dev/vmnet8 done
NAT service on /dev/vmnet8 done
VMware Server Authentication Daemon (background) done
Shared Memory Available done

yet;
> root@visionserver:/usr/lib/vmware# /etc/init.d/vmware-core status
Bridged networking on /dev/vmnet0 is running
Host network detection is not running
Host-only networking on /dev/vmnet1 is running
DHCP server on /dev/vmnet1 is running
Host-only networking on /dev/vmnet8 is running
DHCP server on /dev/vmnet8 is running
NAT networking on /dev/vmnet8 is running
Module vmmon loaded
Module vmnet loaded

...and no machines starting.

Please help me in these dark hours,

//Thanks in advance!

---

### Post by dcstar on 2009-09-25
> **CalleJ said:**
> Edit: Downgrading the kernel from 2.6.24-24.60 to 2.6.24-24.59 did the trick.
.........

Then please mark the thread appropriately.

---

