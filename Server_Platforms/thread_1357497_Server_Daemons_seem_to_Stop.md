---
title: "Server Daemons seem to Stop"
date: 2009-12-17
forum: Server Platforms
---

### Post by Matuku on 2009-12-17
I'm having some very odd problems with my Ubuntu Server, which I yesterday did a fresh install of 9.10 on; it seems that several of the daemons stop working after around 10 minutes of inactivity.

The two I've definitely noticed are sshd (after 10 minutes trying to log in gives a "No route to host" message) and acpid (after a while pressing the power button doesn't cause it to initiate shutdown as it should). Has anyone heard of anything like this before?

---

### Post by cariboo on 2009-12-17
Try:

```
sudo apt-get -f install
```

to install any missing dependencies.

---

### Post by oneloveamaru on 2009-12-17
The program wouldn't be fully installed if dependencies were missing, thus wouldn't be possible to start. If for some odd reason this were possible, openssh-server (sshd) dependencies are all part of the base install.

Are you sure sshd is actually stopping and not the computer losing its network connection? Have you checked /var/log/syslog ?

---

### Post by BkkBonanza on 2009-12-17
This definitely sounds more like a network issue than sshd stopped. If sshd stopped and your network was ok then you would get a "connection refused" because nothing is answering on port 22.

acpid may be an unrelated issue. The way to check if sshd is running is use the command "ps afx" and see if sshd and acpid are listed. If they are then something else is going on. Next step is "netstat -lntp" and make sshd is listed as listening on the port you connect to.

And for sure check your logs for any messages about problems. 

less /var/log/messages

in addition to suggestion in post above.

There is some hardware that acpid can have problems on so that could just be something like that. Unfortunately I don't know how you track that down. Probably google is best bet, like "acpid ubuntu mfr/model of mainboard" etc.

---

### Post by Matuku on 2009-12-17
The only reason I think it can't be network related is because there was no issue before I upgraded.

When running "sudo netstat -lntp" I get:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      949/mysqld      
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1009/vsftpd     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      795/sshd        
tcp6       0      0 :::80                   :::*                    LISTEN      1081/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      795/sshd        

```

Should sshd be listed twice?

---

### Post by Matuku on 2009-12-17
Also, what would I be looking for in /var/log/syslog to indicate a connection error?

---

### Post by BkkBonanza on 2009-12-17
Yes, sshd would be twice - one for IPv4 and one for IPv6. Well, at least it always has for mine. I'm not sure what you would find in the logs. Just browse for something that seems it may be related or wrong.

Anyway sshd appears to be up and listening. So I would make sure a firewall isn't causing issues. 

sudo iptables -L

will show if rules may be preventing connections. Some firewalls provide a test mode that times out for debugging. Usually it reverts to no rules though not the opposite.

At the point when you cannot connect any more you would want to try network tests.
"No route to host" is generally a message from the system you are on saying it cannot get to the destination - not the destination saying it has a problem. So maybe start with ping and traceroute. That may indicate why the route fails and where.

---

### Post by Matuku on 2009-12-18
"sudo iptables -L" gives:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

I'll try the ping/traceroute when it fails.

---

### Post by Matuku on 2009-12-18
Interesting; traceroute doesn't seem to give anything out at all:

```

smith@smith-laptop:~$ traceroute 192.168.1.8
traceroute to 192.168.1.8 (192.168.1.8), 30 hops max, 60 byte packets
 1  smith-laptop (192.168.1.44)  3009.378 ms !H  3009.358 ms !H  3009.319 ms !H
smith@smith-laptop:~$

```

(192.168.1.8 is the server, 192.168.1.44 is the laptop I'm trying to ssh from)

I'm not entirely sure what the output of traceroute should look like but this doesn't seem to be doing anything as far as I can tell?

---

### Post by BkkBonanza on 2009-12-18
iptables looks fine.
traceroute indicates not even single hop, so only means it's blocked.
!H next to times indicates host not reachable.
how is your network connected together? your laptop and server connected via router only?
there is some networking error. have no idea why it works for 10 minutes though and then stops. I guess I would check over all connections, cables, router options and config. try alternate arrangements hoping to see a problem - like use a switch not router or even direct connect with X cable maybe. try to eliminate possible reasons.
see if the reverse path still works, ie. trace from server to laptop. just looking for clues.

---

### Post by Matuku on 2009-12-18
Does not even a single hop mean it's not passing through the router? Perhaps it is a problem with the wireless part of the network rather than the wired; the laptop is connected to the router wirelessly; from there the router is plugged into a switch and from the switch into the server and a desktop.

---

### Post by oneloveamaru on 2009-12-18
> **BkkBonaza said:**
> iptables looks fine.
traceroute indicates not even single hop, so only means it's blocked.
!H next to times indicates host not reachable.
how is your network connected together? your laptop and server connected via router only?
there is some networking error. have no idea why it works for 10 minutes though and then stops. I guess I would check over all connections, cables, router options and config. try alternate arrangements hoping to see a problem - like use a switch not router or even direct connect with X cable maybe. try to eliminate possible reasons.
see if the reverse path still works, ie. trace from server to laptop. just looking for clues.

You won't see any hops because you are running a traceroute on the SAME network. Hops indicate a gateway.

I'm not sure what you want to look for in syslog, anything that would indicate your network connection going down. Have you tried a different cable?

When you can't SSH into the server, have you tried SSH'ing from the server to another computer? You need to test network connection in and out when its acting up. Troubleshooting when it's working won't give you anything.

---

### Post by BkkBonanza on 2009-12-18
It's behaving as though you are on different subnets for the wifi and the LAN. What's strange is that it works and then stops after some time. Other than the time issue it seems like a misconfiguration.

You should be getting a hop indicating the router and then one for the destination server. At least that's what I get here when I try it. At the very least you'll get the target without !H in the output.

Perhaps thew wifi is acting up. Can you get anywhere else from the laptop when the server is not reachable? ie. is it the whole wordl that is unreachable? It's a bit hard to guess at it form here so you'll have to try various traces between server, desktop, laptop, router, internet until you get a clear idea of what's talking before/after the problems starts.

---

### Post by Matuku on 2009-12-23
Found the apparent source of the issue; it appears the new kernel is causing problems with intel onboard cards when no monitor is plugged in (after around 10 minutes which is when it tries to send it to sleep or some such I'd hazard). This is one of the most bizarre bugs I've had the misfortune to encounter.

[http://ubuntuforums.org/showthread.php?t=1311112](http://ubuntuforums.org/showthread.php?t=1311112)

---

