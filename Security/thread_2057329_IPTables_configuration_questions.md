---
title: "IPTables configuration questions"
date: 2012-09-13
forum: Security
---

### Post by jwright8 on 2012-09-13
I have an IPTables script that I wrote myself.  I will paste the relevant parts of the script below:

```

## Default policies
#
iptables -P INPUT DROP
        # Drops all but approved input
iptables -P OUTPUT ACCEPT
        # See output filtering rules below
iptables -P FORWARD ACCEPT
        # Forward has to be set to accept for the connections to go through to the other side to the LAN
        # See forward filtering rules below

``````

# FTP
iptables -A OUTPUT -p tcp -s 10.1.10.71 --dport 21 -j ACCEPT
iptables -A FORWARD -p tcp -s 10.1.10.71 --dport 21 -j ACCEPT

iptables -A OUTPUT -p tcp -s 10.1.10.72 --dport 21 -j ACCEPT
iptables -A FORWARD -p tcp -s 10.1.10.72 --dport 21 -j ACCEPT

# SMTP
iptables -A OUTPUT -p tcp -s 10.1.10.71 --dport 25 -j ACCEPT
iptables -A FORWARD -p tcp -s 10.1.10.71 --dport 25 -j ACCEPT

iptables -A OUTPUT -p tcp -s 10.1.10.72 --dport 25 -j ACCEPT
iptables -A FORWARD -p tcp -s 10.1.10.72 --dport 25 -j ACCEPT


```The two internal IPs having access to SMTP/FTP is intentional.  No other IPs on the LAN do.

```

## Dropped outgoing ports
#
iptables -A OUTPUT -p tcp --dport 21 -j DROP
iptables -A OUTPUT -p tcp --dport 22 -j DROP
iptables -A OUTPUT -p tcp --dport 23 -j DROP
iptables -A OUTPUT -p tcp --dport 25 -j DROP
iptables -A OUTPUT -p tcp --dport 43 -j DROP
iptables -A OUTPUT -p tcp --dport 53 -j DROP
iptables -A OUTPUT -p tcp --dport 79 -j DROP
iptables -A OUTPUT -p tcp --dport 80 -j DROP # HTTP
iptables -A OUTPUT -p tcp --dport 110 -j DROP
iptables -A OUTPUT -p tcp --dport 115 -j DROP
iptables -A OUTPUT -p tcp --dport 119 -j DROP
iptables -A OUTPUT -p tcp --dport 143 -j DROP
iptables -A OUTPUT -p tcp --dport 389 -j DROP
iptables -A OUTPUT -p tcp --dport 443 -j DROP # HTTPS


``````

## Dropped forwarding ports
#
iptables -A FORWARD -p tcp --dport 21 -j DROP
iptables -A FORWARD -p tcp --dport 22 -j DROP
iptables -A FORWARD -p tcp --dport 23 -j DROP
iptables -A FORWARD -p tcp --dport 25 -j DROP
iptables -A FORWARD -p tcp --dport 43 -j DROP
iptables -A FORWARD -p tcp --dport 53 -j DROP
iptables -A FORWARD -p tcp --dport 79 -j DROP
iptables -A FORWARD -p tcp --dport 80 -j DROP # HTTP
iptables -A FORWARD -p tcp --dport 110 -j DROP
iptables -A FORWARD -p tcp --dport 115 -j DROP
iptables -A FORWARD -p tcp --dport 119 -j DROP
iptables -A FORWARD -p tcp --dport 143 -j DROP
iptables -A FORWARD -p tcp --dport 389 -j DROP
iptables -A FORWARD -p tcp --dport 443 -j DROP # HTTPS

``````

## Allowed users
#
iptables -A INPUT -s xx.xxx.xx.xx -j ACCEPT # Allowed Person 1
iptables -A INPUT -s xx.xxx.xx.xx -j ACCEPT # Allowed Person 2
## Permanent allowed users (LAN)
#
iptables -A INPUT -s 127.0.0.1 -j ACCEPT
iptables -A INPUT -s localhost -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

```----------------------

The script is actually quite long, so let me know if something doesn't make sense and I'll try to check and see if i left an important chunk of it out.

The goal here is that I have the following setup

