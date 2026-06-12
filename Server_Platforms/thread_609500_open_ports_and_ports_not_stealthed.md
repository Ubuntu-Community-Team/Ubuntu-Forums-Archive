---
title: "open ports and ports not stealthed"
date: 2007-11-11
forum: Server Platforms
---

### Post by chauster on 2007-11-11
Hi, I'm new to linux and barely started using ubuntu for about a week now.  I just noticed that some of my ports are opened and most of them are not stealthed.  I have iptables running and don't have any server apps installed.

Is it normal to have these ports open and not stealthed?  If not, how do I fix this?  Thanks in advance.


> 
----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2007-11-11 at 07:59:30

Results from scan of ports: 0-1055

    3 Ports Open
 1051 Ports Closed
    2 Ports Stealth
---------------------
 1056 Ports Tested

Ports found to be OPEN were: 23, 443, 992

Ports found to be STEALTH were: 80, 135

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

----------------------------------------------------------------------


---

### Post by Frak on 2007-11-11
This is normal, but install [firestarter]("apt:firestarter") and configure it to not respond to requests; this can lead to problems though.

---

### Post by stimpack on 2007-11-11
They are very strange ports to have open for someone new to linux, you are running telnet and https servers?. Open telnet, is really bad if you don't know what you are doing and dont have a strong password..

Like Frak said, get Firestarter as soon as possible. Being behind a router is also nice.

---

### Post by HermanAB on 2007-11-11
Note that open ports paranoia is a Windows thing, because on Windows you don't know what servers Microsoft is running and their network stack is a huge mess.

On Linux, 'ps-e' will show you what is running, so iptables (netfilter) is only required to remove malicious packets, don't worry about ports, since if the service isn't running, nothing can connect to it, and if it is running, then you probably want to connect to it...

Cheers,

Herman

---

### Post by chauster on 2007-11-11
Not sure why these are open.  I don't have a telnet server / https server installed.  Is there a command to check which programs are using these ports (if any)?

Thanks!

---

### Post by Frak on 2007-11-11
> **chauster said:**
> Not sure why these are open.  I don't have a telnet server / https server installed.  Is there a command to check which programs are using these ports (if any)?

Thanks!
firestarter will tell you.

---

### Post by chauster on 2007-11-11
Currently firestarter shows that I have no active connections and no policies (inbound & outbound) in the GUI.

---

### Post by steve.horsley on 2007-11-11
**sudo netsat -plntu** 
will tell you which ports are open and by which process.

---

### Post by CanonKen on 2007-11-11
Found this on Shields up - might be of some help

Port 23
Name: 	telnet
Purpose: 	Telnet
Description: 	
Telnet is one of the earliest, original protocols of the Internet. A machine offering Telnet services is essentially offering to accept an "across the Internet" remote console terminal connection from any client device. This makes Telnet quite powerful and, without proper security, a significant security concern.

Port 443

Name: 	https
Purpose: 	http protocol over TLS/SSL
Description: 	
This port is used for secure web browser communication. Data transferred across such connections are highly resistant to eavesdropping and interception. Moreover, the identity of the remotely connected server can be verified with significant confidence. Web servers offering to accept and establish secure connections listen on this port for connections from web browsers desiring strong communication security.

Once established, web browsers inform their users of these secured connections by displaying an icon — a padlock, an unbroken key, etc. — in the status region of their window.

Port 993
Name: 	telnets
Purpose: 	telnet protocol over TLS/SSL

---

### Post by HermanAB on 2007-11-11
If there is no service listening on a port then there will be no response when the port is tested, so any test result is quite meaningless.

---

### Post by chauster on 2007-11-11
This is the output, does it look right?  Don't really know what to make of it.  Thanks!

**sudo netstat -plntu**

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:39266           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     5561/smbd           
tcp        0      0 0.0.0.0:59214           0.0.0.0:*               LISTEN     4641/rpc.statd      
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4622/portmap        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5368/cupsd          
tcp        0      0 0.0.0.0:46042           0.0.0.0:*               LISTEN     5522/rpc.mountd     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     5561/smbd           
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          4641/rpc.statd      
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          5522/rpc.mountd     
udp        0      0 0.0.0.0:32772           0.0.0.0:*                          5699/avahi-daemon:  
udp        0      0 192.168.1.4:137         0.0.0.0:*                          5559/nmbd           
udp        0      0 0.0.0.0:137             0.0.0.0:*                          5559/nmbd           
udp        0      0 192.168.1.4:138         0.0.0.0:*                          5559/nmbd           
udp        0      0 0.0.0.0:138             0.0.0.0:*                          5559/nmbd           
udp        0      0 0.0.0.0:68              0.0.0.0:*                          6248/dhclient       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          5699/avahi-daemon:  
udp        0      0 0.0.0.0:1001            0.0.0.0:*                          4641/rpc.statd      
udp        0      0 0.0.0.0:111             0.0.0.0:*                          4622/portmap        

