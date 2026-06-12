---
title: "Built-in Network Security Features"
date: 2010-11-22
forum: Security
---

### Post by dcaunt on 2010-11-22
Hi all,

I'm new to Ubuntu Server (migrating from SLES 10.3 to Ubuntu 10.10 Server) and I'm setting up a firewall using iptables.  I used a fairly thorough iptables script on my SLES box (modified one that I found online a while ago) but I keep hearing people say things like "Ubuntu's built-in network security covers that" while looking through some posts regarding iptables.  So, I'm wondering if I need any of the "basic" rules that my old script had, or if these are all things that Ubuntu does by default.

For example, my old script has things like:

# Disable response to ping.
/bin/echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all
# Disable response to broadcasts.
/bin/echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
# Don't accept source routed packets.
/bin/echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
# Disable ICMP redirect acceptance.
/bin/echo "0" > /proc/sys/net/ipv4/conf/all/accept_redirects
# Enable bad error message protection.
/bin/echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
# Turn on reverse path filtering.
for interface in /proc/sys/net/ipv4/conf/*/rp_filter; do
   /bin/echo "1" > ${interface}
done
# SYN-FLOODING PROTECTION
iptables -N syn-flood
iptables -A INPUT -p tcp --syn -j syn-flood
iptables -A syn-flood -m limit --limit 1/s --limit-burst 4 -j RETURN
iptables -A syn-flood -j DROP
# Make sure NEW tcp connections are SYN packets
iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
# Log fragments just to see if we get any, and deny them too.
iptables -A INPUT -f -j LOG --log-prefix "IPTABLES FRAGMENTS: "
iptables -A INPUT -f -j DROP
# Refuse spoofed packets pretending to be from your IP address.
iptables -A INPUT -s $IPADDR -j DROP
# Refuse packets claiming to be from a Class A private network.
iptables -A INPUT -s $CLASS_A -j DROP
# Refuse packets claiming to be from a Class B private network.
iptables -A INPUT -s $CLASS_B -j DROP
# Refuse packets claiming to be from a Class C private network.
iptables -A INPUT -s $CLASS_C -j DROP
# Refuse Class D multicast addresses. Multicast is illegal as a source address.
iptables -A INPUT -s $CLASS_D_MULTICAST -j DROP
# Refuse Class E reserved IP addresses.
iptables -A INPUT -s $CLASS_E_RESERVED_NET -j DROP

Are these examples of things that I don't need to include in my iptables-based firewall script?  Are any of them already taken care of by Ubuntu's security systems?  Or should these things still be included in a paranoid server admin's firewall script?

Thanks.

Dan

---

### Post by cariboo on 2010-11-22
Ubuntu's security model is for the most part the same as any other distribution, so your firewall rules should work just as well here, as they would on other distros.

---

### Post by dcaunt on 2010-11-22
Thanks, cariboo907.  I'm also currently reading more about the options in the sysctl.conf file.  Things like SYN cookies can be handled there, but most of these features are off by default.  I assume they're off because they can break certain communications and not because they're deprecated or untrusted security features.  Is this a good assumption, and would these all be good features to consider turning on (after individual consideration)?  Or is there a different reason that these are off by default?  Do you use any of the sysctl.conf features, like SYN cookies or Spoof Protection?

Dan

---

