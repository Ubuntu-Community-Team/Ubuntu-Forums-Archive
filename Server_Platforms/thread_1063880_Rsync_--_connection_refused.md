---
title: "Rsync -- connection refused"
date: 2009-02-08
forum: Server Platforms
---

### Post by DrJohn999 on 2009-02-08
(Mythbuntu) 8.10: Trying to get backuppc to pull backups onto a LTS 8.04 server on this new box. No problems for backuppc on any of the other 5 clients here, Linux or Windows.

When I attempt to list available rsync modules on the server command line I get 'connection refused':
Code:

```
:/etc$ rsync john@m3n78EM::
rsync: failed to connect to m3n78EM: Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(105) [receiver=2.6.9]
```

The same command, directed, for example, to my Ubuntu 8.10 laptop running rsyncd set up the same way gives:
Code:

```
/etc$ rsync john@dell-d610u::
Root            Full Backup
/etc$
```

Similar results for the others except this new machine. Rsyncd apparently starts on the system OK as S20rsync in /etc/rc2.d:
Code:

```
$ cat /var/log/rsyncd.log
2009/02/07 13:27:59 [6903] rsyncd version 3.0.3 starting, listening on port 873
$
```

/etc/rsyncd.conf:
Code:

```
log format = %h %o %f %l %b
log file = /var/log/rsyncd.log

[Root]
        path = /
        comment = Full Backup
        uid = root
        gid = root
        read only = true
        auth users = john
        secrets file = /etc/rsyncd.secrets

```
/etc/rsyncd.secrets:
Code:

```
john:_my_password_

```
File permissions:
Code:

```
/etc$ ls -lisa rsync*
596731 4 -rw-r--r-- 1 root root 199 2009-02-07 14:03 rsyncd.conf
596733 4 -rw------- 1 root root  16 2009-01-24 08:50 rsyncd.secrets
/etc$

```
There is no apparent firewalling going on:
Code:

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
$

```
I can't see what's different bewteen this system and the others, apart from its being Mythbuntu. No replies from that forum on this topic. 

Suggestions? Magic dust?

Thanks,

DJ

---

### Post by hictio on 2009-02-08
Not magic dust :) , but, just check the very basic network connection to the rsync port on that host.
Try:

```

telnet ip.address 873 ENTER

```

Does it open a connection?

---

### Post by DrJohn999 on 2009-02-08
Well, that found it, but not for the reason you might think:
```
:~$ telnet m3n78em 873
Trying 192.168.2.14...
telnet: Unable to connect to remote host: Connection refused
:$
```

Huh -- the <fixed> IP of the Mythbuntu box is ...15 not 14. Turns out I mistyped in /etc/hosts: crossed between ...14 and ...15.

Thanks, hictio for heading me in the right direction.

DJ

---

### Post by hictio on 2009-02-08
Wy are you using '/etc/hosts'? How many boxes do you have in your LAN?

---

### Post by cserpell on 2009-03-09
Unfortunately, I have the a problem very close to the above one, but I am sure that I didn't  misstyped the ip numbers...

What we do is having a replicating server that connects through rsync to each machine and saves its files locally.

We copied the same configuration files to each machine, and there is one that says:

```
cserpell@pc:/opt/resp$ rsync -arzvl --password-file=/opt/resp/password.rsync rsync://resp@172.17.67.145/etc/excluded.txt  /resp/bio-3/etc

rsync: failed to connect to 172.17.67.145: Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(105) [receiver=2.6.9]

```

The rsync daemon is running in the machine, but if yoou try to connect through telnet:

```

cserpell@pc:/opt/resp$ telnet 172.17.67.145 873
Trying 172.17.67.145...
telnet: Unable to connect to remote host: Connection refused

