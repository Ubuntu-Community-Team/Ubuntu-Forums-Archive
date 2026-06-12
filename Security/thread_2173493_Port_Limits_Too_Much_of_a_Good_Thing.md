---
title: "Port Limits: Too Much of a Good Thing?"
date: 2013-09-09
forum: Security
---

### Post by BuntuSeriously on 2013-09-09
Greetings!

Had a "really simple" idea/question for the community tonight; and need some savvy to move things along ;)

In that spirit, I'll submit the well-known "ufw limit ssh/tcp" commandline which is proffered as a means of thwarting a brute-force attack on a plain-jane client install:

```

root@laptop1:~# ufw limit ssh/tcp
Rule added
Skipping unsupported IPv6 'limit' rule

root@laptop1:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     LIMIT IN    Anywhere
```

OK, so we're setting up a rule to quash a dictionary attack directed @ port 22.  Good enough.

However, hypothetically, let's say we have a scenario in which other (unforeseen) ports on the subject machine could present themselves as a useful target for some miscreant passerby.

In that (academic?) case, how does this look as a way of essentially telling a would-be interloper to buzz off & stop hammering at all possible points of entry:

```

root@laptop1:~# ufw limit proto tcp from any to any port 1:65535
Rule added
Skipping unsupported IPv6 'limit' rule

root@laptop1:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
1:65535/tcp                LIMIT IN    Anywhere
```

In sum, what are the pros & cons of setting up a rule like this on a typical client; and would such an arrangement, indeed, have the net collective effect of blockading the entire portset from brute-force attack?

Finally, what are the relevant implications in the ubiquitous warning "Skipping unsupported IPv6 'limit' rule"?


Thanks again --

---

### Post by CharlesA on 2013-09-10
I just use iptables, not ufw for writing those rules.

```
# Impliment 90 minute lockout by rejecting any connections from an IP that is trying to bruteforce SSH.
# Blame Doug S: http://ubuntuforums.org/showthread.php?t=2137073
# Log anything that gets rejected - Commment this line out if you don't want logging enabled.
iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j LOG --log-prefix "SSH Attack: " --log-level info
iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j REJECT
iptables -A INPUT -p tcp -m tcp --dport 22 -m recent --set --name SSH -j ACCEPT

```

---

### Post by Cavsfan on 2013-09-10
> **CharlesA said:**
> I just use iptables, not ufw for writing those rules.

```
# Impliment 90 minute lockout by rejecting any connections from an IP that is trying to bruteforce SSH.
# Blame Doug S: http://ubuntuforums.org/showthread.php?t=2137073
# Log anything that gets rejected - Commment this line out if you don't want logging enabled.
iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j LOG --log-prefix "SSH Attack: " --log-level info
iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j REJECT
iptables -A INPUT -p tcp -m tcp --dport 22 -m recent --set --name SSH -j ACCEPT

```

Would you put that in the home directory and execute it at startup?

---

### Post by CharlesA on 2013-09-10
> **Cavsfan said:**
> Would you put that in the home directory and execute it at startup?

I suppose you could.

I have my iptables script sitting in /etc/network/if-pre-up.d/ so it runs before the network interface comes up.

Those aren't my full rules, but it'll block any traffic coming on it port 22 after 3 new connections are made in rapid succession.

As far as the OP's question goes, I'm not too sure what the limit part of ufw does as I don't use it, but I suspect you can find out by checking iptables directly:

```
sudo iptables -L
```

---

### Post by Cavsfan on 2013-09-10
> **Cavsfan said:**
> Would you put that in the home directory and execute it at startup?

> **CharlesA said:**
> I suppose you could.

I have my iptables script sitting in /etc/network/if-pre-up.d/ so it runs before the network interface comes up.

Those aren't my full rules, but it'll block any traffic coming on it port 22 after 3 new connections are made in rapid succession.

As far as the OP's question goes, I'm not too sure what the limit part of ufw does as I don't use it, but I suspect you can find out by checking iptables directly:

```
sudo iptables -L
```