Internet ->
Modem/Router (only one physical port enabled)->
Ubuntu x64 server with OpenVPN (eth0 in and eth1 out, configured to br0 bridge adapter in tap0) ->
Switch ->
Client machines

The idea behind the IPTables config here is to disallow any inputs at all under any circumstances from the outside unless i explicitly allow their IP, no matter what circumstances/programs.  If I allow their IP, they should be able to connect to my OpenVPN (port 5556) and SSH (port 5555).  

Once the connection is established, these outside systems will have access to port 80 traffic (ONLY the IPs that are reserved for the VPN, not the internal LAN clients). They need access to Windows network drives, but I don't have an explicit rule for that (it's just not blocked once the connection to the VPN is established). I have the rules written and working for that.  The systems on the internal LAN, however, I really only need them to be able to use whatever port is used for windows networked drive access/activity (which I admittedly don't know).  


My main question though, is about the FORWARD rules I have above.  Does forwarding in IPTables mean forwarding from CLIENT#1 the inside of the LAN through the linux box into the outside world, into the Linux box from the outside world on the way to CLIENT#1, or both?  Ideally, what I'm trying to do with the above script, is to, again, not allow ANY traffic under any circumstance from the outside world (not even access to SSH/OpenVPN) unless I explicitly allow their IP.  

Someone suggested I try the following forwarding rule instead of the one I have at the very top:
```


iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 10.1.10.0/24 -j ACCEPT
iptables -P FORWARD -j REJECT

```The only problem with this rule is that when I enable it, all the internal LAN client computers have access to the ports that I blocked (like port 80 for internet access).  I'm not sure why, but I suspect that it has to do with the first line about an established connection being allowed (though admittedly it doesn't make any sense in light of the fact that my original rule is merely ACCEPT).

Sorry if this seems a bit confusing, and I might already have it right, but something I read the other day kind of made me skittish about what could be a misconception about the IPTables forwarding principles.

Thanks for looking!

---

### Post by jwright8 on 2012-09-21
> **jwright8 said:**
> 

My main question though, is about the FORWARD rules I have above.  Does  forwarding in IPTables mean forwarding from CLIENT#1 the inside of the  LAN through the linux box into the outside world, into the Linux box  from the outside world on the way to CLIENT#1, or both?  Ideally, what  I'm trying to do with the above script, is to, again, not allow ANY  traffic under any circumstance from the outside world (not even access  to SSH/OpenVPN) unless I explicitly allow their IP.  



Does anyone have any idea if the forwarding above is applied in the correct way?  

I was pretty confident up until recently, and I was hoping someone might be able to tell me if I've been under a false assumption that I had things configured the way I envisioned them. 

Thanks in advance!

---

