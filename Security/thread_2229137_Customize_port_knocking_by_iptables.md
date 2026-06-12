---
title: "Customize port knocking by iptables"
date: 2014-06-11
forum: Security
---

### Post by alex218 on 2014-06-11
I want to customize port knocking in my VPS but haven`t any success whole day.
I find [this article]("https://www.digitalocean.com/community/tutorials/how-to-configure-port-knocking-using-only-iptables-on-an-ubuntu-vps") and trying repeat same, but there solution not work for me. I even try write myseft script.
I also try knockd but it also not work: or I can connect without knocking, or I can`t connect at all. Please, help me find solution. How you customize port knocking on your servers?

Override iptables script:
```

#!/bin/bash

# to be ensure overriding default rules
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F

# enable current connection, local network, http and https
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# manage ssh access port forwarding
sudo iptables -N SSHACCESS

# helpful steps blocks
sudo iptables -N STEP1
sudo iptables -N STEP2
sudo iptables -N STEP3

# enable access to ssh port (current: 2222)
sudo iptables -N PASSED
sudo iptables -A PASSED -m recent --name STEP3 --remove
sudo iptables -A PASSED -p tcp --dport 2222 -j ACCEPT
sudo iptables -A PASSED -j STEP1

# disable access to ssh port
# not connect to chain now
sudo iptables -N CLOSED
sudo iptables -A CLOSED -m recent --name OPEN1 --remove
sudo iptables -A CLOSED -m recent --name OPEN2 --remove
sudo iptables -A CLOSED -m recent --name OPEN3 --remove
sudo iptables -A CLOSED -p tcp --dport 2222 -j REJECT
sudo iptables -A CLOSED -j STEP1

# starting main logic
# redirect all input to sshaccess
# next logic block: BLOCK1
sudo iptables -A INPUT -j SSHACCESS

# BLOCK2    
# step1: add unique name or die
sudo iptables -A STEP1 -p tcp --dport 1155 -m recent --name OPEN1 --set -j DROP
sudo iptables -A STEP1 -j DROP

# BLOCK3
# step2: clear first 
sudo iptables -A STEP2 -m recent --name OPEN1 --remove
sudo iptables -A STEP2 -p tcp --dport 1255 -m recent --name OPEN2 --set -j DROP
sudo iptables -A STEP2 -j DROP

# BLOCK4
# step3: clear second
sudo iptables -A STEP3 -m recent --name OPEN2 --remove
sudo iptables -A STEP3 -p tcp --dport 1355 -m recent --name OPEN3 --set -j DROP
sudo iptables -A STEP3 -j DROP

# BLOCK1
# checking step number, DESC
# next logic block: BLOCK2 above
sudo iptables -A SSHACCESS -m recent --rcheck --name OPEN3 -j PASSED
sudo iptables -A SSHACCESS -m recent --rcheck --name OPEN2 -j STEP3
sudo iptables -A SSHACCESS -m recent --rcheck --name OPEN1 -j STEP2
sudo iptables -A SSHACCESS -j STEP1
```


Check script:

```
!/bin/bash

ports="1155 1255 1355"
host="%some_ip%"

for x in $ports
do
  nmap -Pn --host_timeout 201 --max-retries 0 -p $x $host
  sleep 1
done
ssh administator@${host} -p 2222
```