```
cavsfan@cavsfan-MS-7529:~$ sudo iptables -L -n -v
Chain INPUT (policy ACCEPT 4185 packets, 4275K bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 3222 packets, 301K bytes)
 pkts bytes target     prot opt in     out     source               destination
```

I guess I have no rules. What file name is that saved as in /etc/network/if-pre-up.d/ ? I see I have the directory but there is just these two files:
```
cavsfan@cavsfan-MS-7529:/etc/network/if-pre-up.d$ ls
wireless-tools  wpasupplicant
```

Do I put that code in one of those files or a new one?
Thanks! Learning curve :)

---

### Post by CharlesA on 2013-09-10
It shouldn't matter. The file I use in named iptables, but it's a script I wrote to apply iptables rule, not something you'd use with ufw.

In any case, just add your rules to the file and run it and you should be good to go.

---

### Post by Cavsfan on 2013-09-11
> **CharlesA said:**
> It shouldn't matter. The file I use in named iptables, but it's a script I wrote to apply iptables rule, not something you'd use with ufw.

In any case, just add your rules to the file and run it and you should be good to go.


Ok Thanks! :)

---

### Post by SeijiSensei on 2013-09-11
> **CharlesA said:**
> I have my iptables script sitting in /etc/network/if-pre-up.d/ so it runs before the network interface comes up.

If you put scripts there, do they start when the network is activated from the desktop?  On servers I always have static addressing and set up the network when the system boots.  Ubuntu, by default, only starts the network after the user logs in.  Are the contents of /etc/network/if-pre-up.d/ run then?

---

### Post by CharlesA on 2013-09-11
> **SeijiSensei said:**
> If you put scripts there, do they start when the network is activated from the desktop?  On servers I always have static addressing and set up the network when the system boots.  Ubuntu, by default, only starts the network after the user logs in.  Are the contents of /etc/network/if-pre-up.d/ run then?

I'm not sure. I don't run iptables like that on anything but my servers.

---

### Post by Doug S on 2013-09-11
> **SeijiSensei said:**
> If you put scripts there, do they start when the network is activated from the desktop?  On servers I always have static addressing and set up the network when the system boots.  Ubuntu, by default, only starts the network after the user logs in.  Are the contents of /etc/network/if-pre-up.d/ run then?I tried it on a desktop computer, just as was described in the previous posts, and it worked fine. However, I had a tcpdump session running on another computer and noticed that the network stuff started on boot, not when I logged in. I thought I read somewhere that the delayed network start stuff only applied if one used something called network manager to configure the network. I didn't do anything to configure the network, it was a fresh saucy daily ISO installation from a day or two ago. (Notes: It was a VM, if that matters; I don't know much about Ubuntu desktop, as I normally only run Ubuntu servers.)

---

### Post by cariboo on 2013-09-11
> **Doug S said:**
> I tried it on a desktop computer, just as was described in the previous posts, and it worked fine. However, I had a tcpdump session running on another computer and noticed that the network stuff started on boot, not when I logged in. I thought I read somewhere that the delayed network start stuff only applied if one used something called network manager to configure the network. I didn't do anything to configure the network, it was a fresh saucy daily ISO installation from a day or two ago. (Notes: It was a VM, if that matters; I don't know much about Ubuntu desktop, as I normally only run Ubuntu servers.)

At one point several releases back, networking didn't start until after you logged in, but there were so many complaints, that networking now starts much sooner in the process. When using initscripts, it was just a matter of where the networking script was placed in the starting order, now that we are using upstart, it think it is a matter where the networking command is placed in the upstart script.

---

### Post by Cavsfan on 2013-09-12
Not sure how worried I am about this. I have never set anything like this up before so I guess it's nice to learn. :)
I put the stuff from CharlesA's post #2 into a text file and named it iptables.sh and I added  **#!/bin/bash** which I *think* is necessary.

