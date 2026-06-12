---
title: "Samba write speed fluctuation"
date: 2016-08-16
forum: Server Platforms
---

### Post by speed... on 2016-08-16
Hi all,

I have some problems with my samba write speed.
First of all some informations:
- Ubuntu 16.04.1 LTS
- ProLiant MicroServer Gen8 (819185-421)
- Intel(R) Celeron(R) CPU G1610T @ 2.30GHz
- 4GB RAM
- 4 disks (1x 300GB, 3x 2TB Western Digital Red)

When I copy something to the server via samba from a Win10 Pc the speed is fluctuating from 110 MB/s to 5-6 MB/s. In the example I copied 18 Files with ca 3 GB.
[ATTACH=CONFIG]270711[/ATTACH]

When I copy something from the server to the Win10 Pc the speed is constant on 110 MB/s.

Here my smb.conf
```
root@srv01:~# cat /etc/samba/smb.conf | egrep -v "(^#.*|^$)"
[global]
   workgroup = WORKGROUP
   netbios name = srv01
        server string = %h server (Samba, Ubuntu)
;   wins server = w.x.y.z
   dns proxy = no
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
;   logon path = \\%N\profiles\%U
;   logon drive = H:
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g
;   include = /home/samba/etc/smb.conf.%m
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   usershare max shares = 100
   usershare allow guests = yes
;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin
[data]
    comment = data
    path = /data/data
    browsable = yes
    write list = user1
    read list = user2
    read only = no
    create mask = 0777

```

Somebody has an idea what could be the cause?

Thank you and when you need additional info let me know :)

Best
Speed

---

### Post by Graham_Willis on 2016-08-17
Are these computers in the same LAN?
Have you tried copying something from the Win10 PC to the machine with Samba Server with another service? Can the same behaviour be observed?
Have you tried to conduct this test using another client machine? In particular, when you're copying from the machine with Samba Server itself, does the problem that you described occur (you can do this using **smbclient**). 
And when you're copying from Win10 PC to the file server, is **iotop **saying something interesting?

It's possible that the problem isn't related to Samba at all, but is an effect of your firewall settings (bandwidth limits), perhaps on your server and perhaps on some intermediary network device. Well, so as a very rudimentary test you can try pinging your file server. Perhaps it'll reveal something.

---

### Post by speed... on 2016-08-17
Thank you for your fast response.

> **Graham_Willis said:**
> Are these computers in the same LAN?
Yes, they are in the same LAN

> **Graham_Willis said:**
> And when you're copying from Win10 PC to the file server, is **iotop **saying something interesting?
Playing around with iotop I saw that kworker and jbd2 use 100% of I/O eveytime when the transfer rate is going down. Thank you for the hint!
[[IMG]https://s4.postimg.org/94l3ukdeh/Disk2.jpg[/IMG]]("https://postimg.org/image/94l3ukdeh/")

Should I change from sync to async in the fstab? (I saw that this could be the solution somewhere)

I will also do the other tests during the day (hopefully...)

Thank you!

---

### Post by speed... on 2016-08-17
> **Graham_Willis said:**
> Have you tried copying something from the Win10 PC to the machine with Samba Server with another service? Can the same behaviour be observed?
Have you tried to conduct this test using another client machine? In particular, when you're copying from the machine with Samba Server itself, does the problem that you described occur (you can do this using **smbclient**).

I tried to copy files from one disk to the other disk on the server via rsync and it seems that the same thing happens. When I try to copy files from another client to the server its still fluctuating.

> **Graham_Willis said:**
> It's possible that the problem isn't related to Samba at all, but is an effect of your firewall settings (bandwidth limits), perhaps on your server and perhaps on some intermediary network device. Well, so as a very rudimentary test you can try pinging your file server. Perhaps it'll reveal something.

Firewall on the server machine is off and there is no particular intermediary network device (both connected to a Fritbox Router).

I think it depends on the kworker and jbd2 using 100% of IO on the disk but I don't know how to solve the problem... Somebody has an idea?

Thank you in advanced :)

---

### Post by Graham_Willis on 2016-08-18
OK, now the situation's much clearer.

