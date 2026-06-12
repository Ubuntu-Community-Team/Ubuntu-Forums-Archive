---
title: "my iptable rules..."
date: 2005-08-09
forum: Server Platforms
---

### Post by CrustyDOD on 2005-08-09
Hey

This is what i came up with for my firewall. I need ports to be open for: ftp, ssh, http, smtp for now

```
#!/bin/sh

#flush rules
iptables -F

#loopback interface
iptables -A INPUT -i lo -p all -j ACCEPT
iptables -A OUTPUT -o lo -p all -j ACCEPT

#Accept established connections
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --tcp-option ! 2 -j REJECT --reject-with tcp-reset

#ftp
iptables -A INPUT -p tcp -i eth0 --dport 21 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --dport 21 -j ACCEPT

#ssh
iptables -A INPUT -p tcp -i eth0 --dport 2001 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --dport 2001 -j ACCEPT

#http
iptables -A INPUT -p tcp -i eth0 --dport 80 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --dport 80 -j ACCEPT

#smtp
iptables -A INPUT -p tcp -i eth0 --dport 25 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --dport 25 -j ACCEPT

#drop everything else...
iptables -P INPUT DROP  

```

Is anything missing, is it ok?
Suggestions wanted... :)

---

### Post by LordHunter317 on 2005-08-09
[QUOTE=CrustyDOD]```

#loopback interface
iptables -A INPUT -i lo -p all -j ACCEPT
iptables -A OUTPUT -o lo -p all -j ACCEPT
```[/quote]The "-p all" here is unneccessary and should probably just be removed.

> ```
iptables -A INPUT -p tcp --tcp-option ! 2 -j REJECT --reject-with tcp-reset
```I'm farily certain this is highly undesirable.

> ```
#ftp
iptables -A INPUT -p tcp -i eth0 --dport 21 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --dport 21 -j ACCEPT
```FTP doesn't use UDP, remove the rule.  Your TCP rule is missing "-m state --state NEW --syn"  If your destination addresse is constant, you should include it.  Use the port name, ftp, instead of the number.  You'll want the FTP conntrack module loaded as well.

> ```
#ssh
iptables -A INPUT -p tcp -i eth0 --dport 2001 -j ACCEPT
```Don't bother running SSH on port 2001.  Same from above applies here, except the FTP conntrack part.

> ```
#http
iptables -A INPUT -p tcp -i eth0 --dport 80 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --dport 80 -j ACCEPT

#smtp
iptables -A INPUT -p tcp -i eth0 --dport 25 -j ACCEPT
iptables -A INPUT -p udp -i eth0 --dport 25 -j ACCEPT
```And for both of these two.

> ```
#drop everything else...
iptables -P INPUT DROP  

```This should be done first, not last.

---

### Post by CrustyDOD on 2005-08-09
wow thanks...

so this is what i did with your suggestions, did i miss something?
Didn't know that you can use 'ftp' instead of port number...
```
#!/bin/sh

#flush rules
iptables -F

#drop everything else...
iptables -P INPUT DROP

#loopback interface
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

#Accept established connections
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

#ftp
iptables -A INPUT -p tcp -m state --state NEW --syn -i eth0 --dport ftp -j ACCEPT

#ssh
iptables -A INPUT -p tcp -m state --state NEW --syn -i eth0 --dport 2001 -j ACCEPT

#http
iptables -A INPUT -p tcp -m state --state NEW --syn -i eth0 --dport http -j ACCEPT

#smtp
iptables -A INPUT -p tcp -m state --state NEW --syn -i eth0 --dport smtp -j ACCEPT

```

Oh and why is ssh on different port? Because its getting scanned like almost every day by some script kiddie on port 22... that's why...

---

### Post by LordHunter317 on 2005-08-09
And if you have strong passwords, he won't get in.  It doesn't provide you with any actual security gain.

He could just portscan you first and then attack, which is what will start happening when the entire world runs SSH on non-standard ports, leaving us right back where we started.

Othere than that, it looks fine.  You should add a /sbin/modprobe ip_conntrack_ftp line at the top to ensure the connection tracking for hte FTP protocol is running.

---

### Post by CrustyDOD on 2005-08-09
ah ok, then i'll just leave it at standart port, ssh i mean....

i inserted /sbin/modprobe ip_conntrack_ftp under #!/bin/sh

thanks for help!

---

### Post by relix42 on 2005-08-17
I would restrict ssh to known ip addresses if possible.  Port 22 is a tempting target for a lot of automated attack attempts using standard username and password combinations.

Something like
```

iptables -A INPUT -p tcp -s 10.10.10.10 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 10.10.10.11 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP

```

That way, only 10.10.10.10 and 10.10.10.11 can actually connect to the ssh daemon.  To everyone else, it doesn't exist.

---

