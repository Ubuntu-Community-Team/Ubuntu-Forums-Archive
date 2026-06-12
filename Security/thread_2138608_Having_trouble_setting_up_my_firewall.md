---
title: "Having trouble setting up my firewall"
date: 2013-04-24
forum: Security
---

### Post by Dural on 2013-04-24
For some reason my ISP (AT&T) had some connection issues a few hours ago. They're fixed now, but I've had trouble connecting to the Internet for the past 3-4 hours. The only way I can connect is to turn off GUFW and I would rather not do that. I decided to reset my settings and use the following guide to setup the firewall rules:
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

When I turn it on, the rules don't work and I can't access any pages online. Here's the rules that I setup

> DHCP Access - Port 67 and 68 UDP

Web Access - Ports 80 and 443 Protocol TCP

DNS Access - Port 53 Protocol TCP and UDP (This is absolutely required)


I'm not sure what I'm doing wrong. Do I need to restart the computer after I'm done? I've tried turning off the firewall and turning it back on in GUFW but that doesn't seem to work.

Here's the message I got in Epiphany:
[IMG]http://i272.photobucket.com/albums/jj196/MargeSimpson/ef7ad0a3-06f4-4f87-bf42-4609498ae305_zpsa0d00a8a.jpg[/IMG]

---

### Post by Doug S on 2013-04-24
Perhaps you could post the iptables rule set that results from your gufw settings. Command:```
sudo iptables -v -x -n -L
```And be sure that the rules you added apply to the destination port, as opposed to the source port. Are you sure the AT&T issues are actually fixed?

---

### Post by Dural on 2013-04-26
Here's the output I got from iptables when I turned on the firewall. 
Here were the settings I have set up in GUFW:
Status: ON
Incoming : Deny
Outcoming : Deny

Firewall Rules:
67,68 - UDP
80, 443 - TCP
53 - Both

All were set to ALLOW OUT
They activated for ipv4 and ipv6. I'm not sure how to turn off the latter in Linux or even if I need to. 
```
Chain INPUT (policy DROP 8 packets, 432 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      56     3512 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      56     3512 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       8      432 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       8      432 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       8      432 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       8      432 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 58 packets, 3580 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     106     6660 ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     106     6660 ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      58     3580 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      58     3580 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      58     3580 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      58     3580 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
       0        0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
       0        0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      48     3080 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
       8      432 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
       8      432 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
      48     3080 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
      58     3580 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-logging-deny (2 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-not-local (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       8      432 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
       0        0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit-accept (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination
```

---

### Post by Doug S on 2013-04-26
Well, the rules you want are not in the resulting iptables rule set. I do not use gufw or ufw or anything other than iptables directly, so do not know about that side of it.

---

### Post by Dural on 2013-04-26
I'm afraid I'm not too familiar with iptables. Do you think uninstalling and reinstalling GUFW might work? I only started having this problem about 2 days ago when the connection went out briefly. It went back to normal and my firewall still worked. Then, I tried adding a rule for FTP using the preset settings in GUFW and that's when it stopped working. I even reset my rules and tried a new set and it didn't work.

---

### Post by CharlesA on 2013-04-26
I don't use ufw either, but here's what I refer to for iptables. :)
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by cariboo on 2013-04-26
Why have you got ports 80 and 443 open, are you running a web server? Ports 80 and 443 are only for incoming connections, web browsers use random high ports to connect to web pages. Check my connection to Google:

```
chromium- 13556 cariboo  126u  IPv4 282352      0t0  TCP 192.168.0.102:**39320**->173.194.33.36:**443** (ESTABLISHED)
```

Note that Chromium is using port 39320 to connect to port 443 on Google's server. As a second example, my-weather-indicator uses port 40877 to connect to port 80 of the Canadian Weather service in Montreal:

```
my-weathe 32754 cariboo   42u  IPv4 249302      0t0  TCP 192.168.0.102:**40877**->142.4.213.166:**80** (CLOSE_WAIT)
```

By blocking all out going except for 67,68, 80, 443 and 53 you are effectively blocking your own access to the internet.

---

### Post by Doug S on 2013-04-27
@Cariboo907: The OP is using a very tight firewall reference written by Dangertux, and (I think) converted to a wiki by Miss Daisy. It is supposed to only allow outgoing to destination ports 80, 443, etc, from any source port. Both those desintation ports are in your examples, and that is what is supposed to be permitted (at least that is my understanding). Some of Dangertux's screen shots got lost, and perhaps some valuable information with them.

@Everyone: All I know from looking at the iptables is that the desired rules are not there. I do not know why. I do not know if uninstalling and re-installing GUFW would help.

---

### Post by Dural on 2013-04-27
I'm trying uninstalling and reinstalling GUFW. I also did the same for UFW. I'm going to try the same rules later.

---

### Post by Dural on 2013-04-30
Alright I tried the same rules after I uninstalled and reinstalled UFW and GUFW. They still didn't work. I want to try using iptables, but the tutorial I used wasn't clear about where the finished script should be saved. So for the time being I've decided to keep the firewall off.

---

### Post by clearski on 2013-05-01
> **Dural said:**
> Alright I tried the same rules after I uninstalled and reinstalled UFW and GUFW. They still didn't work. I want to try using iptables, but the tutorial I used wasn't clear about where the finished script should be saved. So for the time being I've decided to keep the firewall off.

If you are not hosting any server on your machine, as others said before, you should allow **outgoing** connections and block **incoming** ones which are not a response to a session started by one of your applications (which *ufw* does by default, unless the rules were altered).

See this thread because I've had the same questions, too:

[http://ubuntuforums.org/showthread.php?t=2137243&](http://ubuntuforums.org/showthread.php?t=2137243&)

The last message explains how to reset* ufw *and set it to default rules, though I would now add allow outgoing firstly, then deny incoming. You don't even need gufw, because the firewall once enabled is loaded at every startup.

I also assume that you're behind a router. My router has a firewall, does some filtering, so if it's properly configured, it should do a good job for basic networking (browsing & email). Everytime I check the logs of the router I see how great it does in blocking & filtering. It is very important how you configure your browser (what it can or cannot do, there are some great add-ons which IMHO are really necessary) and what you visit and click after you're alone out there.

---

### Post by HermanAB on 2013-05-01
Hmm, note that you don't really need a firewall script.  Firewalls are mainly there to protect Windows machines.

---

### Post by Dural on 2013-05-06
> **clearski said:**
> If you are not hosting any server on your machine, as others said before, you should allow **outgoing** connections and block **incoming** ones which are not a response to a session started by one of your applications (which *ufw* does by default, unless the rules were altered).

See this thread because I've had the same questions, too:

[http://ubuntuforums.org/showthread.php?t=2137243&](http://ubuntuforums.org/showthread.php?t=2137243&)

The last message explains how to reset* ufw *and set it to default rules, though I would now add allow outgoing firstly, then deny incoming. You don't even need gufw, because the firewall once enabled is loaded at every startup.

I also assume that you're behind a router. My router has a firewall, does some filtering, so if it's properly configured, it should do a good job for basic networking (browsing & email). Everytime I check the logs of the router I see how great it does in blocking & filtering. It is very important how you configure your browser (what it can or cannot do, there are some great add-ons which IMHO are really necessary) and what you visit and click after you're alone out there.

I intend to do some testing of my web page on my computer. That would require instaling LAMP. Would that count as running a server?

---

### Post by haqking on 2013-05-06
> **Dural said:**
> I intend to do some testing of my web page on my computer. That would require instaling LAMP. Would that count as running a server?

any machine which provides a service is a server, and yes it would be a web server

---