Terminal output(when can`t connect):

```
--host-timeout is specified in milliseconds unless you qualify it by appending 's', 'm', or 'h'. The value must be greater than 1500 milliseconds
QUITTING!
--host-timeout is specified in milliseconds unless you qualify it by appending 's', 'm', or 'h'. The value must be greater than 1500 milliseconds
QUITTING!
--host-timeout is specified in milliseconds unless you qualify it by appending 's', 'm', or 'h'. The value must be greater than 1500 milliseconds
QUITTING!
ssh: connect to host %some_ip% port 2222: Connection timed out
```


sudo iptables -L output:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
SSHACCESS  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain CLOSED (0 references)
target     prot opt source               destination         
           all  --  anywhere             anywhere             recent: REMOVE name: OPEN1 side: source
           all  --  anywhere             anywhere             recent: REMOVE name: OPEN2 side: source
           all  --  anywhere             anywhere             recent: REMOVE name: OPEN3 side: source
REJECT     tcp  --  anywhere             anywhere             tcp dpt:2222 reject-with icmp-port-unreachable
STEP1      all  --  anywhere             anywhere            

Chain PASSED (1 references)
target     prot opt source               destination         
           all  --  anywhere             anywhere             recent: REMOVE name: STEP3 side: source
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:2222
STEP1      all  --  anywhere             anywhere            

Chain SSHACCESS (1 references)
target     prot opt source               destination         
PASSED     all  --  anywhere             anywhere             recent: CHECK seconds: 30 name: OPEN3 side: source
STEP3      all  --  anywhere             anywhere             recent: CHECK seconds: 10 name: OPEN2 side: source
STEP2      all  --  anywhere             anywhere             recent: CHECK seconds: 10 name: OPEN1 side: source
STEP1      all  --  anywhere             anywhere            

Chain STEP1 (3 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere             tcp dpt:1155 recent: SET name: OPEN1 side: source
DROP       all  --  anywhere             anywhere            

Chain STEP2 (1 references)
target     prot opt source               destination         
           all  --  anywhere             anywhere             recent: REMOVE name: OPEN1 side: source
DROP       tcp  --  anywhere             anywhere             tcp dpt:1255 recent: SET name: OPEN2 side: source
DROP       all  --  anywhere             anywhere            

Chain STEP3 (1 references)
target     prot opt source               destination         
           all  --  anywhere             anywhere             recent: REMOVE name: OPEN2 side: source
DROP       tcp  --  anywhere             anywhere             tcp dpt:1355 recent: SET name: OPEN3 side: source
DROP       all  --  anywhere             anywhere 

```

---

### Post by untrustytahr on 2014-06-12
I didn't test this so you will have to do so.  I just mentally traced it and I am by no means an expert on iptables.  You should also increase the timeout to 1500 milliseconds on the host_timeout in your check script.

```

#!/bin/bash

# to be ensure overriding default rules
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F

# enable current connection, local network, http and https
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# create chains for knocking
sudo iptables -N SSHACCESS
sudo iptables -N STEP1
sudo iptables -N STEP2
sudo iptables -N STEP3
sudo iptables -N PASSED

# redirect all input to sshaccess
sudo iptables -A INPUT -j SSHACCESS

# step1: add flag OPEN1 or die
sudo iptables -A STEP1 -p tcp --dport 1155 -m recent --name OPEN1 --set -j DROP
sudo iptables -A STEP1 -j DROP

# step2: strip first check flag & set second flag if matched.
#            send back to first chain to die or be tagged with flag1
sudo iptables -A STEP2 -m recent --name OPEN1 --remove
sudo iptables -A STEP2 -p tcp --dport 1255 -m recent --name OPEN2 --set -j DROP
sudo iptables -A STEP2 -j STEP1

# step3: strip second check flag & set third flag if matched.
#      send back to first chain to die or be tagged with flag1
sudo iptables -A STEP3 -m recent --name OPEN2 --remove
sudo iptables -A STEP3 -p tcp --dport 1355 -m recent --name OPEN3 --set -j DROP
sudo iptables -A STEP3 -j STEP1

# Configure PASSED chain
sudo iptables -A PASSED -m recent --name OPEN3 --remove
sudo iptables -A PASSED -p tcp --dport 2222 -j ACCEPT
sudo iptables -A PASSED -j STEP1

# Configure SSHACCESS chain
sudo iptables -A SSHACCESS -m recent --rcheck --seconds 30 --name OPEN3 -j PASSED
sudo iptables -A SSHACCESS -m recent --rcheck --seconds 10 --name OPEN2 -j STEP3
sudo iptables -A SSHACCESS -m recent --rcheck --seconds 10 --name OPEN1 -j STEP2
sudo iptables -A SSHACCESS -j STEP1

```

---

