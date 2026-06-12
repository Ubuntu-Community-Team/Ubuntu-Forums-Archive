---
title: "Firewall adjustments GUF -GUFW"
date: 2021-08-08
forum: Security
---

### Post by steveson on 2021-08-08
Hi out there

I'm trying to configure my GUFW.

Well, for now I understood, that it is good to set profile's options to Incoming/Outcoming= deny and then set up specific rules for each application.

I do not really understand how the ports are working... In the forum, I red that each application runs in its own port. I used: $ sudo nmap -p 1-65535 -sT localhost and result is:


Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2021-08-08 13:11 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00014s latency).
Not shown: 65532 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
7793/tcp open  unknown
9050/tcp open  tor-socks

seems that those are the only used ports?! 

On which ports will I configure then firefox and thunderbird (and other apps which should get access to the internet) ? I do not have Tor installed, so it makes me wonder why it shows me this port...:roll:

I'm new to Linux and really interested on understanding more on how to work with this system. So if anybody has the mood to explain me a bit around that topic, would be great.

Thanks and Cheers
Steve

---

### Post by steveson on 2021-08-08
Ah, and I used: sudo ss -lntup

which gives quite some qbittorrent ... which I've never used and most likely will not use.
And there is the avahi- daemon, of which I do not really understand what for it is.

Any help highly welcome :)

---

### Post by The Cog on 2021-08-08
Running nmap against localhost is pointless, because ufw (and any sane firewall application) always allows the host to talk to itself.
sudo ss -lntup will tell you what processes are listening on what sockets - this may be what you need to know.

I would advise that you allow all outgoing connections. This will allow browsers etc. to work as they should, making outgoing connections to anywhere on the internet. 
Deny all incoming connections except for applications/ports you know you want to receive connections from outside. Consider limiting which external addresses you allow to connect in, to your home network only for instance.
If you open ssh incoming, configure it to only accept password-less logins using public keys, perhaps listen on a non-standard port instead of port 22, and install failtoban to block addresses that try to brute-force access.

---

### Post by TheFu on 2021-08-08
The Cog nailed it.  In case that isn't clear, I'll try with different words.

On computers, different processes will often communicate using sockets and the localhost addresses.  Those are 127.x.x.x/8, so there are a bunch, 16777214 to be exact. That's just IPs they can use, then add in the 64K ports for each ...  anyways, don't worry about daemons listening on localhost.  

What we care about are daemons listening on the public IP(s) or LAN IPs.  To see which are open to the outside, you'll want to scan from a different computer.

Network security is about layers.  If your computers are behind a router with the firewall enabled, then you don't need to worry much about internet attacks. If you ever open any firewall ports or if you have laptops, then setting up the firewall rules on the computer become more important.  

Almost all my systems have minimal computer firewalls.  These have just a few rules like deny all inbound and allow all outbound because that is simple and a reasonable starting point.  That is the default for ufw ... which is an interface into the kernel's firewall.  For most people, that's the end of it.

```
$ sudo ufw status verbose
Status: active
Logging: on (low)
[COLOR="#FF0000"]Default: deny (incoming), allow (outgoing), deny (routed)
[/COLOR]New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    172.16.0.0/12             
22/tcp                     LIMIT IN    Anywhere
```
My LAN subnet for that system is 172.22.22.0/24. But I have multiple LAN subnets, so to make life easier, I allow the entire class B private subnet access.  The 22/tcp rule is redundant - that's for ssh.  I really want to be able to ssh into all my systems from the LAN ... or anywhere that isn't blocked already.

Some other systems here get different rules:
```
$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     LIMIT IN    Anywhere                  
8080                       DENY IN     Anywhere                  
137,138/udp (Samba)        ALLOW IN    Anywhere                  
139,445/tcp (Samba)        ALLOW IN    Anywhere           
``` 
I was doing some Samba testing and enabled it.  I need to disable samba and the firewall.  Just get into the habit of 
[LIST=1]
[*]  enable a network service
[*]  setup a firewall rule for that service
[/LIST]
Ok, the samba rule is gone:
```
$ sudo ufw status numbered 
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     LIMIT IN    Anywhere                  
[ 2] 8080                       DENY IN     Anywhere    
```    

For ssh, I also use **fail2ban**.  This ties into the firewall and dynamically enabled/disables it based on brute force attacks. By default, fail2ban is already configured for port 22/tcp (the default sshd port).  On the LAN, I use the default port. Over the internet, I have the router do port translation from the Public IP:64000 ---> LAN IP:22 .  That way, I can absolutely know which route my ssh connections take based on the port used in the command.  It's a security thing.

As you can see, on these systems I'm not blocking outbound anything. My systems are remotely accessed almost always, so if I get the firewall rules wrong, it would be a challenge to regain access.  Some systems have email blocks, so they cannot send email out except to my email server. That prevents my server from being abused by any of the clients as a spammer system.  That rule is setup only on high-risk systems.

---

### Post by steveson on 2021-08-12
Many thanks TheFu and The Cog!

It took me a while to understand it :D

Thanks for updating and educating me - really helpfull

Cheers

---

