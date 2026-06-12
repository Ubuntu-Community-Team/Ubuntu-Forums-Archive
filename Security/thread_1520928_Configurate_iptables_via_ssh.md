---
title: "Configurate iptables via ssh"
date: 2010-06-30
forum: Security
---

### Post by thangnguyen on 2010-06-30
Dear all 
I've read the instruction about setting up the iptables rules to filter all port except HTTP, SSH, FTP.
I require first remove all default iptables rules and set default rules to all chains as DROP:
> # Set default-deny policies for all three default chains 
$IPTABLES -P INPUT DROP 
$IPTABLES -P FORWARD DROP 
$IPTABLES -P OUTPUT DROP

Then allow only some ports:
 > #Accept inbound packets that are part of previously-OK'ed sessions 
$IPTABLES -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED     
# Accept inbound packets which initiate SSH sessions 
$IPTABLES -A INPUT -p tcp -j ACCEPT --dport 22 -m state --state NEW     
# Accept inbound packets which initiate FTP sessions 
$IPTABLES -A INPUT -p tcp -j ACCEPT --dport 21 -m state --state NEW     
# Accept inbound packets which initiate HTTP sessions 
$IPTABLES -A INPUT -p tcp -j ACCEPT --dport 80 -m state --state NEW     
# Log anything not accepted above $IPTABLES -A INPUT -j LOG --log-prefix "Dropped by default:"
But I hired a VPS from other country so the only mean I can manage it is via SSH.
If I setup the default rule to DROP first, I afraid that I can no longer connect via SSH to tell iptables allow SSH :mad:
So my question is:
- Does the IP tables take effect immediately after I input a rule?
- Is there any mean to run this as a batch job (create a script and run all these rules one time).
- My VPS has a web control panel which have a terminal via web. Is this a native terminal or just a connection via port 80 or 22??
Thank you

---

### Post by spynappels on 2010-06-30
From a security point of view, you would be better to set up a VPN connection and administer the server through SSH that way and disable all SSH access from the eth0 interface. 

It is a good idea to set the default policy to ACCEPT and then make the last rule in the chain DROP. This means if you flush IPTables, you will not get locked out.

Oh, and have a look at iptables-save and iptables-restore for configuring remote IPTables setups.

---

### Post by cdenley on 2010-06-30
> **spynappels said:**
> From a security point of view, you would be better to set up a VPN connection and administer the server through SSH that way and disable all SSH access from the eth0 interface. 


Why would VPN be more secure than SSH?

---

### Post by Bachstelze on 2010-06-30
> **cdenley said:**
> Why would VPN be more secure than SSH?

It's not a matter of security, both are supposedly secure. It's just useful because if you make a mistake in your firewall config and lock ssh on the eth interface, you won't be locked out of your server since you'll be connecting from the VPN interface. The VPN acts as a "safety net", so to speak. Then you can just stop it after you're done with your config if you don't need it.

---

### Post by cdenley on 2010-06-30
> **Bachstelze said:**
> **It's not a matter of security**, both are supposedly secure. It's just useful because if you make a mistake in your firewall config and lock ssh on the eth interface, you won't be locked out of your server since you'll be connecting from the VPN interface. The VPN acts as a "safety net", so to speak. Then you can just stop it after you're done with your config if you don't need it.

Wouldn't the VPN server require traffic to be allowed on the eth interface in order for anything to reach the VPN interface? You can't access the VPN interface directly, only through a tunnel established on the eth interface.

> **spynappels said:**
> **From a security point of view**, you would be better to set up a VPN connection and administer the server through SSH that way and disable all SSH access from the eth0 interface.

---

### Post by Bachstelze on 2010-06-30
> **cdenley said:**
> Wouldn't the VPN server require traffic to be allowed on the eth interface in order for anything to reach the VPN interface? You can't access the VPN interface directly, only through a tunnel established on the eth interface.

