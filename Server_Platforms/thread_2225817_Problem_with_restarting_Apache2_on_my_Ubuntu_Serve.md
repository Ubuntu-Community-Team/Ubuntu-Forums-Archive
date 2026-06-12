---
title: "Problem with restarting Apache2 on my Ubuntu Server 14.04"
date: 2014-05-23
forum: Server Platforms
---

### Post by dusan3 on 2014-05-23
Hi everybody.
I have a problem when i'm trying to restart Apache2 on my Ubuntu Server 14.04. I'm getting this error:


 * Restarting web server apache2                                                            [Fri May 23 18:50:56.662042 2014] [alias:warn] [pid 8635] AH00671: The Alias directive in /etc/apache2/conf-enabled/phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.
(98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
AH00015: Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                                     [fail]
 * The apache2 instance did not start within 20 seconds. Please read the log files to discover problems


Can somebody help me to fix this error?


Thanks in advance.

---

### Post by slickymaster on 2014-05-23
Moved to the **Server Platforms** sub-forum.

---

### Post by SeijiSensei on 2014-05-23
Did you use "sudo service apache2 restart" or just "start"?  You need to use "restart" in these situations.

---

### Post by dusan3 on 2014-05-23
i have used sudo /etc/init.d/apache2 restart command for this and i got this error ...

---

### Post by Doug S on 2014-05-23
Post the output of "sudo netstat -lnpt". Example:```
doug@s15:~/temp$ [COLOR=#ff0000]sudo netstat -lnpt[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      2267/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2813/apache2
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      881/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1659/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      881/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2813/apache2
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      2211/dnsmasq
tcp        0      0 10.0.3.1:53             0.0.0.0:*               LISTEN      1864/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1507/sshd
```

---

### Post by dusan3 on 2014-05-23
This is the output of sudo netstat -lnpt

root@testseek:/# sudo netstat -lnpt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4631/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      755/sshd
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      671/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      755/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      755/sshd
tcp6       0      0 :::22                   :::*                    LISTEN      755/sshd

---

### Post by Doug S on 2014-05-23
You need to change the secure shell server so that it does not use ports 80 (IPV6) and 80 (IPV4). The apache web server can not start because sshd is using the ports.

---

### Post by dusan3 on 2014-05-23
Can you show me how to do that? I'm new in Linux.

Thanks.

---

### Post by Doug S on 2014-05-23
Ugh, how did you manage to get sshd to listen to those ports in the first place? Just undo whatever was done.

There should be a file /etc/ssh/sshd_config
If that file is close to the original file at all, then there should be a line near the top, just make it right. Example:```
# Package generated configuration file
# See the sshd_config(5) manpage for details

[COLOR=#ff0000]# What ports, IPs and protocols we listen for
Port 22[/COLOR]
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
```

---

### Post by dusan3 on 2014-05-23
Thanks Doug....i just saw theres also port80 in that file so i just deleted that line and now when i restart apache i got this error:
(98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
AH00015: Unable to open logs
Action 'start' failed.



Seems like that turning port 80 didnt do job....
Dont know what to do....

---

### Post by Doug S on 2014-05-23
after editing sshd_config, did you restart the ssh server daemon? Example:```
sudo service ssh restart
```

---

### Post by dusan3 on 2014-05-23
Thanks Doug....i forgot that to do .... now its working...
Thank you once again.

---

