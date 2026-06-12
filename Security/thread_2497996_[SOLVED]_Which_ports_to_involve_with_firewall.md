---
title: "[SOLVED] Which ports to involve with firewall?"
date: 2024-05-25
forum: Security
---

### Post by 909mjolnir on 2024-05-25
if I use the common familiar Linux firewall stuff, how do I know which ports to edit?  
This is the main stumbling block I have so my systems end up insecure and the hackers in this area are fierce.   

Please help, if you can.  

I'm in between distros for now, so I have nothing in front of me yet.  

SOLVED:  See posts by 'TheFu' in this thread.  
Thanks 'TheFu' !  Awesome response.

---

### Post by currentshaft on 2024-05-25
What do you mean by "edit"? Blocking ports is typically not necessary unless you're planning on vising untrusted networks, and even then the default Ubuntu installation does not really expose anything.

---

### Post by 909mjolnir on 2024-05-27
@[[COLOR=#000000]currentshaft[/COLOR]]("https://ubuntuforums.org/member.php?u=2187870")[COLOR=#000000] :

Yeah, I've heard that before, years ago.  But it just isn't true anymore.  There's tone of articles since about 2019 talking about Linux's need for better security defaults and implementation.  I can't find hardy any tutorials yet.  [/COLOR]

---

### Post by #&amp;thj^% on 2024-05-27
This looks interesting: [https://safing.io/](https://safing.io/)

It will take a small learning curve.

---

### Post by currentshaft on 2024-05-27
> **909mjolnir said:**
> @[[COLOR=#000000]currentshaft[/COLOR]]("https://ubuntuforums.org/member.php?u=2187870")[COLOR=#000000] :

Yeah, I've heard that before, years ago.  But it just isn't true anymore.  There's tone of articles since about 2019 talking about Linux's need for better security defaults and implementation.  I can't find hardy any tutorials yet.  [/COLOR]

It is true. The burden is on you to provide objective evidence to the contrary. A vague first-hand recollection of some 5 year old "articles" does not suffice for the same. The lack of "hardy any tutorials [sic]" is proof you don't need to worry about this problem.

If you want to care about security, that's great, but the network firewall is not something to concern yourself with, unless you travel to sketchy places, and even then the default set of services on Ubuntu presents no risk.

---

### Post by Rubi1200 on 2024-05-28
> **909mjolnir said:**
> if I use the common familiar Linux firewall stuff
What does that mean?

Are you using a GUI frontend?

There are many threads on the forum that discuss ports and basic rules about what to block (or not). 

Would be worthwhile searching for them I think.

---

### Post by gezzer2 on 2024-05-28
i use GUFW which i enable then set to 'public' it does most of the basic 'firewall stuff' that is needed ..

---

### Post by TheFu on 2024-05-28
For high security, block everything coming in and everything going out.  Then open outbound ports in the firewall that are needed for the specific things you do.  

For example, do you want to connect to a mail server for reading and replying to email?  That's usually port 465/tcp (SMTPs) and 993/tcp (IMAPS).

Do you want to access remote websites?  Those use post 80/tcp and 443/tcp, typically.  Streaming videos may hop to a different port and may use UDP instead of TCP.
You'll likely want DNS to be allowed. Depending on which type of DNS you use, that can be on port 53/udp or 53/tcp or if you use DNS-over-HTTPS, that would use 443/tcp.

Want to print to a network printer?  CUPS is usually on port 631/tcp.

The major ports used for different network services are listed in the /etc/services file. May want to review that.

CIFS, NFS, ssh, are a few other things commonly used.

What most people do is to block all incoming connections, then allow all outbound connections on their workstations.  Then they would add specific rules for the inbound network services only if needed.  You can allow those for any systems on the same subnet or for specific IPs on the subnet.  If you do specific IPs, then you'll need to have a well-managed network.
For one of my LAN servers, here are all the inbound firewall rules
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
4949/tcp                   ALLOW       172.22.22.4               
111                        ALLOW       172.22.22.0/24            
2049                       ALLOW       172.22.22.0/24            
22/tcp                     ALLOW       172.22.22.0/24            
8096                       ALLOW       172.22.22.0/24            
13025                      ALLOW       172.22.22.0/24            
5353                       ALLOW       172.22.22.0/24            
3142                       ALLOW       172.22.22.0/24             # apt-cacher-ng
1900                       ALLOW       172.22.22.0/24             # DLNA
6600                       ALLOW       172.22.22.0/24            
123/udp                    ALLOW       172.22.22.0/24            
7359/udp                   ALLOW       172.22.22.0/24             # Jellyfin Discovery UDP
8000                       ALLOW       172.22.22.0/24             # Jellyfin TV Icons
8181                       ALLOW       172.22.22.0/24
```
Each was carefully selected for specific reasons.  Another servers has these rules:
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
631                        ALLOW       172.22.22.0/24            # Printing
22                         ALLOW       172.22.22.0/24            # ssh
4949/tcp                   ALLOW       172.22.22.4
5353/udp                   ALLOW       Anywhere                  # zeroconf/avahi/mdns
2049                       ALLOW       172.22.22.0/24            # NFS
13025                      ALLOW       172.22.22.0/24            # NFS
111                        ALLOW       172.22.22.0/24            # ident

```

My desktop has these rules:
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere                  
4949/tcp                   ALLOW       172.22.22.4          
```

I figured seeing real examples would be helpful.  These are only the rules controlled by UFW.  I have some other rules that get added dynamically when using VPN software.  My VPN server has a bunch of rules to allow connections between different subnets.

---

### Post by currentshaft on 2024-05-28
With all due respect, a traditional firewall as you've described is effectively 100% security theater which is not going to prevent Real Bad Things(tm) from happening.

Local malware will just use TCP port 443, the same port which is allowed for web browsing.

If anything, these sort of firewalls actually worsen security because they provide a false sense of protection, by creating a proverbial moat which appears impenetrable but is in reality a weak and meaningless boundary.

If you want security, do not install and expose unnecessary services, and those which are exposed should use mutual authentication based on strong crypto. This is also known as "zero trust".

---

### Post by TheFu on 2024-05-29
Security is about layers.  The first layer is always in the network, preventing access to attackers that don't have any need to have access.  Home user's aren't banks.  Avahi isn't really something that can be "authenticated", at least not today, so the best we can do is to prevent access by other clients outside the expected LAN.  Of course, other protocols and tools DO support key-based authentication.  Use keys/certs whenever possible. Avoid passwords when possible, but sometimes that's all we have available.

BTW, you may notice that in my firewall rules, port 443 isn't open, so the only way that access would be allowed is if I'm running a web-clients that is accessing a remote server and opens a connection.  3rd parties don't get to ride that connection. They are blocked unlike with many home routers.  Linux firewalls aren't THAT dumb.

For example, here's a 3rd party trying to piggyback on a request, but being blocked ... 
```
May 28 09:28:50 hadar kernel: [859693.112304] [UFW BLOCK] IN=br0 OUT= MAC=0c:9d:92:87:ce:13:00:0d:b9:41:67:05:08:00 SRC=213.186.33.19 DST=172.22.22.6 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=48698 DF PROTO=TCP SPT=443 DPT=33398 WINDOW=18 RES=0x00 ACK URGP=0
```

This is an example for why we need both the router firewall AND the on-system, software firewall enabled.  BTW, my router isn't a dumb consumer router, but clearly, it isn't blocking everything unwanted. If it was, then the desktop system would never have seen the request from OVH and needed to block it.

Layers of security.  That's the plan.

For services that do have authentication, say ssh, preventing outsiders may not be needed, but there have been bugs, so I use tcp-wrappers and ssh-keys, in addition to the firewall blocks.  I'm a belts AND suspenders person. I assume I'll make a human mistake from time to time and want the other layers of security to protect the service for those occasions.

I also run a VPN for remote access rather than allowing things like NextCloud to sit on the internet.  No VPN?  No access to our family nextcloud server.  Of course, inside the trusted, wired, network things different.  However, wifi systems inside the building still have to use the VPN to authenticate to the network first.  I know that wifi cannot be trusted.  It has been proven over and over.  Don't get me started about Bluetooth.  Just-don't-use-it.  They have marketing people who smile way too much, perhaps because they know how bad the security of it is. IDK.

Belts and suspenders.

---

### Post by currentshaft on 2024-05-29
> **TheFu said:**
> Security is about layers.  The first layer is always in the network, preventing access to attackers that don't have any need to have access.  Home user's aren't banks.  Avahi isn't really something that can be "authenticated", at least not today, so the best we can do is to prevent access by other clients outside the expected LAN.  Of course, other protocols and tools DO support key-based authentication.  Use keys/certs whenever possible. Avoid passwords when possible, but sometimes that's all we have available.


Attackers already don't have access to internal networks due to NAT: that IS the security defense against outside threats. No one can reach your computer from the Internet unless you enable port forwarding or other means of access explicitely.

> **TheFu said:**
> 
BTW, you may notice that in my firewall rules, port 443 isn't open, so the only way that access would be allowed is if I'm running a web-clients that is accessing a remote server and opens a connection.  3rd parties don't get to ride that connection. They are blocked unlike with many home routers.  Linux firewalls aren't THAT dumb.


I don't understsand what this means. Linux firewalls ARE that dumb. They are not layer 7; they have no idea what application is talking to what. They know ports and IP addresses, that's it. When you open your firewall for "accessing a remote server", so does the malware. This is all, by the way, assuming the malware doesn't have root (which is trivial to get on Linux) and just ignores your firewall altogether.

> **TheFu said:**
> 
For example, here's a 3rd party trying to piggyback on a request, but being blocked ... 
```
May 28 09:28:50 hadar kernel: [859693.112304] [UFW BLOCK] IN=br0 OUT= MAC=0c:9d:92:87:ce:13:00:0d:b9:41:67:05:08:00 SRC=213.186.33.19 DST=172.22.22.6 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=48698 DF PROTO=TCP SPT=443 DPT=33398 WINDOW=18 RES=0x00 ACK URGP=0
```


What's hilarious about this example is you're actually showing a return packet from a server being blocked to you. Which means your computer has already sent a packet to that server, which you allegedly "block". Oops!

> **TheFu said:**
> 
This is an example for why we need both the router firewall AND the on-system, software firewall enabled.  BTW, my router isn't a dumb consumer router, but clearly, it isn't blocking everything unwanted. If it was, then the desktop system would never have seen the request from OVH and needed to block it.

Layers of security.  That's the plan.

Layers of security which make sense. Having two firewalls, with one of them on a device behind a trusted NAT, makes zero sense. It is the equivalent of using multiple full disk encryption methods when LUKS does a fine job. Sorry, but you have not demonstrated the value of the same to me.

> **TheFu said:**
> 
For services that do have authentication, say ssh, preventing outsiders may not be needed, but there have been bugs, so I use tcp-wrappers and ssh-keys, in addition to the firewall blocks.  I'm a belts AND suspenders person. I assume I'll make a human mistake from time to time and want the other layers of security to protect the service for those occasions.

Okay, but where is the limit? Why not have three layers of security, or four, or five? Because of diminishing returns, added complexity and possibly even increased attack surface from it.

> **TheFu said:**
> 
I also run a VPN for remote access rather than allowing things like NextCloud to sit on the internet.  No VPN?  No access to our family nextcloud server.  Of course, inside the trusted, wired, network things different.  However, wifi systems inside the building still have to use the VPN to authenticate to the network first.  I know that wifi cannot be trusted.  It has been proven over and over.  Don't get me started about Bluetooth.  Just-don't-use-it.  They have marketing people who smile way too much, perhaps because they know how bad the security of it is. IDK.

Belts and suspenders.

That's great, and for remote access those tools have a place. We're discussing a machine on a trusted local network behind a NAT that's not running any public services. It does not need a firewall applied.

---

### Post by TheFu on 2024-05-29
> **currentshaft said:**
> Attackers already don't have access to internal networks due to NAT: that IS the security defense against outside threats. No one can reach your computer from the Internet unless you enable port forwarding or other means of access explicitely.


Uh ... you can believe that if you like. I know different.  I've seen it.  NAT isn't a firewall. People are confused about that. I've seen traffic from outside get inside a LAN that had no external ports open or forwarded.  This was at a client's office. They did DoD work from IPs that didn't have any domain name assigned beyond the ISP subnet as a way to obscure who they were.

Security issues often break down to who understands the RFC better and which side understands the specifications.  Often, there are things NOT in the RFCs, so specific implementations ignore those aspects, leaving security issues.

For a home network, whether a firewall is needed on each system depends on many possible things, including the risks and likely attackers.

Lots of people definitely run their LAN systems without a firewall on each computer.  That's their choice.  When they take their laptop into the world, they definitely NEED a firewall enabled.  I think we can agree on that.

---

### Post by 909mjolnir on 2024-05-29
@TheFu

My god, man, you have the answer.  
I don't know how anybody ever learns this stuff.  
It's not exactly common knowledge.  

Thanks so much.  
I will see if I can give it a go eventually.  
I don't want to mess up my internet.  

But thanks!  Seems like the answer.  

> **TheFu said:**
> For high security, block everything coming in and everything going out.  Then open outbound ports in the firewall that are needed for the specific things you do.  

For example, do you want to connect to a mail server for reading and replying to email?  That's usually port 465/tcp (SMTPs) and 993/tcp (IMAPS).

Do you want to access remote websites?  Those use post 80/tcp and 443/tcp, typically.  Streaming videos may hop to a different port and may use UDP instead of TCP.
You'll likely want DNS to be allowed. Depending on which type of DNS you use, that can be on port 53/udp or 53/tcp or if you use DNS-over-HTTPS, that would use 443/tcp.

Want to print to a network printer?  CUPS is usually on port 631/tcp.

The major ports used for different network services are listed in the /etc/services file. May want to review that.

CIFS, NFS, ssh, are a few other things commonly used.

What most people do is to block all incoming connections, then allow all outbound connections on their workstations.  Then they would add specific rules for the inbound network services only if needed.  You can allow those for any systems on the same subnet or for specific IPs on the subnet.  If you do specific IPs, then you'll need to have a well-managed network.
For one of my LAN servers, here are all the inbound firewall rules
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
4949/tcp                   ALLOW       172.22.22.4               
111                        ALLOW       172.22.22.0/24            
2049                       ALLOW       172.22.22.0/24            
22/tcp                     ALLOW       172.22.22.0/24            
8096                       ALLOW       172.22.22.0/24            
13025                      ALLOW       172.22.22.0/24            
5353                       ALLOW       172.22.22.0/24            
3142                       ALLOW       172.22.22.0/24             # apt-cacher-ng
1900                       ALLOW       172.22.22.0/24             # DLNA
6600                       ALLOW       172.22.22.0/24            
123/udp                    ALLOW       172.22.22.0/24            
7359/udp                   ALLOW       172.22.22.0/24             # Jellyfin Discovery UDP
8000                       ALLOW       172.22.22.0/24             # Jellyfin TV Icons
8181                       ALLOW       172.22.22.0/24
```
Each was carefully selected for specific reasons.  Another servers has these rules:
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
631                        ALLOW       172.22.22.0/24            # Printing
22                         ALLOW       172.22.22.0/24            # ssh
4949/tcp                   ALLOW       172.22.22.4
5353/udp                   ALLOW       Anywhere                  # zeroconf/avahi/mdns
2049                       ALLOW       172.22.22.0/24            # NFS
13025                      ALLOW       172.22.22.0/24            # NFS
111                        ALLOW       172.22.22.0/24            # ident

```

My desktop has these rules:
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere                  
4949/tcp                   ALLOW       172.22.22.4          
```

I figured seeing real examples would be helpful.  These are only the rules controlled by UFW.  I have some other rules that get added dynamically when using VPN software.  My VPN server has a bunch of rules to allow connections between different subnets.

---

### Post by 909mjolnir on 2024-06-14
One thing to keep in mind, sometimes people hack us Linux guys, and some of them pass themselves off as doing technical support for us when we get clobbered.  So beware.

---

### Post by The Cog on 2024-07-23
@TheFu: Re: "For example, here's a 3rd party trying to piggyback on a request, but being blocked ..."
Can you explain more about that packet? And what you mean by piggy-backing?
At first glance, it looks like a normal ACK on an existing connection, outgoing judging by the addresses and port numbers. But if that were the case, the firewall shouldn't drop it.
Maybe a hangover from a recently closed outgoing connection?
Maybe a probe to test whether you are using stateless firewall rules, or stateless NAT (see if they get a RST response).
What else do you read into it?

---

### Post by TheFu on 2024-07-23
> **kjones120320 said:**
> <snip>

This post looks like a copy/pasted answer from a "how to setup an all-in-one linux server" from 20 yrs ago.  Times are different.

Those are for servers on the internet and nobody should be using plain FTP there the last 22 yrs.  Just remove that from your list.  

Same for the unencrypted IMAP/POP3 ports.  There are TLS encrypted ports which may need to be enabled, but for email, we stopped allowing client-access to email directly from the internet nearly 15 yrs ago and only allow access with a full VPN connection first.

And it is unlikely anyone really should have their DNS open for public use either. Internal and those using the organization's VPN can use our DNS. No need for the world to have it. Pay professionals $20/yr to manage your public DNS records. 1000x more secure, if they are reputable.  Outbound DNS doesn't require inbound DNS ports to be enabled.

While security through obscurity isn't great, moving ssh to non-standard ports will drastically reduce the hack attempts in your logs. Of course, no internet ssh connection should ever be allowed using a username/password. Only key-based authentication and preferably limited to the subnets where you know the people who need access are located.  Blocking 99% of the internet from ssh into your systems still leaves huge numbers of possible attackers, but it is better than not blocking any.

---

### Post by currentshaft on 2024-07-23
> **kjones120320 said:**
> <snip>

I think you're confused, because that's literally what Network Address Translation (NAT) is: a default-deny policy to all non-internal traffic, also known as ... a firewall.

> **TheFu said:**
>  I've seen traffic from outside get inside a LAN that had no external ports open or forwarded.  This was at a client's office. They did DoD work from IPs that didn't have any domain name assigned beyond the ISP subnet as a way to obscure who they were.

That's a first hand anecdote, without any qualified evidence, just a "trust me bro" which is meaningless for productive discussions.

Do you have objective evidence of this happening, which has been verified by a third party, or is this one of those "look at how long I've used Linux" ego trips?

> **TheFu said:**
>  
Lots of people definitely run their LAN systems without a firewall on each computer.  That's their choice.  When they take their laptop into the world, they definitely NEED a firewall enabled.  I think we can agree on that.

90%+ of desktops and servers don't have a "firewall" and rely on NAT to protect themselves from badness. Yet the sky is not falling and people aren't being "hacked" left and right as a result.

Unless you are deliberately installing services with network listeners, you do not need a firewall.

---

### Post by coffeecat on 2024-07-23
> **TheFu said:**
> This post looks like a copy/pasted answer from a "how to setup an all-in-one linux server" from 20 yrs ago.  Times are different.

In fact, more recent than that, sad to say. It was a copy-paste from ChatGPT or one of its cousins. I've edited out the AI-garbage from the quote box in your post. Thanks for noticing the questionable content. Please report anything you think might be AI-generated so that we can investigate. The so-called user has been banned, and their post removed.

---

### Post by coffeecat on 2024-07-23
For heavens sake, I've only just removed AI-garbage from one post, and already someone else has posted and quoted from the same AI spam. Please people - if you suspect AI-generated text, **do not quote it**. It's only more garbage for the staff to clean up

---

