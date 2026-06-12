---
title: "Problem on ssh connect the server"
date: 2008-07-06
forum: Server Platforms
---

### Post by satimis on 2008-07-06
Hi folks,


Ubuntu LAMP 6.06 amd64
IP 192.168.0.52


Local PC
IP 192.168.0.10


Without iptables running the local PC can ssh connect the server at port 2222.  


Just have iptables up running local PC fails to ssh-connect the server

$ ssh -p 2222 192.168.0.52```

ssh: connect to host 192.168.0.52 port 2222: Connection timed out

```


$ tail /var/log/lastlog (local PC)```

&#994;iHtty4A&#65533;HttySKGtty1Gtty1&#65533;BGtty1satimis@mail:~$ 
```


$ tail /var/log/faillog(local PC) ```

tty1&#65533;&#65533;&#65533;tty1
           toHtty1#&#65533;Hsatimis@mail:~$ 
```

I can't understand the meaning of the codes.  Are these the right files to check?


$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# Allow ssh from workstation local IP

iptables -A INPUT -s 192.168.0.10 -p tcp --dport 22 -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -j LOG



# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT ACCEPT

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

```

Please advise.  TIA


B.R.
satimis

---

### Post by sil3nt on 2008-07-06
I could be stating the obvious here but you have an allow rule for port 22 not port 2222 in iptables.

If you allow 2222 then you should be all good I am pretty sure.

---

### Post by satimis on 2008-07-06
> **sil3nt said:**
> I could be stating the obvious here but you have an allow rule for port 22 not port 2222 in iptables.

If you allow 2222 then you should be all good I am pretty sure.
Hi sil3nt,


Thanks.  I made a mistake on port number.  It works now.


B.R.
satimis

---

### Post by sil3nt on 2008-07-06
No worries mate, I make typo mistakes like that all the time ;)

---

