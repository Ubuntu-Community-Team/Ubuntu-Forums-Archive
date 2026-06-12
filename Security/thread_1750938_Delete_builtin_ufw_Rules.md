---
title: "Delete builtin ufw Rules"
date: 2011-05-06
forum: Security
---

### Post by davidkazuhiro on 2011-05-06
How do you delete ufw rules which you didn't make?

I want to block the FTP ports (20 & 21) but even if I put in DENY rules, it appears that these rules are letting traffic through

```
       9      400 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:20 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 21,20 state RELATED,ESTABLISHED 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 21,20 state RELATED,ESTABLISHED 
```


How do I delete these rules? I've tried.
```
sudo ufw delete allow 20
sudo ufw delete proto tcp from any to any 20
```
but I get "Could not delete non-existent rule".

Since I didn't make those rules I have no idea what OpenBSD's PF syntax (what ufw uses) is for them. Any help?

---

### Post by sj1410 on 2011-05-06
well deleting a rule is simple, simply prefix the original rule with delete. but it seems that the existing rules are not added with ufw

just check 

```

sudo ufw status

```

for info you can have a look at [Ubuntu Uncomplicated Firewall]("http://blog.swapnil.me/2011/04/ubuntu-uncomplicated-firewall.html")

---

### Post by bodhi.zazen on 2011-05-06
An easier method is to delete rules by number.

List your rules with:

```
sudo ufw status numbered
```

Then to delete a specific rule you use

```
sudo ufw delete 3
```

See [man ufw](http://manpages.ubuntu.com/manpages/natty/en/man8/ufw.8.html) for details.

Order of rules is important.

The default ufw rules do NOT allow incoming connections, it must be something you added or modified. Are you using any other firewall tools ? Did you edit rules / config files yourself ?

If you need assistance post your rules.

```
sudo ufw status verbose
```

---

