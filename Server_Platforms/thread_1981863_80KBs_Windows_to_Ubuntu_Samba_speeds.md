---
title: "80KB/s Windows to Ubuntu Samba speeds"
date: 2012-05-17
forum: Server Platforms
---

### Post by Hwest on 2012-05-17
Hi

I just installed SAMBA onto my Ubuntu 12.04 server and when I try copying a file from windows 7 to the share the transfer is only 80KB/s.
Any ideas on how to increase speeds?

Cheers

---

### Post by Cheesemill on 2012-05-17
What is your network setup?
How are the server and Windows machine talking to each other?

---

### Post by arrrghhh on 2012-05-17
Samba is slow, but network topology is needed to further understand what's going on.

Did you verify raw connectivity between the two devices using iperf?  I would recommend it.

---

### Post by Hwest on 2012-05-18
Both the windows and Server have WIFI Gigabyte adapters, connected to a Billion BiPAC 6404VGPR3. Thats 54MB/s. Peak download from the internet is 1.2MB/s.

I did a reinstall of Samba following a guide and now im getting 400-600KB/s. Averaging around 530. Its better but still too slow for my use.

And sorry, How do I use iperf?

Edit: Current transfer just hit 130KB/s

---

### Post by Hwest on 2012-05-18
Thanks to google, Im trying a windows app called Teracopy, and my upload speeds havent dropped below 500KB/s, Its normally around 600-770KB/s.

Once again, Better but anyway to get it >1MB/s?

---

### Post by arrrghhh on 2012-05-18
> **Hwest said:**
> Thanks to google, Im trying a windows app called Teracopy, and my upload speeds havent dropped below 500KB/s, Its normally around 600-770KB/s.

Once again, Better but anyway to get it >1MB/s?

Did you try iperf?  It will help you get the raw transfer rates between machines... Very little overhead.

You just need it running on the server and the client.

54mbps/8 = 6.75MB/s.  That's absolutely ideal, which is really never the case with wifi.  I usually get 4-5MB/s, but I'm on N - 135mbps...

---

### Post by ian dobson on 2012-05-18
Hi,

You could try modifying your /etc/samba/smb.conf. These are the settings I'm using on my big backend server (8core,16Gb ram,20Tb RAID arrays)

```

[global]
read raw = yes
write raw = yes
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
max xmit = 131072
use sendfile = Yes
dead time = 15
getwd cache = Yes

disable netbios = yes
nmbd bind explicit broadcast = no
netbios name = alpha2

min receivefile size = 13638
aio read size = 64360
aio write size = 64360
aio write behind = true

##Optimize tcp
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 12826144
strict allocate = yes

```

With this configuration I get about 8MByte/sec from windows7 to the server over 5GHz wireless network abd 30MByte/sec from a second linux box over a GBit lan.

Regards
Ian Dobson

---

### Post by CharlesA on 2012-05-18
> **arrrghhh said:**
> Did you try iperf?  It will help you get the raw transfer rates between machines... Very little overhead.

You just need it running on the server and the client.

54mbps/8 = 6.75MB/s.  That's absolutely ideal, which is really never the case with wifi.  I usually get 4-5MB/s, but I'm on N - 135mbps...
That sounds about the speeds I get over wireless. If I need to transfer a lot of files, I'll go over wired gigabit.

---

### Post by Hwest on 2012-05-18
> **ian dobson said:**
> Hi,

You could try modifying your /etc/samba/smb.conf. These are the settings I'm using on my big backend server (8core,16Gb ram,20Tb RAID arrays)

```

[global]
read raw = yes
write raw = yes
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
max xmit = 131072
use sendfile = Yes
dead time = 15
getwd cache = Yes

disable netbios = yes
nmbd bind explicit broadcast = no
netbios name = alpha2

min receivefile size = 13638
aio read size = 64360
aio write size = 64360
aio write behind = true

##Optimize tcp
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE

write cache size = 12826144
strict allocate = yes

```

With this configuration I get about 8MByte/sec from windows7 to the server over 5GHz wireless network abd 30MByte/sec from a second linux box over a GBit lan.

Regards
Ian Dobson

Cheers for the config, Ill try that out after this transfer is done.

How do I do an iperf?

---

### Post by arrrghhh on 2012-05-18
> **Hwest said:**
> How do I do an iperf?

I would recommend reading up on it, but it's basically a cross platform tool to test network performance.  Put it on the server and the client, then run it between the two devices.  It's quite easy to use, just check the manpage.  man iperf (you'll probably have to sudo apt-get install iperf first ;)).

[http://www.enterprisenetworkingplanet.com/netos/article.php/3657236/Measure-Network-Performance-with-iperf.htm](http://www.enterprisenetworkingplanet.com/netos/article.php/3657236/Measure-Network-Performance-with-iperf.htm)

That's also a pretty thorough guide on it ^^

---

### Post by Hwest on 2012-05-20
Thanks for the help guys, I think It was just a router thing.
I rebooted the router and the server, since then ive been getting 1-1.3 MB/s transfer. Thats enough for me, Ill take it.

Cheers for the help :)

---

