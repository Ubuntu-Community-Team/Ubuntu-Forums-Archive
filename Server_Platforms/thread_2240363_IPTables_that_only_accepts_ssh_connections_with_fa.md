---
title: "IPTables that only accepts ssh connections with fail2ban on Ubuntu Server 14.04"
date: 2014-08-19
forum: Server Platforms
---

### Post by excetara2 on 2014-08-19
I just installed Ubuntu Server 14.04 and don't have much experience with IPtables. I am trying to get a basic setup going where I only accept SSH connections on port 22 and 2222. Everything else at the moment I want to block. Below is the setup that works:

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N fail2ban-ssh
-A INPUT -p tcp -m multiport --dports 22,2222 -j fail2ban-ssh
-A fail2ban-ssh -j RETURN

I tried to change it either to:

-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N fail2ban-ssh
-A INPUT -p tcp -m multiport --dports 22,2222 -j fail2ban-ssh
-A fail2ban-ssh -j RETURN

or:

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N fail2ban-ssh
-A INPUT -p tcp -m multiport --dports 22,2222 -j fail2ban-ssh
-A INPUT -j DROP
-A fail2ban-ssh -j RETURN

I have noticed that the rules for fail2ban-ssh are automatically added to my iptables on boot because if I save them with iptables-persistant they are entered twice. How do I go about blocking everything accept those 2 ports using fail2ban?

---

### Post by nerdtron on 2014-08-19
I'm not an expert in fail2 ban but I think the ports to monitor are in the config of fail2ban, therefore, just input your normal accept/reject ports in IPtables and then let fail2ban block/unblock IP addresses that violate it rules. fail2ban will add its own iptables entries.

---

### Post by excetara2 on 2014-08-19
Yes they're are ports I set in the config but I want to block all other ports but ssh ports. I don't think fail2ban monitors everything?? Just those ports. I want to block all other ports but when I setup the rule to do so no ports are allowed.

---

### Post by Doug S on 2014-08-20
There are some other things you will need to deal with in the INPUT chain if you want to have it default to "DROP".
You should specifically allow the lo interface. Example:```
$IPTABLES -A INPUT -i lo -j ACCEPT
```You should specifically allow packets on an existing or established connection. Example:```
$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

### Post by excetara2 on 2014-08-20
This is my final table. My main issue I belive was not having the accept 22,2222 also because I had tried using drop with both the

```
-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
```

but to no avail. After I added in the lines to accept 22 and 2222 I had no problems. I guess the fail2ban just check the logs and returns as long as not to many login attempts but these ports still have to be open in iptables.

```
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N fail2ban-ssh
-A INPUT -p tcp -m multiport --dports 22,2222 -j fail2ban-ssh
-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 2222 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 4242 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 4282 -j ACCEPT
-A INPUT -j DROP
-A fail2ban-ssh -j RETURN
```

---

