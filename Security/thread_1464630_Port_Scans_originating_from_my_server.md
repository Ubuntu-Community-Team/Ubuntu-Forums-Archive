---
title: "Port Scans originating from my server"
date: 2010-04-28
forum: Security
---

### Post by studiogrynn on 2010-04-28
Firewall is showing these UDP fragments from and to random ports between my server and a fixed destination IP. These appear to be starting at some point during the night. When I arrive in the a.m. a couple hundred perl processes are running under the parent PID 1 (init)

A restart of the machine stops the offending process for a day or so.

There are thousands of these log entries in the firewall from this morning:


2010-04-28 08:52:40	crit	Fragmented traffic! From xxx.xxx.xxx.xxx:32864 to 188.40.157.54:4606, proto UDP (zone Trust, int trust). Occurred 1 times.
2010-04-28 08:52:40	crit	Fragmented traffic! From xxx.xxx.xxx.xxx:32864 to 188.40.157.54:4605, proto UDP (zone Trust, int trust). Occurred 1 times.
2010-04-28 08:52:40	crit	Fragmented traffic! From xxx.xxx.xxx.xxx:60864 to 188.40.157.54:3656, proto UDP (zone Trust, int trust). Occurred 1 times.
2010-04-28 08:52:40	crit	Fragmented traffic! From xxx.xxx.xxx.xxx:60864 to 188.40.157.54:3655, proto UDP (zone Trust, int trust). Occurred 1 times.
2010-04-28 08:52:40	crit	Fragmented traffic! From xxx.xxx.xxx.xxx:32864 to 188.40.157.54:4604, proto UDP (zone Trust, int trust). Occurred 1 times.


Thoughts? Suggestions? Should I just shoot myself?

---

### Post by iponeverything on 2010-04-28
Probably nothing to worry about.

> a couple hundred perl processes are running

what's the output of:

```
sudo ps uaxwwww|grep perl|tail -20
```

and 

```
sudo lsof -p <perl-pid>
```

where <perl-pid> is the pid of one of the perl processes.

---

### Post by studiogrynn on 2010-04-28
Right now, the machine is behaving and sudo netstat -ntulp shows no outbound activity for this machine, nor does the firewall. 

However, here are the present results

sudo ps uaxwwww|grep perl|tail -20
root      1944  0.0  0.3  12952  1276 ?        Ss   09:39   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
1000      3644  0.0  0.2   3040   796 pts/3    S+   11:45   0:00 grep perl


