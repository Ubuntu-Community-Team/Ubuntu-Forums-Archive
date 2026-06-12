---
title: "Setting up NTP using Webmin"
date: 2009-10-15
forum: Server Platforms
---

### Post by will81 on 2009-10-15
Hi,

The short story: Why is Webmin synchronising my Ubunut 9.04 Server's clock using the Unix TIME protocol instead of NTP?

The long story...

I'm running a web server on Ubuntu Server 9.04:

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
```

It doesn't have any GUI installed so I am reasonably comfortable using the terminal (SSH) to configure it but I am using Webmin 1.490 where possible, for convenience and to reduce the chance of me typing the wrong thing.  Most things are running smoothly.

The only thing I'm struggling with is network time synchronisation.  Using Webmin, I've gone to Hardware -> System time -> Time server sync, entered "ntp2c.mcc.ac.uk" and enabled "Set hardware time too".  When I click "Sync and Apply", it thinks about it for a few seconds, then says "Failed to connect to ntp2c.mcc.ac.uk:37 : No route to host".  This is okay: I know that port 37 of our router is closed, but what I don't understand is why it is using the Unix TIME protocol (on port 37) instead of NTP (on port 123, which is open).

The Webmin documentation on the matter is sparse, stating only that "For your system to use NTP for synchronization you must have the ntpdate NTP client program installed."  It is installed, and works:

```
$ sudo ntpdate ntp2c.mcc.ac.uk
15 Oct 16:48:01 ntpdate[31061]: step time server 130.88.200.6 offset -279.724975 sec
```

I'm stuck.  Any ideas?  Thanks in advance.

-Will.

---

### Post by will81 on 2009-10-15
Digging around has led me to /etc/webmin/time/config, which contains the following:

```
timeserver_hardware=1
seconds=1
lease=5
timeserver=ntp2c.mcc.ac.uk
ntp_only=0
zone_style=linux
hwtime=1
```

Changing line 5 to ntp_only=1, then re-clicking the "Sync and Apply" button in Webmin now yields the following:

```
NTP time synchronization failed : 15 Oct 17:37:15 ntpdate[32034]: no server suitable for synchronization found
```

What I don't understand is why it fails for Webmin but works at the shell.  A permissions problem?  Maybe but if I omit the "sudo" it just says Is there a way I can "-bash: /usr/sbin/ntpdate: Permission denied".  Is there a way I can find out what command it's actually trying to run?

-Will.

---

### Post by will81 on 2009-10-15
Now I'm wondering whether sudo ntpdate really is working at the shell.  It seems to work outright but fails in debugging mode:

```
$ sudo ntpdate ntp2c.mcc.ac.uk
15 Oct 17:49:21 ntpdate[32247]: adjust time server 130.88.200.6 offset 0.023490 sec
```

```
$ sudo ntpdate -d ntp2c.mcc.ac.uk
15 Oct 17:49:26 ntpdate[32248]: ntpdate 4.2.4p4@1.1520-o Wed May 13 21:05:44 UTC 2009 (1)
transmit(130.88.200.6)
transmit(130.88.200.6)
transmit(130.88.200.6)
transmit(130.88.200.6)
transmit(130.88.200.6)
130.88.200.6: Server dropped: no data
server 130.88.200.6, port 123
stratum 0, precision 0, leap 00, trust 000
refid [130.88.200.6], delay 0.00000, dispersion 64.00000
transmitted 4, in filter 4
reference time:    00000000.00000000  Thu, Feb  7 2036  6:28:16.000
originate timestamp: 00000000.00000000  Thu, Feb  7 2036  6:28:16.000
transmit timestamp:  ce81d11a.12034f3f  Thu, Oct 15 2009 17:49:30.070
filter delay:  0.00000  0.00000  0.00000  0.00000 
         0.00000  0.00000  0.00000  0.00000 
filter offset: 0.000000 0.000000 0.000000 0.000000
         0.000000 0.000000 0.000000 0.000000
delay 0.00000, dispersion 64.00000
offset 0.000000

