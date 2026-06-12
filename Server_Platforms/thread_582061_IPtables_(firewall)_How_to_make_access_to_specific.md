---
title: "IPtables (firewall): How to make access to specific web sites?"
date: 2007-10-19
forum: Server Platforms
---

### Post by abcuser on 2007-10-19
Hi,
how to enable users to have access only to [www.google.com](www.google.com). Users must not have any access beyond [www.google.com](www.google.com)

I know how to put access to google:
```
sudo iptables -A OUTPUT -s 0/0 -d www.google.com -p tcp -j ACCEPT
```

I know how to drop all privileges:
```
sudo iptables -A OUTPUT -s 0/0 -d 0/0 -p tcp -j DROP
```

But how to use them together? So dropping all privileges except allowing access to [www.google.com](www.google.com).

Thanks,
Abcuser

---

### Post by abcuser on 2007-10-20
Hi,
I have found out that this is also my solution. So specify accept rules before drop. For drop command I could also write without all parameters. So the final code is:
```
sudo iptables -A OUTPUT -s 0/0 -d www.google.com -p tcp -j ACCEPT
sudo iptables -A OUTPUT -j DROP
```

There is a good iptables how-to:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Thanks,
Abcuser

---

### Post by abcuser on 2007-10-20
Hi,
one little problem. Google is using multiple IP addresses for [www.google.com](www.google.com). So the above solution works for some time and then stops. It is dependent from witch IP address is hiding behind  [www.google.com](www.google.com) at the time of browsing.

It looks like [www.google.com](www.google.com) is translated to IP addresses. Is there any way I can set fitler to DNS name instead of IP address?
Thansk,
Abcuser

---

### Post by CromagDK on 2007-10-25
I think this could help, i hope :)

cromagDK@server:~$ nslookup [www.google.com](www.google.com)

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 66.102.9.104
Name:   [www.l.google.com](www.l.google.com)
Address: 66.102.9.147
Name:   [www.l.google.com](www.l.google.com)
Address: 66.102.9.99

cromagDK@server:~$

if you can use them ip's try if it works.

---

### Post by KevinM1 on 2007-10-25
Newbie question here:

If you block user website access to everything but Google, then wouldn't the sites returned in a search be blocked as well?

---

### Post by whit on 2007-10-25
If you're trying to control your users' browsing, the traditional way is to set up a web proxy server. You set that up with the firewall so that they can't directly get to the web at all, but have to send requests through the proxy, on which you whitelist or blacklist sites.

I think you'll find that Google actually resolves to scores of different IPs, in an every-shifting way - they've got a highly-distributed system. So just handling it with iptables is next to impossible.

---

### Post by whit on 2007-10-25
> **KevinM1 said:**
> If you block user website access to everything but Google, then wouldn't the sites returned in a search be blocked as well?Yeah, but not the Google cache version of most of the sites it finds.

---

