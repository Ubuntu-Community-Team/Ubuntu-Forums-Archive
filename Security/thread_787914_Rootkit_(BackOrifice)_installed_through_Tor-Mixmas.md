---
title: "Rootkit (BackOrifice?) installed through Tor-Mixmaster-Privoxy"
date: 2008-05-09
forum: Security
---

### Post by persistentstubborn on 2008-05-09
I updgraded to Ubuntu 8.04 Hardy, started messing with tor, mixmaster and privoxy and ended with reportedly Back Orifice rootkit installed on my PC. I hope this is the right thread to post it.

**Some introductory info**:

I installed bastille, aide, tiger and chkrootkit, but I haven't configured aide properly yet. I also installed firestarter, but haven't writen rules in iptables.

I also managed not to read tor and privoxy manuals thoroughly, and haven't even read man pages of mixmaster. (Well, that should have been to my not to do list long ago, but still :D )

I also purged tor and mixmaster once, but reinstalled them.

I run ADSL, where two PCs are connected to an external Thomson modem, that came pre-installed with some lousy software and "don't touch anything" instructions from my ISP (requires admin login and password) and has no firewall capabilities. PCs are not inter-connected except through modem and the other PC is hopefully still intact.

**First simptoms**

I couldn't have used wget to fetch some files from internet - hosts denied connections to me, or terminated it shortly. I purged it, reinstalled and managed to do that by using sudo wget only. I initially thought it might have been caused by my mounting /tmp partition nodev,noexec,usrquote,grpquota according to Securing Debian Manual advice, or by my restriction of su login according to the same Manual (that I'm even not sure is appropriate for Ubuntu 8.04, but I wanted to make an experiment).

**Info**

(My comments within logs are added [color=blue]blue[/color]. I colored suspicious part of logs [color=red]red[/color]. I do apologize if the post is too colored, I tried to make it easier.)

Why do I say it's back orifice? Because firestarter detetcts it as such:
> Source	Destination	Port	Service	Program
ubuntu.lan	kunden2.hostimpact.de	31337	[color=red]Back orifice[/color]	tor
127.0.0.1	127.0.0.1	9050	Unknown
127.0.0.1	127.0.0.1	8118	Unknown

I took a screenshot of it intending to upload it, but it was copied bad on usb, and I already got the disk out of my PC - he was distrubing boot of 2 live CDs sessions.
 