sudo lsof -p 1944:
COMMAND    PID USER   FD   TYPE     DEVICE SIZE/OFF   NODE NAME
miniserv. 1944 root  cwd    DIR        8,1    12288 983207 /usr/share/webmin
miniserv. 1944 root  rtd    DIR        8,1     4096      2 /
miniserv. 1944 root  txt    REG        8,1  1306332 802845 /usr/bin/perl
miniserv. 1944 root  mem    REG        8,1  1319364 825794 /lib/tls/i686/cmov/libc-2.10.1.so
miniserv. 1944 root  mem    REG        8,1    22056 802883 /usr/lib/perl/5.10.0/auto/Socket/Socket.so
miniserv. 1944 root  mem    REG        8,1   108596 802880 /usr/lib/perl/5.10.0/auto/POSIX/POSIX.so
miniserv. 1944 root  mem    REG        8,1  1315612 828719 /lib/i686/cmov/libcrypto.so.0.9.8
miniserv. 1944 root  mem    REG        8,1    83608 825926 /lib/libz.so.1.2.3.3
miniserv. 1944 root  mem    REG        8,1    38344 959672 /usr/lib/perl5/auto/Authen/PAM/PAM.so
miniserv. 1944 root  mem    REG        8,1    17924 802878 /usr/lib/perl/5.10.0/auto/IO/IO.so
miniserv. 1944 root  mem    REG        8,1    34420 818923 /usr/lib/perl/5.10.0/auto/SDBM_File/SDBM_File.so
miniserv. 1944 root  mem    REG        8,1    30684 825810 /lib/tls/i686/cmov/librt-2.10.1.so
miniserv. 1944 root  mem    REG        8,1    26400 825801 /lib/tls/i686/cmov/libnss_compat-2.10.1.so
miniserv. 1944 root  mem    REG        8,1   113320 825847 /lib/ld-2.10.1.so
miniserv. 1944 root  mem    REG        8,1     9748 825830 /lib/tls/i686/cmov/libutil-2.10.1.so
miniserv. 1944 root  mem    REG        8,1    38504 825805 /lib/tls/i686/cmov/libnss_nis-2.10.1.so
miniserv. 1944 root  mem    REG        8,1   149392 825798 /lib/tls/i686/cmov/libm-2.10.1.so
miniserv. 1944 root  mem    REG        8,1    13796 802875 /usr/lib/perl/5.10.0/auto/Fcntl/Fcntl.so
miniserv. 1944 root  mem    REG        8,1   116920 825808 /lib/tls/i686/cmov/libpthread-2.10.1.so
miniserv. 1944 root  mem    REG        8,1   362912 983099 /usr/lib/perl5/auto/Net/SSLeay/SSLeay.so
miniserv. 1944 root  mem    REG        8,1     9736 825797 /lib/tls/i686/cmov/libdl-2.10.1.so
miniserv. 1944 root  mem    REG        8,1    22024 818958 /usr/lib/perl/5.10.0/auto/Sys/Syslog/Syslog.so
miniserv. 1944 root  mem    REG        8,1   282112 828720 /lib/i686/cmov/libssl.so.0.9.8
miniserv. 1944 root  mem    REG        8,1    46736 825841 /lib/libpam.so.0.82.1
miniserv. 1944 root  mem    REG        8,1    42444 983081 /usr/lib/perl5/auto/IO/Tty/Tty.so
miniserv. 1944 root  mem    REG        8,1    38360 825796 /lib/tls/i686/cmov/libcrypt-2.10.1.so
miniserv. 1944 root  mem    REG        8,1    17840 818847 /usr/lib/perl/5.10.0/auto/Digest/MD5/MD5.so
miniserv. 1944 root  mem    REG        8,1    79676 825800 /lib/tls/i686/cmov/libnsl-2.10.1.so
miniserv. 1944 root  mem    REG        8,1    42572 825803 /lib/tls/i686/cmov/libnss_files-2.10.1.so
miniserv. 1944 root    0r   CHR        1,3      0t0   1204 /dev/null
miniserv. 1944 root    1w   CHR        1,3      0t0   1204 /dev/null
miniserv. 1944 root    2w   REG        8,1     4598 206035 /var/webmin/miniserv.error
miniserv. 1944 root    3u  unix 0xd6802b40      0t0   7600 socket
miniserv. 1944 root    4w   CHR        1,3      0t0   1204 /dev/null
miniserv. 1944 root    5u  IPv4       7601      0t0    TCP *:webmin (LISTEN)
miniserv. 1944 root    6u  IPv4       7602      0t0    UDP *:10000 
miniserv. 1944 root    7u   REG        8,1     1024 206037 /var/webmin/sessiondb.pag
miniserv. 1944 root    8u   REG        8,1        0 206038 /var/webmin/sessiondb.dir

---

### Post by cdenley on 2010-04-28
Very suspicious. That IP appears to belong to a CentOS server running apache, ssh, and an IRC server. I'm guessing your system is being used to attack another server. Anything suspicious in /var/log/auth.log. Is webmin protected with a really strong password? Are you running an ssh server? Did you set a root password?

---

### Post by studiogrynn on 2010-04-28
> **cdenley said:**
> Very suspicious. That IP appears to belong to a CentOS server running apache, ssh, and an IRC server. I'm guessing your system is being used to attack another server. Anything suspicious in /var/log/auth.log. Is webmin protected with a really strong password? Are you running an ssh server? Did you set a root password?


