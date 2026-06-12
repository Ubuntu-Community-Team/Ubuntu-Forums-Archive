---
title: "Tomcat5.5 logging permission problems"
date: 2009-01-24
forum: Server Platforms
---

### Post by devinWhalen on 2009-01-24
Hey,

I am having problems getting log4j to work with tomcat5.5.  I created a logger with a log4j.properties file like so:
```

# define the root logger with two appenders writing to console and file
log4j.rootLogger = DEBUG, CONSOLE, FILE

#define your own logger named com.foo
log4j.logger.com.foo=com.foo.MyLogger
#assign appender to your own logger
log4j.logger.com.foo.appender=FILE

#define the appender named
log4j.appender.FILE=org.apache.log4j.FileAppender
log4j.appender.FILE.File=/var/www/marlowe_dev/WEB-INF/logs/marlowe.log

#define the appender named CONSOLE
log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
log4j.appender.CONSOLE.conversionPattern=%m%n

```


I just copied this example and changed the file path.  When I try to hit my jsp pages I get the following error:

java.security.AccessControlException: access denied (java.io.FilePermission /var/www/marlowe_dev/WEB-INF/logs/marlowe.log write)
	java.security.AccessControlContext.checkPermission(AccessControlContext.java:323)

tomcat55 is the owner of this directory and has read/write permissions.

I read somewhere that you need to alter the catalina.policy file for I added this to that:
grant codeBase "file:/var/www/marlowe_dev/WEB-INF/logs/-"{
    permission java.security.AllPermission;
};


And I still get the same error.  Does anyone know what the issue is?  I have spent quite a bit of time just trying to get this logger working.

Thanks.

---

### Post by devinWhalen on 2009-01-25
I was able to get my webapp to run with no errors by adding this to the catalina.policy file:

```

grant codeBase "file:/var/www/marlowe_dev/-"{
    permission java.security.AllPermission;
};

```

However, the log files are created but no information is written to the file, but I guess this is a problem with my log4j.properties file.

---

