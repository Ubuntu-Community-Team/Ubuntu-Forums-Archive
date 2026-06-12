---
title: "Interpreting netstat output"
date: 2011-11-04
forum: Security
---

### Post by Azrael84 on 2011-11-04
Hi,

Could anyone kindly help me interpret the following: 

```
 Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      2029/sendmail: MTA:
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1100/cupsd      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      2029/sendmail: MTA:
tcp        0      0 192.168.0.2:52065       4.79.142.192:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:42912       4.79.142.202:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:52063       4.79.142.192:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:54852       209.85.169.106:80       TIME_WAIT   -               
tcp        0      0 192.168.0.2:42921       4.79.142.202:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:42920       4.79.142.202:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:42909       4.79.142.202:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:42908       4.79.142.202:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:42918       4.79.142.202:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:42919       4.79.142.202:443        TIME_WAIT   -               
tcp        0      0 192.168.0.2:52066       4.79.142.192:443        TIME_WAIT   -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      1100/cupsd  
```output from netstat -atpvn.I know the 127.0.0.1 are local  and nothing to worry about, but what are all the other tcp connections? in particular does the last one mean cups is listening to the world at large?

---

### Post by CharlesA on 2011-11-04
The ones in TIME_WAIT are more then likely connections from your web browser - port 80 is HTTP and port 443 is HTTPS.

The others are fine.

::1 is loopback in IPv6 - the same as 127.0.0.1 in IPv4

---

### Post by Azrael84 on 2011-11-04
> **CharlesA said:**
> The ones in TIME_WAIT are more then likely connections from your web browser - port 80 is HTTP and port 443 is HTTPS.

The others are fine.

::1 is loopback in IPv6 - the same as 127.0.0.1 in IPv4

Thanks a lot.

---

### Post by dfreer on 2011-11-06
> **CharlesA said:**
> The ones in TIME_WAIT are more then likely connections from your web browser - port 80 is HTTP and port 443 is HTTPS.

This. I'm guessing, but you probably ran the command like so:
```
netstat -ntlpa
```

The -a in particular shows not just ports being listened on, but also established connections (i.e. your internet browsing sessions). Note that your computer has opened a random high-level port to connect to the web server's TCP ports 80 ([www.google.com](www.google.com)) and 443 ([http://www.grc.com](http://www.grc.com)). The outgoing request from the random high-level port will be a SYN packet, and when the web server replies it will use a SYN/ACK packet to the same port. If you use iptables as your firewall, and use state-based firewall rules, this is important to know. It allows you to accept only ESTABLISHED and RELATED connections from ports 80 and 443, so that you can browse the internet normally without having to know which port your browser is currently using (randomized for security reasons). The TIME_WAIT means "the socket is waiting after close to handle packets still in the network" (from the man page). 
You might also try running netstat with the -u argument:
```
netstat -ntulpa
```
So that you can see UDP information as well, if you didn't already.

---

### Post by The Cog on 2011-11-06
> in particular does the last one mean cups is listening to the world at large?
Yes. 
Since you are behind a NAT router, connections from the internet to CUPS can only happen if the router performs port forwarding, relaying connections addressed to itself:631 to your computer, but it is listening for incoming connections and your local network will be able to connect to CUPS.

Listening on :::* means it is listening on all IPv4 and IPv6 addresses that the PC might have.

**Correction:** No. See CharlesAs' correction below. I was looking at the wrong column. Slaps head!

---

### Post by CharlesA on 2011-11-06
> **The Cog said:**
> Yes. 
Since you are behind a NAT router, connections from the internet to CUPS can only happen if the router performs port forwarding, relaying connections addressed to itself:631 to your computer, but it is listening for incoming connections and your local network will be able to connect to CUPS.

Listening on :::* means it is listening on all IPv4 and IPv6 addresses that the PC might have.

In that case, :::* was the foreign address and ::1 was the local, so it's only listening on the IPv6 loopback address. :)

---

### Post by Azrael84 on 2011-11-07
Thanks again.

I'm slightly confused as my ufw rules are :

