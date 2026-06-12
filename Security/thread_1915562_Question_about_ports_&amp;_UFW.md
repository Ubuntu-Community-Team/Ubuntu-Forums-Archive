---
title: "Question about ports &amp; UFW"
date: 2012-01-26
forum: Security
---

### Post by MadsRC on 2012-01-26
I'll start of by saying: I'm far from any networking wiz, which I think my question will show you.

In this scenario I've started an SSH session to an offsite server (from now on "Server") from a pc (from now on "Client"). The client have the following UFW rules:
```
sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
53,137,138/udp             ALLOW OUT   Anywhere
20,21,22,80,443,1863,8001/tcp ALLOW OUT   Anywhere
5222/tcp                   ALLOW OUT   Anywhere
465                        ALLOW OUT   Anywhere
993                        ALLOW OUT   Anywhere
51413                      ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
53,137,138/udp             ALLOW OUT   Anywhere (v6)
20,21,22,80,443,1863,8001/tcp ALLOW OUT   Anywhere (v6)
5222/tcp                   ALLOW OUT   Anywhere (v6)
465                        ALLOW OUT   Anywhere (v6)
993                        ALLOW OUT   Anywhere (v6)
51413                      ALLOW OUT   Anywhere (v6)
Anywhere (v6)              DENY OUT    Anywhere (v6)
```and the server has the following iptables:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```From the client, with an open ssh connection, netstat display's:
```
sudo netstat -tupan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      966/cupsd       
tcp       38      0 cl.ie.nt.ip:54637      91.189.89.105:443       CLOSE_WAIT  3226/gvfsd-http 
tcp       38      0 cl.ie.nt.ip:54578      91.189.89.105:443       CLOSE_WAIT  3226/gvfsd-http 
tcp        1      0 cl.ie.nt.ip:47751      91.189.89.106:80        CLOSE_WAIT  3226/gvfsd-http 
tcp        1      0 cl.ie.nt.ip:54389      91.189.89.31:80         CLOSE_WAIT  3226/gvfsd-http 
tcp        0      0 cl.ie.nt.ip:51013      se.rv.er.ip:22        ESTABLISHED 10057/ssh       
tcp       38      0 cl.ie.nt.ip:54657      91.189.89.105:443       CLOSE_WAIT  3226/gvfsd-http 
tcp        1      0 cl.ie.nt.ip:47678      91.189.89.106:80        CLOSE_WAIT  3226/gvfsd-http 
tcp        1      0 cl.ie.nt.ip:47737      91.189.89.106:80        CLOSE_WAIT  3226/gvfsd-http 
tcp6       0      0 ::1:631                 :::*                    LISTEN      966/cupsd       
udp        0      0 0.0.0.0:36433           0.0.0.0:*                           938/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1457/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           938/avahi-daemon: r
udp6       0      0 :::43563                :::*                                938/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                938/avahi-daemon: r
```And from the server, netstat prints:
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0     48 se.rv.er.ip:22        cl.ie.nt.ip:51013      ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     

```Now, the boring stuff's over.

My question is about the client's UFW rules.
1) Is there any reason for the clients port 22 to be open? From what I understand, the client connect out of port 51013 to the server at port 22. This would mean that IF the client didn't have "allow outgoing" it would need to have an "allow in 51013" or else the clients own firewall would block the connection?

2) The clients "allow outgoing" would that mean that any connection that is initiated by the client itself would be allowed, and "deny "incomming" would mean that any connection that originates from outside the client would be rejected (besides the exeptions which is created by the other rules) ?

3) Why is it called "allow outgoing" when the rules that have to be created have to be "allow out"? Isn't all outgoing connections allowed?

Please, if i left something out, tell me and I'll add it ASAP.

---

### Post by CharlesA on 2012-01-26
1) Port 22 isn't open on the client. It's connecting to port 22 on the server via a random high number port (which is normal)
2) Correct
3) No idea. It looks like it's set that way by default so that you don't lock it out if you change the default rules.

---

### Post by MadsRC on 2012-01-26
Isn't port 22 open on the client? The second line in the UFW code should have port 22 mentioned with tcp? Doesn't that mean it's open?

---

### Post by CharlesA on 2012-01-26
> **MadsRC said:**
> Isn't port 22 open on the client? The second line in the UFW code should have port 22 mentioned with tcp? Doesn't that mean it's open?
This line?

```
20,21,22,80,443,1863,8001/tcp ALLOW OUT   Anywhere
```

---

### Post by MadsRC on 2012-01-26
Yes, doesn't that line state that the ports listed, including 22, should be open for TCP connection via those ports?

---

### Post by CharlesA on 2012-01-26
Only outbound connections. Incoming connections are still blocked.

---

### Post by MadsRC on 2012-01-26
So, basicly, if you wanted someone to be able to SSH into the client, you would have to open port 22 (if using SSH over port 22) for incomming connections (connections that originated from outside the client). Would that rule be called "22/tcp allow in" or 22/tcp allow out"?

---

