---
title: "MySQL security issue"
date: 2013-05-25
forum: Server Platforms
---

### Post by remeny on 2013-05-25
I have MySQL 5.5.31 running on Ubuntu server 12.04.1. I really don't know much about MySQL and, I managed to set it up so the data base can only be accessed from a computer with a specific ip address. 

I would like to set it up to be accessed from any computer on my network. I have been trying to figure out where I went wrong and have hit a brick wall.
 I can post which ever configuration files are needed

Thanks in advance

---

### Post by sandyd on 2013-05-25
> **remeny said:**
> I have MySQL 5.5.31 running on Ubuntu server 12.04.1. I really don't know much about MySQL and, I managed to set it up so the data base can only be accessed from a computer with a specific ip address. 

I would like to set it up to be accessed from any computer on my network. I have been trying to figure out where I went wrong and have hit a brick wall.
 I can post which ever configuration files are needed

Thanks in advance

Use iptables to make it so that only a specific network is allowed to access it. - see below example where 10.0.0.0/8 is my network. This restricts all data incoming to the server so that only those on the network can send incoming data
Run the below **(warning, it will remove all your current iptables rules) **
```

sudo iptables -F
sudo iptables -A INPUT -m tcp -p tcp -s 10.0.0.0/8 -d <ip of your server here> -j ACCEPT
sudo  iptables -A INPUT -m tcp -p tcp -d <ip of your server here> -j REJECT
sudo iptables-save > /path/to/iptables/rules

```

Replace /path/to/iptables/rules with an appropriate place to save the iptables rules

Now, to set the rules, just run
```

sudo iptables-restore < /path/to/iptables/rules

```

To make it apply on startup (If youve already done this, remove it)
```

sudo nano /etc/network/if-up.d/iptables

```
Enter in the below
```

#!/bin/bash
sudo iptables-restore < /path/to/iptables/rules
```
Control +X to save.

Run
```

sudo chmod +x /etc/network/if-up.d/iptables
``` to enable it.

To add more rules, just run iptables-restore, add the rules to iptables like above, and use iptables-save like above.

---

### Post by remeny on 2013-05-26
I think I see what you are getting at.
Does /etc/bash_completion.d/ sound like the place for the iptable rules?
Also I'm getting
 "iptables v1.4.12: Couldn't load target `DENY':No such file or directory" when that line runs.
Any Ideas?

---

### Post by sandyd on 2013-05-26
try again (updated)
make sure you are following all the direction to point

---

### Post by remeny on 2013-05-26
I cant ssh into the server any more, Ill get back as soon as I get a monitor on it. I guess I shouldn't mess with iptables while using ssh

---

### Post by sandyd on 2013-05-26
You should make sure that the subnet in your iptables is correct (mine is 10.0.0.0/8), in addition, you will only be able to ssh in from that network

---

### Post by CharlesA on 2013-05-26
> **remeny said:**
> I cant ssh into the server any more, Ill get back as soon as I get a monitor on it. I guess I shouldn't mess with iptables while using ssh

If you are going to mess with iptables remotely, use iptables-apply instead of iptables-restore. :)

You will need to add any existing firewall rules to the script sandyd provided or add a similar line to your existing firewall rules.

---

### Post by remeny on 2013-05-26
I'm thinking the issue is with MySQL. I can SSH into the server and use the database that way. I can Also connect using MySQL workbench. I can't, however get KMy money to connect unless I am at a specific IP address. I can't seem to find any MySQL error logs unfortunately.

---

### Post by CharlesA on 2013-05-26
Are you sure mysql is listening on the external interface and not lo?

It should show up as 0.0.0.0 in netstat.

---

### Post by remeny on 2013-05-26
How does this look to you


```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0    160 192.168.1.11:ssh        192.168.1.8:35161       ESTABLISHED
tcp        0      0 192.168.1.:microsoft-ds 192.168.1.8:33421       ESTABLISHED
udp        0      0 localhost:41373         localhost:41373         ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  8      [ ]         DGRAM                    8776     /dev/log
unix  3      [ ]         STREAM     CONNECTED     10139    
unix  3      [ ]         STREAM     CONNECTED     10138    
unix  2      [ ]         DGRAM                    10463    
unix  3      [ ]         STREAM     CONNECTED     10458    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     10056    
unix  3      [ ]         STREAM     CONNECTED     10436    
unix  3      [ ]         STREAM     CONNECTED     10435    
unix  3      [ ]         STREAM     CONNECTED     10434    

```

---

### Post by remeny on 2013-05-26
I figured it out!
The problem was that the user didn't have the permission to access the database from the host IP.
Once i gave the proper permissions, everything worked fine.
Thanks for the help, I appreciate it!:p

I just cant figure out how to mark this solved now.

---

