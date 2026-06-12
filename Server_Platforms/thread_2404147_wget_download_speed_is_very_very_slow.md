---
title: "wget download speed is very very slow"
date: 2018-10-20
forum: Server Platforms
---

### Post by void.pointer on 2018-10-20
I'm seeing some weird behavior in Ubuntu Server 18.04. The primary purpose of this machine is to host a lot of docker containers. I don't really have much else running on it.

When I run `wget`, I get very slow downstream speeds (Note: My connection is capable of 400Mbps downstream). My server is wired to my gigabit network:

```

user@machine:~$ wget [http://ipv4.download.thinkbroadband.com/1GB.zip](http://ipv4.download.thinkbroadband.com/1GB.zip)
--2018-10-20 14:40:22--  [http://ipv4.download.thinkbroadband.com/1GB.zip](http://ipv4.download.thinkbroadband.com/1GB.zip)
Resolving ipv4.download.thinkbroadband.com (ipv4.download.thinkbroadband.com)... 80.249.99.148
Connecting to ipv4.download.thinkbroadband.com (ipv4.download.thinkbroadband.com)|80.249.99.148|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1073741824 (1.0G) [application/zip]
Saving to: ‘1GB.zip.2’


1GB.zip.2                                1%[                                                                          ]  10.30M  1.38MB/s    eta 12m 34s

```

When I download this same file on my Windows desktop machine, I get at least 17MB/s, so I know it's not the remote server that is slow. On my Ubuntu machine I'm only getting 1-2MB/s. I tried the same thing with `curl`:

```

user@machine:~$ curl -o big.zip http://ipv4.download.thinkbroadband.com/1GB.zip
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  2 1024M    2 21.3M    0     0  1395k      0  0:12:31  0:00:15  0:12:16 1452k

```

Same results. Needless to say, all my docker containers are slow because of this as well.

Weirdly, though, if I run a speed test, it appears to be as fast as I expect:

```

user@machine:~$ curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -
Retrieving speedtest.net configuration...
Testing from Spectrum (<snip>)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by <snip> [49.36 km]: 23.608 ms
Testing download speed................................................................................
Download: 338.40 Mbit/s
Testing upload speed................................................................................................
Upload: 16.52 Mbit/s

```

No idea what the heck is going on here... can someone help me diagnose the issue? My expectation is that wget/curl is able to download the file as close as possible to 50MB/s.

---

### Post by TheFu on 2018-10-20
Simplify and test.
Simplify and test.
Repeat.

wget is recognized by many download sites as a batch download tool. They throttle it when it is seen in the user-agent setting. You can change that to anything you like to see if the remote site is throttling in that way.  Same for curl.

Make the simplest network between 2 containers on the same physical machine and test transferring files.  What is the performance?  Is is GigE or limited by something else, like storage contention?

Next, test the network transfer performance between systems on the same LAN.  How does that work?  What is limiting it?

Clear all the limitations, then do transfers over the internet.

Start with shutting down all the containers and trying to transfer using only the physical host. Anything close to 360 Mbps (90% of the paid-for bandwidth) would be great, but speedtest is sowing only 338 Mbps, so there is some limitation somewhere.

Use iperf3 and bonnie++ to test the different subsystems.  I don't know the issue, but suspect it is the network setup used by Docker and disk contention impacting performance.  There is a point where thing downloaded have to be written to disk. Depending on the storage subsystem, it is very easy to run against that with faster network connections.  I see it all-the-time moving TV recordings around my LAN.

You can watch the disk and network buffers used on Linux using the **free -mh** command.  Transfers should be very fast until the buffers are full, then drop back to whatever the storage can support.  USB connected storage is always slower than SATA/eSATA and NVMe connected storage.

Also, check the system log files for any issues.

Good hunting.

---

### Post by void.pointer on 2018-10-20
> **TheFu said:**
> Simplify and test.
Simplify and test.
Repeat.

wget is recognized by many download sites as a batch download tool. They throttle it when it is seen in the user-agent setting. You can change that to anything you like to see if the remote site is throttling in that way.  Same for curl.

Make the simplest network between 2 containers on the same physical machine and test transferring files.  What is the performance?  Is is GigE or limited by something else, like storage contention?

Next, test the network transfer performance between systems on the same LAN.  How does that work?  What is limiting it?

Clear all the limitations, then do transfers over the internet.

Start with shutting down all the containers and trying to transfer using only the physical host. Anything close to 360 Mbps (90% of the paid-for bandwidth) would be great, but speedtest is sowing only 338 Mbps, so there is some limitation somewhere.

