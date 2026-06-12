---
title: "GUFW unrelated questions about profiles &amp; ufw app.profiles"
date: 2020-06-22
forum: Security
---

### Post by Byb on 2020-06-22
Hi
Is there something under the hood or wip about Gufw profiles to detect interfaces change and prompt user to choose a profile like Windows does ? I ask because of the supplied default profiles names that mimic Windows ones.
Now, about a problem that I meet, please tell me what I do miss about the UPnP and SSDP app profiles: I see they overlap with port 1900, and also there is a walk through ufw-not-local and then a rule in ufw-before-input about uPnP I beleive (--dp=1900). Although it doesn't work for me to puch a hole in my router with miniupnpc. I had to add a home-made rule with -s 192.168.0.0/16 **--sp**=1900 for this to work (I didn't guess, logs suggested this). If not, miniupnpc reported no IGD on the network. I needed this to drop a RPi+SSHd behind a consumer ISP router, assuming I don't want to change settings and UPnP is enabled (/16 because I saw some local nets mainly are 0.0 and others are 1.0, and over all because 224.0.0.0-239.255.255.250 didn't work and I didn't want to leave "any"... I read SSDP replies with unicast).
Please what do I miss with UPnP? I know this is no more recommended (but as long as ISPs drop their boxes with it enabled, let's go*). Maybe the rules available to **G**UFW users (so for ufw-user-input chain) with --dp=1900 are rather intended for ufw-user-output? I read many RFCs and SSDP/UPnP drafts but I did not understand. I only enabled the "Home" profile (Deny all IN, Allow all out) and only added at first a rule for SSH, no other customization.

I have a little understanding of firewalls and I wonder if a request on multicast UDP can have a **RELATED** UDP reply with unicast? 

*ok, this is not a good enough reason.

Thank you for lights

---

### Post by EuclideanCoffee on 2020-06-22
I don't think GUFW has that feature yet. I haven't checked recently, so it may be different.

What you may be looking for is called an Application Firewall, the best example is opensnitch.

[https://itsfoss.com/opensnitch-firewall-linux/](https://itsfoss.com/opensnitch-firewall-linux/)

---

### Post by Byb on 2020-06-27
Hi EuclideanCoffee
Glad to read such a firewall exists. Although this is not what I refered and there was no confusion in my mind about "Application" meaning in my question. It was all about in the context of the meaning in GUFW, that is definition files stored in [COLOR=#0000ff]/etc/gufw/app_profile[/COLOR] directory, e.g. [COLOR=#008000]ssh.gufw_service[/COLOR], which has nothing to do with the ssh(d) binary, and better example to make my question more precise: [COLOR=#008000]/etc/gufw/app_profiles/simple-service-discovery-protocol.jhansonxi[/COLOR]  and [COLOR=#008000]/etc/gufw/app_profiles/upnp_apps.gufw[/COLOR]. I don't understand how/why these very two definition files, once selected, end in iptables rules mainly based on destination port instead of source port, when modifying them to source port made UPnP work for me. In fact I only worked with ssdp's, that is port 1900. And what makes me even more puzzled if the fact that ufw has a default OOTB allow packets rule with _destination_ port=1900 in the **ufw-before-input** chain which is one unskilled user should not change, **ufw-user-input** chain being dedicated for users tweaks, as its name leads to believe.
```
sudo iptables -nvL ufw-before-input

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  15M   28G ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
  61M   35G ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
 3999  164K ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
 3999  164K DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    7  2304 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
 157K   29M ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 5846  828K ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
  429  145K ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
 151K   28M ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
```

---

### Post by EuclideanCoffee on 2020-06-27
Firewalls are quite simple. They handle egress and ingress of data. GUFW is the graphical interface for UFW, which supplies a default profile to block all inbound data unless you specify a rule that "allows" data leaving a specified portal number and data packet identity (udp or tcp). It by default allows all outbound, so ssh and upnp clients will work regardless of packet type.

Regardless of blocking all inbound traffic, you will still have remarkable functionality on your computer. There are plenty of peer-to-peer technology that will rely on your computer to LISTEN for data while online, so the network communication is complete, as long as your computer initiates the connection, which could be done without the user's knowledge.

---

### Post by Byb on 2020-06-28
> **EuclideanCoffee said:**
> Firewalls are quite simple. They handle egress and ingress of data. GUFW is the graphical interface for UFW, which supplies a default profile to block all inbound data unless you specify a rule that "allows" data leaving a specified portal number and data packet identity (udp or tcp). It by default allows all outbound, so ssh and upnp clients will work regardless of packet type.

Regardless of blocking all inbound traffic, you will still have remarkable functionality on your computer. There are plenty of peer-to-peer technology that will rely on your computer to LISTEN for data while online, so the network communication is complete, as long as your computer initiates the connection, which could be done without the user's knowledge.
I know all this. I just wonder why the behaviour doesn't match what I'd expect:
1) I'm aware sshd (=server) is NOT upnp aware. That's why for this very own use case, once I created the ssh[SIZE=2] (g)ufw[/SIZE] rule, I had to run a separate tool, miniupnpc, to ~auto~-punch a hole (kind of automatic portforward, in fact driven by a miniupnpc cron job) in the router so that the path from the outside is complete. Please notice that the letter "c" at the end of miniupnpc stands for client. Please could you tell me more than general info (I think I already gave enough proofs of basic knowledge and search trials above). What do I miss please, i.e. why did I have to add a -p UDP **--sport** 1900 -s 192.168.0.0/16 rule ?
```
0/15 * * * * a=`hostname -I|cut -d" " -f1` && upnpc -a $a -e ssh2pi 15222 15222 TCP 3600
```
I'm not english native speaker so I'd like lenient and nevertheless technical gentlement answer instead of implied RTFM for RFC's & tcpdump/wireshark which will be of no help leaving me alone with my lonesome interpretations.
ATM my interpretation is that upnpc is both client and server, and ufw upnp rule in ufw-before-input chain is only for one of the roles (with help of another rule to allow multicast in a previous chain: ufw-not-local). When the cronjob runs a upnpc server multicast discovery anounce over UDP 1900, the router would as an upnp client unicast answer...that's the whole point of my question : is it possible a reply to be RELATED when using UDP and the channel changes from MCAST to UCAST plus ports source/destination also change?
Am I doing something worst than upnp istself, that no-one at ubuntu forums had the weird idea before  :confused:

[EDIT] : I know my code above is sub-optimal, as I read that upnp-V2 would refuse requests for in-port and out-port to be the same... I will change my code accordingly, but ATM it works as is, the routeur being set to upnp-v1, even I tested it OK when set to V2... another :rolleyes:

---

### Post by EuclideanCoffee on 2020-06-28
>  -p UDP **--sport** 1900 -s 192.168.0.0/16 rule ? 

With the default UFW rules, you will need --sport 1900 opened to receive broadcasts.

> 
[FONT=Verdana][SIZE=-1][COLOR=#000066][FONT=Verdana][SIZE=2][COLOR=#000066]This  UDP port is opened and used by Universal Plug N' Play (UPnP) devices to  receive broadcasted messages from other UPnP devices. UPnP devices  broadcast subnet-wide messages to simultaneously reach all other UPnP  devices.
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=-1][COLOR=#000066][FONT=Verdana][SIZE=2][COLOR=#000066]

This problem appears pretty common.

[https://askubuntu.com/questions/1028570/ufw-blocking-upnp-port-mapping](https://askubuntu.com/questions/1028570/ufw-blocking-upnp-port-mapping)
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by Byb on 2020-06-28
> **EuclideanCoffee said:**
> With the default UFW rules, you will need --sport 1900 opened to receive broadcasts.
[FONT=Verdana][SIZE=-1][COLOR=#000066][FONT=Verdana][SIZE=2][COLOR=#000066]
This problem appears pretty common.

[https://askubuntu.com/questions/1028570/ufw-blocking-upnp-port-mapping](https://askubuntu.com/questions/1028570/ufw-blocking-upnp-port-mapping)
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

Broadcast now ? Although, I read UPnP draft where they state replies to multicast queries are done with unicast. This is surely what was puzzling me... also because I'm far from being an expert.
And about your link EuclieanCoffee, 2 years is not so old, so maybe ufw team did not have time or do not want to make upnp work OOTB, who knows.
Ok, glad not to be alone with this issue and my workaround was not so bad.
Sorry for the noise, this is my story and anybody's one too on the Internet where all answers and their opposite exists, the problem is to ask the good/well worded question, which is equivalent to have the good answer... so don't ask :)

Thank you man 8-)

---