My auth.log only goes back to April 26.
```
These lines show up during reboots on a couple of recent days:
Apr 27 07:35:05 xxxxxxxxx sudo:     root : TTY=unknown ; PWD=/ ; USER=xxxxxxxx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Apr 27 07:35:06 xxxxxxxxx sudo:     root : TTY=unknown ; PWD=/ ; USER=xxxxxxxxx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Apr 27 07:35:06 xxxxxxxxx sudo:     root : TTY=unknown ; PWD=/ ; USER=xxxxxxxxx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
```

And these from earlier dates:
```
Apr 14 06:48:50 xxxxxxxx sshd[20444]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:48:50 xxxxxxxx sshd[20444]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:48:52 xxxxxxxx sshd[20444]: Failed password for invalid user ubuntu from 82.76.12.197 port 42950 ssh2
Apr 14 06:48:54 xxxxxxxx sshd[20446]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:48:54 xxxxxxxx sshd[20446]: Invalid user ts from 82.76.12.197
Apr 14 06:48:54 xxxxxxxx sshd[20446]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:48:54 xxxxxxxx sshd[20446]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:48:56 xxxxxxxx sshd[20446]: Failed password for invalid user ts from 82.76.12.197 port 43080 ssh2
Apr 14 06:48:57 xxxxxxxx sshd[20448]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:48:57 xxxxxxxx sshd[20448]: Invalid user www from 82.76.12.197
Apr 14 06:48:57 xxxxxxxx sshd[20448]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:48:57 xxxxxxxx sshd[20448]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:48:59 xxxxxxxx sshd[20448]: Failed password for invalid user www from 82.76.12.197 port 43189 ssh2
Apr 14 06:49:00 xxxxxxxx sshd[20450]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:00 xxxxxxxx sshd[20450]: Invalid user walter from 82.76.12.197
Apr 14 06:49:00 xxxxxxxx sshd[20450]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:00 xxxxxxxx sshd[20450]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:02 xxxxxxxx sshd[20450]: Failed password for invalid user walter from 82.76.12.197 port 43289 ssh2
Apr 14 06:49:04 xxxxxxxx sshd[20455]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:04 xxxxxxxx sshd[20455]: Invalid user gold from 82.76.12.197
Apr 14 06:49:04 xxxxxxxx sshd[20455]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:04 xxxxxxxx sshd[20455]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:05 xxxxxxxx sshd[20455]: Failed password for invalid user gold from 82.76.12.197 port 43380 ssh2
Apr 14 06:49:07 xxxxxxxx sshd[20457]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:07 xxxxxxxx sshd[20457]: Invalid user connie from 82.76.12.197
Apr 14 06:49:07 xxxxxxxx sshd[20457]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:07 xxxxxxxx sshd[20457]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:09 xxxxxxxx sshd[20457]: Failed password for invalid user connie from 82.76.12.197 port 53024 ssh2
Apr 14 06:49:11 xxxxxxxx sshd[20460]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:11 xxxxxxxx sshd[20460]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197  user=mail
Apr 14 06:49:12 xxxxxxxx sshd[20460]: Failed password for mail from 82.76.12.197 port 53138 ssh2
Apr 14 06:49:14 xxxxxxxx sshd[20462]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:14 xxxxxxxx sshd[20462]: Invalid user luke from 82.76.12.197
Apr 14 06:49:14 xxxxxxxx sshd[20462]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:14 xxxxxxxx sshd[20462]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:16 xxxxxxxx sshd[20462]: Failed password for invalid user luke from 82.76.12.197 port 53238 ssh2
Apr 14 06:49:18 xxxxxxxx sshd[20464]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:18 xxxxxxxx sshd[20464]: Invalid user lea from 82.76.12.197
Apr 14 06:49:18 xxxxxxxx sshd[20464]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:18 xxxxxxxx sshd[20464]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:20 xxxxxxxx sshd[20464]: Failed password for invalid user lea from 82.76.12.197 port 53363 ssh2
Apr 14 06:49:21 xxxxxxxx sshd[20466]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:21 xxxxxxxx sshd[20466]: Invalid user simon from 82.76.12.197
Apr 14 06:49:21 xxxxxxxx sshd[20466]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:21 xxxxxxxx sshd[20466]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:24 xxxxxxxx sshd[20466]: Failed password for invalid user simon from 82.76.12.197 port 53472 ssh2
Apr 14 06:49:25 xxxxxxxx sshd[20468]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:25 xxxxxxxx sshd[20468]: Invalid user samuel from 82.76.12.197
Apr 14 06:49:25 xxxxxxxx sshd[20468]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:25 xxxxxxxx sshd[20468]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:28 xxxxxxxx sshd[20468]: Failed password for invalid user samuel from 82.76.12.197 port 53597 ssh2
Apr 14 06:49:29 xxxxxxxx sshd[20470]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:29 xxxxxxxx sshd[20470]: Invalid user matteo from 82.76.12.197
Apr 14 06:49:29 xxxxxxxx sshd[20470]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:29 xxxxxxxx sshd[20470]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:31 xxxxxxxx sshd[20470]: Failed password for invalid user matteo from 82.76.12.197 port 53723 ssh2
Apr 14 06:49:32 xxxxxxxx sshd[20472]: reverse mapping checking getaddrinfo for 82-76-12-197.rdsnet.ro [82.76.12.197] failed - POSSIBLE BREAK-IN ATTEMPT!
Apr 14 06:49:32 xxxxxxxx sshd[20472]: Invalid user mac from 82.76.12.197
Apr 14 06:49:32 xxxxxxxx sshd[20472]: pam_unix(sshd:auth): check pass; user unknown
Apr 14 06:49:32 xxxxxxxx sshd[20472]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=82.76.12.197 
Apr 14 06:49:34 xxxxxxxx sshd[20472]: Failed password for invalid user mac from 82.76.12.197 port 53810 ssh2
```