There are also two zombie processes shown, 
1) bash->startx->xinit->ck-launch-session->[color=red]scim[/color]
2) deskbar-applet->[color=red]sh[/color]
Here is the link to a screenshot of it (this one was succesfull)
[http://img373.imageshack.us/img373/3899/screenshotsystemmonitorhs9.png](http://img373.imageshack.us/img373/3899/screenshotsystemmonitorhs9.png)
> persistentstubborn@persistentstubborn-desktop:/$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
[color=red]169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0[/color]
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 eth0

> persistentstubborn@persistentstubborn-desktop:/$ df -aT
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda5     ext3      695684    439592    220752  67% /
[color=red]proc          proc           0         0         0   -  /proc
/sys         sysfs           0         0         0   -  /sys
varrun       tmpfs     2395540    409356   1864496  19% /var/run
varlock      tmpfs     2395540    409356   1864496  19% /var/lock
udev         tmpfs      647744        80    647664   1% /dev
devshm       tmpfs      647744         0    647744   0% /dev/shm
devpts      devpts           0         0         0   -  /dev/pts
lrm          tmpfs      647744     38176    609568   6% /lib/modules/2.6.24-16-generic/volatile[/color]
/dev/sda6     ext3      139985     41273     91485  32% /boot
/dev/sda11    ext3     4814936    171608   4398740   4% /home
/dev/sda1  fuseblk    20273996   4511100  15762896  23% /media/sda1
/dev/sda8     ext3       85528      5723     75389   8% /tmp
/dev/sda9     ext3     9424268   2194364   6751172  25% /usr
/dev/sda10    ext3      956596     17612    890392   2% /usr/local/src
/dev/sda7     ext3     2395540    409356   1864496  19% /var
tmpfs        tmpfs      647744         0    647744   0% /dev/shm
securityfs
        [color=red]securityfs           0         0         0   -  /sys/kernel/security[/color]

The above in red are not actuall filesystems, than something hacked on my PC.
> persistentstubborn@persistentstubborn-desktop:/$ netstat -a | less
[color=blue]disconnected from network[/color]
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:8118          *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:9050          *:*                     LISTEN     
udp        0      0 *:48606                 *:*                                
udp        0      0 *:mdns                  *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
[color=blue]further omitted

And now connected to network[/color]

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:8118          *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:9050          *:*                     LISTEN     
[color=red]udp        0      0 *:bootpc                *:*[/color]                                
udp        0      0 *:48606                 *:*                                
udp        0      0 *:mdns                  *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
[color=blue]further omitted[/color]


Here is what I got from root (I'm posting the entire mail from root). Sda1 fuseblk is NTFS Windows XP partition, I guess securityfts is the same.

> /var/mail/persistentstubborn
From root@persistentstubborn-desktop Wed May 07 14:00:02 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Wed, 07 May 2008 14:00:02 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JtiJW-0003dW-89
	for root@persistentstubborn-desktop; Wed, 07 May 2008 14:00:02 +0200
From: "Tiger automatic auditor at persistentstubborn-desktop" <root@persistentstubborn-desktop>
To: root@persistentstubborn-desktop
Subject: Tiger Auditing Report for persistentstubborn-desktop
Message-Id: <E1JtiJW-0003dW-89@persistentstubborn-desktop>
Date: Wed, 07 May 2008 14:00:02 +0200


# Checking listening processes 
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 50746 (UDP on every interface) is run by avahi. 
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 5353 (UDP on every interface) is run by avahi. 
--WARN-- [lin003w] The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp. 

From root@persistentstubborn-desktop Wed May 07 16:00:12 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Wed, 07 May 2008 16:00:12 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JtkBd-0006FB-U1
	for root@persistentstubborn-desktop; Wed, 07 May 2008 16:00:12 +0200
From: root@persistentstubborn-desktop (Cron Daemon)
To: root@persistentstubborn-desktop
Subject: Cron <root@persistentstubborn-desktop>    test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; }
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <DEFAULT=/etc/default/tiger>
X-Cron-Env: <NICETIGER=10>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1JtkBd-0006FB-U1@persistentstubborn-desktop>
Date: Wed, 07 May 2008 16:00:12 +0200

--CONFIG-- [con010c] Filesystem 'fuseblk' used by '/dev/sda1' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem

From root@persistentstubborn-desktop Wed May 07 20:00:02 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Wed, 07 May 2008 20:00:02 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1Jtnvu-0005Ak-3a
	for root@persistentstubborn-desktop; Wed, 07 May 2008 20:00:02 +0200
From: "Tiger automatic auditor at persistentstubborn-desktop" <root@persistentstubborn-desktop>
To: root@persistentstubborn-desktop
Subject: Tiger Auditing Report for persistentstubborn-desktop
Message-Id: <E1Jtnvu-0005Ak-3a@persistentstubborn-desktop>
Date: Wed, 07 May 2008 20:00:02 +0200

# Checking listening processes
OLD: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 50746 (UDP on every interface) is run by avahi.
NEW: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 57022 (UDP on every interface) is run by avahi.

From root@persistentstubborn-desktop Thu May 08 00:00:17 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Thu, 08 May 2008 00:00:17 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JtrgO-0002Og-VO
	for root@persistentstubborn-desktop; Thu, 08 May 2008 00:00:16 +0200
From: "Tiger automatic auditor at persistentstubborn-desktop" <root@persistentstubborn-desktop>
To: root@persistentstubborn-desktop
Subject: Tiger Auditing Report for persistentstubborn-desktop
Message-Id: <E1JtrgO-0002Og-VO@persistentstubborn-desktop>
Date: Thu, 08 May 2008 00:00:16 +0200

# Checking for existence of log files...
# Checking listening processes
OLD: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 57022 (UDP on every interface) is run by avahi.
[color=red]OLD: --WARN-- [lin003w] The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp.[/color][color=blue]I guess that's when I installed tor&mixmaster&privoxy for the first time[/color]
NEW: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 54952 (UDP on every interface) is run by avahi.

From root@persistentstubborn-desktop Thu May 08 00:00:17 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Thu, 08 May 2008 00:00:17 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JtrgA-0001oP-C1
	for root@persistentstubborn-desktop; Thu, 08 May 2008 00:00:17 +0200
From: root@persistentstubborn-desktop (Cron Daemon)
To: root@persistentstubborn-desktop
Subject: Cron <root@persistentstubborn-desktop>    test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; }
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <DEFAULT=/etc/default/tiger>
X-Cron-Env: <NICETIGER=10>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1JtrgA-0001oP-C1@persistentstubborn-desktop>
Date: Thu, 08 May 2008 00:00:17 +0200

--CONFIG-- [con010c] Filesystem 'fuseblk' used by '/dev/sda1' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem

From root@persistentstubborn-desktop Thu May 08 07:41:52 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Thu, 08 May 2008 07:41:52 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1Jtyt6-0001YY-AC
	for root@persistentstubborn-desktop; Thu, 08 May 2008 07:41:52 +0200