```
To                         Action      From
--                         ------      ----
51413/udp                  ALLOW       Anywhere
51413/tcp                  ALLOW       Anywhere
Anywhere                   DENY        Anywhere
51413/udp                  ALLOW       Anywhere (v6)
51413/tcp                  ALLOW       Anywhere (v6)
Anywhere (v6)              DENY        Anywhere (v6)

53/udp                     ALLOW OUT   Anywhere
5222,5223/tcp              ALLOW OUT   Anywhere
21,80,443,587,993/tcp      ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
5222,5223/tcp              ALLOW OUT   Anywhere (v6)
21,80,443,587,993/tcp      ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)

```

the 51413 being for transmission, 5222,5223(gtalk). Yet spotify is working just fine, as well as liferea etc, and netstat seems to reveal they are connecting on various ports, how can this be when I have deny out/in except these few ports above?

---

### Post by OpSecShellshock on 2011-11-07
> **Azrael84 said:**
> Thanks again.

I'm slightly confused as my ufw rules are :

```
To                         Action      From
--                         ------      ----
51413/udp                  ALLOW       Anywhere
51413/tcp                  ALLOW       Anywhere
Anywhere                   DENY        Anywhere
51413/udp                  ALLOW       Anywhere (v6)
51413/tcp                  ALLOW       Anywhere (v6)
Anywhere (v6)              DENY        Anywhere (v6)

53/udp                     ALLOW OUT   Anywhere
5222,5223/tcp              ALLOW OUT   Anywhere
21,80,443,587,993/tcp      ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
5222,5223/tcp              ALLOW OUT   Anywhere (v6)
21,80,443,587,993/tcp      ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)

```the 51413 being for transmission, 5222,5223(gtalk). Yet spotify is working just fine, as well as liferea etc, and netstat seems to reveal they are connecting on various ports, how can this be when I have deny out/in except these few ports above?

Your computer is what is referred to as the client-side. Client-side connections will use whatever high port is available to establish connections to the external sites, which is called server-side.

I'm fairly certain that since liferea is just a feed reader, it's connecting to port 80 on the server side, which you have allowed. Spotify is likely using at least 80 while running and possibly 443 when logging in (I'd hope). Outbound rules apply to the server-side ports, so those connections are allowed.

---

### Post by Azrael84 on 2011-11-07
netstat when just it's just spotify running gives:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:25384           0.0.0.0:*               LISTEN      2518/spotify    
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:4370          0.0.0.0:*               LISTEN      2518/spotify    
tcp        0      0 0.0.0.0:57621           0.0.0.0:*               LISTEN      2518/spotify    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:4380          0.0.0.0:*               LISTEN      2518/spotify    
tcp        0      1 192.168.0.2:53520       31.53.168.140:39619     SYN_SENT    2518/spotify    
tcp        0      1 192.168.0.2:49969       85.56.234.175:46279     SYN_SENT    2518/spotify    
tcp        0      0 192.168.0.2:49223       216.137.57.227:80       ESTABLISHED 2518/spotify    
tcp        0      0 192.168.0.2:37789       209.85.169.102:80       ESTABLISHED 2518/spotify    
tcp        0      1 192.168.0.2:56198       79.159.76.152:25154     SYN_SENT    2518/spotify    
tcp        0      1 192.168.0.2:33845       86.22.72.138:40354      SYN_SENT    2518/spotify    
tcp        0      1 192.168.0.2:42133       85.53.186.214:48542     SYN_SENT    2518/spotify    
tcp        0      0 192.168.0.2:37577       78.31.8.49:80           ESTABLISHED 2518/spotify    
tcp        0      0 192.168.0.2:52273       216.137.57.105:80       ESTABLISHED 2576/gvfsd-http 
tcp6       0      0 ::1:631                 :::*                    LISTEN
```

I take it this means spotify has established on http 80 as you said, as the SYN_SENT just means it's attempting to establish on these other random high ports? should I allow it some other port to clear port 80 for http use? or will this no affect my browsing aversely anyway?

---

### Post by OpSecShellshock on 2011-11-07
If the application is working properly and you can listen to music with no problems, then I wouldn't change anything.

---

