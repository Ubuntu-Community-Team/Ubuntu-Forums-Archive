---
title: "Open ports on 10.04 Apache Server"
date: 2011-03-15
forum: Server Platforms
---

### Post by dyous87 on 2011-03-15
I have a new Ubuntu 10.04 server I set up. It is running Apache2, SSH, and MYSQL. When I run an nmap on it from an outside IP address this is what returns:

```
Host is up (0.038s latency).
Not shown: 994 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
554/tcp  open     rtsp
3306/tcp open     mysql
7070/tcp open     realserver

```I know I need 22, 80, and 3306 open. My question is do I necesarily need port 25 open if I'm not going to use this as a mail server. I will be using the php mail function in certain scripts but does port 25 need to be open for that.

Also do any of you know why I would have port 554 and port 7070 open?

Thanks in advance.

David

---

### Post by CharlesA on 2011-03-15
It says "filtered" which means the port is closed.

You can check the list of open ports by running this:

```
netstat -l
```

---

### Post by dyous87 on 2011-03-15
Thanks so filtered is closed. Do you have any idea about those other two:

```

554/tcp  open     rtsp
7070/tcp open     realserver

```

Thanks!
David

---

### Post by wongo888 on 2011-03-15
Try the command CharlesA gave you. You can also try:

```
$ sudo lsof -i
```

---

### Post by dyous87 on 2011-03-15
netstat -l gives me this:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:mysql                 *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     1119     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     3201     /var/run/mysqld/mysqld.sock

```

so that means my server is only listening on the mysql, http and ssh ports. When then did it give me those other ports as open when I did an nmap from a foreign machine?

---

### Post by wongo888 on 2011-03-15
This variation will give you more info on the PID, etc:

```
$ netstat -anp
```

---

### Post by dyous87 on 2011-03-15
netstat -anp returns:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      2333/mysqld     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      3081/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2504/sshd       
tcp        0      0 50.56.93.165:22         108.27.75.131:38919     ESTABLISHED 7363/sshd: betterbi
tcp        0      0 50.56.93.165:22         108.27.75.131:36851     ESTABLISHED 7191/sshd: betterbi
tcp        0      0 50.56.93.165:22         108.27.75.131:45775     ESTABLISHED 7253/0          
tcp        0     84 50.56.93.165:22         108.27.75.131:50947     ESTABLISHED 7364/sshd: betterbi
tcp6       0      0 :::22                   :::*                    LISTEN      2504/sshd       
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  7      [ ]         DGRAM                    3088     2289/rsyslogd       /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     1119     1/init              @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    2759     2108/udevd          @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     3201     2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     59044    7364/sshd: betterbi 
unix  3      [ ]         STREAM     CONNECTED     59043    7388/sshd: betterbi 
unix  2      [ ]         DGRAM                    59037    7364/sshd: betterbi 
unix  3      [ ]         STREAM     CONNECTED     59020    7363/sshd: betterbi 
unix  3      [ ]         STREAM     CONNECTED     59019    7376/sshd: betterbi 
unix  2      [ ]         DGRAM                    59013    7363/sshd: betterbi 
unix  3      [ ]         STREAM     CONNECTED     58964    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58963    7360/apache2        
unix  3      [ ]         STREAM     CONNECTED     58823    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58822    6297/apache2        
unix  3      [ ]         STREAM     CONNECTED     58773    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58772    6298/apache2        
unix  3      [ ]         STREAM     CONNECTED     58770    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58769    7233/apache2        
unix  3      [ ]         STREAM     CONNECTED     58767    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58766    7279/apache2        
unix  3      [ ]         STREAM     CONNECTED     58681    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58680    7283/apache2        
unix  3      [ ]         STREAM     CONNECTED     58669    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58668    7232/apache2        
unix  3      [ ]         STREAM     CONNECTED     58663    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58662    6339/apache2        
unix  3      [ ]         STREAM     CONNECTED     58660    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58659    6296/apache2        
unix  3      [ ]         STREAM     CONNECTED     58657    2333/mysqld         /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     58656    7281/apache2        
unix  2      [ ]         DGRAM                    47849    7253/0              
unix  3      [ ]         STREAM     CONNECTED     41082    7191/sshd: betterbi 
unix  3      [ ]         STREAM     CONNECTED     41081    7202/sshd: betterbi 
unix  2      [ ]         DGRAM                    41075    7191/sshd: betterbi 
unix  2      [ ]         DGRAM                    3298     1/init              
unix  3      [ ]         DGRAM                    2762     2108/udevd          
unix  3      [ ]         DGRAM                    2761     2108/udevd          
unix  3      [ ]         STREAM     CONNECTED     2753     1/init              @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     2750     2046/upstart-udev-b 

```

---

### Post by CharlesA on 2011-03-15
I don't know where those other two came from. It doesn't look like anything is listening on those ports.

---

### Post by wongo888 on 2011-03-15
Are you running an Airport?

[http://blog.nephtaliproject.com/?p=129](http://blog.nephtaliproject.com/?p=129)

---

### Post by SeijiSensei on 2011-03-15
Is there a reason why MySQL needs to listen on a public interface?  If you're using it to support web applications, it should only be listening on the localhost (127.0.0.1) interface.  If you need to connect to MySQL over the Internet, then I'd make sure you have a iptables rules that limits access to port 3306 to specific IP addresses like this:

```

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p tcp -s 10.10.10.10 --dport 3306 -j ACCEPT
iptables -A INPUT -p tcp -s 10.10.10.11 --dport 3306 -j ACCEPT
iptables -A INPUT -p tcp --dport 3306 -j REJECT

```

The first rule grants all rights to the localhost interface, the next two grant access to specific IP addresses, and the last denies access from anywhere else.

(I don't use MySQL often, and a quick Google search doesn't bring up any native method to limit access by IP.  In PostgreSQL, which is my preferred database, you can control access in the "pg_hba.conf" file using a variety of methods including IP address.)

---