To: root@persistentstubborn-desktop
Subject: premature termination - Daily AIDE report for persistentstubborn-desktop
Message-Id: <E1Jtyt6-0001YY-AC@persistentstubborn-desktop>
From: root <root@persistentstubborn-desktop>
Date: Thu, 08 May 2008 07:41:52 +0200

The cron job was terminated because lock /var/run/aide/cron.daily.lock could not be obtained.

From root@persistentstubborn-desktop Thu May 08 08:00:16 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Thu, 08 May 2008 08:00:16 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JtzAf-0001mS-R1
	for root@persistentstubborn-desktop; Thu, 08 May 2008 08:00:16 +0200
From: root@persistentstubborn-desktop (Cron Daemon)
To: root@persistentstubborn-desktop
Subject: Cron <root@persistentstubborn-desktop>    test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; }
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <DEFAULT=/etc/default/tiger>
X-Cron-Env: <NICETIGER=10>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1JtzAf-0001mS-R1@persistentstubborn-desktop>
Date: Thu, 08 May 2008 08:00:16 +0200

--CONFIG-- [con010c] Filesystem 'fuseblk' used by '/dev/sda1' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem

From root@persistentstubborn-desktop Thu May 08 08:12:56 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Thu, 08 May 2008 08:12:56 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JtzNA-0005Gf-5i
	for root@persistentstubborn-desktop; Thu, 08 May 2008 08:12:56 +0200
From: Anacron <root@persistentstubborn-desktop>
To: root@persistentstubborn-desktop
Subject: Anacron job 'cron.daily' on persistentstubborn-desktop
Message-Id: <E1JtzNA-0005Gf-5i@persistentstubborn-desktop>
Date: Thu, 08 May 2008 08:12:56 +0200

/etc/cron.daily/aide:
/etc/cron.daily/aide: line 65: /var/lib/aide/aide.conf.autogenerated: No such file or directory
/etc/cron.daily/aide: line 66: /var/lib/aide/aide.conf.autogenerated: No such file or directory
dotlockfile: /var/run/aide: no such directory
run-parts: /etc/cron.daily/aide exited with return code 1

From root@persistentstubborn-desktop Thu May 08 10:00:01 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Thu, 08 May 2008 10:00:01 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1Ju12n-0005ZQ-Gd
	for root@persistentstubborn-desktop; Thu, 08 May 2008 10:00:01 +0200
From: "Tiger automatic auditor at persistentstubborn-desktop" <root@persistentstubborn-desktop>
To: root@persistentstubborn-desktop
Subject: Tiger Auditing Report for persistentstubborn-desktop
Message-Id: <E1Ju12n-0005ZQ-Gd@persistentstubborn-desktop>
Date: Thu, 08 May 2008 10:00:01 +0200

# Checking listening processes
NEW: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 43216 (UDP on every interface) is run by avahi.
OLD: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 54952 (UDP on every interface) is run by avahi.
NEW: --WARN-- [lin003w] The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp.

From root@persistentstubborn-desktop Thu May 08 16:00:07 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Thu, 08 May 2008 16:00:07 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1Ju6fB-0007PO-S2
	for root@persistentstubborn-desktop; Thu, 08 May 2008 16:00:07 +0200
From: root@persistentstubborn-desktop (Cron Daemon)
To: root@persistentstubborn-desktop
Subject: Cron <root@persistentstubborn-desktop>    test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; }
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <DEFAULT=/etc/default/tiger>
X-Cron-Env: <NICETIGER=10>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1Ju6fB-0007PO-S2@persistentstubborn-desktop>
Date: Thu, 08 May 2008 16:00:07 +0200

--CONFIG-- [con010c] Filesystem 'fuseblk' used by '/dev/sda1' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem

From root@persistentstubborn-desktop Fri May 09 00:00:07 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Fri, 09 May 2008 00:00:07 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JuE9i-0001xI-7o
	for root@persistentstubborn-desktop; Fri, 09 May 2008 00:00:07 +0200
From: root@persistentstubborn-desktop (Cron Daemon)
To: root@persistentstubborn-desktop
Subject: Cron <root@persistentstubborn-desktop>    test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; }
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <DEFAULT=/etc/default/tiger>
X-Cron-Env: <NICETIGER=10>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1JuE9i-0001xI-7o@persistentstubborn-desktop>
Date: Fri, 09 May 2008 00:00:07 +0200