15 Oct 17:49:31 ntpdate[32248]: no server suitable for synchronization found
```

Huh?

---

### Post by zappepcs on 2009-11-28
I'm having the same or similar problems with webmin and Ubuntu 9.10 i386desktop. Something is going on. Using the GUI to set ntp options for ntp.org servers, Ubuntu seems happy, but Webmin is NOT. Trying ntpdate from cli gives an error while ntpd is running. NTPD is holding port 123 (both ipv4 and ipv6). If you stop ntpd (sudo /etc/init.d/ntp stop) then webmin quits complaining completely... huh?

user@chow:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
user@chow:~$ sudo ntpdate 1.north-america.pool.ntp.org

28 Nov 21:16:27 ntpdate[9334]: the NTP socket is in use, exiting
user@chow:~$ sudo ntpdate 1.north-america.pool.ntp.org
28 Nov 21:16:31 ntpdate[9336]: the NTP socket is in use, exiting

user@chow:~$ sudo /etc/init.d/ntp stop
 * Stopping NTP server ntpd                                                                          [ OK ] 

user@chow:~$ sudo ntpdate 1.north-america.pool.ntp.org
28 Nov 21:17:08 ntpdate[9361]: adjust time server 173.9.142.98 offset 0.001746 sec

---

### Post by will81 on 2009-11-29
I think I eventually gave up trying to get Webmin to play nicely with NTP and just set it up at the command line.  It was pretty easy.  Here are the notes I made at the time:

```

Install the NTP daemon (the client is installed by default but the daemon is better)
	sudo apt-get install ntp

Configure ntpd
	sudo nano /etc/ntp.conf
		statsdir /var/log/ntpstats		# Just uncomment this line
		server 0.europe.pool.ntp.org		# Add this line
		server 1.europe.pool.ntp.org		# Add this line
		server 2.europe.pool.ntp.org		# Add this line
		server 3.europe.pool.ntp.org		# Add this line
		server 4.europe.pool.ntp.org		# Add this line
		server ntp.ubunutu.com			# This line was already there

Restart ntpd and check it's working
	sudo tail --follow /var/log/daemon.log | grep ntp
	(then, in a separate terminal session)
	sudo /etc/init.d/ntp restart

```

---

### Post by AboveTheLogic on 2009-12-04
> **zappepcs said:**
> I'm having the same or similar problems with webmin and Ubuntu 9.10 i386desktop. Something is going on. Using the GUI to set ntp options for ntp.org servers, Ubuntu seems happy, but Webmin is NOT. Trying ntpdate from cli gives an error while ntpd is running. NTPD is holding port 123 (both ipv4 and ipv6). If you stop ntpd (sudo /etc/init.d/ntp stop) then webmin quits complaining completely... huh?

user@chow:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
user@chow:~$ sudo ntpdate 1.north-america.pool.ntp.org

28 Nov 21:16:27 ntpdate[9334]: the NTP socket is in use, exiting
user@chow:~$ sudo ntpdate 1.north-america.pool.ntp.org
28 Nov 21:16:31 ntpdate[9336]: the NTP socket is in use, exiting

user@chow:~$ sudo /etc/init.d/ntp stop
 * Stopping NTP server ntpd                                                                          [ OK ] 

user@chow:~$ sudo ntpdate 1.north-america.pool.ntp.org
28 Nov 21:17:08 ntpdate[9361]: adjust time server 173.9.142.98 offset 0.001746 sec

This is normal.

NTP listens and communicates both on port 123, so when the daemon is running its occupying that port.

If you want to run ntpdate with the ntp daemon running, use "ntpdate -u" and it will use some other port.

---

### Post by will81 on 2010-03-28
> **will81 said:**
> I think I eventually gave up trying to get Webmin to play nicely with NTP and just set it up at the command line.
One thing to add: I also had to disable Webmin's time sync because, with ntpd working on port 123, ntpdate (used by Webmin) was unable to use the port and sent me an e-mail every hour to tell me so.

---

