---
title: "Wildcard's in Firestarter."
date: 2005-06-09
forum: Server Platforms
---

### Post by dmccarney on 2005-06-09
Hello, I currently have a policy enabled in my firestarter that only allows access to port 22 from one ip address (the one and only other computer I generally use). The problem is that this other computer is a windows workstation that is assigned an ip by DHCP (I think that is the right acronym). I'm not the administrator of this network and it would difficult for me to get this workstation to use a static ip. So, as you can imagine my problem is that my firewall at home only allows connections for a few days, as soon as the ip changes it blocks it. I've been poking around looking for a way to use a wild-card on the last digit of the ip for my rule but I've been unable to find a solution. This is probably an RTFM question but I figure I'd post anyway and perhaps get some feedback. I know exactly what the ip of this workstation will be consistantly except for the very last digit. Any solutions/suggestions would be appreciated.

---

### Post by word_virus on 2005-06-10
You can specifiy a range of ips for Firestarter to admit or deny.  The following from the Firstarter FAQ ([http://www.fs-security.com/docs/faq.php):](http://www.fs-security.com/docs/faq.php):)

Q: How do you specify a range of IPs or use wildcards in the rules?
Wherever in Firestarter a single numerical IP address can be inputted as part of a policy rule, a human readable hostname or a network identifier can also be used. This last form allows you to apply rules to a range of IP addresses. 

A range is entered as either address/netmask, for example 192.168.0.1/255.255.255.0, or more commonly in CIDR format as 192.168.0.1/24. 

The CIDR address consists of a standard dotted format 32-bit IP address and a postfix of the number of network identifying bits. This might sound confusing, and it is, but it is the only valid way to group IP addresses on the Internet. 

Luckily you don't have to break out your pocket calculator to work out an IP range, as there exists many IP calculators online. 

CIDR range notation examples:
```

CIDR format         First host          Last host           Number of hosts 
192.168.0.1/24   192.168.0.1      192.168.0.254              254 
192.168.0.1/25   196.168.0.1      192.168.0.126              126 
192.168.0.1/26   192.168.0.1      192.168.0.62                  62 
192.168.0.1/27   192.168.0.1      192.168.0.30                  30 
192.168.0.1/29   192.168.0.1      192.168.0.9                      6 
192.168.0.9/29   192.168.0.9      192.168.0.14                    6 
192.168.0.10/30 192.168.0.10    192.168.0.11                    2 
10.0.0.0/8           10.0.0.1            10.255.255.254  16777214 
10.0.1.17/28       10.0.1.17          10.0.1.30                        14
```

---

