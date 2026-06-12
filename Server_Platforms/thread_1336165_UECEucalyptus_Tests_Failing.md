---
title: "UEC/Eucalyptus Tests Failing"
date: 2009-11-24
forum: Server Platforms
---

### Post by aur0ra on 2009-11-24
I have been testing/playing with UEC for the past few days now and I'm having some troubles and hope someone can point me in the right direction. I'll try to provide as much detail as possible.

I have simple setup right now with one cloud controller and one cloud node. Both workstations are identical: 2.33GHz Intel Dual Core, with 4GB of RAM and 500GB SATA 7200 RPM drives in each. The installs of UEC completed successfully on both the controller and node. I followed the tutorial from: [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall) (primarily) and pulled pieces from here: [http://fnords.wordpress.com/2009/10/04/run-your-own-uec-part-1/](http://fnords.wordpress.com/2009/10/04/run-your-own-uec-part-1/)

Both the controller and node have obtained their IP addresses from DHCP. The controller IP is 10.1.1.60 (obviously assigned by DHCP) and the controller is 10.1.1.61. When the installations are complete the node discovery is successful and I can hit the [https://10.1.1.60:8443](https://10.1.1.60:8443) page from my laptop successfully. Logging in, setting the admin password, and installing the Ubuntu 9.10 (amd64) image from the "Store" tab is also successful. Everything else is left as it was when it was installed (i.e. config files, etc.).

Here are where my issues occur. Logged into the controller as user and sudo'ed to root, I pull down the credentials and generate mykey.priv. I followed the rest of the steps and then try to run the instance of the Ubuntu 9.10 image downloaded earlier. The system chugs for a few minutes with the image listed as "pending." Then the status of the image changes immediately to "terminated."

Scratching my head I decided to hit the Eucalyptus web page at [http://10.1.1.60:8773/services/Eucalyptus](http://10.1.1.60:8773/services/Eucalyptus) and the response is:

Failure: 500 Internal Server Error

Then I checked the logs and it looks like the connection to the database gets broken somehow. Here is a snippet from the /var/log/eucalyptus/cloud-error.log file:

```

07:53:58 [JDBCExceptionReporter:SystemClockTimer]  ERROR Connection is broken: java.net.SocketException: Connection timed out
07:53:58 [TxHandle:SystemClockTimer]  ERROR javax.persistence.PersistenceException: org.hibernate.exception.JDBCConnectionException: Cannot open connection
javax.persistence.PersistenceException: org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.hibernate.ejb.AbstractEntityManagerImpl.throwPersistenceException(AbstractEntityManagerImpl.java:614)
	at org.hibernate.ejb.TransactionImpl.begin(TransactionImpl.java:41)
	at com.eucalyptus.util.TxHandle.<init>(TxHandle.java:40)
	at com.eucalyptus.util.EntityWrapper.<init>(EntityWrapper.java:100)
	at com.eucalyptus.util.EntityWrapper.<init>(EntityWrapper.java:93)
	at edu.ucsb.eucalyptus.cloud.cluster.VmTypes.update(VmTypes.java:111)
	at edu.ucsb.eucalyptus.cloud.cluster.VmTypes.list(VmTypes.java:140)
	at com.eucalyptus.cluster.handlers.ResourceStateHandler.trigger(ResourceStateHandler.java:31)
	at com.eucalyptus.cluster.handlers.AbstractClusterMessageDispatcher.fireTimedStatefulTrigger(AbstractClusterMessageDispatcher.java:140)
	at com.eucalyptus.cluster.handlers.ResourceStateHandler.fireEvent(ResourceStateHandler.java:39)
	at com.eucalyptus.event.ReentrantListenerRegistry.fireEvent(ReentrantListenerRegistry.java:80)
	at com.eucalyptus.event.ReentrantListenerRegistry.fireEvent(ReentrantListenerRegistry.java:65)
	at com.eucalyptus.event.ListenerRegistry.fireEvent(ListenerRegistry.java:69)
	at com.eucalyptus.event.SystemClock.run(SystemClock.java:35)
	at java.util.TimerThread.mainLoop(Timer.java:534)
	at java.util.TimerThread.run(Timer.java:484)
Caused by: org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.hibernate.exception.SQLStateConverter.convert(SQLStateConverter.java:97)
	at org.hibernate.exception.JDBCExceptionHelper.convert(JDBCExceptionHelper.java:66)
	at org.hibernate.exception.JDBCExceptionHelper.convert(JDBCExceptionHelper.java:52)
	at org.hibernate.jdbc.ConnectionManager.openConnection(ConnectionManager.java:449)
	at org.hibernate.jdbc.ConnectionManager.getConnection(ConnectionManager.java:167)
	at org.hibernate.jdbc.JDBCContext.connection(JDBCContext.java:142)
	at org.hibernate.transaction.JDBCTransaction.begin(JDBCTransaction.java:85)
	at org.hibernate.impl.SessionImpl.beginTransaction(SessionImpl.java:1353)
	at org.hibernate.ejb.TransactionImpl.begin(TransactionImpl.java:38)
	... 14 more
Caused by: java.sql.SQLException: Connection is broken: java.net.SocketException: Connection timed out
	at org.hsqldb.jdbc.Util.sqlException(Unknown Source)
	at org.hsqldb.jdbc.jdbcConnection.getAutoCommit(Unknown Source)
	at com.mchange.v2.c3p0.impl.NewProxyConnection.getAutoCommit(NewProxyConnection.java:1083)
	at org.hibernate.connection.C3P0ConnectionProvider.getConnection(C3P0ConnectionProvider.java:82)
	at org.hibernate.jdbc.ConnectionManager.openConnection(ConnectionManager.java:446)
	... 19 more

```

There isn't much out there on the web about this error, so I checked the eucalyptus database directories to make sure they had the proper permissions, which they do. /var/lib/eucalyptus/db and all files under that directory are all have the owner and group set to eucalyptus. 

Next, I opened the /etc/eucalyptus/eucalyptus.conf file to see if there was anything out of the ordinary in there. The only things I thought were "odd" was that the HYPERVISOR and INSTANCE_NAME variables were both set to "not_configured." (This might have something to do with the instance not starting properly).

I'm really at a loss here. If anyone has any thoughts or can point me in the right direction, I would greatly appreciate it. Please let me know if I need to provide more detailed information. I have all of the logs (cloud-debug.log, cloud-output.log and cloud-error.log) which can be provided. Thank you very much for any help.

---

### Post by john-boy on 2010-02-09
Did you ever resolve this problem? I am experiencing what sounds like the same issue where status of virtual machine instances change from pending to terminated.

---

