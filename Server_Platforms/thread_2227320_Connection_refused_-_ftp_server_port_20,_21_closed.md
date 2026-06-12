---
title: "Connection refused - ftp server port 20, 21 closed"
date: 2014-06-01
forum: Server Platforms
---

### Post by dagring on 2014-06-01
I have tried numerous things to get my ftp server working. I seems the port 20,21 is closed. My output of iptables -L shows:

$sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:21

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp spt:20

It seems right for me, but it isn't. Something is blocking the ports. Can anybody give me a hint?

Dag R

---

### Post by Hugo_Serrano on 2014-06-01
Hi!

Can you see those ports if you do:
```
netstat -tlpn
```

Cheers,
Hugo.

---

### Post by dagring on 2014-06-01
No I cannot see them. I see http port, ssh port etc, but not port 20,21

Dag R

---

### Post by Hugo_Serrano on 2014-06-01
My guess is that the service is not running. 
Can you see it on process list? 
```
ps -aux | grep -i ftp
```

---

### Post by delanov on 2014-07-17
> **Hugo_Serrano said:**
> My guess is that the service is not running. 
Can you see it on process list? 
```
ps -aux | grep -i ftp
```

I'm attempting to ftp to another computer within my home.  From MINT 11 >> vsftpd will ftp to UBUNTU 14.04.   However, UBUNTU 14.04 >> vsftp does not ftp to MINT 11.  

I run the following four codes on UBUNTU.  I need help deciphering the results, and would appreciate all input.


(1) **root@ddval-p6653w:~# nmap -Pn 192.168.x.xxx**

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2014-07-17 19:01 PDT
Nmap scan report for 192.168.x.xxx
Host is up (0.0035s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
Nmap done: 1 IP address (1 host up) scanned in 5.55 seconds

(2) **ddval@ddval-p6653w:~$ sudo iptables -L -n**
[sudo] password for ddval: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


(3) **ddval@ddval-p6653w:~$ netstat -tlpn**

root@ddval-p6653w:~# netstat -tlpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1125/dnsmasq    
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      876/vsftpd      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      873/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1668/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      574/smbd        
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      574/smbd        
tcp6       0      0 :::22                   :::*                    LISTEN      873/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1668/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      574/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      574/smbd  


(4) **root@ddval-p6653w:~# ps -aux | grep -i ftp**

root       876  0.0  0.0   4780   952 ?        Ss   18:19   0:00 /usr/sbin/vsftpd
root      2687  0.0  0.0   4684   808 pts/0    R+   18:45   0:00 grep --color=auto -i ftp

---

