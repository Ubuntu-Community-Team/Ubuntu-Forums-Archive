---
title: "OpenVPN and UFW"
date: 2009-05-21
forum: Security
---

### Post by Steve1961 on 2009-05-21
I'm about to try out the witopia openvpn service and need to configure my firewall.  At the moment I'm using ufw but I will need to modify it's configuration to get it working.  From what I understand I need to add manual rules to the before ufw scripts.  The basic iptables syntax I need to add is:

iptables -A INPUT -i eth0 -p udp --dport 1194 -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp --dport 1194 -j ACCEPT
iptables -A INPUT -i tun0 -j ACCEPT
iptables -A OUTPUT -o tun0 -j ACCEPT
iptables -A FORWARD -o tun0 -j ACCEPT 

Anyone know how to ufw-ise these commands, and whereabout in the before ufw script I need to place them?

---

### Post by bodhi.zazen on 2009-05-21
Edit /etc/ufw/before.rules

The syntax is similar to iptables-save, so the rule

iptables -A INPUT -i eth0 -p udp --dport 1194 -j ACCEPT

becomes

-A INPUT -i eth0 -p udp --dport 1194 -j ACCEPT

in the before.rules (drop "iptables")

---

### Post by Steve1961 on 2009-05-22
OK thanks,  And does it matter where I insert these rules in the script?

---

### Post by bodhi.zazen on 2009-05-22
Probably not, I would put them at the end, with comments ...

---

### Post by Steve1961 on 2009-05-22
OK, thanks for that

---

### Post by The Cog on 2009-05-23
Note that OpenVPN will create a tunnel interface which looks like another ethernet interface. If you want, you can apply separate firewalls to this interface, and thereby treat connections through the VPN differently to connections over the normal ethernet - more or less restrictive as you prefer.

---

### Post by Steve1961 on 2009-05-30
> **The Cog said:**
> Note that OpenVPN will create a tunnel interface which looks like another ethernet interface. If you want, you can apply separate firewalls to this interface, and thereby treat connections through the VPN differently to connections over the normal ethernet - more or less restrictive as you prefer.

Cheers.  However, to me it looks like ufw is going to be a right pain to set something up like this.  It might be easier just to move to guarddog or firestarter in the end I think

---

### Post by kevdog on 2009-05-31
Actually I think its just easier to write a iptables script and run it that way.  The syntax is nearly the same, and you can bypass the ufw part since I don't think in this instance its giving you anything -- which would be ease of use.

---

### Post by Steve1961 on 2009-06-01
> **kevdog said:**
> Actually I think its just easier to write a iptables script and run it that way.  The syntax is nearly the same, and you can bypass the ufw part since I don't think in this instance its giving you anything -- which would be ease of use.

Yep I think you're right.  I've been putting off learning iptables for years, perhaps it's now time to learn.

---

### Post by bodhi.zazen on 2009-06-01
> **Steve1961 said:**
> Yep I think you're right.  I've been putting off learning iptables for years, perhaps it's now time to learn.

If you can do ufw, you can do iptables.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by Steve1961 on 2009-06-02
> **bodhi.zazen said:**
> If you can do ufw, you can do iptables.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

That was my thinking.  I've just done a first draft script which I've posted for feedback here:

[http://ubuntuforums.org/showthread.php?p=7386031#post7386031](http://ubuntuforums.org/showthread.php?p=7386031#post7386031)

---

### Post by workingman on 2009-07-20
Hey guys,

Was trying to do pretty much the same and figured it out without too much trouble.  I had already modified before.rules to drop pings and stuck the OpenVPN stuff right after.  Here's my changes:

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
#-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow all traffic via our OpenVPN interface
-A INPUT -i tun0 -j ACCEPT
-A FORWARD -i tun0 -j ACCEPT

#
# ufw-not-local
#

---

### Post by workingman on 2009-07-20
Found I was logging a ton of stuff I didn't care about since it was going out my tun0 interface.  

# allow all traffic via our OpenVPN interface
-A INPUT -i tun0 -j ACCEPT
-A FORWARD -i tun0 -j ACCEPT
-A FORWARD -o tun0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -o tun0 -m state --state RELATED,ESTABLISHED -j ACCEPT

The traffic was flowing but generating too much log chatter.  Adding these RELATED,ESTABLISHED rules fixed that.

Useful bit of info!  Use tun+ instead of tun# if you have multiple tun interfaces that should all be treated the same.

---

### Post by sefs on 2009-08-10
Hi there I have a openvpn here but I am using bridging as opposed to routing....

the IPTable rules look like this

```

iptables -A INPUT -i tap0 -j ACCEPT
iptables -A INPUT -i br0 -j ACCEPT
iptables -A FORWARD -i br0 -j ACCEPT

```

How would i set up ufw to reflect that along with your chatter modifications.

Currently when I connect i can only ping the vpn server as the firewall on it (ufw) is blocking it from seeing anything behind.

Thanks.

---

### Post by srguru on 2011-01-06
Thank you Workingman for the rules.  I used a slight modification of these in the file /etc/ufw/before.rules:

.
.
.
# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

# allow all traffic via our OpenVPN interface
-A ufw-before-input -i tun0 -j ACCEPT
-A ufw-before-forward -i tun0 -j ACCEPT
-A ufw-before-forward -o tun0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -o tun0 -m state --state RELATED,ESTABLISHED -j ACCEPT
.
.
.

---

