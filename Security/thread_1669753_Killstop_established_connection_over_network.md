---
title: "Kill/stop established connection over network"
date: 2011-01-18
forum: Security
---

### Post by rainbow99984 on 2011-01-18
Hi,
  I'm running Ubuntu 10.10 
Q1. while I did netstat, I saw few unwanted connections running on, is there any way to kill them?
Q2. I work on a Local Network some time people connect to my system over ssh/ftp as login is shared/common between team, Is there any way to prevent this sort of login until I allow which machine can login like this.
Thanks,
Rahul

---

### Post by HermanAB on 2011-01-18
Something like this:
iptables -I -i eth0 -s 1.2.3.4 -j DROP

---

### Post by rainbow99984 on 2011-01-20
Thanks though one question, I'm some what confused can i use local address instead of ip address like normally i have stat as:

Proto Recv-Q Send-Q Local Address           Foreign Address         State   
tcp     0      0     rahul:48688            web-proxy.abc:3128    ESTABLIS

in all the listing i just want to kill it. I can not use the foreign address here ie web-proxy.abc:3128 as this is used in other communications as well so without droping others is it possible to just drop this.
Thanks,
Rahul

---

### Post by HermanAB on 2011-01-21
Hmm, I would run tcpdump to see what it is connecting to and then block it using the distant IP address.

---

### Post by pl@yer on 2011-01-21
> **rainbow99984 said:**
> Hi,
  I'm running Ubuntu 10.10 
Q1. while I did netstat, I saw few unwanted connections running on, is there any way to kill them?

```

steve@steve-HP-Compaq-dc7100-CMT-PJ075UA:~/Downloads/hideout$ netstat -atunop|grep -i esta
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
tcp        0      0 142.134.145.248:5226    142.134.124.237:22      ESTABLISHED 947/ssh          keepalive (7200.49/0/0)
tcp        0      0 142.134.145.248:5225    142.134.124.237:22      ESTABLISHED 862/ssh          keepalive (7167.72/0/0)

```
Note the 2 ssh connections have different PIDs (947,862) just kill the PID for the connection you want to drop.

> 
Q2. I work on a Local Network some time people connect to my system over ssh/ftp as login is shared/common between team, Is there any way to prevent this sort of login until I allow which machine can login like this.
Thanks,
Rahul

I would suggest you use something to configure iptables on your system (maybe guarddog). You could use this script to create a chain and allow only certain systems (FTPSSH_ALLOW) to connect. Like I said I suggest you not use this script...instead use something to configure your iptables.

```

FTPSSH_ALLOW="192.168.1.12 192.168.1.14 192.168.1.111"
iptables -N FTPSSH
 
iptables -I INPUT -p tcp --syn --dport 22 -j FTPSSH
iptables -I INPUT -p tcp --syn --dport 21 -j FTPSSH
iptables -I INPUT -p tcp --syn --dport 20 -j FTPSSH
 
## FTPSSH ALLOW
for systs in $FTPSSH_ALLOW; do
    iptables -A FTPSSH -s $systs -j ACCEPT
done

iptables -A FTPSSH -j REJECT

```

---

