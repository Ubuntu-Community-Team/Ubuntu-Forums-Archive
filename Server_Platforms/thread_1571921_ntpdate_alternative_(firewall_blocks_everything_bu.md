---
title: "ntpdate alternative (firewall blocks everything but port 22)"
date: 2010-09-10
forum: Server Platforms
---

### Post by junkpete on 2010-09-10
Hi guys,

both ntpdate -u and ntpdate -d doesnt work on my server, I get this output:

```
root@kes:~# /usr/sbin/ntpdate de.pool.ntp.org
10 Sep 14:22:54 ntpdate[13027]: no server suitable for synchronization found


root@kes:~# /usr/sbin/ntpdate -d de.pool.ntp.org
10 Sep 14:23:20 ntpdate[13051]: ntpdate 4.2.4p6@1.1549-o Fri Dec  4 18:08:43 UTC 2009 (1)
transmit(192.53.103.108)
transmit(212.224.90.41)
transmit(85.31.187.67)
transmit(192.53.103.108)
transmit(212.224.90.41)
transmit(85.31.187.67)
transmit(192.53.103.108)
transmit(212.224.90.41)
transmit(85.31.187.67)
transmit(192.53.103.108)
transmit(212.224.90.41)
transmit(85.31.187.67)
transmit(192.53.103.108)
transmit(212.224.90.41)
transmit(85.31.187.67)
192.53.103.108: Server dropped: no data
212.224.90.41: Server dropped: no data
85.31.187.67: Server dropped: no data
server 192.53.103.108, port 123
stratum 0, precision 0, leap 00, trust 000
refid [192.53.103.108], delay 0.00000, dispersion 64.00000
transmitted 4, in filter 4
reference time:    00000000.00000000  Thu, Feb  7 2036  7:28:16.000
originate timestamp: 00000000.00000000  Thu, Feb  7 2036  7:28:16.000
transmit timestamp:  d034a1bb.9c941c82  Fri, Sep 10 2010 14:23:23.611
filter delay:  0.00000  0.00000  0.00000  0.00000 
         0.00000  0.00000  0.00000  0.00000 
filter offset: 0.000000 0.000000 0.000000 0.000000
         0.000000 0.000000 0.000000 0.000000
delay 0.00000, dispersion 64.00000
offset 0.000000

server 212.224.90.41, port 123
stratum 0, precision 0, leap 00, trust 000
refid [212.224.90.41], delay 0.00000, dispersion 64.00000
transmitted 4, in filter 4
reference time:    00000000.00000000  Thu, Feb  7 2036  7:28:16.000
originate timestamp: 00000000.00000000  Thu, Feb  7 2036  7:28:16.000
transmit timestamp:  d034a1bb.cfc6b8b6  Fri, Sep 10 2010 14:23:23.811
filter delay:  0.00000  0.00000  0.00000  0.00000 
         0.00000  0.00000  0.00000  0.00000 
filter offset: 0.000000 0.000000 0.000000 0.000000
         0.000000 0.000000 0.000000 0.000000
delay 0.00000, dispersion 64.00000
offset 0.000000

server 85.31.187.67, port 123
stratum 0, precision 0, leap 00, trust 000
refid [85.31.187.67], delay 0.00000, dispersion 64.00000
transmitted 4, in filter 4
reference time:    00000000.00000000  Thu, Feb  7 2036  7:28:16.000
originate timestamp: 00000000.00000000  Thu, Feb  7 2036  7:28:16.000
transmit timestamp:  d034a1bc.02fa5093  Fri, Sep 10 2010 14:23:24.011
filter delay:  0.00000  0.00000  0.00000  0.00000 
         0.00000  0.00000  0.00000  0.00000 
filter offset: 0.000000 0.000000 0.000000 0.000000
         0.000000 0.000000 0.000000 0.000000
delay 0.00000, dispersion 64.00000
offset 0.000000

10 Sep 14:23:25 ntpdate[13051]: no server suitable for synchronization found


root@kes:~# /usr/sbin/ntpdate -u de.pool.ntp.org
10 Sep 14:23:43 ntpdate[13052]: no server suitable for synchronization found

root@kes:~# 

```

So is there a way to update the time (which is horribly wrong day to day) on this linux server? Since the server is behind the firewall of my university, there is no way to open any ports, only port 22 is open for SSH access.

---

### Post by aeiah on 2010-09-10
since you can only use ssh i guess you are kinda limited. the inaccurate way would be to grab the time from an external server:

```

ssh user@server 'date'

```

but if you need accuracy you'll want to create an ssh tunnel and direct all port 123 traffic out through it.

for both you'll need an external server of course, that you have shh access to. there are a number of free shell providers. [http://devio.us](http://devio.us) are pretty good

---

### Post by aeiah on 2010-09-10
your tunnel would be something like:
```

ssh username@externalserver.com -L 123:externalserver.com:123

```

you need to be root because port 123 (ntp, unless im mistaken) is special.

if you put an -N on the end it'll fork it to the background. probably useful to do that in a script because once the tunnel is up you'll want to issue your ntpdate command.

---

### Post by junkpete on 2010-09-10
OK I think I made a mistake on the title.

The firewall blocks everything but port 22 from outside, I can connect with my server to port 80, 21 and as far as I know also to port 123. I dont really understand the network setup, but I was assuming ntpdate doesnt work anyways. Maybe there is some kind of solution? Does anybody has a clue whats going on?

---

### Post by terazen on 2010-09-10
If they are blocking outbound ntp (i can't even think of why) then ask your network guys what ntp server they use and point ntpdate to that.

They have one locally that works internal to your network I'm sure.

---

### Post by hictio on 2010-09-10
If they are actually blocking NTP traffic from within your network towards the internet (meaning publicly available NTP servers) it can be that either:

- they are not aware of that,
- they don't know how to properly firewall the ntp service;
- or they actually have a local ntp server from which you should actually sync from (it makes sense to actually have a local server, and make all the boxes on the LAN sync from that one).

In any case, You should ask them.

If nothing works, and you can access HTTP over the firerwall (outbound, that is) you might want to try [http Time Protocol](http://www.clevervest.com/htp/), it is not as accurate as ntpd tho.
You can get htp from the repositories, at least on Lucid.

---