--CONFIG-- [con010c] Filesystem 'fuseblk' used by '/dev/sda1' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem
[color=red]--CONFIG-- [con010c] Filesystem 'fuse.gvfs-fuse-daemon' used by 'gvfs-fuse-daemon' is not recognised as a local filesystem[/color][color=blue]this fuse.gvfs-fuse-daemon appeared in filesistema - further info below[/color]

From root@persistentstubborn-desktop Fri May 09 07:28:08 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Fri, 09 May 2008 07:28:08 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JuL9M-0001UU-DO
	for root@persistentstubborn-desktop; Fri, 09 May 2008 07:28:08 +0200
To: root@persistentstubborn-desktop
Subject: premature termination - Daily AIDE report for persistentstubborn-desktop
Message-Id: <E1JuL9M-0001UU-DO@persistentstubborn-desktop>
From: root <root@persistentstubborn-desktop>
Date: Fri, 09 May 2008 07:28:08 +0200

The cron job was terminated because lock /var/run/aide/cron.daily.lock could not be obtained.

From root@persistentstubborn-desktop Fri May 09 07:46:07 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Fri, 09 May 2008 07:46:07 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JuLQl-00021G-1b
	for root@persistentstubborn-desktop; Fri, 09 May 2008 07:46:07 +0200
From: Anacron <root@persistentstubborn-desktop>
To: root@persistentstubborn-desktop
Subject: Anacron job 'cron.daily' on persistentstubborn-desktop
Message-Id: <E1JuLQl-00021G-1b@persistentstubborn-desktop>
Date: Fri, 09 May 2008 07:46:07 +0200

