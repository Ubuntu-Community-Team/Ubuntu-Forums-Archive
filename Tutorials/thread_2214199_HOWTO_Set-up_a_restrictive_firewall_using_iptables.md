---
title: "HOWTO: Set-up a restrictive firewall using iptables (RTFM-friendly)"
date: 2014-03-30
forum: Tutorials
---

### Post by Xentime on 2014-03-30
[B]This HOWTO is starting point for those who want a restrictive firewall for incoming, forwarded, and outgoing traffic.
[/B]
Here is an iptables configuration script (shell script) that I use as a starting point for all my machines. It drops all incoming and forwarded connections, while allowing outgoing connections on the FTP (21), SSH (22), HTTP (80), HTTPS (443), and DNS (53) ports. This allows you to perform software updates, browse the web, and establish remote connections to SSH servers running on their default port, while restricting all other traffic.

1. Open the Text Editor application (gedit) and paste the following into a new document:
```

#!/bin/sh

# Flush iptables
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -t raw -F
iptables -t security -F

# Delete user-defined chains
iptables -X
iptables -t nat -X
iptables -t mangle -X
iptables -t raw -X
iptables -t security -X

# Set iptables rules
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#iptables -A FORWARD -i lo -j ACCEPT
#iptables -A FORWARD -o lo -j ACCEPT
#iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 21 -j ACCEPT # FTP port
iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT # SSH port
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT # HTTP port
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT # HTTPS port
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT # DNS port

# Set iptables logging (Uncomment to enable)
#iptables -A INPUT -j LOG --log-level info --log-prefix "iptables(I) dropped: "
#iptables -A FORWARD -j LOG --log-level info --log-prefix "iptables(F) dropped: "
#iptables -A OUTPUT -j LOG --log-level info --log-prefix "iptables(O) dropped: "

# Set iptables default policy
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

# Save rule-set to file
sh -c "iptables-save > /etc/iptables.rules"
sh -c "iptables-save > /etc/iptables.downrules"

# Add the following to "/etc/network/interfaces":
# pre-up iptables-restore < /etc/iptables.rules
# post-down iptables-restore < /etc/iptables.downrules

# DD-WRT | Wireshark
# DD-WRT:
# iptables -t mangle -I FORWARD -j ROUTE --gw <monitor-ip> --tee
# Wireshark:
# ip.src==<target-ip>
# ip.dst==<target-ip>

exit 0

```

2. Save the file into your Home folder and name it "iptables.sh" (without the quotes).

3. Open up the Terminal application. (Ctrl+Alt+T)

4. Set the file permissions for "iptables.sh" to execute:
```

chmod +x iptables.sh

```

5. Run the shell script as root:
```

sudo ./iptables.sh

```

6. Open up the network interfaces configuration file for editing as root:
```

sudo nano /etc/network/interfaces

```

7. Add the following to the configuration file so the rules load on start-up:
```

pre-up iptables-restore < /etc/iptables.rules
post-down iptables-restore < /etc/iptables.downrules

```

8. Save the file and exit the text editor. (Ctrl+O <Enter> then Ctrl+X)

9. Restart/Reboot your computer.

10. Open up the Terminal application. (Ctrl+Alt+T)

11. Check iptables to ensure the rules have been applied:
```

sudo iptables -vL

```

Steps 6 and 7 are noted in shorthand within the shell script to aid with configuration when moving from one machine to another.


**Allow/Drop Outgoing Connections**
There are times you may want to use an application that will create outgoing connections not allowed by the rules in place for a limited time but do not want to poke holes in your firewall indefinitely (i.e. computer games). This is best achieved by simply allowing all outgoing connections and then restricting them when you are done. This is achieved by doing the following.

1. Open up the Terminal application. (Ctrl+Alt+T)

2-A. Allow all outgoing connections:
```

sudo iptables -P OUTPUT ACCEPT

```

or

2-B. Drop all outgoing connections (minus those that have ACCEPT rules):
```

sudo iptables -P OUTPUT DROP

```

3. Check iptables to ensure the rules have been applied:
```

sudo iptables -vL

```



References used in the creation of the shell script I wrote above:
[http://manpages.ubuntu.com/manpages/precise/man8/iptables.8.html](http://manpages.ubuntu.com/manpages/precise/man8/iptables.8.html)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

