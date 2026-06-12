---
title: "Unable to block icmp requests permanently"
date: 2010-04-30
forum: Security
---

### Post by iavor on 2010-04-30
i've tried blocking ping requests with iptables.. and it didnt work

> iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

also tried editing sysctl.conf.. which worked perfectly but after i restarted the system i was able to ping my ubuntu machine from my lappy
here is what i added to sysctl.conf and then executed it with sysctl -p

> net.ipv4.icmp_echo_ignore_all = 1

here is another atempt to block..
this one worked too... but again after the restart i was able to ping my machine..

> echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all

Thanks in advance

P.S. im using Ubuntu 10.04.. but i've had the same issue with 9.10

---

### Post by cdenley on 2010-04-30
Using both iptables and sysctl blocked ICMP echo requests for me. Are you sure you're pinging your ubuntu system, not your router? Run this on your ubuntu system before you ping it.
```

sudo tcpdump -v -i eth0 'icmp[icmptype] = icmp-echo'

```

---

### Post by iavor on 2010-05-01
> **cdenley said:**
> Using both iptables and sysctl blocked ICMP echo requests for me. Are you sure you're pinging your ubuntu system, not your router? Run this on your ubuntu system before you ping it.
```

sudo tcpdump -v -i eth0 'icmp[icmptype] = icmp-echo'

```

yep im sure im pinging my pc :)

EDIT: the tcpdump output showed that i pinged it properly :)

---

### Post by iavor on 2010-05-01
i've tried editing /etc/rc.local and typed echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all 
and now its works after the restart ..

---

### Post by cdenley on 2010-05-01
> **iavor said:**
> i've tried editing /etc/rc.local and typed echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all 
and now its works after the restart ..

Sorry, I missed that the problem was after a reboot. This would be the proper way.
```

echo net.ipv4.icmp_echo_ignore_all = 1|sudo tee -a /etc/sysctl.conf

```

---

### Post by iavor on 2010-05-01
> **cdenley said:**
> Sorry, I missed that the problem was after a reboot. This would be the proper way.
```

echo net.ipv4.icmp_echo_ignore_all = 1|sudo tee -a /etc/sysctl.conf

```

thanks ill try that! :)

EDIT: ive tried it and it wasnt any different than editing sysctl.conf with nano :) the changes didnt stay permanent ! :)

---

### Post by fbnaia on 2010-05-01
Read this: **[https://help.ubuntu.com/community/UFW]("https://help.ubuntu.com/community/UFW")**

Specifically the **"Enable PING"**, It reads as follows:

Note: Security by obscurity may be of very little actual benefit with modern cracker scripts. By default, UFW allows ping requests. You may find you wish to leave (icmp) ping requests enabled to diagnose networking problems.

You need to edit /etc/ufw/before.rules and remove edit the following lines:

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

Change the "ACCEPT" to "DROP" or

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

---

### Post by cdenley on 2010-05-01
> **iavor said:**
> ive tried it and it wasnt any different than editing sysctl.conf with nano :) the changes didnt stay permanent ! :)

You mean the new line in sysctl.conf disappears when you reboot, or are you saying that the line in sysctl.conf is getting ignored?
```

sudo sysctl net.ipv4.icmp_echo_ignore_all

```

---

### Post by iavor on 2010-05-02
> **fbnaia said:**
> Read this: **[https://help.ubuntu.com/community/UFW]("https://help.ubuntu.com/community/UFW")**

Specifically the **"Enable PING"**, It reads as follows:

Note: Security by obscurity may be of very little actual benefit with modern cracker scripts. By default, UFW allows ping requests. You may find you wish to leave (icmp) ping requests enabled to diagnose networking problems.

You need to edit /etc/ufw/before.rules and remove edit the following lines:

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

Change the "ACCEPT" to "DROP" or

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

Thanks m8 that fixed my issue.. much appreciated

---

