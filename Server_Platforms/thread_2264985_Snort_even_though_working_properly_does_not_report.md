---
title: "Snort even though working properly does not report majority of rules"
date: 2015-02-11
forum: Server Platforms
---

### Post by AcLime on 2015-02-11
I have installed Snort 2.9.7.0 and it does not detect majority of attacks, such as nmap port scans, downloading exe files, opening documents containing keyword "root".

I use Snort together with Pulled Pork and Barnyard2. Everything seems to function and I can see alerts on the website that is powered by BASE.

The problem is that I can only trigger 3 different alerts. Everything else is simply not detected. I want obviously to be able to get alerts when someone performs port scanning, trying to attempt to perform DDOS attack and so on. This I cannot trigger. Do I have to enable something somewhere?...

I have made my own local.rules file, which contains a single rule - monitoring of ICMP echo packets.

Pulled Pork does show that it has downloaded over 20000 rules and over 5000 rules are enabled. This can be seen in snort.rules file, which I included in snort.conf file.

The 3 alerts I am able to trigger are:

stream5: TCP Small Segment Threshold Exceeded (this is due to my old Win SCP client)
ssh: Protocol mismatch (this is due to my old Putty client)
ICMP test (my own rule from local.rules)
My snort.conf can be found on the following website (had to move it there, because i reached max chars list): [https://paste.ee/p/RTUgY](https://paste.ee/p/RTUgY)

My pulledpork.conf can be found on the following website: [https://paste.ee/p/ixZqW](https://paste.ee/p/ixZqW)

My local.rules looks like this (which does work):

```
alert icmp any any -> $HOME_NET any (msg:"ICMP test"; sid:10000001; rev:001;)
```

---

