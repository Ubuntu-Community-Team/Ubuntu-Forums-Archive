---
title: "tcpdump ipv6 DAD"
date: 2011-03-02
forum: Security
---

### Post by jeff.sadowski on 2011-03-02
I can't figure out how to filter correctly with tcpdump
I'd like to use tcpdump so that I can get just the Duplicate Address Detection packets of IPv6. It doesn't need to be tcpdump  but it has to be something that is scriptable. I'd like to use it to do dynamic DNS updates to bind. Right now I just want a ipv6 address to mac address mapping. If there is an ipv6 arp that would do.

---

### Post by lemming465 on 2011-03-05
My, that is hard to figure out, isn't it?

Let us know how you fare; since [UNH-IOL says DHCPv6 is not ready for prime time]("http://www.enterprisenetworkingplanet.com/netsp/article.php/3926691/Does-IPv6-Even-Work.htm"), a bunch of the rest of us are going to be needing to go from SLAAC addresses to ip6.arpa reverse DNS just like you.

> ... If there is an ipv6 arp ...
Um, no.  For those who are new to IPv6, it bundles the functionality of IPv4 protocols 1 (ICMP) plus 2 (IGMP) plus ARP plus mobility stuff all into the shiny new ICMPv6 protocol, aka next header # 58.  In particular, while IPv4 translates IPv4 addresses on-link into ethernet addresses by broadcasting *address resolution protocol* requests, IPv6 does it differently.  ICMPv6 *neighbor discovery* **multicasts** various kinds of solicitations, expecting unicast ICMPv6 advertisement responses.

For link-local unicast addresses (FE80::/64 prefix) plus any global scope unicast addresses (2000::/3 prefix), IPv6 hosts will do *duplicate address detection* before starting to use those addresses.

An IPv4 host would do a gratuitous ARP, broadcasting its ethernet vs IPv4 association to the far corners of its VLAN.  An IPv6 host will do a narrow multicast of a neighbor solicitation (NS) instead.  In either case, if some other host answers, the original host, v4 or v6, should refuse to use the duplicated address.

I haven't read every line of the relevant RFC's yet, but the behavior I observe from windows 7 and ubuntu 10.10 for DAD on native v6 is to send a single ICMPv6 NS, with:
```

ethernet (layer 2):
  source=unicast host ethernet MAC
  destination= IPv6 multicast ND group, meaning
     33:33:FF:xx:yy:zz, where xxyyzz is the last 24 bits of the IPv6 address under test
IPv6 (layer 3):
  source address :: (all zeroes)
  destination address: ICMPv6 link-local self ND multicast group, meaning
     FF02::1:FFxx:yyzz
  next header 58 (0x3a)
ICMPv6 (layer 4)
  type = 135, code = 0
  target = interfaces' full IPv6 address under consideration

```
The bad news is that when you read the documentation for pcap-filter(7) the only relevant keywords you find are "ip6" and "icmp6".  In the spirit of "Use the source, Luke", reading the source code for tcpdump-4.whatever/tcpdump.c shows that it just punts the filter arguments to pcap_compile().  Following on down the rabbit hole, reading the source code for pcap-compile's lex tokenizer (character parser) in libpcap-whatever/scanner.l shows that the man page has no ommissions, there are no further ICMPv6 related keywords available.  Ugh!

So, what we probably want to do is forget about tcpdump, and use tshark from the wireshark group instead.  We're still stuck with the libpcap BPF filters at the capture stage, but once we get to the processing phase, wireshark has icmp6 keywords for type and code, just like we want.  So something like:```
tshark -i eth0 -f 'icmp6' -R 'ipv6.src eq :: && icmpv6.type eq 135 && icmpv6.code eq 0'
```
gets us the right packets. 

The next problem is that even tshark lacks output keywords for the target address, so to get the info you need you will have to either use XML output (-T pdml) or verbose output (-V) and parse the multiline result (e.g. with awk); or write the packet to stdout (-w -) and parse out the chunks you need with, say, perl.  Unless you want to write a lua script plugin for tshark?

Finally, we need to be able to see the ICMPv6 NS packets in the first place.  The whole design point of multicasting them is **not** to show them to everyone, so you are going to need enterprise grade network switches which have *span* port capability or *monitor session* or what ever your gear calls it when you designate one special port to get a cloned copy of all the traffic on the other ports.  An alternative to all this might be to query the switch for IPv6 addresses using SNMP.

---

### Post by jeff.sadowski on 2011-03-06
Thank you so much lemming465 :-) I was also asking on the tcpdump mailing list and someone on there also recommended tshark. Your's was much more helpful.

---

