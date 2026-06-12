---
title: "Fail2Ban Identifies Filter Actions in Log, but Ban ineffective"
date: 2020-06-05
forum: Security
---

### Post by ptamarin on 2020-06-05
Hello All,

Huge fan of Ubuntu on the desktop and server. I am setting up a Ubuntu Server 18.04 with Webmin/Virtualmin, Apache, Bind DNS, MySQL, PostFix, and PHP. Using webmin to configure Firewalld as the primary firewall. Things are overall working well. I had some issues with the filters for named-refused in fail2ban but was able to remedy them by accessing the new filter code directly from their git for the new version. 

Onto the issue:
Fail2Ban recognizes an event fitting a filter from PostFix-Sasl or Named-Refused and applies the ban. The ban does not seem to be registered in firewalld or iptables. I tried to check the fail2ban process is running as root which it is. I tried firewallcmd-allports and iptables-allports, both do not seem to ban IPs.

Fail2ban log example (notice the "already banned": 
```
2020-06-05 23:05:53,756 fail2ban.filter         [845]: INFO    [named-refused] Found 3.81.25.142 - 2020-06-05 23:05:53
2020-06-05 23:05:53,788 fail2ban.filter         [845]: INFO    [named-refused] Found 3.81.25.142 - 2020-06-05 23:05:53
2020-06-05 23:05:53,818 fail2ban.filter         [845]: INFO    [named-refused] Found 3.81.25.142 - 2020-06-05 23:05:53
2020-06-05 23:05:53,835 fail2ban.actions        [845]: NOTICE  [named-refused] 3.81.25.142 already banned
2020-06-05 23:06:04,486 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.70 - 2020-06-05 23:06:04
2020-06-05 23:06:06,291 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.66 - 2020-06-05 23:06:06
2020-06-05 23:06:12,023 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 89.248.168.218 - 2020-06-05 23:06:12
2020-06-05 23:06:53,336 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.66 - 2020-06-05 23:06:53
2020-06-05 23:06:53,337 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.70 - 2020-06-05 23:06:53
2020-06-05 23:06:53,886 fail2ban.actions        [845]: WARNING [postfix-sasl] 87.246.7.66 already banned
2020-06-05 23:07:41,999 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.66 - 2020-06-05 23:07:41
2020-06-05 23:07:42,000 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.70 - 2020-06-05 23:07:41
2020-06-05 23:08:29,519 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.70 - 2020-06-05 23:08:29
2020-06-05 23:08:29,519 fail2ban.filter         [845]: INFO    [postfix-sasl] Found 87.246.7.66 - 2020-06-05 23:08:29
2020-06-05 23:08:29,987 fail2ban.actions        [845]: WARNING [postfix-sasl] 87.246.7.70 already banned
2020-06-05 23:08:46,874 fail2ban.filter         [845]: INFO    [named-refused] Found 3.85.224.129 - 2020-06-05 23:08:46
2020-06-05 23:08:50,907 fail2ban.filter         [845]: INFO    [named-refused] Found 3.85.224.129 - 2020-06-05 23:08:50
2020-06-05 23:08:50,937 fail2ban.filter         [845]: INFO    [named-refused] Found 3.85.224.129 - 2020-06-05 23:08:50
2020-06-05 23:08:50,967 fail2ban.filter         [845]: INFO    [named-refused] Found 3.85.224.129 - 2020-06-05 23:08:50
2020-06-05 23:08:50,998 fail2ban.filter         [845]: INFO    [named-refused] Found 3.85.224.129 - 2020-06-05 23:08:50
2020-06-05 23:08:51,026 fail2ban.actions        [845]: NOTICE  [named-refused] Ban 3.85.224.129
```


Please help! I've spent 10 hours on this googling and checking settings.

---

### Post by ptamarin on 2020-06-05
Ran this

```
root@cp:/etc/fail2ban/action.d# iptables -L f2b-named-refused -v -n
Chain f2b-named-refused (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

---

