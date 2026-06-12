---
title: "PSAD is sending my hundreds of emails after UFW was enabled"
date: 2011-10-07
forum: Security
---

### Post by pcarlos853 on 2011-10-07
Hello, 

I am running a Ubuntu 10.04 (10.192.81.25) server. I installed psad a month ago and today I after I enabled UFW I started a getting bunch of emails. The emails look like:

```
  =-=-=-=-=-=-=-=-=-=-=-= Fri Oct  7 13:45:24 2011 =-=-=-=-=-=-=-=-=-=-=-=
   
   
           Danger level: [2] (out of 5)
   
           icmp packets: [2]
         iptables chain: OUTPUT (prefix "[UFW AUDIT]"), 1 packets
         iptables chain: OUTPUT (prefix "[UFW ALLOW]"), 1 packets
   
                 Source: 10.192.81.25
                    DNS: [No reverse dns info available]
               OS guess: Linux (2.4.x kernel)
   
            Destination: 10.192.81.22
                    DNS: [No reverse dns info available]
   
     Overall scan start: Fri Oct  7 13:45:24 2011
     Total email alerts: 5
        Syslog hostname: UbuntuSvr-1
   
           Global stats: chain:   interface:   TCP:   UDP:   ICMP:  
                         OUTPUT   eth0         0      0      2      
   
   
  [+] ICMP scan signatures:
   
     "ICMP PING"
         sid:       384
         chain:     OUTPUT
         packets:   2
         classtype: misc-activity
  
```I am running nagios3 on the box as well. I think that psad is reporting because Nagios3 is pinging servers on our lan. Today I enabled UFW on the system around 10am and that is when the emails started:

```
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere

22                         ALLOW OUT   Anywhere
80/tcp                     ALLOW OUT   Anywhere
3389                       ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere
587                        ALLOW OUT   Anywhere

```How can I run psad and nagios on the same box?

Thanks,
Carlos

---

### Post by bodhi.zazen on 2011-10-07
Whitelist your niagios box

---

### Post by pcarlos853 on 2011-10-08
Sorry still somewhat new to Linux. How would I white-list nagios?

Thanks,
Carlos

---

### Post by bodhi.zazen on 2011-10-08
See your configuration file, it is well commented.

See also /etc/psad/auto_dl

See also [http://bodhizazen.net/Tutorials/psad](http://bodhizazen.net/Tutorials/psad) or the man page for pasd.

There are many options and only you can configure psad the way you wish.

---

### Post by pcarlos853 on 2011-10-12
Bodhi.Zazen,

I added 

```
 MY-IP       0;          # Ignore this IP.
127.0.0.1          0;          # Ignore localhost

```

So far it seems to have solved the problem. Thanks for your help (and all the Ubuntu security guides you have written)

Carlos

---

### Post by bodhi.zazen on 2011-10-12
> **pcarlos853 said:**
> Bodhi.Zazen,

I added 

```
 MY-IP       0;          # Ignore this IP.
127.0.0.1          0;          # Ignore localhost

```

So far it seems to have solved the problem. Thanks for your help (and all the Ubuntu security guides you have written)

Carlos

Perfect. IMO, with security, it is best to understand what you are doing.

---