```
cavsfan@cavsfan-MS-7529:/etc/network/if-pre-up.d$ cat iptables.sh
#!/bin/bash
# Impliment 90 minute lockout by rejecting any connections from an IP that is trying to bruteforce SSH.
# Blame Doug S: http://ubuntuforums.org/showthread.php?t=2137073
# Log anything that gets rejected - Commment this line out if you don't want logging enabled.
iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j LOG --log-prefix "SSH Attack: " --log-level info
iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j REJECT
iptables -A INPUT -p tcp -m tcp --dport 22 -m recent --set --name SSH -j ACCEPT

```

I made it executable **sudo chmod +x iptables.sh**
```
cavsfan@cavsfan-MS-7529:/etc/network/if-pre-up.d$ ls -l
total 12
-rwxr-xr-x 1 root root  344 Apr 28  2012 ethtool
-rwxr-xr-x 1 root root  569 Sep 12 11:56 iptables.sh
-rwxr-xr-x 1 root root 3839 May  3  2012 wireless-tools
lrwxrwxrwx 1 root root   32 Aug  8 10:47 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh
```

Rebooted and **sudo iptables -L** still doesn't seem to show anything.
```
cavsfan@cavsfan-MS-7529:/etc/network/if-pre-up.d$ sudo iptables -L
[sudo] password for cavsfan: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       
```

Is something wrong here?

---

### Post by CharlesA on 2013-09-12
I have my script just named iptables. Maybe that's part of the problem?

Here's what my script looks like.

```
#!/bin/bash

iptables=/sbin/iptables

# Flush current rules
echo "Flushing Firewall Rules"
$iptables -F
echo "Applying Firewall Rules"
# Accept Established/Related traffic
$iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# Accept ICMP packets
$iptables -A INPUT -p icmp -m limit --limit 1/sec  -j ACCEPT
# Impliment 90 minute lockout by rejecting any connections from an IP that is trying to bruteforce SSH.
# Blame Doug S: http://ubuntuforums.org/showthread.php?t=2137073
# Log anything that gets rejected - Commment this line out if you don't want logging enabled.
$iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j LOG --log-prefix "SSH Attack: " --log-level info
$iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j REJECT
$iptables -A INPUT -p tcp -m tcp --dport 22 -m recent --set --name SSH -j ACCEPT
# Allow HTTP
$iptables -A INPUT -p tcp -m tcp --dport 80 -m state --state NEW -j ACCEPT
# Allow HTTPS
$iptables -A INPUT -p tcp -m tcp --dport 443 -m state --state NEW -j ACCEPT
# Allow loopback
$iptables -A INPUT -i lo -j ACCEPT
# Reject everything else
$iptables -A INPUT -j REJECT

```

---

### Post by Cavsfan on 2013-09-12
> **CharlesA said:**
> I have my script just named iptables. Maybe that's part of the problem?

Here's what my script looks like.

```
#!/bin/bash

iptables=/sbin/iptables

# Flush current rules
echo "Flushing Firewall Rules"
$iptables -F
echo "Applying Firewall Rules"
# Accept Established/Related traffic
$iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# Accept ICMP packets
$iptables -A INPUT -p icmp -m limit --limit 1/sec  -j ACCEPT
# Impliment 90 minute lockout by rejecting any connections from an IP that is trying to bruteforce SSH.
# Blame Doug S: http://ubuntuforums.org/showthread.php?t=2137073
# Log anything that gets rejected - Commment this line out if you don't want logging enabled.
$iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j LOG --log-prefix "SSH Attack: " --log-level info
$iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j REJECT
$iptables -A INPUT -p tcp -m tcp --dport 22 -m recent --set --name SSH -j ACCEPT
# Allow HTTP
$iptables -A INPUT -p tcp -m tcp --dport 80 -m state --state NEW -j ACCEPT
# Allow HTTPS
$iptables -A INPUT -p tcp -m tcp --dport 443 -m state --state NEW -j ACCEPT
# Allow loopback
$iptables -A INPUT -i lo -j ACCEPT
# Reject everything else
$iptables -A INPUT -j REJECT

```

Thank you! I'm trying this now. :)

---

### Post by Cavsfan on 2013-09-12
Thank you! That worked well!
Not too sure I understand it but, I will take it that it does good. :)

---

