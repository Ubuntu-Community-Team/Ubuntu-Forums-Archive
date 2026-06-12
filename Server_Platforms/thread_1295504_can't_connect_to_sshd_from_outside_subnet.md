---
title: "can't connect to sshd from outside subnet"
date: 2009-10-19
forum: Server Platforms
---

### Post by kspider on 2009-10-19
I can ssh to my ubuntu 9.10 server from any IP within the same subnet that it's on (192.168.1.1/24), but I cannot ssh to it from outside the subnet.  I am using port forwarding at the NAT router.  I already have port forwarding for ssh successfully configured for a different server.  The router is configured to forward a high port (not 22) to port 22 on the working server.

If I change the ubuntu server's IP to the IP of the server for which the port forward works (and of course change the IP of the working server to something else), I cannot connect to the ubuntu server.  Here is the client output:

OpenSSH_3.6.1p2, SSH protocols 1.5/2.0, OpenSSL 0x0090701f
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Rhosts Authentication disabled, originating port will not be trusted.
debug2: ssh_connect: needpriv 0
debug1: Connecting to <external name> [<external IP>] port <non-22 port>.

It just hangs there.  Also, the router logs show that a connection was successfully passed to port 22 on the ubuntu server.

On the server side, there is no firewall:
iptables -L -v -n
Chain INPUT (policy ACCEPT 5470 packets, 619K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1791 packets, 382K bytes)
 pkts bytes target     prot opt in     out     source               destination

It's also not tcpwrappers (hosts.deny and hosts.allow have nothing defined in them).

Finally, using tcpdump, I can see that at least some packets are reaching the ubuntu server on port 22.  But even with logging set to DEBUG, no information about the attempted connection shows up in the logs.  Similarly, if I run sshd in debug mode (sshd -d), the connection never even attempts to set up.

I have the exact same problem with another machine running ubuntu desktop 9.04, which is why I categorized it as all variants.

All in all, it appears that ssh packets make it through the router and to the ubuntu server, but are never picked up by sshd.  I can't figure out what is stopping them.  Any ideas?

---

### Post by openfly on 2009-10-19
Confirm your sshd system can route outside the network... have it traceroute something external.  If you are going through a nat / gateway... check firewall rules and ensure you have any necessary port forwarding to port 22 that you might need.

Also turn off reverse dns lookups in the sshd_config to speed up connects.

---

### Post by windependence on 2009-10-19
Don't forward your high port to 22 on the Ubuntu box, AFAIK that doesn't work. Forward your high port to the same port on your Ubuntu box and then start an ssh daemon on that port to listen, e.g. :

```
/usr/sbin/sshd -p 2222
```

That would start a daemon on port 2222. Then you would forward 2222 back to 2222 on the Ubuntu machine.

-Tim

---

### Post by kspider on 2009-10-21
openfly - the system can route to names/IPs outside the local subnet.  I tried running sshd w/o DNS lookups, but it didn't help.

windependence - I thought you were on to something, but unfortunately, it didn't work.  I ran sshd on port 1223 and forwarded that port on the router.  Using `tcpdump port 1223, I could again see packets getting to that port, but sshd never picked them up.

Any more ideas?

---

### Post by Lars Noodén on 2009-10-21
Uncomment the banner line in /etc/ssh/sshd_config on your target system:
[INDENT][FONT="Courier New"]Banner /etc/issue.net[/FONT][/INDENT]
and then fill issue.net with something useful, then reload sshd, to know if you've gotten to the right machine. 

You can also use ssh-keyscan and ssh-keygen to verify via the key, if you don't want to change or use the banner.

[INDENT][FONT="Courier New"]$ ssh-keyscan xx.yy.zz.aa  > /tmp/x
$ ssh-keygen -lf /tmp/x[/FONT][/INDENT]

The idea is to see immediately if you are connecting to the right machine or not.  If not, then use the same methods to figure out where you really are connecting to.

---

