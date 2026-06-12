---
title: "ssh/ufw"
date: 2009-02-24
forum: Security
---

### Post by madis_ on 2009-02-24
alright you hackers, its either time to prove that ubuntu is highgly secure or that you are highly skilled. i've got a really challenging nut to crack here. 

i'm an experienced win user, but began recently using ubuntu more frequently. 
a month ago i decided to install ubuntu 8.10 server on one of my servers, and followed in detail most of the guidlines provided in [https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

i'm very pleased with the vast amount of documentation found on various ubuntu-related sites. its was more than enough to manually complete all necessary steps for a secure and stable server.

however, a few days ago.. my first "real" problem with ubuntu emerged. i seem to somehow have lost the access to ssh and, of course, i'm eagrly struggling to gain the back the access. i've spend several days on trying to find a solution. of course, by searching through the documentation. however, very little is found regarding this issue, and due to the security features of ubuntu, all attempts failed (to my great [windows mind] surprise). i know that the chances of getting back the access is very small by now (which only increased my admiration for ubuntu), but my hopes are that some of you still might have an ace up your sleeve, as i'm still in full controll of some parts, as there are some backdoors.

let me give you some more detailed info of the server:
- ubuntu 8.10 server
- ufw enabled
- openssh. running on port 22929
- svn. svn automatically updates itself (the server) when i commit something (from my local computer).
- mysql. also access to phpmyadmin. root mysql user. 
- apache, php. running as user www-data.
- webmin. running on port 10000. however, that port is being blocked by ufw. 
- mail configurations

by svn automatically updating itself, i can upload basically anything. thus, i can also read most of the files on the server, using web-based file managers. 

i tried to execute sudo commands through php scripts, but the password (for root) is incorrect it says. later i discovered that it asks for the password of user www-data and not of the root password. is there some way to still identify as root using php? or is this a deadlock? 
(i have two folders, outside the www folder, that i can upload files to, that are chmod 755 and chown www-data:www-data, if this could be of value)

i thought of asking the hosting company just restarting the server (resetting the ufw and to gaining access to port 10000), but: 
```
# /etc/ufw/ufw.conf

ENABLED=yes
```

so ufw is still enabled after a restart (right?).

after some further research i found that port to ssh (22929) was not blocked:
```
# /var/lib/ufw/user.rules

*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
### RULES ###

### tuple ### allow any 80 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 80 -j ACCEPT
-A ufw-user-input -p udp --dport 80 -j ACCEPT

### tuple ### allow any 22929 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 22929 -j ACCEPT
-A ufw-user-input -p udp --dport 22929 -j ACCEPT

### tuple ### allow tcp 25 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 25 -j ACCEPT

### tuple ### deny any 10000 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 10000 -j DROP
-A ufw-user-input -p udp --dport 10000 -j DROP

### tuple ### allow any 143 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 143 -j ACCEPT
-A ufw-user-input -p udp --dport 143 -j ACCEPT

### tuple ### allow any 993 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 993 -j ACCEPT
-A ufw-user-input -p udp --dport 993 -j ACCEPT

### tuple ### allow any 110 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 110 -j ACCEPT
-A ufw-user-input -p udp --dport 110 -j ACCEPT

### tuple ### allow any 995 0.0.0.0/0 any 0.0.0.0/0
-A ufw-user-input -p tcp --dport 995 -j ACCEPT
-A ufw-user-input -p udp --dport 995 -j ACCEPT

### END RULES ###
-A ufw-user-input -j RETURN
-A ufw-user-output -j RETURN
-A ufw-user-forward -j RETURN
-A ufw-user-limit -m limit --limit 3/minute -j LOG --log-prefix "[UFW LIMIT]: "
-A ufw-user-limit -j REJECT
-A ufw-user-limit-accept -j ACCEPT
COMMIT
```

nevertheless, a port scan on the server tells me that port 22929 is not open. and when i try to ssh (or sftp) on that port, nothing happens (i receive a connection timeout after a short period of time). so does this mean that the ssh is down? 
ssh(d)_config is attached.

all i need to execute ufw allow 10000 and via webmin the rest can be fixed. 

- can i access the webmin from port 80 somehow? 
- what happened with the ssh?

echo passthru("ps aux | grep ssh 2>&1");  returns the following
```

root      6638  0.0  0.1   5396  1060 ?        Ss   Feb20   0:00 /usr/sbin/sshd
www-data 30776  0.0  0.0   1844   500 ?        S    10:59   0:00 sh -c ps aux | grep ssh 2>&1
www-data 30778  0.0  0.0   2020   612 ?        S    10:59   0:00 grep ssh

```

---

### Post by madis_ on 2009-02-24
contacted the hosting company. problem solved.

the problem was not on the server.. the hosting company firewalled all not-so-common ports. 

well, now i can sleep well knowing that the server is secure :)

---

