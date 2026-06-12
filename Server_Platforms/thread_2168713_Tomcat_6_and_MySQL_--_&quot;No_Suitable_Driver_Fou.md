---
title: "Tomcat 6 and MySQL -- &quot;No Suitable Driver Found&quot;"
date: 2013-08-19
forum: Server Platforms
---

### Post by rknop on 2013-08-19
I had this working back in 10.04, but with Ubuntu 12.04 it is not working.  When I try to connect to a MySQL database, I get "No suitable driver found for jdbc:mysql://localhost:3306/(etc)"

I have several Tomcat 6 web aps that use MySQL, and that worked under 10.04 with exactly the same database connection URL.  Now, however, they fail to find a MySQL driver.

I *do* have mysql.jar in /usr/share/tomcat6/lib -- it's a symbolic link to /usr/share/java/mysql-connector-java-5.1.16.jar, which came out of the libmysql-java package.  Everything I've read googling the web suggests that this should fix my problem, but it doesn't.

What's going on here?

As an aside, if I run the following code:

```

    ClassLoader aploader = this.getClass().getClassLoader();
    if (aploader != null)
    { 
      URL[] urls = ((URLClassLoader)aploader).getURLs();
      for (int i = 0 ; i < urls.length ; ++i)
      { 
        System.err.format("  SampleWebApp Class Loader Path: %1$s\n", urls[i].getFile());
      }
    }
    aploader = ClassLoader.getSystemClassLoader();
    URL[] urls = ((URLClassLoader)aploader).getURLs();
    for (int i = 0 ; i < urls.length ; ++i)
    { 
      System.err.format("  System Class Loader Path: %1$s\n", urls[i].getFile());
    }
  }

```

This is all the more output I get in my catalina.out lot file:

```

  SampleWebAp Class Loader Path: /usr/local/tomcat6/samplewebapp/WEB-INF/classes/
  SampleWebAp Class Loader Path: /usr/local/tomcat6/samplewebapp/WEB-INF/lib/ldap.jar
  System Class Loader Path: /usr/share/tomcat6/bin/bootstrap.jar

```

The ldap.jar file is indeed a jar file that I have installed, so I'm not surprised it's there.  And, indeed, it functions,  However, looking at /etc/tomcat6/catalina.properties, I would expect there to be a lot more there.  Am I dumping the known classes right?  If so, it looks like Tomcat6 is not seeing the large number of jar files that exist in /usr/share/tomcat6/lib

What am I doing wrong?  What do I need to do in order to get tomcat6 to see the mysql JBDC classes, as it was able to back on Ubuntu 10.04?

---

### Post by rknop on 2013-08-19
As another addendum: mysql works just fine from Java applications run from the commandline; my problems are with Tomcat6 webapps.

Also, if I put mysql.jar in my WEB-INF directory, it *does* show up with my little "dump the class path" code above, but I still get the  "no suitable driver" error.

---

### Post by hawkmage on 2013-08-20
I assume that you are using at least java 1.6, If you are you are not supposed to need it anymore but try adding the following before you connection line:
```
Class.forName("com.mysql.jdbc.Driver");
```
This will explicitly load the MySQL JDBC driver class.  If this works you are having an issue with the way the class loader is loading things and that can be a major pain to figure out.

Also I usually put all of the jar files I need in the applications lib directory so that the war/ear is self contained and doesn't need to rely on the containers class loader.

---