### Post by kspider on 2009-10-21
Thanks Lars, but the connection is not making it to sshd, so the Banner never comes in to play.  The connection makes it to the server at the TCP/IP level (confirmed by tcpdump - but I don't know the protocol so I can't confirm that ALL the necessary packets make it), but sshd never sees it.

---

### Post by kspider on 2009-11-05
Any one have any more ideas?  I'm stumped.

Thanks.

---

### Post by Iowan on 2009-11-05
Port can be set up in */etc/ssh/sshd_config*. Dunno how this works versus starting daemon on different port.

---

### Post by Lars Noodén on 2009-11-06
> **kspider said:**
> Thanks Lars, but the connection is not making it to sshd, so the Banner never comes in to play.  The connection makes it to the server at the TCP/IP level (confirmed by tcpdump - but I don't know the protocol so I can't confirm that ALL the necessary packets make it), but sshd never sees it.

If you are logged in at the server and running tcpdump on the server, it is enough to know that some packets are getting through to port 22.

What does it say in sshd_config regarding your port?  
Also, how about the ip number?
For that matter is sshd even running?  Try 
[INDENT][FONT="Courier New"]pgrep -l sshd[/FONT][/INDENT]

---

### Post by kspider on 2009-11-06
Thanks for replying.

sshd is definitely running.  I've always been able to connect to sshd from a computer on the same subnet.

sshd_config specifies port 22.  No ListenAddress is specified, but here is some output from netstat that confirms that sshd is listening on any IP on port 22:

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      0          7313        2766/sshd

---

### Post by Lars Noodén on 2009-11-07
> **kspider said:**
>  I've always been able to connect to sshd from a computer on the same subnet.

Then it's a routing or firewall problem.  Describe what's between you and your server when you try to connect from the 'problem' network.

---

### Post by Zeosa on 2009-11-07
I can't help, but just wanted to chime in, I'm getting the same thing since upgrading to 9.10 here. If I connect to my vpn first, I can ssh in and out to my hearts content, but if trying to connect from outside it's a no go.

I can watch the packets go through the router, I get a login prompt, (initially, I didn't even get this, but after restarting the daemon the login prompt appeared) but after entering my user/password the connection dies after some time. The only thing in the logs are (auth.log) is: 
```

Nov  7 11:45:42 ubuntu sshd[9718]: Timeout, client not responding.

```

---

### Post by windependence on 2009-11-08
> **Lars Noodén said:**
> Then it's a routing or firewall problem.  Describe what's between you and your server when you try to connect from the 'problem' network.

I agree with Lars here. Can you get to this box at all from the outside? I'm thinking incoming packets are OK, but outgoing packets are being dropped or blocked. It would be really helpful if we knew exactly what error you were getting on the outside. Also, are your logs showing you anything funny?

-Tim

---

### Post by Zeosa on 2009-11-08
> **windependence said:**
> I agree with Lars here. Can you get to this box at all from the outside? I'm thinking incoming packets are OK, but outgoing packets are being dropped or blocked. It would be really helpful if we knew exactly what error you were getting on the outside. Also, are your logs showing you anything funny?

-Tim



I can't speak for the OP, but in my case at least, I'm able to access everything except ssh from outside (openvpn, http, imaps are all thats exposed anyway). I've completely flushed my fw rules trying to troubleshoot to no avail.

Out of the 3 9.10 boxes I've got set up, this is the only one with the problem...

---

### Post by Zeosa on 2009-11-08
Well, I finally figured mine out...

kspider, do you happen to have multiple interfaces? if so, double check /etc/network/interfaces to make sure you didn't do the same bone-headed thing I did (set a gateway for 2 seperate interfaces, which results in multiple default gateways lol)

---

### Post by kspider on 2009-11-11
Zeosa - that wasn't exactly it, but you tipped me off to the real problem.  We have two Internet connections here and the server was configured to use a default gateway for one, and the port forward to sshd was coming over the other.

I don't really understand why that should be a problem, but it is.

Thanks!

---

