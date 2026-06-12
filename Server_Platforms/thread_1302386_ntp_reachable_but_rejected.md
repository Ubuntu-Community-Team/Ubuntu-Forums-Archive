---
title: "ntp reachable but rejected"
date: 2009-10-27
forum: Server Platforms
---

### Post by mosestruong on 2009-10-27
I am behind a firewall, and we have a ntp server that is synced to the outside world, I am trying to get my computer synced to this server. However, the status I get is reject, and the time is not synced.

Here is the results of ntpq when querying the server,
```
#ntpq -pcrv ntp
assID=0 status=06b4 leap_none, sync_ntp, 11 events, event_peer/strat_chg,
version="ntpd 4.2.2p1@1.1570-o Sat Nov 10 12:33:50 UTC 2007 (1)",
processor="i686", system="Linux/2.6.18-53.1.6.el5", leap=00, stratum=2,
precision=-20, rootdelay=772.863, rootdispersion=571.373, peer=51935,
refid=128.250.33.242,
reftime=ce910ccc.430e37a3  Tue, Oct 27 2009 16:08:12.261, poll=9,
clock=ce910e28.43982e46  Tue, Oct 27 2009 16:14:00.264, state=4,
offset=13.811, frequency=138.883, jitter=63.866, noise=18.060,
stability=1.198, tai=0
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+ntp.tbpl.com.au .GPS.            1 u  277  512   75  748.888   -0.211   6.754
*mumnunah.csse.u .GPS.            1 u  350  512   61  772.863   46.184  59.484
+202-89-184-139. 203.12.160.2     3 u 1249  512  114  674.257    8.241  10.285
-ds001.hostingsh 128.250.36.3     2 u  470  512   75  704.389  -10.172  17.141
 203.31.84.4     128.250.33.242   2 u   96  512  353  706.836   15.704  60.259

```

And this is the result when querying my computer:
```
#ntpq -pcrv 
assID=0 status=c011 sync_alarm, sync_unspec, 1 event, event_restart,
version="ntpd 4.2.4p6@1.1549-o Fri Aug 21 01:18:41 UTC 2009 (1)",
processor="x86_64", system="Linux/2.6.31-11-generic", leap=11,
stratum=16, precision=-20, rootdelay=0.000, rootdispersion=74.760,
peer=0, refid=INIT,
reftime=00000000.00000000  Thu, Feb  7 2036 16:28:16.000, poll=6,
clock=ce910e3f.8ce883cc  Tue, Oct 27 2009 16:14:23.550, state=1,
offset=0.000, frequency=-10.000, jitter=0.001, noise=0.001,
stability=0.000, tai=0
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 172.23.68.1     128.250.33.242   2 u   23   64  377    0.224  -1715.1  44.961

```

The associations are:
```
ind assID status  conf reach auth condition  last_event cnt
===========================================================
  1 12978  9014   yes   yes  none    reject   reachable  1

```

My configuration file with the comments stripped out is:
```
driftfile /var/lib/ntp/ntp.drift

server 172.23.68.1 iburst
restrict 172.23.68.1

restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

restrict 127.0.0.1
restrict ::1

```

Would anyone give me a pointer as to why it is rejecting the ntp server? Thanks.

---

### Post by Vegan on 2009-10-27
Open up the port. NTP is on port 119.

---

### Post by mosestruong on 2009-10-27
I thought NTP is port 123.

Anyway, I don't think it is a firewall issue since from my computer I can query the server, and I've just tested, from the server I can query my computer as well.

The problem is that my computer is rejecting the time from the server, and I just wanted to know why and how to stop it from rejecting it.

---

### Post by Lars Noodén on 2009-10-28
NTP is indeed port 123, check /etc/services to see that:

ntp             123/tcp
ntp             123/udp                         # Network Time Protocol

It usually uses UDP on port 123 for both machines.  

Make sure that the firewall allows that.

---

### Post by Lars Noodén on 2009-10-28
> **mosestruong said:**
> I thought NTP is port 123.

Anyway, I don't think it is a firewall issue since from my computer I can query the server, and I've just tested, from the server I can query my computer as well.

The problem is that my computer is rejecting the time from the server, and I just wanted to know why and how to stop it from rejecting it.

The logs for regular ntpd are mixed in with the other system logs.  You can separate them with grep, and for the older logs with zgrep:

```

# check the more recent logs first
grep ntpd /var/log/syslog | less

# if still no clue, then check the older logs
zgrep ntpd /var/log/syslog.*.gz |*less

```