Of course, but that's only if you disable *all* traffic on the eth interface. Unless you're extremely paranoid (in which care you really shouldn't make that kind of mistake to begin with), you only block TCP traffic, not UDP, and UDP is what most VPNs use, at least by default.

---

### Post by cdenley on 2010-06-30
> **Bachstelze said:**
> Of course, but that's only if you disable *all* traffic on the eth interface. Unless you're extremely paranoid (in which care you really shouldn't make that kind of mistake to begin with), you only block TCP traffic, not UDP, and UDP is what most VPNs use, at least by default.

Using iptables to filter incoming traffic is usually only for the paranoid to begin with. You wouldn't start a listening process which listens for external connections unless you wanted people to be able to connect. If you're trying to filter malware or processes which you are unaware of, then those processes can just as easily listen for UDP traffic as they can TCP. Most malware probably uses TCP, but just because UDP malware is rare doesn't mean it can be ignored.

Besides, most iptables mistakes probably result in all traffic being filtered, not just TCP. For example, in the first post, he talked about setting the default policy to DROP before adding any rules.

---

### Post by anomie on 2010-06-30
[QUOTE=thangnguyen]But I hired a VPS from other country so the only mean I can manage it is via SSH.
If I setup the default rule to DROP first, I afraid that I can no longer connect via SSH to tell iptables allow SSH :mad:[/QUOTE]

At least you're thinking about this in advance. I had to learn this one the hard way. 

Here's how I handle the situation: 

Create a file, **fw-bailout.bash**, and add to it: 
```
#!/bin/bash

# Intended to be run with an at(1) job. Flushes all rules in the event
# that we screwed up a firewall change. 

cmd='/sbin/iptables'

for I in INPUT OUTPUT FORWARD ; do 

  ${cmd} -P ${I} ACCEPT

done

${cmd} -F

exit 0

```

Next, **# chmod 755 ./fw-bailout.bash**

Now, *any time* you intend to make ruleset changes, first set up an at(1) job that will flush everything for you - just in case you bork your ruleset. 

**# at -f ./fw-bailout.bash 20:30** 

(where 20:30 should be replaced by, say, 20 minutes into the future.) 

And, of course, cancel the at(1) job after you've deployed a working ruleset. 

-------

For more details on the (simple but effective) concept, see this BSD-centric guide I put together awhile back: 
[http://www.daemonforums.org/showthread.php?t=887](http://www.daemonforums.org/showthread.php?t=887)

---

### Post by yeleek on 2010-06-30
> **anomie said:**
> At least you're thinking about this in advance. I had to learn this one the hard way. 

Here's how I handle the situation: 

Create a file, **fw-bailout.bash**, and add to it: 
```
#!/bin/bash

# Intended to be run with an at(1) job. Flushes all rules in the event
# that we screwed up a firewall change. 

cmd='/sbin/iptables'

for I in INPUT OUTPUT FORWARD ; do 

  ${cmd} -P ${I} ACCEPT

done

${cmd} -F

exit 0

```

Next, **# chmod 755 ./fw-bailout.bash**

Now, *any time* you intend to make ruleset changes, first set up an at(1) job that will flush everything for you - just in case you bork your ruleset. 

**# at -f ./fw-bailout.bash 20:30** 

(where 20:30 should be replaced by, say, 20 minutes into the future.) 

And, of course, cancel the at(1) job after you've deployed a working ruleset. 

-------

For more details on the (simple but effective) concept, see this BSD-centric guide I put together awhile back: 
[http://www.daemonforums.org/showthread.php?t=887](http://www.daemonforums.org/showthread.php?t=887)

Good idea!!!

---

### Post by bodhi.zazen on 2010-06-30
If you are managing iptables via ssh on a remote server ...

1. I advise you do NOT set a default policy of DROP. If you do, 

```
sudo iptable -F
``` == lockout.

Instead, make the last rule in your chain to drop all traffic.

2. Rather then using iptables, I advise you use iptables-save

```
sudo iptables-save > /etc/iptables.rules
```

You then edit the rules and use iptables-apply

```
sudo iptables-apply /etc/iptables.rules
```

iptables-apply will un-do the rules in the event of a lockout.

> root@secure_server:/# iptables-apply /etc/iptables.save
Applying new ruleset... done.
Can you establish NEW connections to the machine? (y/N) apparently not...
Timeout. Something happened (or did not). Better play it safe...
Reverting to old ruleset... done.

If you are unable to confirm (type yes) the rules are reversed (as you can see).

In the event you are NOT locked out ...

> root@secure_server:/# iptables-apply /etc/iptables.save
Applying new ruleset... done.
Can you establish NEW connections to the machine? (y/N) y
... then my job is done. See you next time.

---

### Post by spynappels on 2010-06-30
cdenley, when I said it was a generally more secure to administer through the VPN tunnel, meant that you drop all inbound traffic on port 22 (or whatever) on eth0, but allow inbound connections to port 22 on tun0, so you can only use SSH if you are connected on the VPN, which should be completely encrypted and only accessible by people you want to have access.

The other points I suggested were shamelessly borrowed from Bodhi!

---

### Post by cdenley on 2010-06-30
> **spynappels said:**
> cdenley, when I said it was a generally more secure to administer through the VPN tunnel, meant that you drop all inbound traffic on port 22 (or whatever) on eth0, but allow inbound connections to port 22 on tun0, so you can only use SSH if you are connected on the VPN, which should be completely encrypted and only accessible by people you want to have access.

SSH is completely encrypted as well. How would allowing a remote user connect to a VPN server be safer than allowing a remote user to connect to a SSH server?

---

### Post by WinstonChurchill on 2010-06-30
> 
#Accept inbound packets that are part of previously-OK'ed sessions 
$IPTABLES -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED     
# Accept inbound packets which initiate SSH sessions 
$IPTABLES -A INPUT -p tcp -j ACCEPT --dport 22 -m state --state NEW     
# Accept inbound packets which initiate FTP sessions 
$IPTABLES -A INPUT -p tcp -j ACCEPT --dport 21 -m state --state NEW     
# Accept inbound packets which initiate HTTP sessions 
$IPTABLES -A INPUT -p tcp -j ACCEPT --dport 80 -m state --state NEW     
# Log anything not accepted above $IPTABLES -A INPUT -j LOG --log-prefix  "Dropped by default:"
With an ESTABLISHED,RELATED clause in iptables, my FTP server will not allow clients to connect unless I explicitly load the FTP connection tracking module:```
user@host:~$ sudo modprobe ip_conntrack_ftp
```...just in case you run into that problem. Obviously, this could be included in a script.

---

### Post by spynappels on 2010-06-30
> **cdenley said:**
> SSH is completely encrypted as well. How would allowing a remote user connect to a VPN server be safer than allowing a remote user to connect to a SSH server?

It removes the ability for anyone not on the VPN to SSH into the server. To connect to a VPN server, or at least the OpenVPN servers I use, requires keys and certs which have to be created on a per-user basis. 

All I was saying is that not allowing SSH traffic into the server through the eth0 interface reduces the attack cross-section. I know tunnelled traffic still uses that interface but it is not stopped by a firewall rule which specifies eth0, the tunneled traffic uses the tun0 interface instead, which can have different rules applied to it. 

I'm not saying what I suggest is the only way, but it definitely does reduce the attack surface.

---

### Post by cdenley on 2010-06-30
> **spynappels said:**
> It removes the ability for anyone not on the VPN to SSH into the server. To connect to a VPN server, or at least the OpenVPN servers I use, requires keys and certs which have to be created on a per-user basis.

OpenSSH supports key authentication as well.

---

### Post by spynappels on 2010-07-01
> **cdenley said:**
> OpenSSH supports key authentication as well.

That is why I said my way is not the only way. It works for me because I need to access a whole lot of servers in different locations (including a bunch of VPS) and using the VPN means I need deal with only one key/cert set, but still keeps the attack surface of the servers smaller.

For a single server, SSH with key authentication would be equally (or even more) efficient I suppose.

---

### Post by thangnguyen on 2010-07-14
Hi all.
I've found this article which totally remove my problem:[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
The basic is: allow port 22 and 80 first, block all other ports later.
> # iptables -A INPUT -p tcp --dport ssh -j ACCEPT
# iptables -A INPUT -p tcp --dport 80 -j ACCEPT
# iptables -A INPUT -j DROP

---

### Post by anomie on 2010-07-14
[QUOTE=thangnguyen]The basic is: allow port 22 and 80 first, block all other ports later.[/QUOTE]

That's a fine approach, but I still recommend one of the belt-and-suspenders methods enumerated [here](http://ubuntuforums.org/showpost.php?p=9530459&postcount=8) or [here](http://ubuntuforums.org/showpost.php?p=9530771&postcount=10). 

We're all human, and ruleset typos (or command line typos) do happen from time to time. May as well idiot-proof things where possible. ;)

---

