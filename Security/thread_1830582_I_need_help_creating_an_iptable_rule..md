---
title: "I need help creating an iptable rule."
date: 2011-08-21
forum: Security
---

### Post by Mouse750 on 2011-08-21
I need help creating an iptable rule.

The iptables are installed on my router. My router also connects to a "hide my a**" vpn account 
at 79.142.65.5:443

The goal is to somehow force the traffic to go through the vpn, because what sometimes happens is,
 the vpn connection drops (for what ever reason) and my real ip becomes exposed. 

Basically, I want to block "myself" from accessing the Internet when not connected to the vpn 
because of privacy concerns.

Below is my iptables. It has the 3 default chains and it also has many custom user chains. I need 
to know what kind of a rule to add, What interface to apply it to (lo,tun0,br-lan,eth1) and the 
correct chain to insert into.

For example, you could tell me something like:

> FORWARD chain, change rule 1 to 
iptables -R FORWARD 1 -j zone_wan_MSSFIX -p tcp --destination-port 443 -i eth1

Obviously, That was just a guess, I need someone that knows iptables to help me.


```
 Chain INPUT (Policy: ACCEPT) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  72.95 KB  DROP               all  *      *      0.0.0.0/0  0.0.0.0/0   state INVALID
Rule 2  1.11 GB   ACCEPT             all  *      *      0.0.0.0/0  0.0.0.0/0   state RELATED,ESTABLISHED
Rule 3  0.00 B    ACCEPT             all  lo     *      0.0.0.0/0  0.0.0.0/0   -
Rule 4  1.52 MB   syn_flood          tcp  *      *      0.0.0.0/0  0.0.0.0/0   tcp flags:0x17/0x02
Rule 5  4.82 MB   input_rule         all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 6  4.82 MB   input              all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain FORWARD (Policy: DROP) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  1.41 GB   zone_wan_MSSFIX    all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 2  23.31 KB  DROP               all  *      *      0.0.0.0/0  0.0.0.0/0   state INVALID
Rule 3  1.40 GB   ACCEPT             all  *      *      0.0.0.0/0  0.0.0.0/0   state RELATED,ESTABLISHED
Rule 4  8.25 MB   forwarding_rule    all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 5  8.25 MB   forward            all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 6  0.00 B    reject             all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain OUTPUT (Policy: ACCEPT) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    DROP               all  *      *      0.0.0.0/0  0.0.0.0/0   state INVALID
Rule 2  484.53 MB ACCEPT             all  *      *      0.0.0.0/0  0.0.0.0/0   state RELATED,ESTABLISHED
Rule 3  0.00 B    ACCEPT             all  *      lo     0.0.0.0/0  0.0.0.0/0   -
Rule 4  66.90 KB  output_rule        all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 5  66.90 KB  output             all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain forward (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  8.25 MB   zone_lan_forward   all  br-lan *      0.0.0.0/0  0.0.0.0/0   -
Rule 2  0.00 B    zone_wan_forward   all  eth1   *      0.0.0.0/0  0.0.0.0/0   -
Rule 3  0.00 B    zone_wan_forward   all  tun0   *      0.0.0.0/0  0.0.0.0/0   -

 Chain forwarding_rule (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  8.25 MB   nat_reflection_fwd all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain input (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  104.06 KB zone_lan           all  br-lan *      0.0.0.0/0  0.0.0.0/0   -
Rule 2  1.36 MB   zone_wan           all  eth1   *      0.0.0.0/0  0.0.0.0/0   -
Rule 3  3.36 MB   zone_wan           all  tun0   *      0.0.0.0/0  0.0.0.0/0   -

 Chain output (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  66.90 KB  zone_lan_ACCEPT    all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 2  61.13 KB  zone_wan_ACCEPT    all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain reject (References: 7) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  1.52 MB   REJECT             tcp  *      *      0.0.0.0/0  0.0.0.0/0   reject-with tcp-reset
Rule 2  2.92 MB   REJECT             all  *      *      0.0.0.0/0  0.0.0.0/0   reject-with icmp-port-unreachable

 Chain syn_flood (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  1.52 MB   RETURN             tcp  *      *      0.0.0.0/0  0.0.0.0/0   tcp flags:0x17/0x02 limit: avg 25/sec burst 50
Rule 2  0.00 B    DROP               all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_lan (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  104.06 KB input_lan          all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 2  104.06 KB zone_lan_ACCEPT    all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_lan_ACCEPT (References: 2) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  5.77 KB   ACCEPT             all  *      br-lan 0.0.0.0/0  0.0.0.0/0   -
Rule 2  104.06 KB ACCEPT             all  br-lan *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_lan_DROP (References: 0) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    DROP               all  *      br-lan 0.0.0.0/0  0.0.0.0/0   -
Rule 2  0.00 B    DROP               all  br-lan *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_lan_MSSFIX (References: 0) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    TCPMSS             tcp  *      br-lan    0.0.0.0/0  0.0.0.0/0   tcp flags:0x06/0x02 TCPMSS clamp to PMTU

 Chain zone_lan_REJECT (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    reject             all  *      br-lan 0.0.0.0/0  0.0.0.0/0   -
Rule 2  0.00 B    reject             all  br-lan *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_lan_forward (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  8.25 MB   zone_wan_ACCEPT    all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 2  0.00 B    forwarding_lan     all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 3  0.00 B    zone_lan_REJECT    all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_wan (References: 2) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    ACCEPT             icmp *      *      0.0.0.0/0  0.0.0.0/0   icmp type 8
Rule 2  290.93 KB ACCEPT             udp  *      *      0.0.0.0/0  0.0.0.0/0   udp dpt:68
Rule 3  4.44 MB   input_wan          all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 4  4.44 MB   zone_wan_REJECT    all  *      *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_wan_ACCEPT (References: 2) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  2.77 KB   ACCEPT             all  *      eth1   0.0.0.0/0  0.0.0.0/0   -
Rule 2  0.00 B    ACCEPT             all  eth1   *      0.0.0.0/0  0.0.0.0/0   -
Rule 3  8.31 MB   ACCEPT             all  *      tun0   0.0.0.0/0  0.0.0.0/0   -
Rule 4  0.00 B    ACCEPT             all  tun0   *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_wan_DROP (References: 0) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    DROP               all  *      eth1   0.0.0.0/0  0.0.0.0/0   -
Rule 2  0.00 B    DROP               all  eth1   *      0.0.0.0/0  0.0.0.0/0   -
Rule 3  0.00 B    DROP               all  *      tun0   0.0.0.0/0  0.0.0.0/0   -
Rule 4  0.00 B    DROP               all  tun0   *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_wan_MSSFIX (References: 1) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    TCPMSS             tcp  *      eth1   0.0.0.0/0  0.0.0.0/0   tcp flags:0x06/0x02 TCPMSS clamp to PMTU
Rule 2  2.68 MB   TCPMSS             tcp  *      tun0   0.0.0.0/0  0.0.0.0/0   tcp flags:0x06/0x02 TCPMSS clamp to PMTU

 Chain zone_wan_REJECT (References: 2) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    reject             all  *      eth1   0.0.0.0/0  0.0.0.0/0   -
Rule 2  1.08 MB   reject             all  eth1   *      0.0.0.0/0  0.0.0.0/0   -
Rule 3  0.00 B    reject             all  *      tun0   0.0.0.0/0  0.0.0.0/0   -
Rule 4  3.36 MB   reject             all  tun0   *      0.0.0.0/0  0.0.0.0/0   -

 Chain zone_wan_forward (References: 2) 
Rule #  Traffic   Target             Prot In     Out    Source     Destination Options
Rule 1  0.00 B    forwarding_wan     all  *      *      0.0.0.0/0  0.0.0.0/0   -
Rule 2  0.00 B    zone_wan_REJECT    all  *      *      0.0.0.0/0  0.0.0.0/0   -
```

