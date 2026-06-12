---
title: "Connect to remote MySQL server"
date: 2014-07-11
forum: Server Platforms
---

### Post by alfirdaous on 2014-07-11
Hello everybody,

I would like to connect to a remote MySQL server, but it doesn't go, these are the configurations that 've made:

From Server IP: a.b.c.d
To Server IP: 1.2.3.4


[COLOR=#ff0000]**To Server:**[/COLOR]

[COLOR=#000080]MySQL:[/COLOR]

```
SELECT password('passwd');
GRANT USAGE ON *.* TO 'USERNAME'@'a.b.c.d' IDENTIFIED BY PASSWORD 'Encrypted_Password';

```[COLOR=#000080]

IPTables:[/COLOR]

```
iptables -A INPUT -i eth0 -s a.b.c.d -p tcp --destination-port 3306 -j ACCEPT

```

[COLOR=#000080]Services Reboot:[/COLOR]

```
service mysql restart
mysql stop/waiting
mysql start/running, process 17985
service apache2 restart
 * Restarting web server apache2                                                                                                         ... waiting                                                                                                                    [ OK ]

```

[COLOR=#000080]Test:[/COLOR]

```
mysql -u USERNAME -p -h 1.2.3.4
ERROR 2003 (HY000): Can't connect to MySQL server on '1.2.3.4' (110)

```

Thanks in advance

---

### Post by minaev on 2014-07-11
Does mysqld listen on the interface 1.2.3.4?
What happens when you try to connect with telnet? Like, 'telnet 1.2.3.4 3306'?

---

### Post by SeijiSensei on 2014-07-11
Most daemons in Ubuntu are configured to listen only on the localhost interface by default for security.

Find this entry in /etc/mysql/my.cnf:
```
bind-address            = 127.0.0.1
```
and comment it out by placing a hash character "#" at the beginning of the line.  Then restart mysql with "sudo service mysql restart".

The server will now listen on all interfaces.

---

### Post by alfirdaous on 2014-07-11
@[**[COLOR=#000000]minaev[/COLOR]**]("http://ubuntuforums.org/member.php?u=233606"):

```

# telnet 1.2.3.4 3306
Trying 1.2.3.4...
telnet: Unable to connect to remote host: Connection timed out

```


@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"): bind-address is commented, and I have another server which is connected successfuly:

```

#bind-address           = 127.0.0.1

```

---

### Post by The Cog on 2014-07-11
Another possibility is the firewall rules. There is no point appending an ACCEPT rule if prior rules already DROP. Try inserting the ACCEPT at the start of the rules instead of appending:
```
iptables -I INPUT -s a.b.c.d -p tcp --destination-port 3306 -j ACCEPT
```

---

### Post by alfirdaous on 2014-07-11
@[**[COLOR=#C61919][B]The Cog**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=437760"): I do have the rule in iptables:

```

iptables -L -n | grep 1.2.3.4
ACCEPT     tcp  --  1.2.3.4          0.0.0.0/0            tcp dpt:3306

```

The thing is why the other server is connected and this one not

---

### Post by volkswagner on 2014-07-11
Since telnet is timing out, either iptables is not configured correctly or there is another firewall/router/forward issue.

Is the mysql server the firewall for the entire lan?

are you trying to connect via WAN or LAN?

---

### Post by alfirdaous on 2014-07-11
@[**[COLOR=#000000]volkswagner[/COLOR]**]("http://ubuntuforums.org/member.php?u=288711"): I am testing from another server and it works perfectly, I am using WAN:

```

mysql -u USERNAME -p -h 1.2.3.4
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 188
Server version: 5.5.37-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2014, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 


```

---

### Post by volkswagner on 2014-07-11
You did not answer about firewall.

What does your structure look like?

Is the mysql server the firewall for the entire lan?  Do you have a router/firewall in front that needs to forward to
the mysql box?

Are you trying test from inside lan possibly causeing NAT issue?

---

### Post by volkswagner on 2014-07-11
Oh, now I'm not keeping up ;)

You can successfully log in to mysql from a different remote machine?
Please explain differences between problem client and working client.
Are both clients on the same network, with same public ip?

---

### Post by alfirdaous on 2014-07-11
Yes, I am using the same machine, and try to connect, but it fails

---

### Post by alfirdaous on 2014-07-11
I created a new user and test it on server1, but it does NOT work

to test the same,

I created a new user and test it on **server2, AND IT WORKS**

I do not know where is the problem with server1

---

### Post by volkswagner on 2014-07-11
This is getting more confusing.

Please do not call a client computer a server. Although the machine may not be a workstation (acting as a server), if it
connects to a MySQL server... it's acting as a client.

From = client
to = server

I don't know how to interpret your last response.

I still have no idea what your network topography is.

You have not answered previous questions about explaining your network.

---

### Post by alfirdaous on 2014-07-11
I don't think there is an issue with the network, since I am using the same one

I created a new username under client client1, it DOES NOT WORK

THEN

I created a new username under client **client2**, [COLOR=#ff0000]**it WORKS**[/COLOR]

---

### Post by alfirdaous on 2014-07-11
I desactivated the IPTables from the client side and it WORKS, what was the problem, I am using the same rules in both clients

---

### Post by alfirdaous on 2014-07-11
These are the rules that I am using in client (where it works), I copied the same, but DOES NOT WORK, it works only if I DESACTIVATED IPTables:

```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          Firewall maison
# Required-Start:    $local_fs $remote_fs $network $syslog
# Required-Stop:     $local_fs $remote_fs $network $syslog
# Default-Start:
# Default-Stop:
# X-Interactive:     false
# Short-Description: Firewall maison
### END INIT INFO

# Mise à 0
iptables -t filter -F
iptables -t filter -X
echo "Mise à 0"

# On bloque tout
iptables -t filter -P INPUT DROP
iptables -t filter -P FORWARD DROP
iptables -t filter -P OUTPUT DROP
echo "Interdiction"

# Ne pas casser les connexions établies
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Autorise le loopback (127.0.0.1)
iptables -t filter -A INPUT -i lo -j ACCEPT
iptables -t filter -A OUTPUT -o lo -j ACCEPT
echo "Loopback"

# ICMP (le ping)
iptables -t filter -A INPUT -p icmp -j ACCEPT
iptables -t filter -A OUTPUT -p icmp -j ACCEPT
echo "Ping OK"

# SSH IN/OUT
iptables -t filter -A INPUT -p tcp --dport 1981 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 1981 -j ACCEPT
echo "SSH OK"

# DNS In/Out
iptables -t filter -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -t filter -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 53 -j ACCEPT
iptables -t filter -A INPUT -p udp --dport 53 -j ACCEPT
echo "DNS OK"

# NTP Out
iptables -t filter -A OUTPUT -p udp --dport 123 -j ACCEPT
echo "NTP OK"

# HTTP + HTTPS Out
iptables -t filter -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 443 -j ACCEPT
# HTTP + HTTPS In
iptables -t filter -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 8443 -j ACCEPT
echo "HTTP / HTTPS OK"

# FTP Out
iptables -t filter -A OUTPUT -p tcp --dport 21 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 20 -j ACCEPT
# FTP In
# imodprobe ip_conntrack_ftp # ligne facultative avec les serveurs OVH
iptables -t filter -A INPUT -p tcp --dport 20 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 21 -j ACCEPT
iptables -t filter -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
echo "FTP OK"

# Mail SMTP:25
iptables -t filter -A INPUT -p tcp --dport 25 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 25 -j ACCEPT
# Mail POP3:110
iptables -t filter -A INPUT -p tcp --dport 110 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 110 -j ACCEPT
# Mail IMAP:143
iptables -t filter -A INPUT -p tcp --dport 143 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 143 -j ACCEPT
# Mail POP3S:995
iptables -t filter -A INPUT -p tcp --dport 995 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 995 -j ACCEPT
echo "Mail OK"

# Monit
iptables -t filter -A INPUT -p tcp --dport 1983 -j ACCEPT
echo "Monit OK"

# Webmin
#iptables -t filter -A INPUT -p tcp --dport 10000 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 8183 -j ACCEPT
echo "Webmin OK"

# Ajenti
iptables -A INPUT -p udp -m state --state NEW --dport 2012 -j ACCEPT
iptables -A INPUT -p tcp -m state --state NEW --dport 2012 -j ACCEPT
echo "Ajenti OK"

# Transmission:
iptables -A OUTPUT -p tcp --dport 9091 -j ACCEPT
iptables -A INPUT -p tcp --dport 9091 -j ACCEPT
iptables -A INPUT -p tcp --dport 51413 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 51413 -j ACCEPT
echo 'Transmission OK'

```

---

### Post by The Cog on 2014-07-11
MySQL uses TCP port 3306 by default. I see no mention of TCP port 3306 being allowed out in the above script so I would not expect MySQL client to be able to connect out to a server.

I would be inclined to investigate what is wrong with the client where mysql **does** work - maybe the firewall script in that machine is broken.

---

### Post by alfirdaous on 2014-07-12
> **The Cog said:**
> I would be inclined to investigate what is wrong with the client where mysql **does** work - maybe the firewall script in that machine is broken.

How can I check it?

---

### Post by The Cog on 2014-07-13
First, I would check that the scripts really are the same, just in case there's been a slip-up in copying. If they are, then I would run 
```
sudo iptables -nvL
```
on both, and compare the outputs. Given identical scripts, I would expect identical iptables listings. I am wondering if perhaps the script on the one that does allow MySQL is failing completely - maybe there are no firewall rules at all for some reason.

One thing to bear in mind though - changing the iptables rules might not interrupt existing connections. So if you connect to MySQL and **then** enter iptables rules that block outgoing MySQL connections, remember that most firewall rulesets have entries that allow ESTABLISHED connections.

---

### Post by alfirdaous on 2014-07-14
I added this line into a server:

```

# Client mysql / Access to remote MySQL into server1
iptables -t filter -A INPUT -p tcp --dport 3306 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 3306 -j ACCEPT
echo 'MySQL client OK'

```


and now it works, however I specified the IP address: of each client on the server, it blocks one and allowed the other one:

```

iptables -A INPUT -i eth0 -s IP_MACHINE_1 -p tcp --destination-port 3306 -j ACCEPT

iptables -A INPUT -i eth0 -s IP_MACHINE_2 -p tcp --destination-port 3306 -j ACCEPT

```

---

