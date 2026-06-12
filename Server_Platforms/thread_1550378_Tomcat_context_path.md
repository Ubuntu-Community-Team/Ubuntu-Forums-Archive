---
title: "Tomcat context path"
date: 2010-08-11
forum: Server Platforms
---

### Post by Astghik on 2010-08-11
Hello All.

I have Apache Tomcat 6 server running on Ubuntu 9.10. . I have changed context path to <Context path="/" docBase="/var/lib/tomcat6/webapps/myapp" > .
[http://myip:8080](http://myip:8080) gives 404 (_The requested resource () is not available._), but [http://myip:8080/myapp](http://myip:8080/myapp) is ok. What I have mistaken?

Thanks.
Astghik

---

### Post by Astghik on 2010-08-13
I've solved the problem by changing server.xml 
```

[IMG]file:///C:/Users/ASTGHI%7E1.MKR/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/ASTGHI%7E1.MKR/AppData/Local/Temp/moz-screenshot-1.png[/IMG]<Engine name="Catalina" defaultHost="localhost">
<Realm className="org.apache.catalina.realm.UserDatabaseRealm" resourceName="UserDatabase"/>
<Host name="localhost" appBase="webapps" unpackWARs="true" autoDeploy="true" xmlValidation="false" xmlNamespaceAware="false">
<Context path="" docBase="myapp" debug="0"/>
</Host>
<Host name="www.myip.com" appBase="/var/lib/tomcat6/webapps">
<Context path="" docBase="myapp"/>
</Host>
</Engine>

```

But I got another problem, all images (there are in /var/lib/tomcat6/webapps/myapp/img dir) are broken and "**An error occurred::  org.springframework.dao.DataAccessResourceFailureException: could not  execute query; nested exception is  org.hibernate.exception.JDBCConnectionException: could not execute query**                 
                " exception is throwing.

How to fix those problems?

Regards,
Astghik

---

