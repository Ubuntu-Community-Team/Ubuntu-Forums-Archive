---
title: "External snmp acces fails."
date: 2006-12-07
forum: Server Platforms
---

### Post by Peturrr on 2006-12-07
There seem to be quite little information available on the forums about using/configuring snmp/snmpd. I am in the process of getting it to work properly, but I've stumbled upon a frustating problem.

I cannot acces the snmp data when connecting from another machine.

It looks like Ubuntu is firewalling my connection somehow. 
*snmpwalk -c* *foo -v 1 localhost *gives me all the data
*snmpwalk -c foo -v 1 10.0.0.2  *from my 10.0.0.1 machine gives me : ```
Timeout: No Response from 10.0.0.2
```The PC's are directly connected with a network cable. Have ssh connectivity, ping etc. 

I have searched the internet and am now using the most simple configuration possible: 
```
rocommunity  foo 10.0.0.1 
rocommunity  foo localhost
```

Strange thing is: It works correctly when I start snmpd directly from the commandline with: ```
sudo snmpd -f -Le -d
``` 

In /etc/default/snmpd I found ```
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'
``` So i guess snmpd binds itself to 127.0.0.1 . This must be able to be configured without editing the default settings I guess.

Is there somebody who got this working?

---

### Post by Peturrr on 2006-12-07
It seems to be that the default configuration is in Ubuntu is not 'correct'.

According to the snmpd manuals/FAQ snmpd is normally binded to 0.0.0.0 e.q. listens on all adresses. In Ubuntu this configuration is set to 127.0.0.1 in /etc/default/snmpd

```
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'
```

Changing this to ```
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 0.0.0.0'
``` solved every problem I had with remote connecting. 

So if anybody is looking for a solution for the problem of not being able to connect remote to a snmp enabled ubuntu. Change the 127.0.0.1 to 0.0.0.0 in the file /etc/default/snmpd

I will check if this default file is indeed changed in Ubuntu, and if so I will file a bug report or a RFC.

---

### Post by Peturrr on 2006-12-07
I received a response from Dave Shield, a developer on Net-SNMP.
It is indeed the /etc/default/snmpd line with 127.0.0.1 that is causing the problem. 

> A better solution would be to drop '127.0.0.1' altogether. 
> It's an defensible configuration, but it's not one that many distributions use. 
It's certainly not something that we ship outselves.
I really think this default configuration is something that should be changed. It should be a default setting in /etc/snmp/snmpd.conf instead of in /etc/default/snmpd. I will post a bug report.

---

