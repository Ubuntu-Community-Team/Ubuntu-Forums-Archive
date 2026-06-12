---
title: "Mounting NFS problem"
date: 2009-09-22
forum: Server Platforms
---

### Post by ene_dene on 2009-09-22
We already had this topic, but for some reason I can't post there, so here's a new one.

Server: (ubuntu server 9.04): 192.168.0.21
Client: (debian lenny 5.0): 192.168.0.20

I installed nfs server on the server:
```
sudo aptitude install nfs-kernel-server nfs-common portmap
```
I installed nfs client on the client:
```
sudo aptitude install nfs-common portmap
```

The directory that I want to share from server is: /media/nfsshare
The directory that I want to mount in on the client is: /media/nfsdisk

I edited on the /etc/exports file on a server and added the line:
```
/media/nfsshare 192.168.0.20(rw,sync,no_subtree_check)
```

After that I did on a server:
```
exportfs -ra
```

I restarted the services, I even restarted the computer.

Now on the client I created directory /media/nfsdisk and tried to mount as a root the directory from server:
```
mount 192.168.0.21:/media/nfsshare /media/nfsdisk
```
which results in a:
```
mount.nfs: mount to NFS server '192.168.0.21' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.21' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.21' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.21' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.21' failed: timed out, giving up
```

I also opened the ports 111, 2049, 32771 on a server. The same thing happens. Every other service works fine, for example without any trouble I can connect from one computer to another via ssh.

What am I doing wrong?

---

### Post by gombadi on 2009-09-22
> 
I also opened the ports 111, 2049, 32771 on a server


What do you mean by opened? Did you have a firewall?

Some systems have portmap listening on 127.0.0.1 only so you can not connect from a remote system.

Have a look at the output of this command to see if portmap is listening on all interfaces -
```

sudo netstat -plntu

```

---

### Post by sahabcse on 2009-09-22
paste the o/p of 

sudo iptables -L

---

### Post by ene_dene on 2009-09-22
> **gombadi said:**
> What do you mean by opened? Did you have a firewall?

Some systems have portmap listening on 127.0.0.1 only so you can not connect from a remote system.

Have a look at the output of this command to see if portmap is listening on all interfaces -
```

sudo netstat -plntu

```
Yes, I have a firewall ufw. Opened in a sense as you need to open port 22 to login via ssh. I've seen on various forums which ports need to be open for nfs to work, so just for testing, I opened all which are mentioned. Here is the output:
```
 sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:58916           0.0.0.0:*               LISTEN      2185/rpc.statd  
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      2168/portmap    
tcp        0      0 0.0.0.0:42225           0.0.0.0:*               LISTEN      2619/rpc.mountd 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2558/sshd       
tcp        0      0 0.0.0.0:33471           0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      2558/sshd       
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:52627           0.0.0.0:*                           2185/rpc.statd  
udp        0      0 0.0.0.0:665             0.0.0.0:*                           2185/rpc.statd  
udp        0      0 0.0.0.0:36393           0.0.0.0:*                           2619/rpc.mountd 
udp        0      0 0.0.0.0:53690           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:111             0.0.0.0:*                           2168/portmap
```


[QUOTE=sahabcse]paste the o/p of

sudo iptables -L [/QUOTE]
```
sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:sunrpc 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:sunrpc 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nfs 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:nfs 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:32771 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:32771 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination   
```

---

### Post by ene_dene on 2009-09-23
So, where seems to be the problem?

---

### Post by ene_dene on 2009-09-23
I've solved the problem.
```
rpcinfo -p
```
Gives the list of ports of which some need to be open:
```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  47838  nlockmgr
    100021    3   udp  47838  nlockmgr
    100021    4   udp  47838  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  55480  nlockmgr
    100021    3   tcp  55480  nlockmgr
    100021    4   tcp  55480  nlockmgr
    100005    1   udp  48131  mountd
    100005    1   tcp  34259  mountd
    100005    2   udp  48131  mountd
    100005    2   tcp  34259  mountd
    100005    3   udp  48131  mountd
    100005    3   tcp  34259  mountd
    100000    2   udp    111  portmapper
    100024    1   udp  50271  status
    100024    1   tcp  35718  status

```
I think that opening the mountd port did the trick. I've tested this on few virtual machines and it seems that this mountd port is randomly set. I'm not sure why I haven't found in any manuals need to open ports, as you would see in ftp manual that 21 port needs to be open, or for http 80.
I hope that this will help someone in the future while struggling the same problem.

---

### Post by powerofpi on 2010-05-10
> **ene_dene said:**
> 
I hope that this will help someone in the future while struggling the same problem.

Rest assured, you helped at least one person. Thank you!

---

### Post by arrrghhh on 2010-05-10
[[SOLVED]](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)??

---

