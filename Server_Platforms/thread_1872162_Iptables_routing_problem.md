---
title: "Iptables routing problem"
date: 2011-10-30
forum: Server Platforms
---

### Post by mmmp on 2011-10-30
Hi 
I have problems to configuring the firewall on my VPN server to work.
My iptables configuration looks like this:

#iptables -F
#iptables -t nat -F
#iptables -t mangle -F
#iptables -X

#iptables -P INPUT DROP 
#iptables -P FORWARD DROP 
#iptables -P OUTPUT DROP

#iptables -A INPUT -i venet0 -p tcp --dport 1723 -j ACCEPT
#iptables -A INPUT -i venet0 -p gre -j ACCEPT
#iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#iptables -A INPUT -j REJECT

#iptables -A OUTPUT -o venet0 -p tcp --dport 1723 -j ACCEPT
#iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#iptables -A OUTPUT -j REJECT

Everything seem to work fine but I have two problems

1 - I can connect to my server but I have limited connection to the network and no internet:

(See attached image)

To solve this problem, I used this command:

#iptables -t nat -A POSTROUTING -j SNAT --to-source XX.XX.XX.XX
or
#iptables -t nat -A POSTROUTING -o venet0 -j MASQUERADE

but all traffic going around the firewall and the firewall has no effect.

2 - For the second when I activate the output policies and filters, I can only connect to server only once.

What is wrong in my configuration and what I shuld add for routing traffic before the firewall to limit several ports?

---

### Post by elico on 2011-10-30
it's related to the forwarding tables which you are using a drop policy...

---

### Post by Dangertux on 2011-10-30
As was stated you need to tune your FORWARD chain a little bit.

Test if it works with 

```

iptables -P FORWARD ACCEPT

```

---

### Post by SeijiSensei on 2011-10-30
Also make sure you have packet forwarding enabled in the kernel.  What does "cat /proc/sys/net/ipv4/ip_forward" return?  If it's zero, edit the file /etc/sysctl.conf and read the section in the file about packet forwarding.

---

### Post by mmmp on 2011-10-30
> **Dangertux said:**
> As was stated you need to tune your FORWARD chain a little bit.

Test if it works with 

```

iptables -P FORWARD ACCEPT

```

I have tested also with:

iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

but I have same problem.

---

### Post by mmmp on 2011-10-30
> **SeijiSensei said:**
> Also make sure you have packet forwarding enabled in the kernel.  What does "cat /proc/sys/net/ipv4/ip_forward" return?  If it's zero, edit the file /etc/sysctl.conf and read the section in the file about packet forwarding.

Yes, I have set it to 1 but I have still same problem.

---

### Post by mmmp on 2011-10-30
> **elico said:**
> it's related to the forwarding tables which you are using a drop policy...

I have tested also with:

iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

but I have same problem.

---

