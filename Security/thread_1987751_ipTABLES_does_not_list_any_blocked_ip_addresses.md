---
title: "ipTABLES does not list any blocked ip addresses ?"
date: 2012-05-26
forum: Security
---

### Post by starz677 on 2012-05-26
Hello,

I am running fail2ban and ipblock on my server

I ran this command and expected to see a long list of IP Addresses that were blocked but there are none.
[B]
sudo [/B]**iptables -L INPUT -v -n**

I am confused.

If ipblock is showing a lot of blocked IP addresses and fail2ban log shows a long list of blocked ipaddresses, why does iptables NOT show any of these ip addresses?

thx

---

### Post by darkod on 2012-05-26
If I'm not mistaken, that would only show you the current rules of iptables. If you never set a rule to block some ip/range manually in iptables, it won't be there.

The block might be logged in /var/log/messages or similar, but the command you posted would give you only the iptables rules, not all blocked entries.

---

### Post by JKyleOKC on 2012-05-27
A default installation of fail2ban will block an IP for only 10 minutes. The time can be changed in the configuration file, however. The idea is that a would-be invader will give up after 10 minutes of being refused access.

When fail2ban discovers a would-be intruder, it adds a rule to iptables to block that address and also sets a scheduled job for 10 minutes in the future. That scheduled job removes the rule from iptables. Thus unless you list the rules during that 10-minute window, you won't see its changes.

However it does write both actions to its log. Here's an example from my own /var/log/fail2ban.log file: ```
2012-05-05 11:36:36,087 fail2ban.actions: WARNING [proftpd] Ban 198.64.149.11
2012-05-05 11:46:36,723 fail2ban.actions: WARNING [proftpd] Unban 198.64.149.11

```

---