Use iperf3 and bonnie++ to test the different subsystems.  I don't know the issue, but suspect it is the network setup used by Docker and disk contention impacting performance.  There is a point where thing downloaded have to be written to disk. Depending on the storage subsystem, it is very easy to run against that with faster network connections.  I see it all-the-time moving TV recordings around my LAN.

You can watch the disk and network buffers used on Linux using the **free -mh** command.  Transfers should be very fast until the buffers are full, then drop back to whatever the storage can support.  USB connected storage is always slower than SATA/eSATA and NVMe connected storage.

Also, check the system log files for any issues.

Good hunting.

Changed user agent like so: wget --user-agent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:21.0) Gecko/20100101 Firefox/21.0" [http://ipv4.download.thinkbroadband.com/1GB.zip](http://ipv4.download.thinkbroadband.com/1GB.zip)
Got same results.


10GB file copy between 2 containers using SCP: 240MB/s


10GB file Between linux machine and Windows: >40MB/s


Shut down all containers (`docker-compose down`)


Did same wget command as earlier, got ~1.5MB/s


Couldn't use `iperf3` since I don't have a public server to test against.


bonnie++ gave me this output: [https://i.imgur.com/EPHA3Zq.png](https://i.imgur.com/EPHA3Zq.png)
(Followed instructions here: [https://www.jamescoyle.net/how-to/913-simple-bonnie-example](https://www.jamescoyle.net/how-to/913-simple-bonnie-example))

---

### Post by void.pointer on 2018-10-20
It's so weird: curl & wget are slow, but apt-get is fast and Docker pull is fast.

---

### Post by TheFu on 2018-10-21
How might we figure out if the issue is related to the NIC or to the docker containers only?

Are the transfers slow just for 1 site or all sites?

Does the size of the files transferred matter?

Are there any known docker bugs?

BTW, I don't know what "Did same wget command as earlier, got ~1.5MB/s" means.  It is ambiguous.

---

### Post by void.pointer on 2018-10-22
So I know I've gone over a lot here but let me simplify:

Forget docker for the moment. Right now I'm just trying to see if everything is good in Ubuntu Server by itself. The only issue I see right now is slow speeds with wget which concerns me. Please refer to my code snippets in previous posts for results on that. I tried wget on several files:

[http://ipv4.download.thinkbroadband.com/1GB.zip](http://ipv4.download.thinkbroadband.com/1GB.zip)
[http://speedtest-ca.turnkeyinternet.net/10000mb.bin](http://speedtest-ca.turnkeyinternet.net/10000mb.bin)
[https://speed.hetzner.de/1GB.bin](https://speed.hetzner.de/1GB.bin)

In each case, I get no more than 2MBytes per second downstream bandwidth. As I said before, my ISP is giving me 400Mbps downstream. As far as I can tell, iperf3 is showing good results:

Command:

```

iperf3 -c iperf.scottlinux.com -R -f M -P 10

```

Results:

```

[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  29.6 MBytes  2.96 MBytes/sec    0             sender
[  4]   0.00-10.00  sec  27.7 MBytes  2.77 MBytes/sec                  receiver
[  6]   0.00-10.00  sec  26.5 MBytes  2.65 MBytes/sec    0             sender
[  6]   0.00-10.00  sec  25.0 MBytes  2.50 MBytes/sec                  receiver
[  8]   0.00-10.00  sec  26.9 MBytes  2.69 MBytes/sec    0             sender
[  8]   0.00-10.00  sec  24.5 MBytes  2.45 MBytes/sec                  receiver
[ 10]   0.00-10.00  sec  29.6 MBytes  2.96 MBytes/sec    0             sender
[ 10]   0.00-10.00  sec  27.4 MBytes  2.74 MBytes/sec                  receiver
[ 12]   0.00-10.00  sec  29.4 MBytes  2.94 MBytes/sec    0             sender
[ 12]   0.00-10.00  sec  27.2 MBytes  2.72 MBytes/sec                  receiver
[ 14]   0.00-10.00  sec  26.0 MBytes  2.60 MBytes/sec    0             sender
[ 14]   0.00-10.00  sec  24.1 MBytes  2.41 MBytes/sec                  receiver
[ 16]   0.00-10.00  sec  28.5 MBytes  2.85 MBytes/sec    0             sender
[ 16]   0.00-10.00  sec  26.9 MBytes  2.69 MBytes/sec                  receiver
[ 18]   0.00-10.00  sec  26.8 MBytes  2.68 MBytes/sec    0             sender
[ 18]   0.00-10.00  sec  24.8 MBytes  2.48 MBytes/sec                  receiver
[ 20]   0.00-10.00  sec  22.5 MBytes  2.25 MBytes/sec    0             sender
[ 20]   0.00-10.00  sec  20.4 MBytes  2.04 MBytes/sec                  receiver
[ 22]   0.00-10.00  sec  29.5 MBytes  2.95 MBytes/sec    0             sender
[ 22]   0.00-10.00  sec  27.5 MBytes  2.75 MBytes/sec                  receiver
[SUM]   0.00-10.00  sec   275 MBytes  27.5 MBytes/sec    0             sender
[SUM]   0.00-10.00  sec   255 MBytes  25.5 MBytes/sec                  receiver

```

And `apt update` seems to go pretty fast, as well as installations. It's literally just wget that is slow. But I want an explanation for why it is slow, and if it indicates a problem that's causing everything else (i.e. docker containers) to go slow.

---

### Post by TheFu on 2018-10-22
If docker is involved, that is an important thing, otherwise it is a distraction.

```
10GB file Between linux machine and Windows: >40MB/s
```
Says it isn't a LinuxOS core issue.  Something else is happening.  I'd like to see LAN-based iperf3 data with 920+ Mbps numbers. 

I haven't seen any APT performance data posted, "seems fast" isn't sufficiently accurate. Data in an easy to see format would be appreciated so the differences between the different test scenarios jump out.

If LAN speeds are also slower than can be reasonably expected, then there is something that can be done.
If LAN speeds are as fast as you can expect, then look upstream for the issue. We don't have any control over what other servers on the internet do.

Could your ISP be throttling batch uses?

Could the remote server be throttling?

Could your router be doing QoS?

ISPs claim speeds all the time that they don't provide. Sometimes they reduce batch transfers so that more immediate needs like E911 calls get priority.  Bandwidth is a shared resource and it does drop when all your neighbors are using it too.  If you are paying for a committed amount of bandwidth, then that is different. Complain.  Every residential contract that I've seen is "best effort" only.  Many of the cheaper commercial ISP contracts aren't committed bandwidth either.  Committed bandwidth contracts aren't cheap. They are constantly monitored and validated by the provider.  I am not on a residential ISP, but I don't have committed bandwidth either. During non-peak periods, I usually get MORE bandwidth than my contract states.

I ran an iperf with iperf.scottlinux.com and saw wildly varying results in the same test.  A few sequences were 0.00 Mbps. Only the first interval was even close to my max bandwidth, which is nothing near yours.  The most consistent bandwidth was 7.7Mbps.

Also did this wget:
```
1GB.zip               2%[                    ]  28.09M  1.36MB/s    eta 12m 21s
```
I'm positive they throttle downloads. That's about 10.9 Mbps.

Mixed IPv4 and IPv6 setups have had issues in the past.  I disable IPV6 on all my systems to avoid that issue and some others.

BTW, most network bandwidth is shown in Mbps, not MB/s. Every time I see it here, it is like converting between kmph and mph for me.

---

### Post by volkswagner on 2018-10-23
I'm not sure if presenting my subjective results and comparing to your's will help... but here goes anyway.

If I read the numbers correctly it seems curl is a little slower and may use more system resources (compared to wget).

From my local server (Debian 9) 100Mb connection:
```

--- wordpress.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 33.957/36.030/38.366/1.816 ms

eric@bun4:/tmp$ time wget https://wordpress.org/latest.tar.gz
--2018-10-22 21:07:47--  https://wordpress.org/latest.tar.gz
Resolving wordpress.org (wordpress.org)... 198.143.164.252
Connecting to wordpress.org (wordpress.org)|198.143.164.252|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8743850 (8.3M) [application/octet-stream]
Saving to: &#8216;latest.tar.gz.2&#8217;

latest.tar.gz.2                        100%[===========================================================================>]   8.34M  26.5MB/s    in 0.3s    

2018-10-22 21:07:47 (26.5 MB/s) - &#8216;latest.tar.gz.2&#8217; saved [8743850/8743850]


real	0m0.370s
user	0m0.164s
sys	0m0.156s


eric@bun4:/tmp$ time curl -O https://wordpress.org/latest.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 8538k  100 8538k    0     0  5677k      0  0:00:01  0:00:01 --:--:-- 5677k

real	0m1.568s
user	0m0.160s
sys	0m0.076s

```

From my 100Mb connected vps hosted online
running Ubuntu 16.04.5 LTS:
```


--- wordpress.org ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 1.365/1.461/1.583/0.065 ms


eric@bun4:~$ time wget https://wordpress.org/latest.tar.gz
--2018-10-23 17:04:51--  https://wordpress.org/latest.tar.gz
Resolving wordpress.org (wordpress.org)... 198.143.164.252
Connecting to wordpress.org (wordpress.org)|198.143.164.252|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8743850 (8.3M) [application/octet-stream]
Saving to: &#8216;latest.tar.gz&#8217;

latest.tar.gz                          100%[===========================================================================>]   8.34M  39.9MB/s    in 0.2s    

2018-10-23 17:04:51 (39.9 MB/s) - &#8216;latest.tar.gz&#8217; saved [8743850/8743850]


real	0m0.266s
user	0m0.164s
sys	0m0.056s


eric@bun4:~$ time curl -O https://wordpress.org/latest.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 8538k  100 8538k    0     0  22.5M      0 --:--:-- --:--:-- --:--:-- 22.5M

real	0m0.395s
user	0m0.204s
sys	0m0.072s

```

---

### Post by TheFu on 2018-10-23
But what do you get from the LAN and VPS for [http://ipv4.download.thinkbroadband.com/1GB.zip](http://ipv4.download.thinkbroadband.com/1GB.zip) ?
I bet it is throttled.

---

### Post by void.pointer on 2018-10-23
I tried the wordpress file he linked, I got about 3MB/s. And for the ubuntu iso:

```

user@computer:~$ wget -O /dev/null http://cdimage.ubuntu.com/releases/18.04.1/release/ubuntu-18.04.1-server-amd64.iso
--2018-10-23 16:50:31--  http://cdimage.ubuntu.com/releases/18.04.1/release/ubuntu-18.04.1-server-amd64.iso
Resolving cdimage.ubuntu.com (cdimage.ubuntu.com)... 91.189.88.39, 2001:67c:1360:8001::1d
Connecting to cdimage.ubuntu.com (cdimage.ubuntu.com)|91.189.88.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 749731840 (715M) [application/x-iso9660-image]
Saving to: &#8216;/dev/null&#8217;


/dev/null                                1%[                                                                            ]   8.97M  1.55MB/s    eta 8m 11s

```

I'm getting consistent speeds across all of these tests for wget.

EDIT: I'm not sure what VPS is (unless you mean virtual private server? but I don't have one of those here). If this is some sort of test I can run, where can I read instructions on steps I should take? Thanks.

EDIT2: Someone else requested LAN -> LAN speeds. I'm on a gigabit network, here is what I got (tested between two physical machines on the network; no docker involved):

```

$ iperf3 -c theserver -R -f m -P 10
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   108 MBytes  90.2 Mbits/sec  197             sender
[  4]   0.00-10.00  sec   107 MBytes  89.7 Mbits/sec                  receiver
[  6]   0.00-10.00  sec   109 MBytes  91.1 Mbits/sec  199             sender
[  6]   0.00-10.00  sec   108 MBytes  90.5 Mbits/sec                  receiver
[  8]   0.00-10.00  sec   107 MBytes  90.0 Mbits/sec  176             sender
[  8]   0.00-10.00  sec   107 MBytes  89.5 Mbits/sec                  receiver
[ 10]   0.00-10.00  sec   108 MBytes  90.4 Mbits/sec  220             sender
[ 10]   0.00-10.00  sec   107 MBytes  90.0 Mbits/sec                  receiver
[ 12]   0.00-10.00  sec   108 MBytes  90.4 Mbits/sec  192             sender
[ 12]   0.00-10.00  sec   107 MBytes  89.9 Mbits/sec                  receiver
[ 14]   0.00-10.00  sec   108 MBytes  90.3 Mbits/sec  134             sender
[ 14]   0.00-10.00  sec   107 MBytes  89.9 Mbits/sec                  receiver
[ 16]   0.00-10.00  sec   108 MBytes  90.3 Mbits/sec  228             sender
[ 16]   0.00-10.00  sec   107 MBytes  90.0 Mbits/sec                  receiver
[ 18]   0.00-10.00  sec   107 MBytes  90.1 Mbits/sec  209             sender
[ 18]   0.00-10.00  sec   107 MBytes  89.6 Mbits/sec                  receiver
[ 20]   0.00-10.00  sec   107 MBytes  90.1 Mbits/sec  258             sender
[ 20]   0.00-10.00  sec   107 MBytes  89.6 Mbits/sec                  receiver
[ 22]   0.00-10.00  sec   107 MBytes  90.0 Mbits/sec  185             sender
[ 22]   0.00-10.00  sec   107 MBytes  89.6 Mbits/sec                  receiver
[SUM]   0.00-10.00  sec  1.05 GBytes   903 Mbits/sec  1998             sender
[SUM]   0.00-10.00  sec  1.05 GBytes   898 Mbits/sec                  receiver


iperf Done.

```

So roughly 90% throughput. I guess that's acceptable? Kids are watching netflix so maybe that accounts for the missing 10%.

---

