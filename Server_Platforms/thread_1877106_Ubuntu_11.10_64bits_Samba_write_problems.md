---
title: "Ubuntu 11.10 64bits Samba write problems"
date: 2011-11-07
forum: Server Platforms
---

### Post by GrenDup on 2011-11-07
Hello,

I have a box with Ubuntu 11.10 64bits server on it. (upgraded from 10.04 was working fine...)

I mainly use it as a NAS over my gigabyte ethernet using SAMBA.

for larges files: writing: 700 Ko/Sec
                       reading: +55000 Ko/Sec

I seems to be a tad slow at last on the writing side no? (unusable for me :-/)

I searched for answers but found none... I'm not a linux guru at all :-/

I have 3 software Raid5 data disks (raid status:clean)

I can provide any log/config file requested

Thank you in advance!

---

### Post by GrenDup on 2011-11-09
Hello again...

I understand my post might not be the most interresting one but still, i'd love to have some help.

As I already told, I searched quite a bit on this problem but found no solution...

anyone?

thanks in advance!

---

### Post by ekko_ on 2011-11-09
Hello GrenDup, 

First of all i have to ask you, why upgrade from 10.04? Being an LTS it should have kept you going comfortably and very stable until 12.04 which is a couple of months away.

But since you did upgrade, lets hope we can find you a solution.

Could you give us more details about your hardware, network details and samba conf


In the mean while, I will first use iperf to check your network throughoutput and try to discard anything network related.

---

### Post by GrenDup on 2011-11-11
Hello ekko_,

I ll check this on sunday... no time before, sorry

Thank you for your time!

---

### Post by GrenDup on 2011-11-13
Hello! 

As for the early upgrade, I learnt the hard way that more recent isn't always better... I won't do this mistake again!

Here come the infos:


[QUOTE=IPerf -d then -r Linux client]------------------------------------------------------------
Client connecting to 192.168.1.46, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  6] local 192.168.1.40 port 38356 connected with 192.168.1.46 port 5001
[  6]  0.0-10.0 sec   848 MBytes   711 Mbits/sec
[  5]  0.0-10.3 sec   210 MBytes   171 Mbits/sec
[  4] local 192.168.1.40 port 5001 connected with 192.168.1.46 port 47434
[  4]  0.0-10.0 sec   976 MBytes   816 Mbits/sec
------------------------------------------------------------
Client connecting to 192.168.1.46, TCP port 5001
TCP window size:  178 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.40 port 38357 connected with 192.168.1.46 port 5001
[  4]  0.0-10.0 sec  1.09 GBytes   940 Mbits/sec

[/QUOTE]

[QUOTE=IPerf -d windows client (-r strange results... so ignored)]------------------------------------------------------------
Client connecting to 192.168.1.40, TCP port 5001
TCP window size: 64.0 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.41 port 61235 connected with 192.168.1.40 port 5001
[  5] local 192.168.1.41 port 5001 connected with 192.168.1.40 port 42729
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   623 MBytes   522 Mbits/sec
[  5]  0.0-10.0 sec   717 MBytes   602 Mbits/sec[/QUOTE]


As for the hardware:
AMD Athlon II x3 440
4 GB RAM
1x 2.5 hdd system
3x 3.5 hdd files (software raid 5)
MB integrated gigabyte LAN card

Network details:

server and clients linked directly via gigabyte switch

Samba:
smb.conf.txt attached...

Tell me if you need anything else!

---

### Post by GrenDup on 2011-11-16
Nobody?

---

### Post by ian dobson on 2011-11-16
Hi,

I also had afew pronlems with the performance of samba on a gigabyte lan. After adding the following options to the smb.conf file I'm getting about 30-40Mbyte/sec write speed.

```

min receivefile size = 16384
aio read size = 16384
aio write size = 16384
aio write behind = true

##Optimize tcp
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 1026144

```

Maybe try playing with the so_rcvbuff/so_sndbuff to find the optimal values for you.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-11-16
Hi,

OK I've played with samba again on my backend server (16Gb ram, 5Drive 10Tb RAID5 array) and increasing the 
write cache size to a much higher value (12826144) increased the throughput to 70Mb/sec

```

dd if=/dev/sda of=/mnt/video/tmp/test.txt  bs=4K count=2000000
2000000+0 records in
2000000+0 records out
8192000000 bytes (8.2 GB) copied, 117.069 s, 70.0 MB/s

```

Regards
Ian Dobson

---

### Post by GrenDup on 2011-11-17
Hello  and thank you for your answer!

I tried with your parameters (I already tried  similar ones before without any luck...) and they didn't changed a thing... my write is still sluggish :-(

something else before I  give up and reinstall the whole  thing ? I'd rather not but if I don't find a solution, I  might be forced to take extreme mesures :-(

---

### Post by ian dobson on 2011-11-17
Hi,

OK here's my entire smb.conf global section:-

```
[global]
wide links=yes
getwd cache=yes
stat cache = yes
strict sync = no
use sendfile = yes
large readwrite = yes
oplock contention limit = 5
oplock break wait time = 100
case sensitive = true
strict allocate = yes
refresh = 1
read raw = No
write raw = Yes
max xmit = 131072
use sendfile = Yes
dead time = 15
getwd cache = Yes
otlocks = Yes

disable netbios = yes
nmbd bind explicit broadcast = no
netbios name = alpha2

min receivefile size = 436384
aio read size = 6436384
aio write size = 6436384
aio write behind = true

##Optimize tcp
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 12826144
strict allocate = yes
```

What network card do you have in the sever? Ihope it's not a realtek card :)

Regards
Ian Dobson

---

### Post by GrenDup on 2011-11-19
Hello!

I finally found an answer and you put me on the tracks to find it... 

F****** Realtek nic! (RTL8112L)

I followed this:

[https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

worked perfectly!

I'll try later to fine tune my smb.conf but right now I'm just happy with what I have ;-)

Thanks!

---

### Post by ian dobson on 2011-11-19
Hi,

so what are you getting?

Regards
Ian Dobson

---

### Post by GrenDup on 2011-12-02
Hi,

with your settings: +20 000 kbps writing and +40 000 kbps reading

thank you again

---

