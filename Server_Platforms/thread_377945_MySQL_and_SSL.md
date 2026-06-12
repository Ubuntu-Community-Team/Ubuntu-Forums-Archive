---
title: "MySQL and SSL"
date: 2007-03-06
forum: Server Platforms
---

### Post by sc0ttbeardsley on 2007-03-06
I'm interested in doing MySQL (ver5.0) replication over SSL. I see the following comments in the my.cnf:

```
# If you want to enable SSL support (recommended) read the manual or my
# HOWTO in /usr/share/doc/mysql-server/SSL-MINI-HOWTO.txt.gz
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem
```

Of course the doc is actually at: /usr/share/doc/mysql-server-5.0/SSL-MINI-HOWTO.txt

A old-looking message in that howto says:
> Please not that OpenSSL is no longer enabled by default so you have to
rebuild the package yourself to get it work.

I've tried enabling SSL in my.cnf but I've never done this before so I'm not sure if it's breaking because of my config or because SSL is not supported. Here is my config:
```
ssl-ca=/etc/mysql/cacert.pem
ssl-cert=/etc/mysql/server-cert.pem
ssl-key=/etc/mysql/server-key.pem
```

With the above config I get the following message on startup:
```
[ERROR] /usr/sbin/mysqld: unknown variable 'ssl-ca=/etc/mysql/cacert.pem'
```