```

**sudo iptables -L**

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  Wireless_Broadband_Router.home  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  Wireless_Broadband_Router.home  anywhere            
ACCEPT     esp  --  xx-xxx-xxx-xxx.ded.pacbell.net  anywhere            
ACCEPT     udp  --  xx-xxx-xxx-xxx.ded.pacbell.net  anywhere            multiport sports isakmp,10000 
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.1.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             localhost           
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  new-host.home        Wireless_Broadband_Router.home tcp dpt:domain 
ACCEPT     udp  --  new-host.home        Wireless_Broadband_Router.home udp dpt:domain 
ACCEPT     esp  --  anywhere             xx-xxx-xxx-xxx.ded.pacbell.net 
ACCEPT     udp  --  anywhere             xx-xxx-xxx-xxx.ded.pacbell.net multiport dports isakmp,10000 
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             localhost           
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere

```

---

### Post by steve.horsley on 2007-11-12
We have conflicting information here. First you say you "don't have any server apps installed", but your process list shows smbd to be running (and listening on ports 139 and 445).  Second, your first post says ports 23 and 443 are open, yet netstat says they're not. 

Now it's possible that you have been hacked and netstat has been modified and is lying to you, but the sambad thing makes me wonder what on earth the truth really is. I don't know. 

You could trying to connect to port 23 yourself to see if its really open. This command:
**telnet 127.0.0.1 23**
should get you a connection refused message. If your connection is accepted then you really are in trouble and netstat is lying to you. If that's the case, a re-install will be needed. If you get connection refused, then your original port scan was wrong for some reason - wrong IP address typed in, perhaps?

P.S.
Those policies acepting encrypted connections from xx-xxx-xxx-xxx.ded.pacbell.net - diid you put those in the firewall? If so then I think everything is looking normal. If not, then I guess you have been hacked and a reinstall is needed.

---

### Post by MJN on 2007-11-12
Given there's a router between your machine and the Internet then that's what GRC has been testing. It is listing ports 'open' on your router, not just your PC.
 
Mathew

---

### Post by stimpack on 2007-11-12
Heh yes. If that was a router then with telnet open on the router, usually means your router is setup for remote adminstration. So fix that, unless you do actually remotely administer it :).

---

### Post by bunny rabbit on 2007-11-12
> **steve.horsley said:**
> **sudo netsat -plntu** 
will tell you which ports are open and by which process.

That's an enlightening application, but I think you meant *sudo _netstat_ -plntu*

---

### Post by chauster on 2007-11-13
Thanks for helping me make sense of this everyone.

---

### Post by otake-tux on 2007-11-13
> **HermanAB said:**
> Note that open ports paranoia is a Windows thing, because on Windows you don't know what servers Microsoft is running and their network stack is a huge mess.

On Linux, 'ps-e' will show you what is running, so iptables (netfilter) is only required to remove malicious packets, don't worry about ports, since if the service isn't running, nothing can connect to it, and if it is running, then you probably want to connect to it...

Cheers,

Herman

this is incorrect and a common misconception.  unnecessary open ports are a concern on all operating systems.

---

### Post by az on 2007-11-13
> **otake-tux said:**
> this is incorrect and a common misconception.  unnecessary open ports are a concern on all operating systems.

Why?

Do you think that an open port is a clue that there is something there?  Do you think that dropping packets (*stealthing *in GMC talk) instead of denying them will hide your presence?  

"Stealthing" your ports is the misconception.  You can not be invisible.  Thinking that you are is a false sense of security.

---

### Post by otake-tux on 2007-11-13
> **az said:**
> Why?

Do you think that an open port is a clue that there is something there?  Do you think that dropping packets (*stealthing *in GMC talk) instead of denying them will hide your presence?  

"Stealthing" your ports is the misconception.  You can not be invisible.  Thinking that you are is a false sense of security.

security is all layers. the real question is; why not stealth them? why make reconnaissance work easier?

---

### Post by nutz on 2007-11-13
> **otake-tux said:**
> security is all layers. the real question is; why not stealth them? why make reconnaissance work easier?

He is right; there is no danger in keeping the port open if no service is listening on it.

---

### Post by az on 2007-11-13
> **otake-tux said:**
> security is all layers. the real question is; why not stealth them? why make reconnaissance work easier?

First off, that's very naive reconnaissance.  Secondly, as I mentioned, it is a false sense of security.  Thirdly, it complicates things when you want to use the network.

---

