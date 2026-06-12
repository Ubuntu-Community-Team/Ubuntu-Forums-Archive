---
title: "IP forwarding through an intermediate host"
date: 2018-04-09
forum: Server Platforms
---

### Post by luckymoonboy1 on 2018-04-09
Hello!

So I am having a problem routing connections through an Ubuntu 16.04 server and forwarding the originating IP address. What I need to accomplish is when A connects to B, B routes it to C, and C sees A's IP address. I know I should be able to accomplish with with some sort of transparent proxy but I am running into an issue. I can get the data to pass through just fine however the IP matches B and not A. There are some constraints to this also, I cannot make any modifications to the various hosts(A), only B and C. 

As for why I want to do this I run a Minecraft server and users, located in the central United States region, are experiencing 12-40% packet loss at random intervals, myself included. I can access the server through my own VPN with no issues. I am attempting to create a sub-domain that will allow users who have trouble with the standard connection to connect through it and avoid whatever is causing the packet loss between the central US and France where the server is hosted. They cannot have B's IP though as the Minecraft server will not allow users to connect when another user is on with the same IP. This would also mean that IP banning would not be an option if that action was needed.

What I have tried so far:
 IP forwarding in /etc/sysctl.conf is set to 1 and is uncommented.
```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
```

I have tried using redir. The following is the result and the connection cannot be made at all. Removing the --transproxy option allows a connection to be made but B's IP is still being sent.
```
alexander@CoastalJawa:~$ sudo redir --syslog --transproxy --lport=25565 --laddr=<Domain for B> --cport=25565 --caddr=<Domain for C> --name=redir
bind_addr: cannot bind to forcerd outgoing addr: Cannot assign requested address
bind_addr: cannot bind to forcerd outgoing addr: Cannot assign requested address
```
The bind_addr: etc. is the same thing that is logged to the syslog.

I attempted to use socat for the same process, it does not however provide a transparent proxy or forwarding option though so I suspected it would not accomplish what I wanted it to. I did confirm this though. The connection can be made using the following, but once again only B's IP is shown.
```
sudo socat TCP-LISTEN:25565,fork TCP:<Domain for C>:25565
```

I have also attempted to route the connection simply through iptables. Currently iptables is configured to allow to following:
```
-A PREROUTING -p tcp -m tcp --dport 25565 -j DNAT --to-destination <IP for C>:25565
-A POSTROUTING -d <IP for C>/32 -p tcp -m tcp --dport 25565 -j MASQUERADE
```
This allows traffic to freely pass through but once again without the forwarded IP.

I haven't attempted any rule modifications in ufw as I haven't a clue where to start with that. Any suggestions or solutions from applications to rule modifications are welcome but they do need to be relatively secure options.

Thank you

---

### Post by wildmanne39 on 2018-04-09
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by The Cog on 2018-04-09
I think the networking forum might be more appropriate, but I don't suppose it matters that much.

I don't think what you are trying to do is going to be easy. And here's why. I assume the user you are trying to help is A, your server is B and the minecraft server is C. If minecraft server C sees A's address, it will send all its packets for A directly back to A - it will have no reason to try to send the packets back via your server B, and no way to do that even if it wanted to. 

This means that A must know it is talking to C, otherwise it will ignore the responses from C as being from something unknown. So A and C must believe that they are connected to each other.

The above rules out any use of address translation. Now, with careful setting up of a VPN between A and B, and tweaking routing tables, it is possible to make A connect to C via a VPN to B. Getting A to use its public IP address for the connections through the VPN tunnel might be a challenge. 

But you cannot influence the return path from C to A because you cannot change C's configuration. So at best, you can only insert B into one direction of the connection, and I have doubts as to whether this would help.

If A is behind a NAT router (most home users are) then you cannot use a VPN to bypass the NAT in one direction only (addresses won't match if you try asymmetric routing round NAT) so I can not think of any solution at all.

---