---

### Post by raja.genupula on 2011-08-22
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

look at that

---

### Post by Mouse750 on 2011-08-22
Thanks for the help but I was hoping for something a little more detailed.

You see, I don't know if I need to change:

Chain [COLOR="Blue"]FORWARD[/COLOR] Rule 5 
or, 
Chain [COLOR="blue"]forward[/COLOR] (Case Sensitive) Rule 1 
or, 
Chain [COLOR="blue"]zone_lan_forward[/COLOR] Rule 1 
or, 
Chain [COLOR="blue"]zone_wan_ACCEPT[/COLOR] Rues 1 thru 4.
or,
Chain [COLOR="Blue"]zone_lan_ACCEPT[/COLOR]

I'm guessing it's one of those five chains.

Also, I'm not sure what the rule should say, I'm guessing something with port 443 in the rule. I'm also not sure what interface to apply it to. I have eth1 (wan),br-lan (lan), and tun0 (vpn) but I'm guessing it's br-lan since I'm trying to block myself. As you can see, there is a whole lot of guessing going on here.

So yes, I understand the basics provided in your link but I'm going to need a little more help then that. 

I need help thinking of a good rule. Could be port based, could be ip based, could be something I have not thought of. I also need to insert the rule(s) in the correct place(s) or even possibly create new user chains.

How does this sound... someone who has good iptables skills helps me out and I will award who ever helps me out the **most** with $20 as gratitude? I would think someone that is good with iptables can solve my thread in just a few minutes.

Below is my iptables except it is in html format instead of plain text. It's click-able which makes following all the various chain flows much easier to comprehend.

[IMG]http://img594.imageshack.us/img594/7962/down2.gif[/IMG]

---

### Post by Mouse750 on 2011-08-23
Well, I solved my own thread...

```
iptables -R zone_wan_ACCEPT 1 -d 79.142.65.5 -j ACCEPT -o eth1
```

This does exactly what I wanted it to do. 

If the vpn is up = Internet works, 
If the vpn is down = Internet does not. 

And regardless if the vpn is up or down all local services such as network printing, samba, ssh to my router, etc are unaffected.


-

---