```

Is there any place in this machine where it can be blocking a certain port? Or is it possible to be a network/routing/firewall problem?

Thanks
Cristián

---

### Post by hictio on 2009-03-09
> **cserpell said:**
> 
Is there any place in this machine where it can be blocking a certain port? Or is it possible to be a network/routing/firewall problem?


The  Rsync server is a Linux box, right?
Are you sure the rsync service -the process I mean- is actually running on the server box?

If yes, take a look at the internal firewall, first of all.

```

sudo /sbin/iptables -nvL ENTER

```

And see if the rsync port (873) is listed as allowed with an origin from the box you are trying to connect.
You might do it like this:

```

sudo /sbin/iptables -nvL | egrep 873 ENTER

```

Another things to check for restriction access are:

- the actual rsyncd.conf file on the server, see if its allowing connections coming form the client's IP address.
- the TCP Wrappers, check the /etc/hosts.allow & /etc/hosts.deny files.

---

### Post by cserpell on 2009-03-09
> **hictio said:**
> The  Rsync server is a Linux box, right?
Are you sure the rsync service -the process I mean- is actually running on the server box?

```

root@server:~$ ps aux | grep rsync
root     10255  0.0  0.0   4392   484 ?        Ss   14:06   0:00 rsync --daemon

```

> 
If yes, take a look at the internal firewall, first of all.

```

sudo /sbin/iptables -nvL ENTER

```

And see if the rsync port (873) is listed as allowed with an origin from the box you are trying to connect.
You might do it like this:

```

sudo /sbin/iptables -nvL | egrep 873 ENTER

```

Another things to check for restriction access are:

- the actual rsyncd.conf file on the server, see if its allowing connections coming form the client's IP address.
- the TCP Wrappers, check the /etc/hosts.allow & /etc/hosts.deny files.

I disables iptables, so now in the server you see:
```
root@server:~$ /sbin/iptables -nvL
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

```

The /etc/hosts.deny file is empty and I added the client IP to hosts.allow

The rsyncd.conf file is the same of the other servers..

Nothing new happent, and in the server logs I don't see anything.

PD: Thanks for the fast reply

---

### Post by hictio on 2009-03-09
Ok, how's the topology there? It seems like everything that might be blocking rsync acces on the server its being taken care.
Is it possible that there is a router/ firewall blocking access to that service before you even reach the server itself?

---

### Post by cserpell on 2009-03-09
> **hictio said:**
> Ok, how's the topology there? It seems like everything that might be blocking rsync acces on the server its being taken care.
Is it possible that there is a router/ firewall blocking access to that service before you even reach the server itself?

Yes. Indeed, I don't have ownership over the network. There is a couple of routers/firewalls in the middle, but for example if I do ping 172.17.67.145 (IP of the rsync server), it responds normally. Now that you say it, maybe the access to that port is restricted. I will ask about it.

---

### Post by hictio on 2009-03-09
> **cserpell said:**
> Yes. Indeed, I don't have ownership over the network. There is a couple of routers/firewalls in the middle, but for example if I do ping 172.17.67.145 (IP of the rsync server), it responds normally. Now that you say it, maybe the access to that port is restricted. I will ask about it.

Mmmhhh... It might be the case, given that rsync port its lower than 1024... Perhaps, just for testing it, you can launch another rsync daemon on the server, using a higher port, just to test it.
Use the '--port' flag.

---

### Post by cserpell on 2009-03-09
> **hictio said:**
> Mmmhhh... It might be the case, given that rsync port its lower than 1024... Perhaps, just for testing it, you can launch another rsync daemon on the server, using a higher port, just to test it.
Use the '--port' flag.

Thanks for your help. Finally, it worked without doing anything more than allowing anybody and asking to allow my connection.

---

### Post by hictio on 2009-03-09
> **cserpell said:**
> Thanks for your help. Finally, it worked without doing anything more than allowing anybody and asking to allow my connection.

What do you mean, I'm sorry...
Asking you mean the "firewall people"?
Nobody, you mean the configuration option on '/etc/rsyncd.conf'?

---

