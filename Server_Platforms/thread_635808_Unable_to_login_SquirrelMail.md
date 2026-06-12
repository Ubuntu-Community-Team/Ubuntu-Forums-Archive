---
title: "Unable to login SquirrelMail"
date: 2007-12-09
forum: Server Platforms
---

### Post by satimis on 2007-12-09
Hi folks,


Ubuntu 7.04 server amd64
SquirrelMail


I can't login SquirrelMail if w/o running "sudo iptables -F'.  So I tried to find out which rule on /etc/rc.local obstructs the connection.  To my surprise after comment out all rules there I still can't login w/o running "sudo iptables -F".

Adding following rules did not help;```

# allows incomming port 143
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 143 -j ACCEPT

```

Replacing eth0 with Server IP address also did not help.  


Remark: ran "sudo /etc/init.d/rc.local start" after changing /etc/rc.local

Please advise how to solve the problem.   TIA


B.R.
satimis

---

### Post by MJN on 2007-12-09
Post your firewall rules (**sudo iptables -L**) when you are unable to connect.

Do you get any error from Squirrelmail (either on-screen or in your Apache logs)?

Mathew

---

### Post by satimis on 2007-12-09
> **MJN said:**
> Post your firewall rules (**sudo iptables -L**) when you are unable to connect.

$ sudo iptables -L```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             220.232.213.178     state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:8222 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:8333 
ACCEPT     tcp  --  anywhere             220.232.213.178     tcp dpt:vmware-authd 
REJECT     0    --  anywhere             220.232.213.178     reject-with icmp-port-unreachable 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  220.232.213.178      anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  220.232.213.178      anywhere            udp dpt:domain 
REJECT     0    --  localhost.localdomain  anywhere            reject-with icmp-port-unreachable 
REJECT     0    --  220.232.213.178      anywhere            reject-with icmp-port-unreachable 

```


$ cat /etc/rc.local```

#
# By default this script does nothing.

#exit 0

#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d 220.232.213.178 --reject-with icmp-port-unreachable

# allows squirrelmail input
#iptables -A INPUT -p ALL -i lo --source 127.0.0.1 -j ACCEPT


#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s 220.232.213.178 -p UDP --destination-port 53

# reject all other traffic from localhost
iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 4 -j REJECT -s 220.232.213.178 --reject-with icmp-port-unreachable

```
comment out the last 2 rules on "OUTPUT", then I can login squirrelmail.


> 
Do you get any error from Squirrelmail (either on-screen or in your Apache logs)?

I got an error message on SquirrelMail login screen```

ERROR
Error connecting to IMAP server: localhost.
110 : Connection timed out

```

However I can browse Apache default page w/o problem (I haven't setup homepage)


B.R.
satimis

---

### Post by MJN on 2007-12-10
It's your second-to-last firewall rule - you are specifically blocking any outgoing traffic from the loopback to anywhere (which includes the loopback itself). Why? Do you not trust your own machine?

Mathew

---

