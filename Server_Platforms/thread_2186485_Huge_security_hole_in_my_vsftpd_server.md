---
title: "Huge security hole in my vsftpd server"
date: 2013-11-07
forum: Server Platforms
---

### Post by snitz2 on 2013-11-07
I have a VPS hosted with Digital Ocean. I installed my Ubuntu 12.01 x32 server with apache2, mysql, phpmyadmin and vsftpd.

I followed this article in setting up the vsftpd server: [https://digitalocean.com/community/articles/how-to-set-up-vsftpd-on-ubuntu-12-04](https://digitalocean.com/community/articles/how-to-set-up-vsftpd-on-ubuntu-12-04)

I wanted to grant access to "var/www" only for "root" so I did this instead:
> [COLOR=#333333][FONT=Monaco]chown root:root /var/www[/FONT][/COLOR]

Now whenever I try to connect to my site via ftp. I get to "/home/root/" which is empty. But if I change the address in the address bar to "var/www/" I can access my files. I can practically access all system folders through the ftp.

I need to stop that please.
I only need access to /var/www for "root"
I have created a new username and gave it root access if that can help.

---

### Post by Lars Noodén on 2013-11-07
If I understand the guide correctly, the login is chrooted. So you won't be able to leave /var/www and all your files will end up there no matter what. 

But ... did you read the big red letters at the top of the guide?  I'd recommend to [stop using FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and use SFTP instead.  That would mean uninstalling vsftpd and changing your passwords.  If you have SSH access to the web site, you probably already have SFTP access.  You can try via your file manager by pressing ctrl-l and entering the uri for your web site:

```

sftp://xx.yy.zz.aa/var/www/

```

Or you can do it in the terminal almost the same way:

```

sftp  snitz2@xx.yy.zz.aa:/var/www/

```

About access to /var/www, if you are the only user, you can chown /var/www to your username.  That will give you write permissions.  If you share with others, you will have to use group permissions instead.

---

### Post by snitz2 on 2013-11-07
Thank you. I was able to access /var/www via sFTP but I can't uninstall vsftpd.

I tried apt-get purge/remove vsftpd but I can still connect fine via FileZilla.
I also can't stop service and it looks like it is running.

> root@maghnatis:~# service vsftpd stop
vsftpd: unrecognized service
root@maghnatis:~# ps -ef | grep vsftpd
root      8735  8449  0 20:13 pts/3    00:00:00 grep --color=auto vsftpd


---

### Post by Lars Noodén on 2013-11-07
Have you tried shutting down vsftpd first?

```

sudo service vsftpd stop
sudo apt-get -y purge vsftpd

```

---

### Post by snitz2 on 2013-11-07
When I try to stop the service I get

```
vsftpd: unrecognized service
```

---

### Post by Lars Noodén on 2013-11-07
Ok.  That means it's uninstalled.   And does manually killing it do anything?

```

pgrep -lf vsftpd
sudo pkill  vsftpd
pgrep -lf vsftpd

```

---

### Post by CharlesA on 2013-11-07
> **snitz2 said:**
> Thank you. I was able to access /var/www via sFTP but I can't uninstall vsftpd.

I tried apt-get purge/remove vsftpd but I can still connect fine via FileZilla.
I also can't stop service and it looks like it is running.

That doesn't show it as running. Run this to see what is actually listening:

```
sudo netstat -nlp
```

---

### Post by snitz2 on 2013-11-07
> **Lars Noodén said:**
> Ok.  That means it's uninstalled.   And does manually killing it do anything?

```

pgrep -lf vsftpd
sudo pkill  vsftpd
pgrep -lf vsftpd

```

None of these commands did anything.
If it's uninstalled, why can I still connect to my ftp server using filezilla and it goes to the same /home/root/ directory and all my other directories are exposed.

This is the netstat log

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      3703/mysqld     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      8107/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      767/sshd        
tcp        0      0 127.0.0.1:9000          0.0.0.0:*               LISTEN      3795/php-fpm.conf)
tcp6       0      0 :::22                   :::*                    LISTEN      767/sshd        
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     16127    3703/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     6345     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     SEQPACKET  LISTENING     6499     317/udevd           /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     7592     686/acpid           /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     6649     393/dbus-daemon     /var/run/dbus/system_bus_socket

```

---

### Post by snitz2 on 2013-11-07
I think it really was uninstalled.
I tried connecting via FileZilla, I keep getting connection failed.

```
Connection attempt failed with "ECONNREFUSED - Connection refused by server".
```

So I guess that's that. Thanks everyone, I appreciate it.

---