/etc/cron.daily/aide:
/etc/cron.daily/aide: line 65: /var/lib/aide/aide.conf.autogenerated: No such file or directory
/etc/cron.daily/aide: line 66: /var/lib/aide/aide.conf.autogenerated: No such file or directory
dotlockfile: /var/run/aide: no such directory
run-parts: /etc/cron.daily/aide exited with return code 1
[color=red]/etc/cron.daily/mixmaster:
/usr/bin/mixmaster-update: Get failed for [http://www.noreply.org/echolot/rlist2.txt](http://www.noreply.org/echolot/rlist2.txt) (500 Can't connect to [www.noreply.org:80](www.noreply.org:80) (Bad hostname 'www.noreply.org'))
Exiting eval via next at /usr/bin/mixmaster-update line 384.
/usr/bin/mixmaster-update: Get failed for [http://www.noreply.org/echolot/mlist2.txt](http://www.noreply.org/echolot/mlist2.txt) (500 Can't connect to [www.noreply.org:80](www.noreply.org:80) (Bad hostname 'www.noreply.org'))
Exiting eval via next at /usr/bin/mixmaster-update line 384.
/usr/bin/mixmaster-update: Get failed for [http://www.noreply.org/echolot/pubring.mix](http://www.noreply.org/echolot/pubring.mix) (500 Can't connect to [www.noreply.org:80](www.noreply.org:80) (Bad hostname 'www.noreply.org'))
Exiting eval via next at /usr/bin/mixmaster-update line 384.
/usr/bin/mixmaster-update: Get failed for [http://www.noreply.org/echolot/rlist.txt](http://www.noreply.org/echolot/rlist.txt) (500 Can't connect to [www.noreply.org:80](www.noreply.org:80) (Bad hostname 'www.noreply.org'))
Exiting eval via next at /usr/bin/mixmaster-update line 384.
/usr/bin/mixmaster-update: Get failed for [http://www.noreply.org/echolot/mlist.txt](http://www.noreply.org/echolot/mlist.txt) (500 Can't connect to [www.noreply.org:80](www.noreply.org:80) (Bad hostname 'www.noreply.org'))
Exiting eval via next at /usr/bin/mixmaster-update line 384.
/usr/bin/mixmaster-update: Get failed for [http://www.noreply.org/echolot/pgp-all.asc](http://www.noreply.org/echolot/pgp-all.asc) (500 Can't connect to [www.noreply.org:80](www.noreply.org:80) (Bad hostname 'www.noreply.org'))
Exiting eval via next at /usr/bin/mixmaster-update line 384.
Downloading of mlist and/or mixring failed (do you need a proxy?). Aborting.
run-parts: /etc/cron.daily/mixmaster exited with return code 22[/color][color=blue]Some error obviously. It isn't possible that was happening at the time when I purged mixmaster, is it?[/color]

From root@persistentstubborn-desktop Fri May 09 08:00:13 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Fri, 09 May 2008 08:00:13 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JuLeD-0002Ei-Qi
	for root@persistentstubborn-desktop; Fri, 09 May 2008 08:00:13 +0200
From: root@persistentstubborn-desktop (Cron Daemon)
To: root@persistentstubborn-desktop
Subject: Cron <root@persistentstubborn-desktop>    test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; }
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <DEFAULT=/etc/default/tiger>
X-Cron-Env: <NICETIGER=10>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1JuLeD-0002Ei-Qi@persistentstubborn-desktop>
Date: Fri, 09 May 2008 08:00:13 +0200

--CONFIG-- [con010c] Filesystem 'fuseblk' used by '/dev/sda1' is not recognised as a local filesystem
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem

From root@persistentstubborn-desktop Fri May 09 10:00:02 2008
Return-path: <root@persistentstubborn-desktop>
Envelope-to: root@persistentstubborn-desktop
Delivery-date: Fri, 09 May 2008 10:00:02 +0200
Received: from root by persistentstubborn-desktop with local (Exim 4.69)
	(envelope-from <root@persistentstubborn-desktop>)
	id 1JuNWM-0003hy-0d
	for root@persistentstubborn-desktop; Fri, 09 May 2008 10:00:02 +0200
From: "Tiger automatic auditor at persistentstubborn-desktop" <root@persistentstubborn-desktop>
To: root@persistentstubborn-desktop
Subject: Tiger Auditing Report for persistentstubborn-desktop
Message-Id: <E1JuNWM-0003hy-0d@persistentstubborn-desktop>
Date: Fri, 09 May 2008 10:00:02 +0200

# Checking listening processes
OLD: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 43216 (UDP on every interface) is run by avahi.
NEW: --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 48606 (UDP on every interface) is run by avahi.
OLD: --WARN-- [lin003w] The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp.

**Tor** configuration file, abbreviated.

> /etc/tor/torrc
SocksListenAddress 127.0.0.1 # accept connections only from localhost
...
#SocksPolicy accept 192.168.0.0/16
#SocksPolicy reject *
...
[color=blue]So I'm not runnin' tor server, am I? The only uncommented line was the SocksLIstenAddress 127.0.0.1 and I can't recall I uncommented it - though it might be the case.[/color]
...
#RunAsDaemon 1
...
So it's not configured to run as deamon, yet it started as service (I purged gdm, so I need to type startx and shutdown -h now, that's how I saw the message about it during shutdown yesterday)
**Privoxy**
> /var/log/privoxy/errofile
May 07 13:54:23.711 Privoxy(b7dab6b0) Info: Privoxy version 3.0.8
May 07 13:54:23.711 Privoxy(b7dab6b0) Info: Program name: /usr/sbin/privoxy
May 07 19:32:19.160 Privoxy(b7e166b0) Info: Privoxy version 3.0.8
May 07 19:32:19.169 Privoxy(b7e166b0) Info: Program name: /usr/sbin/privoxy
May 07 23:50:16.213 Privoxy(b7d846b0) Info: Privoxy version 3.0.8
May 07 23:50:16.221 Privoxy(b7d846b0) Info: Program name: /usr/sbin/privoxy
May 08 07:36:47.186 Privoxy(b7d956b0) Info: Privoxy version 3.0.8
May 08 07:36:47.195 Privoxy(b7d956b0) Info: Program name: /usr/sbin/privoxy
May 09 07:23:02.380 Privoxy(b7d5b6b0) Info: Privoxy version 3.0.8
May 09 07:23:02.388 Privoxy(b7d5b6b0) Info: Program name: /usr/sbin/privoxy

/var/log/privoxy/logfile
May 07 17:15:45.534 Privoxy(b7dab6b0) Info: (Re-)Opening logfile '/var/log/privoxy/logfile'
May 07 17:15:45.534 Privoxy(b7dab6b0) Info: Privoxy version 3.0.8
May 07 17:15:45.534 Privoxy(b7dab6b0) Info: Program name: /usr/sbin/privoxy
May 07 17:42:01.235 Privoxy(b5553b90) Info: Decompression didn't result in any content.
May 07 17:42:04.755 Privoxy(b5553b90) Info: Decompression didn't result in any content.
May 07 17:43:48.215 Privoxy(b6d56b90) Info: Decompression didn't result in any content.
May 07 17:45:14.459 Privoxy(b5553b90) Info: Decompression didn't result in any content.
May 07 17:46:00.247 Privoxy(b4551b90) Info: Decompression didn't result in any content.
May 07 17:53:24.094 Privoxy(b7dab6b0) Info: Reloading configuration file '/etc/privoxy/config'
[color=blue]It's strange it ceased loging on May 07, though I did edited /etc/privoxy/config several times I can't recall I commented this.[/color]
...

persistentstubborn@persistentstubborn-desktop:/etc/privoxy$ sudo grep -G ^ config
[blue=I omitted most of the commented results, but here is what I got![/color]

user-manual /usr/share/doc/privoxy/user-manual
confdir /etc/privoxy
logdir /var/log/privoxy
actionsfile standard.action  # Internal purpose, recommended
actionsfile global.action    # Global default setting for all sites
actionsfile default.action   # Main actions file
actionsfile user.action      # User customizations
filterfile default.filter
#filterfile user.filter      # User customizations [color=blue]I know it's uncommented[/color]
logfile logfile
#debug   1    # log each request destination (and the crunch reason if Privoxy intercepted the request)
#debug   4096 # Startup banner and warnings [color=blue]This one was uncommented at times[/color]
#debug   8192 # Non-fatal errors [color=blue]This one was uncommented at times, too[/color]
listen-address  127.0.0.1:8118
enable-remote-toggle  0
enable-remote-http-toggle  0
enable-edit-actions 0
enforce-blocks 0
buffer-limit 4096
[color=blue]Now interesting part: If I open console over the entire screen, the following lines look commented:[/color]
[color=red]#
#        forward-socks4a   /       socks-gw.example.com:1080    www-cache.isp.example.net:8080 
#        forward           .example.com        .
#
#
[/color]
[color=blue]But when I minimize the console, a part of it looks uncommented! (I'm not sure if that's just a visual effect or not)[/color]
[color=red]#
#        forward-socks4a   /       socks-gw.example.com:1080    www-cache.isp.e
xample.net:8080 
#        forward           .example.com        .
#[/color]
	forward-socks4a   /               127.0.0.1:9050 . [color=blue]I just uncommented that line, so this option does have some blank spaces before it[/color]
forwarded-connect-retries  0
accept-intercepted-requests 0
allow-cgi-request-crunching 0
split-large-forms 0
show-on-task-bar 1
close-button-minimizes 1

> persistentstubborn@persistentstubborn-desktop:/$ sudo chkrootkit

ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `crontab'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not infected
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not infected
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
[color=red]Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9b5/.autoreg
/usr/lib/firefox/.autoreg [/color][color=blue]this might be one of the two extensions I installed in mozilla to browse anonymously - RefControl 0.8.10[/color]
[color=red]/usr/lib/firefox-3.0b5/.autoreg[/color] [color=blue]this might be one of the two extensions I installed in mozilla to browse anonymously - FoxyProxy 2.7.2[/color]
[color=red]/lib/modules/2.6.24-16-generic/volatile/.mounted[/color]

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
[color=red]Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security[/color]
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for rootedoor... nothing found
Searching for ENYELKM rootkit default files... nothing found
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted
Tor log
> 
/var/log/tor/log

May 09 07:46:04.279 [notice] Tor 0.1.2.19 opening new log file.
May 09 07:55:41.065 [warn] Received http status code 404 ("Not found") from server '88.198.7.215:80' while fetching "/tor/status/fp/38D4F5FCF7B1023228B895EA56EDE7D5CCDCAF32.z". I'll try again soon.
May 09 08:38:35.583 [notice] We stalled too much while trying to write 1125 bytes to addr [scrubbed].  If this happens a lot, either something is wrong with your network connection, or something is wrong with theirs. (fd 11, type Directory, state 1, marked at main.c:641).
May 09 08:40:10.533 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up.
May 09 08:43:10.047 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 08:46:10.187 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 08:48:34.451 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:16:33.287 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:16:33.287 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:16:33.287 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:16:33.287 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:16:33.287 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:16:34.291 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:16:34.291 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
May 09 09:18:33.307 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)

/var/log/tor/log1

May 08 11:55:35.681 [notice] Tor 0.1.2.19 opening new log file.
May 08 11:55:36.466 [notice] I learned some more directory information, but not enough to build a circuit.
May 08 12:00:37.232 [notice] We stalled too much while trying to write 259 bytes to addr [scrubbed].  If this happens a lot, either something is wrong with your network connection, or something is wrong with theirs. (fd 4, type Directory, state 1, marked at main.c:641).
May 08 12:00:52.532 [notice] I learned some more directory information, but not enough to build a circuit.
May 08 12:01:01.125 [notice] I learned some more directory information, but not enough to build a circuit.
May 08 12:01:04.361 [notice] I learned some more directory information, but not enough to build a circuit.
May 08 12:01:08.220 [notice] I learned some more directory information, but not enough to build a circuit.
May 08 12:01:11.944 [notice] I learned some more directory information, but not enough to build a circuit.
May 08 12:01:14.365 [notice] We now have enough directory information to build circuits.
May 08 12:01:20.598 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
May 08 12:03:46.133 [warn] Received http status code 404 ("Not found") from server '213.73.91.31:80' while fetching "/tor/status/fp/38D4F5FCF7B1023228B895EA56EDE7D5CCDCAF32.z". I'll try again soon.
May 08 12:05:53.740 [notice] We stalled too much while trying to write 3993 bytes to addr [scrubbed].  If this happens a lot, either something is wrong with your network connection, or something is wrong with theirs. (fd 19, type Directory, state 1, marked at main.c:641).
May 08 12:21:09.164 [notice] We stalled too much while trying to write 224 bytes to addr [scrubbed].  If this happens a lot, either something is wrong with your network connection, or something is wrong with theirs. (fd 10, type Directory, state 1, marked at main.c:641).
May 09 00:09:38.287 [notice] Interrupt: exiting cleanly.
May 09 07:23:05.248 [notice] Tor 0.1.2.19 opening log file.
May 09 07:23:08.183 [notice] We now have enough directory information to build circuits.
May 09 07:23:18.811 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
May 09 07:30:11.935 [notice] We stalled too much while trying to write 99 bytes to addr [scrubbed].  If this happens a lot, either something is wrong with your network connection, or something is wrong with theirs. (fd 11, type Directory, state 1, marked at main.c:641).
May 09 07:31:25.412 [warn] Received http status code 404 ("Not found") from server '192.251.226.205:80' while fetching "/tor/status/fp/38D4F5FCF7B1023228B895EA56EDE7D5CCDCAF32.z". I'll try again soon.
May 09 07:46:04.278 [notice] Received reload signal (hup). Reloading config.

mixmaster
> 
persistentstubborn@persistentstubborn-desktop:/var/log$ ls -l
total 5684
...
[color=red]drwxrw**s---**[/color] 2 root        mixmaster    4096 2008-01-15 00:07 mixmaster
...
[color=red]persistentstubborn@persistentstubborn-desktop:/var/log$ sudo chgrp root mixmaster
persistentstubborn@persistentstubborn-desktop:/var/log$ cd mixmaster
bash: cd: mixmaster: Permission denied
persistentstubborn@persistentstubborn-desktop:/var/log$ sudo chmod 776 mixmaster
persistentstubborn@persistentstubborn-desktop:/var/log$ cd mixmaster
bash: cd: mixmaster: Permission denied
persistentstubborn@persistentstubborn-desktop:/var/log$ ls -l
drwxrwsrw- 2 root        root      4096 2008-01-15 00:07 [/color][color=green]mixmaster[/color]


[size=3]**Questions:**[/size]

1) It seems it's back orifice on Linux, througth mixmaster, isn't it?

2) Is there a way to get rid of it, save from reformating linux partitions and reinstalling?

2.1) Do I need to format again two NTFS partitions on the same disk (one fresh XP Window$ install, not booted after messing with tor, the second just formatted this morning by partition magic boot floppy)

2.2.) I'd appreciate info how to clear RAM memory, not to have rootkit stored there (a link would suffice)

3) What should I do with my ADSL modem (external, another computer uses it as well)? How could I determine if it's been rootkitted too? I don't know how to disinfect it. **I now realize that it might be the first victim, since I encountered decrease of speed during boot of live CD even prior to this installation of 8.04**.

3.1) I anyway planned to set an old P2 as a firewall only - I've prepared EnGarde SELinux for it - Could someone point to an info how to use hardware parts of ADSL modem (splitter between the telephone line and ADSL line and those hardware parts of the modem - input telephone line part and output cable)? Link would suffice. I actually don't know how to get a cable from ADSL spliter and connect it to eth0/eth1 card.

4) I think this info might be useful to send to a security list. Any suggestions? If someone knows how and where, please, please be my guest.

5) What actually happened? Where did I get it wrong?

I'd like to make benefit of this by learning what happened, to avoid it in future, regardless I don't actuall have a need for an onion router and will hardly use it in future.

---

### Post by /etc/init.d/ on 2008-05-09
There is nothing there that even remotely suggests you have been compromised by a Windows-only program.

Linux only has a Back Orifice client, and also it isn't a rootkit.

Tor can use randomly-generated port numbers.  It's likely that Tor just happened to be using the same port as B.O.

The file systems you highlighted are completely normal. 

At the end it looks like you have purposefully messed up your permissions and group membership on /var/log.

The only thing I'm seeing here is paranoia.

---

### Post by persistentstubborn on 2008-05-09
> **/etc/init.d/ said:**
> The only thing I'm seeing here is paranoia.

That would be fine, but if I may ask for several clarifications.

> **/etc/init.d/ said:**
> There is nothing there that even remotely suggests you have been compromised by a Windows-only program.

Linux only has a Back Orifice client, and also it isn't a rootkit.

I have no clue what it is. Firestarter reported is such, as Back Orifice. I could go once again and return HD into PC and make another screenshot if you don't believe me.

> **/etc/init.d/ said:**
> 
Tor can use randomly-generated port numbers.  It's likely that Tor just happened to be using the same port as B.O.

The file systems you highlighted are completely normal.

If you are sure that those filesystems mounted on my / partitions are just tor, it would be excellent. I can go back and purge it, I just wanted to wait and see if I should examine something else.

> **/etc/init.d/ said:**
> At the end it looks like you have purposefully messed up your permissions and group membership on /var/log.


I wasn't able to see the content of /var/log/mixmaster folder. Neither from GUI, nor from console. Then I started chmode, chown and chgrp, with no results.

BTW, I started with Linux in the first place since I was an unaware victim of B.O. under Window$.

Anyway, thanks.

---

### Post by damatta on 2008-05-09
I am not the expert but it does not seem you have been compromised. Those entries from rkhunter are fine. When you issue netstat -antu in the terminal whilst disconnected, its normal to see bootpc listening because you probably need DHCP service for when you reconnect. You can also install Wireshark and watch for suspicious traffic.

---

### Post by persistentstubborn on 2008-05-09
Tnx, I just did it again from live CD I'm running at the moment, see the results:

> ubuntu@ubuntu:~$ netstat -a | less
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 sysresccd.lan:60628     213.254.238.153:www     TIME_WAIT  
tcp        1      0 sysresccd.lan:53871     nrl.onion-router.ne:www CLOSE_WAIT 
tcp        1      0 sysresccd.lan:39755     84.53.182.147:www       CLOSE_WAIT 
udp        0      0 *:32768                 *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                
Active UNIX domain sockets (servers and established)

sysresccd was what I booted succesfully first after getting HD out. Now I'm on Ubuntu Live CD, but the network is still sysresccd.lan (that's modem) and there is still onioun-router registered, though tor was installed neither at SytemRescueDisk1.0.2. nor in Ubuntu 7.10 Live.

Btw, the quotation in my initial post regarding mixmaster was wrong. I did first try to log to /var/log/mixmaster from GUI but permission was denied, than console cd mixmaster, but permission was denied, than sudo cd, permission again denied (that suprised me). Only then I started messing with chgrp.

I appreaciate any input really. I still don't want to erase the disk, but to wait and determine what happened.

Is it possible that it is completely normal tor behaviour?

---

### Post by persistentstubborn on 2008-05-09
Again, after I disconnected from network and unplugged modem for couple of minutes

> ubuntu@ubuntu:~$ netstat -a | less
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 ubuntu.lan:59961        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59937        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59944        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59953        ohiggins.canonical.:www TIME_WAIT  
[color=red]tcp        1      0 ubuntu.lan:53871        nrl.onion-router.ne:www CLOSE_WAIT[/color] 
tcp        0      0 ubuntu.lan:59959        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59948        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59950        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59955        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59951        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59938        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59958        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59942        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59945        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59946        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59943        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59941        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:41323        213.254.238.153:www     ESTABLISHED
tcp        0      0 ubuntu.lan:59936        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59949        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59947        ohiggins.canonical.:www TIME_WAIT  
[color=red]tcp        1      0 ubuntu.lan:39755        84.53.182.147:www       CLOSE_WAIT[/color] 
tcp        0      0 ubuntu.lan:59954        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59952        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59939        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59956        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59933        ohiggins.canonical.:www TIME_WAIT  
tcp        0      0 ubuntu.lan:59934        ohiggins.canonical.:www TIME_WAIT  
udp        0      0 *:32768                 *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path

How is that possible still to have onion-router and 84.53.182.147 (which isn't address related to my IPS) still registered?

Both connections sent 1 packet to me and are CLOSE_WAIT. What does that mean?

---

### Post by damatta on 2008-05-09
> How is that possible still to have onion-router and 84.53.182.147 (which isn't address related to my IPS) still registered?

Both connections sent 1 packet to me and are CLOSE_WAIT. What does that mean?

IT means the socket is being closed.
Personally I don't fancy TOR, it might come in handy for certain purposes but I would never input real sensitive data.

---

### Post by Chayak on 2008-05-13
It's just Tor traffic using random high number ports that firestarted thinks is BO.  There are no BO implants for linux and besides ubuntu is a lot harder to crack than you'd think (other than people using weak passwords and getting ssh bruteforce attacks to own their boxes because they have openssh server installed).  Tor can be chatty if it's polling for paths or acting as a relay.

---

