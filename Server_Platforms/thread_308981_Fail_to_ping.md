---
title: "Fail to ping"
date: 2006-11-29
forum: Server Platforms
---

### Post by satimis on 2006-11-29
Hi folks,

Ubuntu-6.06-LAMP-server-amd64
Dynamic IP

I have satimis.homelinux.com registered with DYNDNS.ORG.  I also have ddclient installed and running on this server.

$ dpkg -l | grep ddclient```

ii  ddclient                                         3.6.2-6ubuntu1              Update dynamic IP address at DynDNS.org

```

IP address was updated on DYNDNS.ORG server whenever this server reconnected.  I have it confirmed on login DYNDNS.ORG website.

But failed to ping my domain.

$ sudo ping -c 3 satimis.homelinux.com```

PING satimis.homelinux.com (58.152.161.53) 56(84) bytes of data.

--- satimis.homelinux.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

```

iptables has been stopped.

Please advise how fix this problem.


B.R.
satimis

---

### Post by iBix on 2007-04-02
i had the same problem, i thought it was because i had mistakenly firewalled loopback interface, but if you still have the same problem without iptables running then i don't know what is causing this... i would like to know though.

---

### Post by rickyjones on 2007-04-02
Is there a router on your connection that your server is behind? This might be blocking the ping command as well.

---

### Post by iBix on 2007-04-02
no not on my case. There is a router, but i have been able to ping my own sytem before.

---

### Post by iBix on 2007-04-02
hmm, my problem seemed to vanish when i [flushed all of iptables rules]("http://doc.gwos.org/index.php/IptablesFirewall#The_flush_script"). 

i also had similar  a problem with a webmin installation i started today as a solution for this problem. after i removed all the iptables rules i could both ping my own machine and log in to my webmin account. voila! 

now i can proceed in setting up the iptables through the webmin interface, hope this is a bit easier than the commandline option :)

---