### Post by wacky_sung on 2012-09-21
I think it is better for you to place your whole script here otherwise nobody can pinpoint to your right direction. If your script is more 50 lines, then i will suggest you to use a gui firewall software such as [Firewall Builder]("http://www.fwbuilder.org/") to help you and it is so much easier that way. :lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by jwright8 on 2012-09-21
As I said in my previous posts, my question is conceptual with respect to how the FORWARD rule works in the context of the two snippets above (or even as a generalization, as the man pages, to me, don't answer the question completely).  The snippets above should be more than sufficient to convey how I was using the FORWARD rule and why (hence my long-winded, thorough explanation about my implementation).  


If you had stopped to read what I was saying and thought about it, instead of trying to be condescending and spamming the LOL emoticons over and over to try to assert some (false) form of superiority, you might have actually been able to help with my question.  If you don't understand what I'm asking, then you were more than welcome to ask me to clarify, and I'd have been happy to do so.  Then again, I understand that certain people would rather use :lolflag: than actually help.  That's their prerogative, but I was genuinely hoping someone that cared to assist others would see this and post to at least clarify or attempt to help.  In short, I would greatly appreciate it if you whored your post count somewhere else and saved the replies for someone that can, and wants, to help.

---

### Post by JKyleOKC on 2012-09-21
> **jwright8 said:**
> The idea behind the IPTables config here is to disallow any inputs at all under any circumstances from the outside unless i explicitly allow their IP, no matter what circumstances/programs.If I take this literally, achieving that goal would make communication impossible, since "any circumstances" would include packets in reply to your outgoing connection requests. It would even include responses to your DNS requests!

I think your intent, though, is probably to prevent NEW connection inputs, while accepting inputs that are part of an established or related connection. The usual way to do this is with the ```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```rule that you already have in your script. However I would put it at the very top of the chain, so that such packets need not traverse all the other rules to reach it.

To address your question about the FORWARD chain, just keep in mind that INPUT and OUTPUT apply **only** to packets to or from the specific machine that is running iptables. Any packets that come through this machine en route to or from other machines on your LAN will go through FORWARD instead. This implies that FORWARD is meaningful **only** if on a machine that is serving as a router or a firewall for the entire LAN. If your machine is not one of these, then the FORWARD chain should never be reached; "iptables -L" will show you the packet count for each rule and if it's "0:0" that confirms the rule is never used.

If FORWARD **is** applicable to your system, then it should duplicate the rules that you establish for INPUT and also for OUTPUT, since any packet addressed to another machine will never reach the INPUT chain, nor will those coming from another place on your LAN get to OUTPUT. The simplest way to do this is to put the rules into new user-defined chains such as "MyIn" and "MyOut" and then put single rules into INPUT and OUTPUT, and two rules into FORWARD, to jump to the appropriate MyIn or MyOut chains for the actual tests. This, incidentally, is pretty much what UFW does behind the scenes to work its magic, although it adds several layers of additional complexity.

EDIT--To answer your more specific later question, it applies to BOTH. I see that you really are using the server box as a firewall and router, so FORWARD will be quite essential to achieve your goals. You may also need to look at the prerouting and postrouting areas, although in my router/firewall system they are both pretty minimal and FORWARD does all the heavy work.

---

### Post by jwright8 on 2012-09-21
> **JKyleOKC said:**
>  The usual way to do this is with the  ```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j  ACCEPT
```rule that you already have in your script. However I would  put it at the very top of the chain, so that such packets need not  traverse all the other rules to reach it..

This makes a ton of sense, and I was actually wondering why I hadn't done that before.  Thank you!


> **JKyleOKC said:**
> 
To address your question about the FORWARD chain, just keep in mind that INPUT and OUTPUT apply **only** to packets to or from the specific machine that is running iptables. Any packets that come through this machine en route to or from other machines on your LAN will go through FORWARD instead. This implies that FORWARD is meaningful **only** if on a machine that is serving as a router or a firewall for the entire LAN. If your machine is not one of these, then the FORWARD chain should never be reached; "iptables -L" will show you the packet count for each rule and if it's "0:0" that confirms the rule is never used.

If FORWARD **is** applicable to your system, then it should duplicate the rules that you establish for INPUT and also for OUTPUT, since any packet addressed to another machine will never reach the INPUT chain, nor will those coming from another place on your LAN get to OUTPUT. The simplest way to do this is to put the rules into new user-defined chains such as "MyIn" and "MyOut" and then put single rules into INPUT and OUTPUT, and two rules into FORWARD, to jump to the appropriate MyIn or MyOut chains for the actual tests. This, incidentally, is pretty much what UFW does behind the scenes to work its magic, although it adds several layers of additional complexity.

Okay, so it seems as if in my application that FORWARD does matter, since the setup is currently:

Internet -> Modem -> Ubuntu Server (the one in question) -> Switch/hub -> client computers

So essentially all the traffic (in/out) goes through the eth1 and eth0 of the box in both directions.  

My current application in this instance that I'm testing out is an OpenVPN server on the Ubuntu box; there is nothing else on there except DenyHosts, SSH (other than the default stuff from a Ubuntu install, of course).  I want to be able to connect remotely to the OpenVPN server and be able to mount a network drive of a client computer behind the OpenVPN server on the LAN and do stuff with it (run programs, copy files, etc.). 

I only want this ability for computers I specifically allow.  To address part of this, I have certificates for each computer that validate when connecting to OpenVPN; however, I'd like the additional capacity for if they went to another network, they would be blocked as well (certificate or no certificate), from communicating with clients behind the OpenVPN server.  

Sorry if this rambles on a bit, but I'm still kind of struggling to grasp how I need to change my forwarding rules to achieve what I want.  I assumed that the INPUT/OUTPUT also had a place in it; I'm glad I asked for clarification instead of operating under a false premise.

Thanks for your help so far!


EDIT:

Upon further thought, I guess the reason it seems like it works now is because the OpenVPN clients are connecting TO the Linux box first; it is not trying to communicate directly to the client computers behind it (that comes later when I mount the network drives).  How would I go about using forward in the same way?

Could I use DROP for all forwarding, then allow exceptions for LAN IPs only?  Since, when they connect to OpenVPN, the remote client computers are assigned a local IP.


EDIT 2:

```

iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A FORWARD -s 10.1.10.0/24 -j ACCEPT 
iptables -P FORWARD -j REJECT

```

The iptables lines above actually seem like they seek to accomplish that.  The only problem is that even with my DROP rules for the forward ports later, everything is still allowed (I don't want the client LAN computers to have access to port 80, 443, 25, 21, 22, etc. traffic, as in the rules from the initial post).  If this solves the forwarding problem from the outside going inward, then that's great, but how do I stop what I want to stop from the inside IP's going out?

---

### Post by JKyleOKC on 2012-09-21
> **jwright8 said:**
> ```

iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A FORWARD -s 10.1.10.0/24 -j ACCEPT 
iptables -P FORWARD -j REJECT

```The iptables lines above actually seem like they seek to accomplish that.  The only problem is that even with my DROP rules for the forward ports later, everything is still allowed (I don't want the client LAN computers to have access to port 80, 443, 25, 21, 22, etc. traffic, as in the rules from the initial post).  If this solves the forwarding problem from the outside going inward, then that's great, but how do I stop what I want to stop from the inside IP's going out?That second rule accepts everything coming in from your LAN; I'm not clear yet as to what, specifically, you want the LAN users to be able to do. However to block them from port 80, for instance, you would need to add (after the first tule above) a rule such as ```
iptables -A FORWARD -s 10.1.10.0/24 --dport 80 -j REJECT 
```This might be the "later DROP rules" but they would have to precede the ACCEPT rule to have any effect for the LAN users.

It's usually much simpler to establish what you want to allow, create rules to ACCEPT those cases, and REJECT or DROP everything else. It's also helpful to create a "LOG_DROP" chain and jump to it, so that you know what got rejected. Here's an example, as part of a configuration file to be loaded via "iptables-restore":```
# define optional chain to log dropped packets
:LOG_DROP - [0:0]
# define rules for optional LOG_DROP chain
-A LOG_DROP -j LOG  --log-prefix "[IPTABLES DROP] : " 
# next rule not needed; policy for INPUT will handle it
-A LOG_DROP -j DROP

```This will put a line into /etc/syslog every time a packet gets dropped, telling you the source and destination IP and ports plus other information. Especially while getting the rules set up, this is nice to have, since it can alert you to other things you need to let through...

I would do the filtering a bit differently, something like this (untested) addition to allow outbound traffic to port 443, only:```
# define chain to filter LAN traffic
:CHECK_LAN - [0:0]
# define rules for LAN filtering chain
-A CHECK_LAN --dport 443 -j ACCEPT
# next rule drops everything else
-A CHECK_LAN -j LOG_DROP

# place as second and third rules in FORWARD chain and delete all after it in that chain
-A FORWARD -s 10.1.10.0/24 -j CHECK_LAN
-A FORWARD -j LOG_DROP

```This applies the filtering only to outbound traffic from the LAN, and rejects everything coming in from outside except what's allowed by the ESTABLISHED rule. 

Hope this helps!

---

### Post by jwright8 on 2012-09-21
Okay, that all makes sense.  That is, in fact, what the DROP rules were supposed to be for.  I guess I've just been getting things backwards in the order they need to go in (I just assumed the default policies would be first, but I know now it's the opposite).

I had thought about disallowing everything and only allowing what I want to allow for forwarding, but I was presented with a problem.  I'm not sure how Windows network drive activity works.  Is it a set port, or does it change?  The primary reason of the VPN is to allow me to run programs that typically only go across the LAN remotely (they don't communicate with the outside world at all, just computer to computer on the LAN).  

The goal is to allow users to communicate however they want as long as it is only LAN to LAN connections; I don't want anything going out other than the two very specific computers I allow to communicate on those two ports outgoing.  I also don't want anyone communicating inward from outside other than the windows network drive traffic (running programs over the network) from those that will already have a local IP assigned, since the OpenVPN authentication would have already happened.

Thank you for all of your help so far, I think I'm finally beginning to understand it.

---

### Post by JKyleOKC on 2012-09-21
We're getting there, I think. The Windows "file and printer sharing" services use ports 137, 138, 139, and 445 to establish their network connections. They use both tcp and udp, so I would put specific rules to allow those ports -- a total of 8 rules in all, although you could group the first three as 137:139 and reduce it to just four. I also oversimplified my examples earlier. The ACCEPT rules in CHECK_LAN should look like this, I believe:```
-A CHECK_LAN -p tcp -m tcp --dport 137:139 -j ACCEPT
-A CHECK_LAN -p udp -m udp --dport 137:139 -j ACCEPT
-A CHECK_LAN -p tcp -m tcp --dport 445 -j ACCEPT
-A CHECK_LAN -p udp -m udp --dport 445 -j ACCEPT
```This ought to allow full interior traffic on the LAN but not allow anything at all with the outside world.

"Not allow anything" however probably means that the VPN server's traffic would also be rejected, if it passes through FORWARD. However since that server is on the single machine that runs iptables, traffic from the LAN destined for the VPN server should come through INPUT, and traffic from the VPN server to the outside world should go through OUTPUT, so this just may do what you are looking for...

One trick that may help getting it working is to create some more LOG_DROP style chains, each with its own unique name and that name in the label that is passed to LOG. Then when you find items in the syslog file, you can tell which group of rules rejected them...

EDIT--Just realized that it could be much simpler, even, by checking for both source and destimation IPs. If both are on the LAN, jump to ACCEPT, otherwise LOG_DROP or REJECT. Port numbers and tcp/udp considerations would not even need to be considered!

---

### Post by jwright8 on 2012-09-21
Wonderful!  That actually makes a lot of sense... thank you for all of your help, I was beginning to go crazy trying to wrap my head around it.  

How would you write the rule to just check and see if an IP was on the LAN, then?  I kind of figured it would turn out simpler when you could safely assume that ALL IP's of relevance would actually already be a LAN IP (since OpenVPN would take care of that, and I do know how to limit the IP's on that side using input/output).  The lines above do seem like they will do what I want (I'll have to test at a later date), but if I were to be able to allow LAN to LAN traffic independent of individual port considerations, it would be opportune to say the least.

---

### Post by wacky_sung on 2012-09-21
Actually i still feel that your iptables shall by default shall drop all connections from input, forward and output for security reasons. Then you start to allow by port and protocol. Anyway it is all yours.

---

### Post by JKyleOKC on 2012-09-21
For the LAN traffic, I think these rules should work:```
-A FORWARD -s 10.1.10.0/24 -d 10.1.10.0/24 -j ACCEPT
-A FORWARD -s 10.1.10.13/32 -j ACCEPT
```This should allow unlimited traffic around the LAN, but only the single IP of 10.1.10.13 would be able to transmit anything outside the LAN. Of course you would still need the RELATED,ESTABLISHED rule ahead of them, to accept responses to packets that 10.1.10.13 sent out. If you wanted to restrict that IP to only a single port or a range of ports, you could expand its rule to do so, and if you wanted to allow a different specific IP to do the same, you could add a rule for it that differed only in the final octet of the source address. Obviously, you would change these IPs to those actually involved, and the network would have to be using static IPs rather than DHCP assignment for the ACCEPT rules to remain consistent.

Just keep in mind that the rules are visited in strict top-to-bottom sequence, so once a packet satisfies a rule that takes it to either ACCEPT or DROP/REJECT no additional rules will see it. A jump to LOG always returns after logging the data, though, and any user-defined chain that does not have an unconditional jump as its last rule will return to the chain that called it. In other words, each rule is like a subroutine in a program.

---

### Post by jwright8 on 2012-09-24
Thank you for all of your help Jim.  I'll mark this thread solved, as I think I finally get it.

---

