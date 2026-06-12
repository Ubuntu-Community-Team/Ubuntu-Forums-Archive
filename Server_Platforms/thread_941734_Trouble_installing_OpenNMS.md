---
title: "Trouble installing OpenNMS"
date: 2008-10-08
forum: Server Platforms
---

### Post by grdlock2002 on 2008-10-08
I'm attempting to install OpenNMS on an Ubuntu Server. Upon running the installation "$OPENNMS_HOME/bin/install -dis" I get this at the end:

```

- adding iplike database function... Exception in thread "main" org.postgresql.util.PSQLException: ERROR: incompatible library "/usr/lib/postgresql/lib/opennms/iplike.so": missing magic block

        at org.postgresql.util.PSQLException.parseServerError(PSQLException.java:139)
        at org.postgresql.core.QueryExecutor.executeV3(QueryExecutor.java:152)
        at org.postgresql.core.QueryExecutor.execute(QueryExecutor.java:100)
        at org.postgresql.core.QueryExecutor.execute(QueryExecutor.java:43)
        at org.postgresql.jdbc1.AbstractJdbc1Statement.execute(AbstractJdbc1Statement.java:517)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.execute(AbstractJdbc2Statement.java:50)
        at org.postgresql.jdbc1.AbstractJdbc1Statement.execute(AbstractJdbc1Statement.java:298)
        at org.opennms.install.Installer.updateIplike(Installer.java:1694)
        at org.opennms.install.Installer.install(Installer.java:265)
        at org.opennms.install.Installer.main(Installer.java:2453)

```

And when I try to start the service I get:

```

 sudo /etc/init.d/opennms start
Starting Open Network Management System: opennms/usr/share/opennms/bin/opennms.sh: OpenNMS not configured.
/usr/share/opennms/etc/configured does not exist.
You need to run the installer -- see the install guide for details.

```

What am I missing here? I've gone through all the steps, installed all the dependencies.

---

### Post by alastair on 2008-10-08
Incompatible library version? Maybe this helps :

[http://www.opennms.org/index.php/IPLIKE](http://www.opennms.org/index.php/IPLIKE)

That was a Google for : "incompatible library" +iplike.so

If OpenNMS is not an Ubuntu package, and dependencies automatically tracked, you may need to do a little extra work.

Alastair

---

