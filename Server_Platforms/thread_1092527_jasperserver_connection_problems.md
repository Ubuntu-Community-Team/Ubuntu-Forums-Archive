---
title: "jasperserver connection problems"
date: 2009-03-10
forum: Server Platforms
---

### Post by mthaddon on 2009-03-10
Hi Folks,

I'm in the process of trying to setup jasperserver on Ubuntu 8.04, and I've run into the following issue. I have everything setup so that I can get to the login screen in the web UI, but whenever I enter a username/password combination as defined in /etc/tomcat5.5/tomcat-users.xml I get the following error message:

WARN JDBCExceptionReporter,http-8180-Processor20:77 - SQL Error: 1054, SQLState: 42S22
ERROR JDBCExceptionReporter,http-8180-Processor20:78 - Unknown column  'this_.previousPasswordChangeTime' in 'field list'
WARN LoggerListener,http-8180-Processor20:55 - Authentication event AuthenticationFailureServiceExceptionEvent: admin; details: org.acegisecurity.ui.WebAuthenticationDetails@fffed504: RemoteIpAddress: 127.0.0.1; SessionId: DAB2C63D58A163633F5657FDBB69A46C; exception: JDBC exception on Hibernate data access; nested exception is org.hib
ernate.exception.SQLGrammarException: could not execute query; nested exception is org.springframework.orm.hibernate3.HibernateJdbcException: JDBC exception on Hibernate data access; nested exception is org.hibernate.exception.SQLGrammarException: could not execute query

I've confirmed that the connection details as defined in $JASPERSERVER_ROOT/META-INF/context.xml are correct (i.e. I can connect to the MySQL database using those connection details.

Any ideas what I might be missing?

Thanks, Tom

---