Here is an ldd on the mysql binary (which makes me suspect mysql doesn't have ssl support compiled in):
```
 # ldd /usr/sbin/mysqld
        librt.so.1 => /lib/librt.so.1 (0x00002b642e896000)
        libz.so.1 => /usr/lib/libz.so.1 (0x00002b642e99e000)
        libwrap.so.0 => /lib/libwrap.so.0 (0x00002b642eab4000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002b642ebbd000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b642ecc0000)
        libcrypt.so.1 => /lib/libcrypt.so.1 (0x00002b642edd5000)
        libnsl.so.1 => /lib/libnsl.so.1 (0x00002b642ef08000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002b642f01f000)
        libm.so.6 => /lib/libm.so.6 (0x00002b642f21c000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002b642f3a1000)
        libc.so.6 => /lib/libc.so.6 (0x00002b642f4af000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b642e77f000)
```

Any pointers? If I need to recompile mysql can anyone point to docs on building deb packages. Any insight to why SSL wouldn't be compiled in by default. Seems to go against the whole "secure by default" rule.

---

### Post by sc0ttbeardsley on 2007-03-06
To answer my own question... To test if your mysql server has SSL support run this:
```
# mysqld --ssl --help
070306 15:03:05 [ERROR] mysqld: unknown option '--ssl'
```

If you get the "unknown option" message you do not have SSL support compiled in.

Instead of recompiling/repackaging mysql from scratch I've decided to use _[stunnel]("http://www.stunnel.org")_ and a technique described in _[this howto]("http://www.stunnel.org/examples/mysql.html")_.

---

### Post by brieweb on 2008-05-03
I did get ssl working with mysql. I did enable the keys as you have shown in my.conf, but then I also granted priveleges so that a user could connect via ssl.

GRANT ALL PRIVILEGES ON *.* TO 'root'@'someremotehost' identified by 'securepasswd' require ssl;
flush privileges;

I generated a cert for the client connection. Then i connected using the mysql command

mysql --ssl=TRUE --ssl-ca=/etc/ssl/foobar-cacert.pem --ssl-cert=/home/brian/openssl/mysql-client-cert.pem --ssl-key=/home/brian/openssl/mysql-client-key.pem --host=brian-laptop -u root -p

It works for me.

Once connected, I issued the \s command which indicates an ssl connection.

mysql> \s

--------------
mysql  Ver 14.12 Distrib 5.0.45, for pc-linux-gnu (i486) using readline 5.2

Connection id:          9
Current database:
Current user:           [email]root@brian-laptop.internal.brie.com[/email]
SSL:                    Cipher in use is DHE-RSA-AES256-SHA
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.0.45-Debian_1ubuntu3.3-log Debian etch distribution
Protocol version:       10
Connection:             brian-laptop via TCP/IP
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    latin1
Conn.  characterset:    latin1
TCP port:               3306
Uptime:                 3 hours 27 min 36 sec


brian

---

### Post by palin_linux on 2008-05-20
> **sc0ttbeardsley said:**
> To answer my own question... To test if your mysql server has SSL support run this:
```
# mysqld --ssl --help
070306 15:03:05 [ERROR] mysqld: unknown option '--ssl'
```

If you get the "unknown option" message you do not have SSL support compiled in.

Instead of recompiling/repackaging mysql from scratch I've decided to use _[stunnel]("http://www.stunnel.org")_ and a technique described in _[this howto]("http://www.stunnel.org/examples/mysql.html")_.

What steps did you use? I follow the guide but this is what i get.

/usr/sbin/stunnel -P -p /usr/local/etc/stunnel/stunnel.pem -d 3307 -r localhost
2008.05.20 10:35:51 LOG3[16361:3086280400]: -P: No such file or directory (2)
 
Can you help me and the community whit a how to...

Thanks,
Jeff

---

### Post by palin_linux on 2008-05-20
> **palin_linux said:**
> What steps did you use? I follow the guide but this is what i get.

/usr/sbin/stunnel -P -p /usr/local/etc/stunnel/stunnel.pem -d 3307 -r localhost
2008.05.20 10:35:51 LOG3[16361:3086280400]: -P: No such file or directory (2)
 
Can you help me and the community whit a how to...

Thanks,
Jeff
I found A great site for the how to mysql over Stunnel [http://linuxgazette.net/107/odonovan.html](http://linuxgazette.net/107/odonovan.html)

5. Using Stunnel to Encrypt MySQL Transactions

    This method can be used to encrypt any service where neither the server nor the client are SSL-enabled. Common examples include CVS, MySQL, etc. 

In the example with POP3 and IMAP above, we were only concerned with providing the server with SSL encryption as the clients generally have this built in. However, neither the standard MySQL server nor client have SSL capabilities - but we can still use Stunnel to provide this.

It involves using a Stunnel daemon on both the server's machine and the client's machine. The configuration for the server side is similar to the one we used above for POP3/IMAP. The default MySQL port is 3306, and since no port is reserved for secure MySQL connections, I will use 3307:

# Sample stunnel configuration file for securing MySQL (server side)

# Provide the full path to your certificate-key pair file
cert = /usr/local/etc/stunnel/stunnel.pem

# lock the process into a chroot jail
chroot = /usr/local/var/run/stunnel/
# and create the PID file in this jail
pid = /stunnel.pid

# change the UID and GID of the process for security reasons
setuid = nobody
setgid = nobody

# Configure our secured MySQL server

[mysqls]
accept  = 3307
connect = 3306

I can now start the Stunnel daemon on the server machine with:

$ stunnel stunnel-mysql-server.conf

where stunnel-mysql-server.conf is a text file containing the above configuration. We also need to set up an Stunnel daemon on the client machine with the following configuration:

# Sample stunnel configuration file for securing MySQL (client side)

# Provide the full path to your certificate-key pair file
cert = /usr/local/etc/stunnel/stunnel.pem

# lock the process into a chroot jail
chroot = /usr/local/var/run/stunnel/
# and create the PID file in this jail
pid = /stunnel.pid

# change the UID and GID of the process for security reasons
setuid = nobody
setgid = nobody

# enable client mode
client = yes

# Configure our secured MySQL client

[mysqls]
accept  = 3306
connect = 1.2.3.4:3307

You'll notice that I have used a new option: client = yes - this enables "client mode" which lets Stunnel know that the remote service uses SSL. Our local Stunnel daemon will now listen for connections on the local MySQL port (3306), encrypt them and forward them to our MySQL server machine (say 1.2.3.4) where another Stunnel is listening on port 3307. The remote Stunnel will decrypt the transmission and forward it to the MySQL server listening on port 3306 of the same machine. All responses will be sent back through the same encrypted channel.

Save the client configuration as stunnel-mysql-client.conf and start off Stunnel with:

$ stunnel stunnel-mysql-client.conf

and then you can connect to the remote MySQL server through the encrypted channel by connecting to the local Stunnel daemon (which is listening on MySQL's 3306 port):

$ mysql -h 127.0.0.1 -u username -p

6. Trouble Shooting
Stunnel can be a bit tricky about permissions - especially when using a chroot jail and reducing your user and group ID to nobody (some systems might need nogroup for setgid). Ensure your chrooted directory is writable by the nobody user and/or the nobody (or nogroup) group.

Stunnel runs in the background by default and doesn't show any error messages. This means you won't know if it worked or not from the command line! You can check that the process is running by searching the output of the ps command:

$ ps -ef | grep stunnel
nobody   21769     1  0 09:12 ?        00:00:00 /usr/local/sbin/stunnel ./stunnel-mysql-server.conf

Stunnel can also be instructed to run in the foreground by adding the following command to the configuration file (above the service configuration):

foreground = yes

As with all services, the best method of diagnosing problems is through the service's log messages. You can enable Stunnel's logging facilities by adding the following commands to the configuration file (above the service configuration):

debug = 7
output = /tmp/stunnel.log

If you are running in the foreground for testing/debugging, then you might prefer to send the log messages to standard out:

debug = 7
output = /dev/stdout

---

