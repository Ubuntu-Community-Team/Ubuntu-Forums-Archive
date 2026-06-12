---
title: "Detecting &amp; Removing Possible Virus"
date: 2009-04-19
forum: Security
---

### Post by fast-Eddie on 2009-04-19
Hi All,

Looking through my Firestarter log I see something on port 6969 that has been repeatedly attempting outbound connectivity for the last day. Its something called 'GateCrasher' and I looked it up on Google and it seems to be a trojan. 

I'm using Ubuntu 8.10 and am pretty much a beginner with it. Can someone please explain how I can detect/locate this problem application/service and also how to get rid of it??

Thanks.

---

### Post by befana on 2009-04-19
Install rkhunter or chkrootkit through Synaptic and scan to make sure you have or not a trojan.
To scan with rkhunter, type in CLI:

sudo rkhunter --check

and to scan with chkrootkit:

sudo chkrootkit

---

### Post by thewolfman on 2009-04-19
An alternate would be to install "Avast" antivirus for Linux which is a freebie and is only an "On Demand Scanner" so it will only scan when and where you need/tell it!!.

Good hunting.

---

### Post by brian_p on 2009-04-19
> **fast-Eddie said:**
> 

Looking through my Firestarter log I see something on port 6969 that has been repeatedly attempting outbound connectivity for the last day. Its something called 'GateCrasher' and I looked it up on Google and it seems to be a trojan.

A sight of the log is important in these situations.

> I'm using Ubuntu 8.10 and am pretty much a beginner with it. Can someone please explain how I can detect/locate this problem application/service and also how to get rid of it??


You could try:

```
sudo lsof -i :6969
```

but Windows code will not run in Linux. Do you use torrents?

---

### Post by fast-Eddie on 2009-04-19
I installed and ran rkhunter with the following results:

Rootkit checks...
   Rootkits checked: 109
   Possible rootkits: 0

File properties checks...
   Files checked: 129
   Suspect files: 8

===========================================================

I noticed the following in the output too as it was all scrolling past:

performing file properties checks - a few warnings
Checking for passwd file changes - Warning
Checking /dev for suspicious file types - Warning

Are these normal??

I also tried running the command: 

sudo lsof -i :6969

and it returned nothing.

I don't usually d/l torrents however I tried it for the first time earlier today for about an hour. I am however not currently downloading anything. Could this be causing it??

---

### Post by brian_p on 2009-04-19
> **fast-Eddie said:**
> 

Are these normal??

Yes. Also, rkhunter is very unlikely to be much help to you here.

> I also tried running the command: 

sudo lsof -i :6969

and it returned nothing.

Which tells you there is no open file on that port. See

```
man lsof
```

```
sudo netstat -tulpan
```

might also be useful.

> I don't usually d/l torrents however I tried it for the first time earlier today for about an hour. I am however not currently downloading anything. Could this be causing it??

Could be. What client did you use? Run it again and monitor. No log available to see?

---

### Post by fast-Eddie on 2009-04-19
sudo netstat -tulpan didn't seem to return anything out of the ordinary. 

I checked the messages log file for anything with port 6969 and here is some of the output:

Apr 19 16:58:04 e kernel: [45253.304739] Outbound IN= OUT=ra0 SRC=192.168.1.8 DST=91.191.138.3 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=5952 DF PROTO=TCP SPT=53902 DPT=6969 WINDOW=5840 RES=0x00 SYN URGP=0 
Apr 19 16:58:07 e kernel: [45256.304120] Outbound IN= OUT=ra0 SRC=192.168.1.8 DST=91.191.138.3 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=5953 DF PROTO=TCP SPT=53902 DPT=6969 WINDOW=5840 RES=0x00 SYN URGP=0 
Apr 19 16:58:07 e kernel: [45256.304789] Outbound IN= OUT=ra0 SRC=192.168.1.8 DST=91.191.138.7 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=27846 DF PROTO=TCP SPT=39825 DPT=6969 WINDOW=5840 RES=0x00 SYN URGP=0 
Apr 19 16:58:08 e psad: src: 192.168.1.8 signature match: "BACKDOOR GateCrasher Connection attempt" (sid: 147) tcp port: 6969
Apr 19 16:58:08 e psad: scan detected: 192.168.1.8 -> 91.191.138.2 tcp: [6969] flags: SYN tcp pkts: 1 DL: 2
Apr 19 16:58:47 e psad: scan detected: 192.168.1.8 -> 91.191.138.7 tcp: [6969] flags: SYN tcp pkts: 2 DL: 2
Apr 19 16:59:31 e psad: src: 192.168.1.8 signature match: "BACKDOOR GateCrasher Connection attempt" (sid: 147) tcp port: 6969
Apr 19 16:59:31 e psad: scan detected: 192.168.1.8 -> 91.191.138.5 tcp: [6969] flags: SYN tcp pkts: 1 DL: 2


I'm also running port scan attack detector (psad) and you'll see in the above output that this program noticed a signature match.

---

### Post by lovinglinux on 2009-04-19
The problem is that Firestarter doesn't really know what's going on. It relies on port number to detect activity and it will give you the service most likely to be using the port. A blocked connection on port 6969 is probably a torrent client trying to connect to a tracker and Firestarter doesn't know that.

Analyzing your log gives us the confirmation. The IP address it is trying to connect is from The PIrate Bay.

```
% This is the RIPE Whois query server #2.
% The objects are in RPSL format.
%
% Rights restricted by copyright.
% See http://www.ripe.net[whois][trace][reverse ip]/db/copyright.html

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag

% Information related to '91.191.138.0[whois][trace][reverse ip] - 91.191.138.63[whois][trace][reverse ip]'

inetnum:        91.191.138.0[whois][trace][reverse ip] - 91.191.138.63[whois][trace][reverse ip]
netname:        SE-TPB
descr:          TPB, Stockholm
country:        SE

```

When I switched from Windows to Ubuntu I was also very concerned about Firestarter logs. I don't use it anymore. Now I use my own rules for iptables (the real firewall behind Firestarter and other firewall managers) , IPTState for monitoring connections and real time log monitoring of blocked connections using the *tail* command. It's safer than using Firestarter. There are reports that running Firestarter for connection monitoring all the time could be a security risk, due to required root privileges. Just to let you know, Firestarter is just a firewall manager, which means it is just a tool that allow you to create iptables rules without knowing the commands. Once you configure Firestarter, you can and should close it, because the real firewall will be running in the background. I'm not sure these rules will stick after reboot, but you can check using the command *iptables -L*.

I recommend reading [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

---

### Post by brian_p on 2009-04-19
> **fast-Eddie said:**
> 

I'm also running port scan attack detector (psad) and you'll see in the above output that this program noticed a signature match.

Your log confirms a connection **out** to port 6969. The malware you were concerned about (which to remind you, only runs on Windows) would have received a connection **in** on port 6969. As lovinglinux has demonstrated, we are looking at torrent activity.

---

### Post by fast-Eddie on 2009-04-19
Thanks brian_p & lovinglinux for your help with this. You've both provided some good insight into this issue for my future reference.

---

