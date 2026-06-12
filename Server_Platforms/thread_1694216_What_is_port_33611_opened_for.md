---
title: "What is port 33611 opened for?"
date: 2011-02-24
forum: Server Platforms
---

### Post by RuralHunter on 2011-02-24
I'm with Ubuntu 10.04.2 server LTS. Just noticed there is port 33611 is opened by some unknown process and I can not figure out which process is using it.
```
root@ubuntu:~# lsof |grep 33611
root@ubuntu:~# netstat -anp |grep LISTEN
tcp        0      0 0.0.0.0:33611           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:44207           0.0.0.0:*               LISTEN      838/rpc.statd   
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      598/portmap     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      891/sshd        
tcp6       0      0 :::22                   :::*                    LISTEN      891/sshd      
```

---

### Post by An Sanct on 2011-02-24
It could be X session ssh tunneling... Just a guess tho...

---

### Post by RuralHunter on 2011-02-24
> **An Sanct said:**
> It could be X session ssh tunneling... Just a guess tho...
There is not any X session related processes running.

---

### Post by gmargo on 2011-02-24
Same thing here.  Could it be a kernel-based process?  I have two such "unowned" ports open, and one is nfs:
```

$ sudo netstat -anp | grep LISTEN | grep -- '-[[:space:]]*$'
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:35555           0.0.0.0:*               LISTEN      -               

```2049 is nfs, but what is 35555?

---

### Post by RuralHunter on 2011-02-24
> **gmargo said:**
> Same thing here.  Could it be a kernel-based process?  I have two such "unowned" ports open, and one is nfs:
```

$ sudo netstat -anp | grep LISTEN | grep -- '-[[:space:]]*$'
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:35555           0.0.0.0:*               LISTEN      -               

```2049 is nfs, but what is 35555?

interesting...I checked another server and found different ports too:
```
root@ubuntu:~# netstat -anp | grep LISTEN | grep -- '-[[:space:]]*$'
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:47623           0.0.0.0:*               LISTEN      -         
```

---

### Post by gmargo on 2011-02-26
**rpcinfo** shows what those ports are used for.  (Since I've rebooted, my new "mystery" port is 52813.)  The "nlockmgr" is part of the NFS server.
```

$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp   4000  status
    100024    1   tcp   4000  status
    100021    1   udp  45882  nlockmgr
    100021    3   udp  45882  nlockmgr
    100021    4   udp  45882  nlockmgr
[COLOR=Red]    100021    1   tcp  52813  nlockmgr
    100021    3   tcp  52813  nlockmgr
    100021    4   tcp  52813  nlockmgr[/COLOR]
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp   4002  mountd
    100005    1   tcp   4002  mountd
    100005    2   udp   4002  mountd
    100005    2   tcp   4002  mountd
    100005    3   udp   4002  mountd
    100005    3   tcp   4002  mountd

```

---

### Post by RuralHunter on 2011-02-26
> **gmargo said:**
> **rpcinfo** shows what those ports are used for.  (Since I've rebooted, my new "mystery" port is 52813.)  The "nlockmgr" is part of the NFS server.
```

$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp   4000  status
    100024    1   tcp   4000  status
    100021    1   udp  45882  nlockmgr
    100021    3   udp  45882  nlockmgr
    100021    4   udp  45882  nlockmgr
[COLOR=Red]    100021    1   tcp  52813  nlockmgr
    100021    3   tcp  52813  nlockmgr
    100021    4   tcp  52813  nlockmgr[/COLOR]
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp   4002  mountd
    100005    1   tcp   4002  mountd
    100005    2   udp   4002  mountd
    100005    2   tcp   4002  mountd
    100005    3   udp   4002  mountd
    100005    3   tcp   4002  mountd

```
great. thanks. mine is also nlockmgr

---

### Post by doas777 on 2011-02-26
glad you figured it out.
just a hint on netstat. if it shows no listening process, that means you need to run the command with sudo. 

without sudo:
```

 LogServer:~$ netstat -ntlup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State                  PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN                 -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN                 -
tcp6       0      0 :::22                   :::*                    LISTEN                 -
udp        0      0 0.0.0.0:514             0.0.0.0:*                                      -
udp6       0      0 :::514                  :::*                                           

```

with sudo:
```

LogServer:~$ sudo !!
sudo netstat -ntlup
[sudo] password for User:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Programame
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      828/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      758/sshd   
tcp6       0      0 :::22                   :::*                    LISTEN      758/sshd   
udp        0      0 0.0.0.0:514             0.0.0.0:*                           584/rsyslog
udp6       0      0 :::514                  :::*                                584/rsyslog

```

---

### Post by RuralHunter on 2011-02-27
> **doas777 said:**
> glad you figured it out.
just a hint on netstat. if it shows no listening process, that means you need to run the command with sudo. 

without sudo:
```

 LogServer:~$ netstat -ntlup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State                  PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN                 -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN                 -
tcp6       0      0 :::22                   :::*                    LISTEN                 -
udp        0      0 0.0.0.0:514             0.0.0.0:*                                      -
udp6       0      0 :::514                  :::*                                           

```with sudo:
```

LogServer:~$ sudo !!
sudo netstat -ntlup
[sudo] password for User:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Programame
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      828/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      758/sshd   
tcp6       0      0 :::22                   :::*                    LISTEN      758/sshd   
udp        0      0 0.0.0.0:514             0.0.0.0:*                           584/rsyslog
udp6       0      0 :::514                  :::*                                584/rsyslog

```
thanks but this is not the case. I've already run netstat with root.

---

