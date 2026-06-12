---
title: "Ubuntu 22.04 USG hardening script breaks DNS resolution"
date: 2023-11-10
forum: Security
---

### Post by jobet on 2023-11-10
[COLOR=#0C0D0E][FONT=-apple-system]Since a few days, I noticed that running USG hardening tool on a freshly installed Ubuntu 22.04 server, breaks DNS resolution. Running for example dig google.com throws out an error:[/FONT][/COLOR]
```
;; communications error to 127.0.0.53#53: timed out
;; communications error to 127.0.0.53#53: timed out
;; communications error to 127.0.0.53#53: timed out

; <<>> DiG 9.18.18-0ubuntu0.22.04.1-Ubuntu <<>> google.com
;; global options: +cmd
;; no servers could be reached

```[COLOR=#0C0D0E][FONT=-apple-system]I looked up almost every DNS setting in this server, and read several DNS troubleshoot tutorials, but haven't found a fix yet. I also compared this server to another one running the same configuration (22.04 and hardened with USG module), and the only difference I've noticed so far is that in the output of resolvectl the line Current DNS Server: 2a01:4ff:ff00::add:1 is missing:[/FONT][/COLOR]
```
Link 2 (eth0)
Current Scopes: DNS
     Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
   DNS Servers: 2a01:4ff:ff00::add:1 2a01:4ff:ff00::add:2 185.12.64.1 185.12.64.2
[COLOR=#0C0D0E][FONT=-apple-system]
```

Any advice will be much appreciated.[/FONT][/COLOR]

---

### Post by make-a-little on 2023-11-15
And some time later, (head wall emoji), the below may be one approach, it's passing DNS for me and not swiss cheesed the config. I actually like the sending it via lo and having tcpdump running continually on a terminal. Just running one or two apps per VM and it can help see what's going on at a glance, not that the same can't be accomplished on another if.

Hope it helps for you.

delete the input chain
re-add it as a policy accept (same)

add a specific rule to cover src 127.0.0.1 to dst 127.0.0.53 dport udp 53 counter accept (DNS request via lo)
add a specific rule to cover src 127.0.0.53 sport udp 53 to dst 127.0.0.1 counter accept (DNS response via lo)
add the 127.0.0.0 counter drop (see what else is going on with the counter)
add the iif "lo" accept back in

tcpdump -i lo was helpful

What  a PITA, soooo much reading to get sooo little knowledge. Someone will  probably poo poo the above and explain why the hack to change  systemd-resolved is the way to go.

Resolution to this problem with hardening script should be really well documented, as it is fundamental.

---

### Post by make-a-little on 2023-11-16
Option 2 - perhaps a little better overall.

change the input filter to be a default policy drop - more standard security approach
add accept rule for 127.0.0.1 to 127.0.0.53 dns
add accept rule for answer over ethernet from dns server back into the i/f
add accept rule for dns 127.0.0.53 to 127.0.0.1
add iif 'lo' accept back in

when you change the output filter to a policy deny this will need to be updated to allow the dns query to egress the eth if

This supports the notion of only allow explicitly defined traffic and deny all else.

---