```
Apr 15 04:37:13 xxxxxxxx sshd[5267]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=98-129-220-166.static.cloud-ips.com  user=root
Apr 15 04:37:16 xxxxxxxx sshd[5267]: Failed password for root from 98.129.220.166 port 41668 ssh2
Apr 15 18:01:26 xxxxxxxx sshd[21299]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=210.17.251.159  user=root
Apr 15 18:01:27 xxxxxxxx sshd[21299]: Failed password for root from 210.17.251.159 port 60685 ssh2
```


Tons of these attempts on ssh. I have recently installed daemonshield to auto block IP's on these attacks. 




The webmin password uses symbols, upper and lower case alpha and numerics and is over 8 char long.

ssh is on but using a non default port. 

As for the root password, It is my understanding (via these forums) that setting the root password is not needed in Ubuntu. -Is this wrong?

---

### Post by cdenley on 2010-04-28
Setting a root password is discouraged, which is why I asked. As you noticed, someone was trying to authenticate as root, but without a password set, that obviously failed. Those gconftool sudo sessions are a scheduled task for update manager. As you can see, using a non-default port for ssh does not eliminate attacks. I don't see any successful authentications, though.
```

sudo netstat -tlnp

```

---

### Post by studiogrynn on 2010-04-28
> **cdenley said:**
> 
```

sudo netstat -tlnp

```

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 xxx.xxx.xxx.xxx:443         0.0.0.0:*               LISTEN      1845/apache2    
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1621/smbd       
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      1660/dovecot    
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      1660/dovecot    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1250/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1621/smbd       
tcp        0      0 127.0.0.1:9101          0.0.0.0:*               LISTEN      1883/bacula-dir 
tcp        0      0 0.0.0.0:9102            0.0.0.0:*               LISTEN      1863/bacula-fd  
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      1660/dovecot    
tcp        0      0 0.0.0.0:9103            0.0.0.0:*               LISTEN      1812/bacula-sd  
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      1660/dovecot    
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1944/perl       
tcp        0      0 xxx.xxx.xxx.xxx:80          0.0.0.0:*               LISTEN      1845/apache2    
tcp        0      0 0.0.0.0:2288            0.0.0.0:*               LISTEN      1091/sshd       
tcp        0      0 xxx.xxx.xxx.xxx:82          0.0.0.0:*               LISTEN      1845/apache2    
tcp        0      0 xxx.xxx.xxx.xxx:53        0.0.0.0:*               LISTEN      1774/dnsmasq    
tcp        0      0 xxx.xxx.xxx.xxx:53          0.0.0.0:*               LISTEN      1021/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1021/named      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1738/cupsd      
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      1362/postgres   
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1581/master     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1021/named      
tcp6       0      0 :::xx                   :::*                    LISTEN      1091/sshd       
tcp6       0      0 :::53                   :::*                    LISTEN      1021/named      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1738/cupsd      
tcp6       0      0 ::1:5432                :::*                    LISTEN      1362/postgres   
tcp6       0      0 ::1:953                 :::*                    LISTEN      1021/named  
```

---

### Post by CharlesA on 2010-04-28
I usually set up keys for SSH instead of passwords. It's a bit more secure and as far as I know, impossible to bruteforce (as long as you have a strong passphrase). Especually since the attacker would need your private key.

Might want to monitor the server for a bit, but if you wanted to be 100% sure that it isn't compromised, do a reinstall.

EDIT: Is apache and mysql secured?

---

### Post by studiogrynn on 2010-04-28
> EDIT: Is apache and mysql secured?

Since I'm not qualified to answer that difinitivly, I'll poke around the threads, see what is recommended and let you know what is in place.

---

### Post by CharlesA on 2010-04-28
Heh I am in the same boat (I don't know how to secure those two), but since I don't run apache or mysql, that's not a problem for me.

---

### Post by rookcifer on 2010-04-28
Pardon me if I missed it above, but what sort of server do you run (i.e. what services do you have opening and listening)?

Upon cursory observation, it does look suspicious.

---

### Post by iponeverything on 2010-04-29
Just from available information (still not very much) I would say that there is pretty good chance that you are compromised. 

That said, if you are, you probably have root-kit on the box which would make most of this poking around mute. Though the fact that, the log of the brute force on ssh still being there, does give some hope. When you decide to reinstall, do not recycle any of your passwords from mysql, user accounts or other services.

---

### Post by OpSecShellshock on 2010-04-29
It would also be a good idea to stop using Webmin altogether.

---

### Post by CharlesA on 2010-04-29
> **OpSecShellshock said:**
> It would also be a good idea to stop using Webmin altogether.
Why is that?

---

### Post by studiogrynn on 2010-04-29
The good news is the firewall was quiet this morning. No sign of port sniffing coming from the server. Of course this can only be taken lightly, but it does help with the analysis. The issue with too many perl processes is still alive. I came in this morning to find about 550 processes active and the gui locked up. I had top running. In hindsight, I should have had netstat running continuous as well. I'll set that up tonight.

Also good news, or bad depending on how you want to look at it:
chkrootkit found this:
```
Checking `lkm'...                                           
You have     3 process hidden for readdir command
You have     3 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

```
I also ran it twice as :> sudo chkrootkit lkm
ROOTDIR is `/'
Checking `lkm'...
You have     2 process hidden for readdir command
You have     2 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
chkdirs: nothing detected

Any thoughts on further confirmation of this as a positive detection?


> **OpSecShellshock said:**
> It would also be a good idea to stop using Webmin altogether.

I removed Webmin yesterday as I no longer need it anyhow. Might as well reduce the attack surfaces. 

> Pardon me if I missed it above, but what sort of server do you run (i.e. what services do you have opening and listening)?
At present,
Postfix: 25 110 143 993 995
Apache: 80 82 443 
Microsoft-ds: 445
domain 53
bacula 9102 9103

> That said, if you are, you probably have root-kit on the box which would make most of this poking around mute. Though the fact that, the log of the brute force on ssh still being there, does give some hope. When you decide to reinstall, do not recycle any of your passwords from mysql, user accounts or other services.

I have shut down ssh altogether for now. I have console access to the machine and don't really need it when I am onsite. I can setup for certs if I need it down the road. An auto ban app has also been installed for the occasional dictionary attack.

Installed  tiger, john, chkrootkit per bodhi.zazen's advice in this post:[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).
The system only failed on a handful of points. One of which allowed source of packets through the host. This hole has been closed as of this morning.

---

