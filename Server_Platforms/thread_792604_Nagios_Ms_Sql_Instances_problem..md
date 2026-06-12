---
title: "Nagios Ms Sql Instances problem."
date: 2008-05-13
forum: Server Platforms
---

### Post by depele on 2008-05-13
Hello, 

I have installed a Ubuntu server box with nagios up and running.
I wrote a script (service check) which uses tsql (freetds) to connect with a mssql server.

The problem right now is that nagios uses the $hostaddress$ variable. 

So in the config file for freetds.conf  I had to specify the ip address as name (between [ ] )

```

[10.0.230.204]
        host = 10.0.230.204
        port = 1433
        tds version = 8.0
```

This makes it impossible to declare a second ip address with the option ```
instance = sqlserver2000.
```

Does somebody know how to fix it or to work around it?

I know this is actually nog a real Linux problem. But I do not know where else to ask it.

Thanks in advance.

grtz..

ARne

---

### Post by benyg19 on 2009-09-14
I have had the same problem, there is a parameter in freetds that specifies whether to read config from the freetds.conf file or from a parameter. I documented the process here: [http://ben.goodacre.name/tech/Monitor_SQL_Server_(MSSQL)_using_Nagios](http://ben.goodacre.name/tech/Monitor_SQL_Server_(MSSQL)_using_Nagios)

Hope it helps!

Ben

---

