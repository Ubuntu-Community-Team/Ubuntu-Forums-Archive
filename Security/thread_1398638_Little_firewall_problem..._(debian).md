---
title: "Little firewall problem... (debian)"
date: 2010-02-04
forum: Security
---

### Post by jargs on 2010-02-04
Hello,

I am trying to setup a webserver, i'm on debian. I have inserted these rules into the iptables:

iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 21 -j ACCEPT
iptables -A INPUT -p tcp --dport 25 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp -j DROP

So basically I want to close all of my other ports and keep those ones open for the web services (ssh, smtp, http, ftp). These rules seem to work alright for SSH and Apache, but for some reason the FTP and SMTP services are being blocked by the firewall. I am using PostFix mail server and ProFTPd. Any help would be greatly appreciated, I have only recently started using Linux again and need to brush up on my knowledge... :)

---

### Post by bodhi.zazen on 2010-02-04
For FTP you probably need to open port 20 as well.

The mail server can be harder, check what ports it uses and some ISP block such traffic.

---

### Post by MoRoBoShi on 2010-02-04
> **bodhi.zazen said:**
> For FTP you probably need to open port 20 as well.


holy words bodhi.zazen..!!;)

---

### Post by jargs on 2010-02-05
still not working after opening port 20...

---

### Post by jargs on 2010-02-05
and it is deffinately not an isp problem because the server is in a datacenter... I just need a simple webserver firewall setup that will allow me to use the services i mentioned

---

### Post by bodhi.zazen on 2010-02-05
> **jargs said:**
> and it is deffinately not an isp problem because the server is in a datacenter... I just need a simple webserver firewall setup that will allow me to use the services i mentioned

Does it work if you flush your rules ?

---

### Post by jargs on 2010-02-05
yes it works when i flush

---

### Post by mick_dundee on 2010-02-05
Depending on the rest of your iptables setup, you may need to add OUTPUT rules for that particular traffic.  In my case I added FORWARD rules also as I have set iptables to drop INPUT, OUTPUT and FORWARD packets by default.

---

### Post by jargs on 2010-02-05
my output table is empty though, those rules i listed above are the only ones i have. would i still need to add output rules even if the chain is empty?

---

### Post by mick_dundee on 2010-02-05
It's worth trying - you can remove them immediately if they don't work.  The way it looks at the moment is that inbound requests are accepted but the reply to those requests aren't being sent out over the public interface (therefore not being received by the client).  Or private interface if it's an internal test machine.

Remember and change --dport to --sport for the outbound rules.

---

### Post by jargs on 2010-02-05
i added these rules

iptables -A OUTPUT -p tcp --sport 20 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 21 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 25 -j ACCEPT

then added the drop rule after

iptables -A INPUT -p tcp -j DROP

and it still doesn't work :(

---

### Post by bodhi.zazen on 2010-02-05
Can yo upost the output of ```
iptables -L -v
```

---

### Post by jargs on 2010-02-05
Chain INPUT (policy ACCEPT 1437K packets, 1993M bytes)
 pkts bytes target     prot opt in     out     source               destination                       
 4050  310K ACCEPT     tcp  --  any    any     anywhere             anywhere                                  tcp dpt:ssh
  752 39200 ACCEPT     tcp  --  any    any     anywhere             anywhere                                  tcp dpt:ftp
1268K  327M ACCEPT     tcp  --  any    any     anywhere             anywhere                                  tcp dpt:www
   19  2985 ACCEPT     tcp  --  any    any     anywhere             anywhere                                  tcp dpt:smtp
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere                                  tcp dpt:ftp-data
 3480  211K DROP       tcp  --  any    any     anywhere             anywhere                          

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                       

Chain OUTPUT (policy ACCEPT 2550K packets, 1460M bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by The Cog on 2010-02-05
Try adding this rule to get printing working again:
> iptables -A INPUT -i lo -j ACCEPT 

and this one to allow responses to outgoing connections (which may fix your FTP problems):
> iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 

---

### Post by jargs on 2010-02-05
won't that accept connections on every port though??

---

### Post by jargs on 2010-02-06
and what do you mean printing? I am using this as a webserver.

---

### Post by CharlesA on 2010-02-06
> **jargs said:**
> won't that accept connections on every port though??

Accepting everything that come in on the lo interface is fine, since it's the loopback interface and not accessible to the outside world.

---

### Post by jargs on 2010-02-06
but what about this one:

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 

won't that accept things from all ports?

---

### Post by The Cog on 2010-02-06
> **jargs said:**
> but what about this one:

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 

won't that accept things from all ports?

It will accept all packets that are on already established connections or related to already established connections. Examples are:

1: An incoming FTP connection to port 21 will be accepted by your rule that accepts FTP. Any further packets on the same connection will be accepted by this rule because the connection is already established. Actually, you will never notice the difference here because if this rule wasn't there, the accept FTP rule would allow the packet in anyway.

2: An FTP data connection trying to transfer data on port 20, as requested by the FTP control connection established in paragraph 1 above. FTP uses separate connectons for control messages and data transfer. Without the RELATED rule, the actual data transfer couldn't happen although you could log in to the FTP server without problem. But by looking at the FTP control connection, the firelwall knows that the the connection on port 20 is related to an established FTP connection on port 21, and allows the connection through.

3: An outgoing connection from the server, such as perhaps a DNS name lookup request (UDP port 53) - it is the ESTABLISHED rule that allows the lookup reply back in because the outgoing name request established a connection. 


As for the loopback interface, well lots of things rely on the computer being able to connect to itself. One that I know of is the print spooler. Even if you were just trying to print your server logs to a locally connected USB printer, it wouldn't work unless the computer could connect to itself because printing involves having the printing application (lpr, gedit, whatever) making a connection to the print spooling service on TCP port 631. This isn't a security issue because by default the spooler service only listens on the loopback address, which can't be connected to by other machines. But it does mean that too restrictive a local firewall rule will stop printing from working, amongst other things that I can't think of right now.

---

### Post by jargs on 2010-02-06
when i used that rule i ran "netstat -nan | grep 22" and it said this:
> 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN   


doesn't this mean all ports are open?

and why doesn't it work when i use rules like this:

iptables -A INPUT -m state --state RELATED,ESTABLISHED -p tcp --dport 21  -j ACCEPT 

?

---

### Post by The Cog on 2010-02-06
No - all that line tells you is that port 22 (SSH) is open. You filtered all the other netstat lines out with grep, so you can't tell what other ports are open.

On top of that, we were talking about firewalls. Netstat won't tell you what ports are blocked or not blocked by the firewall, so even ports that are open might be blocked by the firewall and therefore not possible to connect to.

> and why doesn't it work when i use rules like this:

iptables -A INPUT -m state --state RELATED,ESTABLISHED -p tcp --dport 21 -j ACCEPT 
Sorry, why doesn't what work?
And that's not the line I said to try.


EDIT
Actually, it occurs to me to wonder why you are trying to mess around with a firewall at all. What are you trying to achieve with your firewall? 

You say you want the ssh, smtp, http, and ftp service open to the public. What other services are you running - what are you trying to block? Unless you are running other services (such as VNC) that you know you want to prevent public access to, then you don't need a firewall at all.

The command ```
netstat -lntu
``` will show what services/ports are actually open.

---