Do you have a dedicated disk for files which are made available with Samba Server or is it the same disk on which you hold your OS? If you have the former configuration, do you observe slow write speed when you're writing to the OS disk? If the latter, can you organise a completely new, fresh disk and check if the phenomena will hapen? Did the slow speed of write operations show up from the very beginning or at a certain point of time after you got the machine? Can you verify if the disk itself isn't damaged (SMART or something)? It might be worth to run filesystem check - but **remember that if you allow it to make repairs the filesystem must be unmounted **(otherwise you'll most likely destroy the data). How many files do you have in the directory which is Samba share?

Aha... and the very basic test - turn off the file server machine for a moment and write something to the disk then. What was the result?

---

### Post by speed... on 2016-08-19
I have a dedicated disk for the files. 
When I copy files via Samba to the "OS disk" the same occur. 
Its a fresh installation on a new server and 2 of the 4 disks are new. This occurs since I have installed the OS and on all disks. I use the same configuration like on the old server that died because of a lightning strike.

I tried to mount the disk with the "commit=600" option and than it works much better. No fluctuations but during the copy process after 30-40% the speed goes down from 100 MB/s to 50 MB/s (2,5 GB, 14 Files). Checking with iotop the kworker process is again using the disk with 99%.
Maybe you have a idea how to solve also this?

Thank you for your patience.
Alex

---

### Post by Graham_Willis on 2016-08-21
[quote="speed..."]Maybe you have a idea how to solve also this?[/quote]

I don't have (but if it's necessary we can work on it), at least nothing that I'd be able to give out of hand, but if you were able to improve performance modifying disk mount parameters, it should be feasible. But the question is this: you're saying that the problems also occurs when you're copying files **via Samba **to the OS disk, but is this the case when you're copying them normally - let's say by rsync, as it happened for the other disk? It'll make a very important difference. If the speed of transfer's slow regardless which method's used, then you really don't have a problem with Samba but with disks and perhaps bad mount options or something - in such a situation I'd recommend starting a new thread with a subject appropriately reflecting the problem you're experiencing.

---

### Post by cariboo on 2016-08-22
Have you tried iperf, it's available in the repositories, to check connection speeds between computers on your network? To test on the server install iperf, and issue the following command:

```
iperf -s
```

Then on your desktop system install iperf and run the following command:

```
iperf -c <server ip address>
```

the result should look something like this:

```
 iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------ 
[  3] local 192.168.0.106 port 47680 connected with 192.168.0.205 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  13.9 MBytes  11.6 Mbits/sec
```

My local network is running at 100Mbps so 11.6Mbits/sec is the fastest I ever see, your results may vary.

There is a version of iperf for Windows available [here]("https://iperf.fr/iperf-download.php"), I haven't tried it, as I very rarely use Windows.

---

### Post by speed... on 2016-08-22
[HR][/HR]The Iperf values are good:
```
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  113 MBytes  944 Mbits/sec
```

Later, when I'm back at home, I will try to copy something via SCP on the OS drive and on the data drive. So we see if it depends on Samba or maybe the disks. i will let you know.

---

### Post by speed... on 2016-08-23
The same thing happens when I copy something via rsync.
Copy from "Disk1" to "Disk2" via rsync -> fluctuating from 5 to 100 MB/s
Copy from "Disk1" to "OS Disk" via rsync -> fluctuating from 5 to 100 MB/s
Copy from "OS Disk" to "Disk 1" via rsync -> fluctuating from 5 to 100 MB/s

So its not depending from Samba... Should I open a new thread?

---

### Post by Graham_Willis on 2016-08-25
Yes. You have a completely different issue and I think that quite a lot of people ignore a thread if its subject doesn't indicate that it's within their field of interest/knowledge. Opening the new thread please include as much information as it's possible - what disks (vendor, model etc.) you have, what mount options are, if the same happen if you're performing copying using another OS and so on.

---

### Post by speed... on 2016-08-26
Ok, thank you for your patience. I will create a [new Thread]("https://ubuntuforums.org/showthread.php?t=2335245").

---

