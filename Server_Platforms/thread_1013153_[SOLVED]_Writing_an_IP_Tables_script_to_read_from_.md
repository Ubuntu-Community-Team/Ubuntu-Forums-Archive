---
title: "[SOLVED] Writing an IP Tables script to read from a blacklist text file"
date: 2008-12-16
forum: Server Platforms
---

### Post by jvincent08 on 2008-12-16
First, here's my script in the making:
```

#!/bin/bash

WHITELIST=good_ips.txt
BLACKLIST=bad_ips.txt
ALLOWED="22 80 3306"

# Ports used: 
# 22 - SSH    
# 80 - HTTP       
# 3306 - MySQL

# Drop all existing rules
iptables -F



# Allow ALL traffic from hosts in $WHITELIST
for x in `cat $WHITELIST`; do 
echo "Permitting $x..."
iptables -A INPUT -t filter -s $x -j ACCEPT
done

# Block all traffic from IP ranges in $BLACKLIST
for x in `cat $BLACKLIST`; do 
echo "Blocking $x..."
iptables -A INPUT -m iprange --src-range $x -j DROP
done

# Allow specific ports in $ALLOWED for trusted hosts
for port in $ALLOWED; do 
echo "Accepting port $port..."
iptables -A INPUT -t filter -p tcp --dport $port -j ACCEPT
done

```
bad_ips.txt contains a list of IP ranges in X.X.X.X-Y.Y.Y.Y format, with each range on its own line. When I run the script, it appears as though iptables is only recognizing the second IP number in each range (which shouldn't produce an error anyway), even though both numbers are stored together in the same variable:
```

root@host:~# sh iptables_init 
Permitting 127.0.0.1...
...cking 3.0.0.0-3.255.255.255
'ptables v1.4.0: iprange match: Bad IP address `3.255.255.255

Try `iptables -h' or 'iptables --help' for more information.
...cking 4.0.25.146-4.0.25.148
'ptables v1.4.0: iprange match: Bad IP address `4.0.25.148

```
And so on for each range. Also notice the odd formatting of the output (not a huge deal, but strange). Executing these commands manually works just fine, with no errors.

I've looked through my code over and over again, and I can't see where I went wrong. Any help?


Edit: Turns out adding a space after each line in the file solved the problem. A simple sed command did the trick:
```

sed -i 's/\r/ /g' bad_ips.txt

```
to replace each carriage return with a space.

---

