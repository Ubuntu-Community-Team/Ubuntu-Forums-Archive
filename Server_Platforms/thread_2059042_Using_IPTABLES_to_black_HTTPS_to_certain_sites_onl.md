---
title: "Using IPTABLES to black HTTPS to certain sites only"
date: 2012-09-17
forum: Server Platforms
---

### Post by Nessaja on 2012-09-17
Hi,

I'm trying to block youtube.com during business hours using squid, however since this is a transparent proxy people are able to bypass it by using [https://.](https://.)...... (port 443).

I want to use iptables to block port 443 but only to youtube.com servers, as other port 443 functionality is required for other tasks.

I've tried a lot of different combinations, including:
```

iptables -A INPUT -p tcp --dport 443 -m string --string "youtube.com" algo bm -j REJECT

```blocking Youtube's ip's is almost impossible as they change each time a do an nslookup.

Does anybody know how this can be done?

---

### Post by Lars Noodén on 2012-09-17
Blocking on 'string' will only block unencrypted packets containing the letters 'youtube.com' in that sequence.

If you want to block Youtube, you'll have to block the whole subnet it is on.  Looking up the ip number(s) for Youtube using [host](http://manpages.ubuntu.com/manpages/precise/en/man1/host.1.html) or dig, we see that there are several hosts using  173.194.32.*.  We can look up one of them with [whois](http://manpages.ubuntu.com/manpages/precise/en/man1/whois.1.html) and see that the network for Youtube is actually 173.194.0.0/16, so that's what you need to try to block.

```

iptables -A OUTPUT -p tcp -d 173.194.0.0/16 --dport 443 -j REJECT

```

However, there are still ways around it.  What you need to do is address the behavioral problems and there isn't going to be a technical solution for that.

---

