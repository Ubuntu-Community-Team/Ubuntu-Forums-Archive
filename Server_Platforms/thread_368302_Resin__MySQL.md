---
title: "Resin / MySQL"
date: 2007-02-23
forum: Server Platforms
---

### Post by Peque on 2007-02-23
Hey Forum. 

I have a strange problem and need some help to get this to work
I have the following setup: 
1 Applicationserver Rinning: 
Ubuntu Dapper - Resin 3.0.21 - JAVA 1.5.0.11

1 DB Server running: 
Ubuntu Dapper - MySQL 5.0 

I get an error on the application when it tries to connect to the DB server .- but have no problem connecting via console,telnet etc etc
all this ( The application) works just great under M$but gives me great problems under Linux. I have downloaded and installed java from Source etc etc. 


I use hibernate under Resin and have checked everything in and out for several days now - and all I get it this error: 
** BEGIN NESTED EXCEPTION ** 

java.net.SocketException
MESSAGE: java.net.ConnectException: Connection refused

STACKTRACE:

java.net.SocketException: java.net.ConnectException: Connection refused
        at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:156)
        at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:284)
        at com.mysql.jdbc.Connection.createNewIO(Connection.java:2555)
        at com.mysql.jdbc.Connection.<init>(Connection.java:1485)
        at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:266)
        at com.mchange.v2.c3p0.DriverManagerDataSource.getConnection(DriverManagerDataSource.java:81)
        at com.mchange.v2.c3p0.WrapperConnectionPoolDataSource.getPooledConnection(WrapperConnectionPoolDataSource.java:96)
        at com.mchange.v2.c3p0.impl.C3P0PooledConnectionPool$1.acquireResource(C3P0PooledConnectionPool.java:89)
        at com.mchange.v2.resourcepool.BasicResourcePool.acquireUntil(BasicResourcePool.java:665)
        at com.mchange.v2.resourcepool.BasicResourcePool.access$500(BasicResourcePool.java:32)
        at com.mchange.v2.resourcepool.BasicResourcePool$AcquireTask.run(BasicResourcePool.java:1206)
        at com.mchange.v2.async.ThreadPoolAsynchronousRunner$PoolThread.run(ThreadPoolAsynchronousRunner.java:368)


** END NESTED EXCEPTION **

Have anybody any idea about this - or should I send more logfiles for herlping you --> helping me

Thanks 
P

---

