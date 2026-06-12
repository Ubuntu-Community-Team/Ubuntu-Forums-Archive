---
title: "iptables block SMTP outgoing to all but few servers."
date: 2008-08-05
forum: Security
---

### Post by SillyChild on 2008-08-05
Hi all,

For my gateway machine, I want to configure the firewall such that it will DROP all outgoing port 25 packets accept those in the white list.

For example, I want it to allow my lan users to connect to SMTP server of 123.123.123.123, 234.234.234.234, 23.23.23.23, 45.45.45.45 etc. This white list can be anywhere from 5 to 20.

Currently I have managed to make it work for one IP only, but not the entire block.

This is what my script looks like (just the line that does it):
```
iptables -t nat -A PREROUTING -p tcp -d ! 45.45.45.45 --dport 25 -j DROP
```
This blocks all outgoing SMTP connection except to 45.45.45.45. This is fine, but how do I allow the rest? Just adding another line that lists another IP isn't working.

Any suggestions will be helpful. Please note that, the IPs will not be in a block range. They will be random specific IPs.

Thanks.

---

### Post by cdenley on 2008-08-05
Something like this?
```

iptables -t nat -A PREROUTING -p tcp -d 123.123.123.123 --dport 25 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -d 234.234.234.234 --dport 25 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -d 23.23.23.23 --dport 25 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -d 45.45.45.45 --dport 25 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 25 -j DROP

```

If you repeat the same rule you posted with another IP, then every IP will match at least one of the rules, so everything will get dropped. You want to accept for each address in the whitelist, then drop all remaining connections on port 25.

---

### Post by SillyChild on 2008-08-06
Sweet! that worked like a gem.

Thanks :)

---

