---
title: "DDoS Attack -- How To Limit Connections?"
date: 2010-06-04
forum: Security
---

### Post by Masked Crusader on 2010-06-04
Hey all.

I have been under a DDoS attack for the past 18 hours and my host is quite useless.  As they use Cisco Guard (which does nothing to aid in mitigating DDoS attacks), I am left to fend for myself here.

I have tried to find the bad IP(s) with the following command: 

> netstat -atun | awk '{print $5}' | cut -d: -f1 | sed -e '/^$/d' |sort | uniq -c | sort -nAll that brought back was tons of IPs that have connections between the range of 1-7 connections.

I am starting to think that if I limit the number of connections for a "bad ip" to 2, that this may resolve the issue.  How do I got about doing something like this in Ubuntu?

Any other tips or suggestions on how to mitigate an attack on Ubuntu 9.04 would be greatly appreciated.

Thanks!

---

### Post by Masked Crusader on 2010-06-04
I did find this morning a couple of IPs whose connections were over 10+ connections.

I "iptables DROP" them.  When I hit the "top" command, whenever a new apache2 process is brought up, it seems to kill it.  The CPU will get to about 17% and then the apache2 request will die off.  My site is still not loading, but my server is at least not getting as terrible of a load as it was previously.

Asking for a server reboot right now to see if that will clear out the old apache2 requests.

---

### Post by lensman3 on 2010-06-04
iptables has options that can limit the number of connections from a single host per time unit.  Where unit is connections per minute, seconds, hours, etc.  It will log and then drop the connections.

Google "iptables firewall arno".  Arno's firewall works very well for me.  I has good logging and will drop ingoing and outgoing packets.

What you need is a "tarpit".  When somebody does DDoS attacks, they get "stuck" to your site.

Hope this helps.

---

### Post by davis.peixoto on 2010-06-04
Masked Crusader,

limiting number of connections on iptables, as seems in MANY tutorials over the internet isn't the always the correct solution.

If you limit your server to receive 10 connections per second, using iptables, you actually make attacker's job easier. Attacker will need only to  SYN 10 time per second against your machine and he will be done.

ACK floods are also possible...

Hmm... The solution I can remember is about TCP Syn Cookies.

Do

```
$cat /proc/sys/net/ipv4/tcp_syncookies
```

If output is "1", it's already active, and you should look for further help. Otherwise, try activate it:
```
$sudo echo 1 > /proc/sys/net/ipv4/tcp_syncookies
```

A little explanation about this almost unknown feature. Usual flow:

1 - client send SYN signal into TCP header
2 - server allocates resources (memory for apache, prefetch a thread for processing the future requests...), and send back the a TCP header with SYN response and ACK signal.
3 - client send another new request (DOS), maybe from another IP (DDoS). Note that this is where a normal client should follow protocol and send normal response...

With TCP SYN Cookies active flow:
1 - client send SYN signal into TCP header (all headers have an identifier, let says for simplicity attacker sends the number 100);
2 - server send back the a TCP header with  SYN/ACK signal, and identifier 200, setting a cookie with NACK 101.
3 - client should send an ACK with identifier 101 and Cookie with NACK 201 as response.
4 - only then server recognizes client, and allocate resources.

As you can see, this can frustrate most not-too-much experient attackers.

You can also be interested in limiting SYN retries and SynAck retries... Look into /proc/sys/net/ipv4/ for more options. editing them is simple like that, just writing the number into file.

Regards.

---