They might give a hint, if the firewall is already open.   

You can check the network situation:
```

# check if DNS is working
host ntp.ubuntu.com && echo "DNS OK"

# check if the time server is online
ping -c1 ntp.ubuntu.com && echo "Host online"

# check the availability and status of port 123 on the time server
sudo nmap -v -sU -pU:123 --reason ntp.ubuntu.com

# leave tcpdump running in another terminal while you
# start or restart ntp or ntpdate
sudo tcpdump -i eth0 udp port 123 or tcp port 123

```

**Edit** - point these at your time server, rather than the Canonical one.

---

### Post by Lars Noodén on 2009-10-28
Sorry for the noise in the post above.  It looks like you may need to open access for your local net.   'no_query' should be removed for the subnet you have:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server)

---

### Post by mosestruong on 2009-10-29
The noquery was on my computer, not the server -

The server has the following restriction:
restrict 172.23.24.0 mask 255.255.255.0 nomodify notrap nopeer
restrict 172.23.68.0 mask 255.255.255.0 nomodify notrap nopeer 
restrict 172.23.125.0 mask 255.255.255.0 nomodify notrap nopeer 

Let me try and illustrate this a little clearer:
```
Internet ---> (xx.xx) Router (68.1) ---> .68 subnet
                                   (24.1) ---> (24.2) Second Router (125.1) ---> .125 subnet 

```

The Router syncs with NTP from the internet, and acts a s a NTP server for the local area network.
The Second Router is able sync without any problem. However computers on the .68 subnet aren't able to even though they have the same ntp configuration...

On the Router, there is an entry for NTP/ACCEPT from both interfaces to the Router. Since the Second Router is able to sync with the Router, that should eliminate firewall issues.

Computers in .68 network can use ntpdate to update the time with the Router, however the result is rejected when trying to use ntpd. 

Any other clues as to what I should be checking? Thanks in advance.

---

### Post by Vegan on 2009-10-29
The is curious, my Linux gear automatically gets everything, and when I installed the deamon, it worked as time server that Windows liked.

I did not touch the settings.

---

### Post by mosestruong on 2009-10-29
Well, it partly works - windows can update from it, and I can use ntpdate to update as well, however, linux computers on the same server cannot use ntpd to update, it is able to get the time information, but for some reason they are rejected...

This is the ntpd log (I'm not sure why it complains that it can't open the log file until I chmod it to 777, even though it's owned by the user ntp):
```
30 Oct 08:01:20 ntpd[7711]: system event 'event_restart' (0x01) status 'sync_alarm, sync_unspec, 1 event, event_unspec' (0xc010)
30 Oct 08:01:21 ntpd[7711]: peer 172.23.68.1 event 'event_reach' (0x84) status 'unreach, conf, 1 event, event_reach' (0x8014)

```

---

### Post by Vegan on 2009-10-30
The ntpd daemon does not run that way, it runs as a system service, so you need to set the permissions, 777 is one way.

---

### Post by Lars Noodén on 2009-10-30
@mosestruong : what is the exact name of the log file you have quoted above?  If it is something other than /var/log/systlog then please post the name.  If it is not, then please consider the following:

> **Vegan said:**
> The ntpd daemon does not run that way, it runs as a system service, so you need to set the permissions, 777 is one way.

Whoa!  Almost nothing gets set 777 on a Linux system.  It would be very dangerous to set *anything* to permissions rwx for user, group and world.  Making the system logs readable to the world is very bad.   Making it writeable ...

> **mosestruong said:**
> ...
This is the ntpd log (I'm not sure why it complains that it can't open the log file until I chmod it to 777, even though it's owned by the user ntp)

The correct settings for syslog are
[INDENT][FONT="Courier New"]-rw-r-----  syslog adm  /var/log/syslog[/FONT][/INDENT]
You can check
[INDENT][FONT="Courier New"]ls -l /var/log/syslog[/FONT][/INDENT]

You can restore them this way for Karmic:

[INDENT]sudo chown syslog:adm /var/log/syslog
sudo chmod 640 /var/log/syslog[/INDENT]

If you are logged in as a user which is a member of the group adm, then you should be able to read that log file with no additional trouble.

---

### Post by mosestruong on 2010-08-09
Dave Hart suggested to add the following to the ntp.conf and restart ntp daemon and it solved the problem.

tos maxdist 2.5

---