### Post by CharlesA on 2012-01-26
Something like that, yeah.

You'd also need openssh-server installed on the client.

---

### Post by MadsRC on 2012-01-26
Then should there be any reason for the second line in UFW to contain the nr. 22, thus opening inbound connections through port 22, when the client should not be able to SSH'ed into (Only be able to SSH out, but that has nothing to do with port 22 on the clientside) ?

---

### Post by CharlesA on 2012-01-26
There isn't anything being allowed in. The default policy is to deny all incoming and there are no rules to allow traffic to a port.

Rule #2 is referring to outbound connections, not incoming ones.

---

### Post by MadsRC on 2012-01-26
Makes sense, since if port 80 isn't open on the clientside, the client wouldn't be able to use HTTP, since a HTTP connection originates from port 80 on the clientside, and if port 80 is closed, then HTTP wouldn't work.

I guess it boils down to: If you need to SSH to xx.xx.xx.xx:22, does that mean port 22 have to be open as an outbound connection on the client side or open as an incomming connection on the server side?

And I'm really sorry if these are really dumb questions, but I want to be sure I get it :P

---

### Post by CharlesA on 2012-01-26
It has to be open on the machine you want to ssh to.

---

### Post by MadsRC on 2012-01-26
So, in theory, the client does not have to have port 22 open, only the server?

Btw CharlesA, I think that was your 12.000th posts, grats :)

---

### Post by CharlesA on 2012-01-26
> **MadsRC said:**
> So, in theory, the client does not have to have port 22 open, only the server?

Btw CharlesA, I think that was your 12.000th posts, grats :)
Not only in theory, in practice as well. ;)

---

### Post by bodhi.zazen on 2012-01-26
Privileged ports, below 1024, can only be bound (used) by root (not users).

Servers (ssh in this case) listen on a port (22 in this case).

Clinets (ssh client in this case) use a random high port ( > 1024 )to connect to the server.

So your ssh client may well use port 5555 to connect to the server port 22.

You can see this with any packet sniffer (wireshark, tcpdump).

See also [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

At lease the first few sections.

---

### Post by MadsRC on 2012-01-26
I have just tried deleting the "allow out 22/tcp" rule for the client, and it would not connect to the server via SSH. But if I added the "allow out 22/tcp" it would connect again.

This kinda contradicts the theory that the client does not need to have port 22 open to SSH to a server via port 22.

But is it because that the firewall looks at the connection to see what port it is bound for (the server port) and if it sees that the bound port isn't allowed in the outgoing, it will be stopped? But no matter what port the connection tries to exit client from (example 5555 as in bodhi.zazen's example) it will be allowed?

I've read the forum stickies and used your (bodhi.zazen) guide on your website/blog, but to be frank, there's still some basic stuff I'm not really 100% sure of.

EDIT: Must admit, I hadn't seen your Basic Networking Concept on your page bodhi.zazen.

I'll see if they will help me better understand networking.

---

### Post by CharlesA on 2012-01-26
The port is not open on the client. You are only allowing traffic to go out on port 22.

You are correct. The firewall checks to see what the destination port is and if it is on the "allow out" list, it will allow it through the firewall. If the destination port is not on the allow out list, it will block the outbound connection.

---

### Post by MadsRC on 2012-01-26
I guess that was the line I was looking for.

So if the destination port is NOT on the allow out list it will be blocked.

Does that also mean that the allow out list have nothing to do with the default deny/allow out/incomming? Because it wouldn't make much sense that we have to say "allow out 22/tcp" when it is set to default allow outgoing. Does default allow outgoing really mean that it don't care what port the connection exits the client from (in your example it exits from 5555 and is destined to 22 on the server) and the default deny incomming means that it will not let anything through that is destined for any port on the client.?

---

### Post by bodhi.zazen on 2012-01-26
> **CharlesA said:**
> The port is not open on the client. You are only allowing traffic to go out on port 22.

You are correct. The firewall checks to see what the destination port is and if it is on the "allow out" list, it will allow it through the firewall. If the destination port is not on the allow out list, it will block the outbound connection.

As CharlesA is telling you, if you look at the actual rules you will see it has nothing to do with port 22 on the client.


```
iptables -A OUTPUT -p tcp -m port --dport 22 -j ALLOW
iptables -A OUTPUT -j DROP
```

---

### Post by CharlesA on 2012-01-26
> **MadsRC said:**
> I guess that was the line I was looking for.

So if the destination port is NOT on the allow out list it will be blocked.

Does that also mean that the allow out list have nothing to do with the default deny/allow out/incomming? Because it wouldn't make much sense that we have to say "allow out 22/tcp" when it is set to default allow outgoing. Does default allow outgoing really mean that it don't care what port the connection exits the client from (in your example it exits from 5555 and is destined to 22 on the server) and the default deny incomming means that it will not let anything through that is destined for any port on the client.?

This rule tells ufw to drop anything that is not allowed:

```
Anywhere                   DENY OUT    Anywhere
```

---

