---
title: "panp4i slow wireless"
date: 2008-10-01
forum: System76 Support
---

### Post by adingo on 2008-10-01
i got a new panp4i recently.  the wireless speed on it is significantly slower than what i'm able to get on a windows laptop.  i get around 1200 kbps on windows, but only 600 kpbs on ubuntu.  both computers are showing connections to the router of 11 Mb/s.  my iwconfig output:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"HOME"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: xxxxxx
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=66/100  Signal level=-60 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i don't know how to get that much detail off windows, but it shows 4/5 bars.  the noise level is high on the above.  turning off the windows machine makes no difference.  there are no other transmitters nearby (and windows doesn't seem to have a problem in the same area...)

a ping to google on the windows machine consistently returns in around 60ms.  ping from ubuntu varies from 80 to over 200 ms.  windows is pinging 32 byes vs ubuntu's 64 byes.

no other applications, to my knowledge, are causing the delta on the ubuntu machine.  the system monitor->resources shows 15 KiB/s in traffic prior to starting a speed test, so i'm reasonably confident another ap isn't the problem

any ideas?

---

### Post by jdb on 2008-10-01
> **adingo said:**
> i got a new panp4i recently.  the wireless speed on it is significantly slower than what i'm able to get on a windows laptop.  i get around 1200 kbps on windows, but only 600 kpbs on ubuntu.  both computers are showing connections to the router of 11 Mb/s.  my iwconfig output:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"HOME"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: xxxxxx
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=66/100  Signal level=-60 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i don't know how to get that much detail off windows, but it shows 4/5 bars.  the noise level is high on the above.  turning off the windows machine makes no difference.  there are no other transmitters nearby (and windows doesn't seem to have a problem in the same area...)

a ping to google on the windows machine consistently returns in around 60ms.  ping from ubuntu varies from 80 to over 200 ms.  windows is pinging 32 byes vs ubuntu's 64 byes.

no other applications, to my knowledge, are causing the delta on the ubuntu machine.  the system monitor->resources shows 15 KiB/s in traffic prior to starting a speed test, so i'm reasonably confident another ap isn't the problem

any ideas?

In most cases the packet size won't make much difference, but if you want to compare apples to apples:

 ping -s 24 [www.google.com](www.google.com)

will cause the ping to show 32 bytes instead of 64

I don't know why there would be more latency from linux than from windows, that's usually a function of the Internet - routing, servers, etc.
Are there any gaps in the seq numbers?
That would be a sign that packets are being lost.
If you find something be sure to let us know.

jdb

---

### Post by adingo on 2008-10-02
> **jdb said:**
> In most cases the packet size won't make much difference, but if you want to compare apples to apples:

 ping -s 24 [www.google.com](www.google.com)

will cause the ping to show 32 bytes instead of 64

I don't know why there would be more latency from linux than from windows, that's usually a function of the Internet - routing, servers, etc.
Are there any gaps in the seq numbers?
That would be a sign that packets are being lost.
If you find something be sure to let us know.

jdb
i don't see much package loss 

--- [www.l.google.com](www.l.google.com) ping statistics ---
108 packets transmitted, 107 received, 0% packet loss, time 110062ms
rtt min/avg/max/mdev = 79.375/207.161/1072.619/191.568 ms, pipe 2

plugging in directly to the router gives performance equal to the windows machine.  that would seem to eliminate everything but the wireless card...  i'm starting to think i might have some bad hardware.

---

### Post by jdb on 2008-10-03
> **adingo said:**
> i don't see much package loss 

--- [www.l.google.com](www.l.google.com) ping statistics ---
108 packets transmitted, 107 received, 0% packet loss, time 110062ms
rtt min/avg/max/mdev = 79.375/207.161/1072.619/191.568 ms, pipe 2

plugging in directly to the router gives performance equal to the windows machine.  that would seem to eliminate everything but the wireless card...  i'm starting to think i might have some bad hardware.

I went out in the back yard to get my link quality below 66/100 & this is what I got:

wlan0     IEEE 802.11g  ESSID:"zoom"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: xxxxxxx   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=61/100  Signal level=-71 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What really stands out here is that I'm getting 54 Mb/s but your only getting 11 Mb/s

edit:

This link has a fix that might work for you:

[http://ubuntuforums.org/archive/index.php/t-392651.html](http://ubuntuforums.org/archive/index.php/t-392651.html)



jdb

---

### Post by adingo on 2008-10-07
I checked the laptop against a friend's wireless and got good speed.  I upgraded my router and the speed is much improved.  The old router (netgear MR814v2) just apparently doesn't play well w/ hardy.  it's only a 802.11b, so possibly it's the old protocal that's causing the problem, though it worked w/ XP.  either way, problem solved.

thanks for the help!

---

