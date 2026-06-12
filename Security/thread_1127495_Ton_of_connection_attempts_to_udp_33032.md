---
title: "Ton of connection attempts to udp 33032??"
date: 2009-04-16
forum: Security
---

### Post by FiberOptix on 2009-04-16
All of the sudden I'm getting a huge amount of incoming connection attempts on port (udp) 33032. I was reasonably sure that this port was closed and nmapping myself confirmed it. Lots of different hosts but they all seem to be originating from Asia...

Anybody know what could be going on?

---

### Post by brian_p on 2009-04-16
> **FiberOptix said:**
> 

Anybody know what could be going on?

The command you used to discover this and an excerpt from the log would help a diagnosis.

---

### Post by FiberOptix on 2009-04-16
> **brian_p said:**
> The command you used to discover this and an excerpt from the log would help a diagnosis.

Watching kern.log, then starting firestarter and watching these events by the second. I started up wireshark and after filtering out the noise, the data field in these udp packets is really interesing... I just jumped to a new AP and I'm still getting hit. 

An excerpt from kern.log

Apr 16 14:57:27 ubuntu kernel: [280176.851992] Inbound IN=wlan0 OUT= MAC=00:aa:00:7e:f9:20:00:1e:58:2e:81:a9:08:00 SRC=85.177.235.130 DST=192.168.0.101 LEN=90 TOS=0x00 PREC=0x00 TTL=115 ID=37050 PROTO=UDP SPT=64086 DPT=33032 LEN=70 
Apr 16 14:57:28 ubuntu kernel: [280178.150107] Inbound IN=wlan0 OUT= MAC=00:aa:00:7e:f9:20:00:1e:58:2e:81:a9:08:00 SRC=88.110.23.151 DST=192.168.0.101 LEN=129 TOS=0x00 PREC=0x00 TTL=115 ID=62319 PROTO=UDP SPT=10183 DPT=33032 LEN=109 
Apr 16 14:57:59 ubuntu kernel: [280209.058784] Inbound IN=wlan0 OUT= MAC=00:aa:00:7e:f9:20:00:1e:58:2e:81:a9:08:00 SRC=89.8.216.69 DST=192.168.0.101 LEN=129 TOS=0x00 PREC=0x00 TTL=108 ID=56133 PROTO=UDP SPT=12378 DPT=33032 LEN=109 
Apr 16 14:58:03 ubuntu kernel: [280212.778681] Inbound IN=wlan0 OUT= MAC=00:aa:00:7e:f9:20:00:1e:58:2e:81:a9:08:00 SRC=212.233.245.11 DST=192.168.0.101 LEN=126 TOS=0x00 PREC=0x00 TTL=106 ID=63705 PROTO=UDP SPT=8455 DPT=33032 LEN=106

---

### Post by FiberOptix on 2009-04-16
Also, I see that my last modified files are: /sbin/udevadm, /sbin/udevsettle, /sbin/vol_id, /sbin/udevd, a lot of /usr/bin/gvfs type files, and arm2hpdl is an interesting one.. 

Rkhunter complains about unhide and unhide-linux26 being modified but when I googled this earlier I saw people commenting this was a common false alarm. It also complains about /usr/bin/dpkg and /usr/bin/dpkg-query and later on when 'Checking /dev for suspicious file types'.

My firewall blocks all inbound connections and I have tcpwrappers set to ALL : PARANOID... I don't know why all of the sudden an entire content would try to connect to a closed udp port, and I was behind a wireless router at the time.

---

### Post by brian_p on 2009-04-16
> **FiberOptix said:**
> Also, I see that my last modified files are: /sbin/udevadm, /sbin/udevsettle, /sbin/vol_id, /sbin/udevd, a lot of /usr/bin/gvfs type files, and arm2hpdl is an interesting one.. 

Which will be due to updates through the package system though, surely?

> Rkhunter complains about unhide and unhide-linux26 being modified but when I googled this earlier I saw people commenting this was a common false alarm. It also complains about /usr/bin/dpkg and /usr/bin/dpkg-query and later on when 'Checking /dev for suspicious file types'.

Rkhunter complains about everything and anything. Does anyone take any notice of it?

> My firewall blocks all inbound connections and I have tcpwrappers set to ALL : PARANOID... I don't know why all of the sudden an entire content would try to connect to a closed udp port, and I was behind a wireless router at the time.

I think iptables logs to kern.log. In your previous post the destination port is 33032. Have you anything running on it?

```
sudo lsof -i :33032
```

Any chance games are involved?

---

### Post by FiberOptix on 2009-04-16
Agree regarding all your points.

> Any chance games are involved?

I have no games installed.

```
sudo lsof -i :33032
```

Gives nothing.  

I have an abundance of logs though, beginning with the aforementioned kern.log as well as wireshark capture, firestarter event lists, etc. The payload of the udp packets looks very interesting. About 3.5 GB of incoming data all in all, during a relatively short time period. The fact that all the inbound traffic followed me from one AP to the next allows me to deduce one single cause, and it don't believe it's a false alarm. I'm a bit hesitant to go into depth about that, so why don't you send me a pm if you're interested?

---

