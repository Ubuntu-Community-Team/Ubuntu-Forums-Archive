---
title: "MySQL connection great problem"
date: 2008-07-08
forum: Server Platforms
---

### Post by legal101205 on 2008-07-08
Hi, i installed yesterday Ubuntu 8.04, Zend Studio for Eclipse, Zend Core & Zend Platform (last versions just downloaded). I am totally new to linux platform, and very lost!

I try under ZS to create a new connection to the mysql database (automatically created by Zend Platform).

The ping error message is the following:

```
com.mysql.jdbc.CommunicationsException: Communications link failure due to underlying exception: 

** BEGIN NESTED EXCEPTION ** 

java.net.ConnectException
MESSAGE: Connection refused

STACKTRACE:

java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(Unknown Source)
	at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
	at java.net.PlainSocketImpl.connect(Unknown Source)
	at java.net.SocksSocketImpl.connect(Unknown Source)
	at java.net.Socket.connect(Unknown Source)
	at java.net.Socket.connect(Unknown Source)
	at java.net.Socket.<init>(Unknown Source)
	at java.net.Socket.<init>(Unknown Source)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:256)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:271)
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:2744)
	at com.mysql.jdbc.Connection.<init>(Connection.java:1553)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)
	at com.zend.php.datatools.core.connection.JDBCConnection.createConnection(Unknown Source)
	at org.eclipse.datatools.connectivity.DriverConnectionBase.internalCreateConnection(DriverConnectionBase.java:104)
	at org.eclipse.datatools.connectivity.DriverConnectionBase.open(DriverConnectionBase.java:53)
	at com.zend.php.datatools.core.connection.JDBCConnectionFactory.createConnection(Unknown Source)
	at org.eclipse.datatools.connectivity.internal.ConnectionFactoryProvider.createConnection(ConnectionFactoryProvider.java:77)
	at org.eclipse.datatools.connectivity.internal.ConnectionProfile.createConnection(ConnectionProfile.java:354)
	at org.eclipse.datatools.connectivity.ui.PingJob.run(PingJob.java:57)
	at org.eclipse.core.internal.jobs.Worker.run(Worker.java:55)


** END NESTED EXCEPTION **



Last packet sent to the server was 0 ms ago.
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:2820)
	at com.mysql.jdbc.Connection.<init>(Connection.java:1553)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)
	at com.zend.php.datatools.core.connection.JDBCConnection.createConnection(Unknown Source)
	at org.eclipse.datatools.connectivity.DriverConnectionBase.internalCreateConnection(DriverConnectionBase.java:104)
	at org.eclipse.datatools.connectivity.DriverConnectionBase.open(DriverConnectionBase.java:53)
	at com.zend.php.datatools.core.connection.JDBCConnectionFactory.createConnection(Unknown Source)
	at org.eclipse.datatools.connectivity.internal.ConnectionFactoryProvider.createConnection(ConnectionFactoryProvider.java:77)
	at org.eclipse.datatools.connectivity.internal.ConnectionProfile.createConnection(ConnectionProfile.java:354)
	at org.eclipse.datatools.connectivity.ui.PingJob.run(PingJob.java:57)
	at org.eclipse.core.internal.jobs.Worker.run(Worker.java:55)
```

While trying to connect to PHPMyAdmin, i get the following error message:

```
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
```

While searching for mysql.log & mysql.err files, i have no result. The '/var/log/mysql' & '/var/run/mysqld/' folders don't exist. 

I have configured MySQL autostart, and it works good.

I am desperate and gave up to find by myself as i have read many posts.

Thanks in advance, Nicolas

---

### Post by windependence on 2008-07-08
The default from mysql server is to be binding to localhost (127.0.0.1), this means it will only accept connections from local applications. 
To change that, edit /etc/mysql/my.cnf and comment out the line bind-address = 127.0.0.1: 
Then you will need to restart the mysql server with: 
/etc/init.d/mysql restart 


-Tim

---

### Post by legal101205 on 2008-07-09
The '/etc/mysql/' directory don't exist.
The my.conf exists in the Zend '/usr/local/Zend/Platform/MySQL/etc' folder but the content is the following:

```
[mysqld]
sql-mode=NO_AUTO_VALUE_ON_ZERO
innodb_flush_log_at_trx_commit=0
innodb_buffer_pool_size=100M
innodb_log_file_size=20M
innodb_log_buffer_size=8M
key_buffer_size=64M
table_cache=256
sort_buffer_size=4M
read_buffer_size=1M
bulk_insert_buffer_size=8M
```

The search for another location on the system files gave no result.

[COLOR="Red"]**Please can a moderator move my thread in the right section, i did not see i was in the Server Platform section and have the desktop version.**[/COLOR]

---

