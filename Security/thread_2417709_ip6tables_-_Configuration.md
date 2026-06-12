---
title: "ip6tables - Configuration"
date: 2019-04-26
forum: Security
---

### Post by redrav3n on 2019-04-26
Hello there ! Some troubles with my ip6tables config.

Everything works... except smtp. I just don't understand why. Can you please help me understand what's happening ?

Thanks in advance !

```
ip6tables -F
ip6tables -X
ip6tables -t nat -F
ip6tables -t nat -X
ip6tables -t mangle -F
ip6tables -t mangle -X
ip6tables -P INPUT DROP
ip6tables -P FORWARD DROP
ip6tables -P OUTPUT DROP 

# Autorise les connexions déjà établies et localhost                
ip6tables -A INPUT -m state --state ESTABLISHED -j ACCEPT       
ip6tables -A OUTPUT -m state --state ESTABLISHED -j ACCEPT  
ip6tables -A INPUT -i lo -j ACCEPT                          
#ip6tables -A OUTPUT -o lo -j ACCEPT


#TOR
ip6tables -A OUTPUT -p tcp -m tcp --dport 9050 -j ACCEPT

# ICMP (Ping)                                       
   ip6tables -A INPUT -p icmpv6 -j ACCEPT						
    ip6tables -A OUTPUT -p icmpv6 -j ACCEPT

# DNS                                           
ip6tables -A OUTPUT -p tcp --dport 53 -j ACCEPT                 
ip6tables -A OUTPUT -p udp --dport 53 -j ACCEPT                     

# HTTP                                          
ip6tables -A OUTPUT -p tcp --dport 80 -j ACCEPT             


#HTTPS
ip6tables -A OUTPUT -p tcp --dport 443 -j ACCEPT                        


# Mail SMTP 

ip6tables -A INPUT -p tcp --dport 25  -j ACCEPT
ip6tables -A OUTPUT -p tcp --dport 25 -j ACCEPT  
ip6tables -A INPUT -p tcp --dport 587 -j ACCEPT
ip6tables -A OUTPUT -p tcp --dport 587 -j ACCEPT
ip6tables -A INPUT -p tcp --dport 465 -j ACCEPT
ip6tables -A OUTPUT -p tcp --dport 465 -j ACCEPT


#Transmission
ip6tables -A INPUT -p udp --dport 51413 -j ACCEPT
ip6tables -A OUTPUT -p udp --sport 51413 -j ACCEPT


# NTP (horloge du serveur) 
ip6tables -A OUTPUT -p udp --dport 123 -j ACCEPT    

# On log les paquets en entrée.
ip6tables -A INPUT -j LOG


exit 0

```

---

### Post by Doug S on 2019-04-26
I think you have only allowed the source side for each outgoing or incoming connection. You need to also allow the receiving side to reply. I think you also need:

```
ip6tables -A INPUT -p tcp --sport 25  -j ACCEPT
ip6tables -A OUTPUT -p tcp --sport 25 -j ACCEPT  
ip6tables -A INPUT -p tcp --sport 587 -j ACCEPT
ip6tables -A OUTPUT -p tcp --sport 587 -j ACCEPT
ip6tables -A INPUT -p tcp --sport 465 -j ACCEPT
ip6tables -A OUTPUT -p tcp --sport 465 -j ACCEPT
```(I did not test it.)

---

### Post by redrav3n on 2019-05-07
Hi there ! Everything works, i just had to accept icmpv6 !

I still have a few questions :

How to apply the rule before the connection to internet via network-manager ?  Someone said to me that placing the script in [FONT=&quot]/etc/network/if-pre-up.d/iptables wasn't great...

[/FONT]And do you see anything i could have forgot to make my firewall more "secure" ?

Thanks in advance !

---

