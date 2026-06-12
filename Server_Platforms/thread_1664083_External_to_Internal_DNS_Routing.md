---
title: "External to Internal DNS Routing"
date: 2011-01-10
forum: Server Platforms
---

### Post by sprouty on 2011-01-10
Hi,

I'm wondering if the below is possible, if so can anyone point me in the right direction or even give some terms to google?

I have one external ip address and a few domains. Would it be possible to have each domain on a internal domain and the box that sits on that external ip route to the internal. This would be for a number of server (mail, apache, imap, pop3, https ) So for example:

Some visit domain1.com ->external ip -> 192.168.10.100
Someone else visit domain2.com ->external ip -> 192.168.10.101
and so one with a number of domains


Sorry if the question if a bit confusing, didn't know how best to describe it.
Many Thanks,

Sprouty.

---

### Post by rubylaser on 2011-01-10
I'm not sure if I understand exactly what you're asking.  If you're wondering if one webhost can be used for multiple domains/subdomains, the answer is yes.  If you're using Apache, you'd accomplish this with vhosts.

If you're wondering if 1 public name can be used to multiple backend machines, you'd be talking about load balancing.

But, I think you're actually wanting to do PAT (Port Address Translation)
[http://en.wikipedia.org/wiki/Port_address_translation]("http://en.wikipedia.org/wiki/Port_address_translation")

To make your life easy, I'd just host all of your subdomains on one box and use Apache vhosts, but that's dependent on the traffic you expect.

---

### Post by NIT006.5 on 2011-01-10
Ok, as far as I understand it, you have one public IP and one Linux box doing the routing between that public IP and the LAN. In this case, PAT is definitely necessary and is probably already being used just to give the LAN internet access (any masquerading or snat would count). 

Normally however, for external traffic coming in, your routing is done based on the port number (port forwarding to LAN hosts). So all port 80 traffic goes to a specific machine, port 110 and port 25 traffic might go to another, etc. This is the most sensible and definitely easiest setup. As mentioned by rubylaser, you could then have your one Web server using virtual hosts to provide all the different web sites based on the domain name the visitor typed into their browser. Apache will use the domain name to serve up the correct site. This could also be done for mail, where one mail server (different to the web server) provides pop/smtp for all the domains, and the mail configuration is then done for virtual hosts as well.

However, purely out of interest, I've just been toying with another possible method, BUT this is certainly not a "normal" approach and there might be reasons why it is not advisable... so I'm just mentioning it here because I was curious to see if it would work. I have also only put about 3 minutes into testing this, so its all still very theoretical. But if you really, really wanted to split traffic the way you first suggested, you could to some degree use iptables with string matching. For instance, you could have a rule such as:

```

iptables -I INPUT -m string --string "test.com" --algo bm -j LOG --log-prefix " TEST.COM "

```

This would match any traffic which ***contains*** the text test.com (and you could create a similar rule for each domain). At present the rule is only logging that traffic, as below:

```

Jan 10 21:24:21 mail kernel: [174035.840734]  **TEST.COM** IN=eth0 OUT= MAC=f4:ce:46:e6:65:68:40:61:86:98:e9:6c:08:00 SRC=10.0.0.2 DST=10.0.0.1 LEN=569 TOS=0x00 PREC=0x00 TTL=64 ID=54730 DF PROTO=TCP SPT=52847 **DPT=80** WINDOW=92 RES=0x00 ACK PSH URGP=0

```

Which shows what happens when I connect to my test server using test.com as the address in the browser (having modified my hosts to point that address to my internal server). Similarly, when I created a second rule for test2.com and repeated this, it was logged as:

```

Jan 10 21:23:43 mail kernel: [173997.645784]  **TEST2.COM** IN=eth0 OUT= MAC=f4:ce:46:e6:65:68:40:61:86:98:e9:6c:08:00 SRC=10.0.0.2 DST=10.0.0.1 LEN=570 TOS=0x00 PREC=0x00 TTL=64 ID=20765 DF PROTO=TCP SPT=52846 **DPT=80** WINDOW=92 RES=0x00 ACK PSH URGP=0

```

So, in theory, it should be very possible to use very similar iptables rules, but instead of just logging the traffic, iptables forwards it to the LAN host in question. On this basis, you could then split port 80 traffic between different in-house servers based on the domain name used in the visitor's browser (provided that both domains have their public DNS set up to point to the same IP).

This also appears to work for smtp traffic. In the example below, I sent a message to smtp server "test.com" and iptables correctly logged it (and if iptables logs it, then iptables can redirect/forward it):

```

Jan 10 21:28:06 mail kernel: [174260.496195]  **TEST.COM** IN=eth0 OUT= MAC=f4:ce:46:e6:65:68:40:61:86:98:e9:6c:08:00 SRC=10.0.0.2 DST=10.0.0.1 LEN=327 TOS=0x00 PREC=0x00 TTL=64 ID=60912 DF PROTO=TCP SPT=46702 **DPT=25** WINDOW=92 RES=0x00 ACK PSH URGP=0

```

HOWEVER: This does not appear to work for pop traffic on port 110. Since this depends entirely on the domain name being transmitted as "part of" the traffic, it won't work for any protocols that don't do that. (And obviously pop does not do this).

ALSO: This is just a kind of "proof of concept", and as stated, is probably not a "common" or "correct" way of doing things. This would most likely also adversely affect the performance of the routing box, which is now doing string matching on all traffic instead of just forwarding it based on port (although that could be lessened by doing rules per port of course). This was done purely as an experiment because I was curious ;)

AND: If any packets are transmitted that don't contain the "matched" string, then they will not be forwarded. I don't know enough about the protocols in question to know how that would work.

---

### Post by NIT006.5 on 2011-01-10
oh and also, normal string matching wouldn't work for any encrypted traffic (such as https)... I *think* there is a way of configuring iptables with the necessary keys to be able decrypt it (and then do string matching), but I've never tried and might be completely wrong.

---

