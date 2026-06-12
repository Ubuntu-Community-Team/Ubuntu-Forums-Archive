---
title: "How do I troubleshoot authbind in Lucid Server?"
date: 2010-07-20
forum: Server Platforms
---

### Post by cloudcontrol on 2010-07-20
Hello,

I did not find one topic which discusses authbind in this forum, so I hope this is the right place to discuss this issue.

I have deployed the latest official Canonical AMI on EC2 for 32-bit Lucid server in the us-west region (ami-c597c680) and followed an [excellent blog post]("http://blog.mycroes.nl/2010/04/installing-alfresco-33-on-ubuntu-lucid.html") to install Alfresco Community 3.3.g.

However, using authbind to allow the tomcat6 server to access privileged port 143 for Alfresco's built-in IMAP server has not worked for me. It seems authbind should report errors and failures to the applications log according to the authbind man page (though I might not be understanding this correctly), but even in debug mode I see nothing in the alfresco.log file.
> ERROR HANDLING
...
The helper program usually reports back to the shared library with an exit status containing an errno value which encodes whether the bind was permitted and successful. This will be returned to the calling program in the usual way.

In the case of apparent configuration or other serious errors the library and/or the helper program may cause messages to be printed to the program's stderr, was well as returning -1 from bind.


Here's some relevant configuration and log info. Everything seems to be in place for authbind to work, but Alfresco 3.3g IMAP fails to bind to port 143. Binding to unprivileged ports works fine.

>  
/etc/default/tomcat6 line 60: AUTHBIND=yes
/etc/authbind/byuid/107 (tomcat UID)= 0.0.0.0/32:1,1023 (also tried removing this file and creating /etc/authbind/byport/143, owned by tomcat6 user)

tomcat6 init script excerpt:

catalina_sh() {
	# Escape any double quotes in the value of JAVA_OPTS
	JAVA_OPTS="$(echo $JAVA_OPTS | sed 's/\"/\\\"/g')"

	AUTHBIND_COMMAND=""
	if [ "$AUTHBIND" = "yes" -a "$1" = "start" ]; then
		JAVA_OPTS="$JAVA_OPTS -Djava.net.preferIPv4Stack=true"
		AUTHBIND_COMMAND="/usr/bin/authbind --deep /bin/bash -c "
	fi

	# Define the command to run Tomcat's catalina.sh as a daemon
	# set -a tells sh to export assigned variables to spawned shells.
	TOMCAT_SH="set -a; JAVA_HOME=\"$JAVA_HOME\"; source \"$DEFAULT\"; \
		CATALINA_HOME=\"$CATALINA_HOME\"; \
		CATALINA_BASE=\"$CATALINA_BASE\"; \
		JAVA_OPTS=\"$JAVA_OPTS\"; \
		CATALINA_PID=\"$CATALINA_PID\"; \
		CATALINA_TMPDIR=\"$CATALINA_TMPDIR\"; \
		LANG=\"$LANG\"; JSSE_HOME=\"$JSSE_HOME\"; \
		cd \"$CATALINA_BASE\"; \
		\"$CATALINA_SH\" $@"

	if [ "$AUTHBIND" = "yes" -a "$1" = "start" ]; then
		TOMCAT_SH="'$TOMCAT_SH'"
	fi


- alfresco.log output:

14:07:20,121 INFO  [org.alfresco.repo.imap.AlfrescoImapServer] IMAP service started on host:port FQDN:143.
14:07:20,123 INFO  [org.alfresco.repo.management.subsystems.ChildApplicationContextFactory] Startup of 'imap' subsystem, ID: [imap, default] complete

~# netstat -an --tcp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:39872           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8100          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50500           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8005          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50501           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50502           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50503           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50504           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50505           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50506           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50508           0.0.0.0:*               LISTEN     
tcp        0      0 10.160.226.81:22        76.233.236.102:54119    ESTABLISHED
tcp        0      0 127.0.0.1:3306          127.0.0.1:57169         ESTABLISHED
tcp        0      0 127.0.0.1:3306          127.0.0.1:57171         ESTABLISHED
tcp        0      0 127.0.0.1:3306          127.0.0.1:57170         ESTABLISHED
tcp        0      0 127.0.0.1:57167         127.0.0.1:3306          ESTABLISHED
tcp        0      0 127.0.0.1:57168         127.0.0.1:3306          ESTABLISHED
tcp        0      0 127.0.0.1:3306          127.0.0.1:57167         ESTABLISHED
tcp        0      0 127.0.0.1:57171         127.0.0.1:3306          ESTABLISHED
tcp        0      0 10.160.226.81:22        76.233.236.102:52785    ESTABLISHED
tcp        0      0 127.0.0.1:3306          127.0.0.1:57168         ESTABLISHED
tcp        0      0 127.0.0.1:57170         127.0.0.1:3306          ESTABLISHED
tcp        0      0 127.0.0.1:3306          127.0.0.1:57172         ESTABLISHED
tcp        0      0 127.0.0.1:57169         127.0.0.1:3306          ESTABLISHED
tcp        0      0 127.0.0.1:50720         127.0.0.1:8100          ESTABLISHED
tcp        0      0 127.0.0.1:57172         127.0.0.1:3306          ESTABLISHED
tcp        0      0 10.160.226.81:22        76.233.236.102:55409    ESTABLISHED
tcp        0      0 127.0.0.1:8100          127.0.0.1:50720         ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN

---

### Post by cloudcontrol on 2010-07-20
Failure to bind is not logged in alfresco.log, but /var/log/tomcat6/catalina.out and error is:
> Exception in thread "Thread-29" java.lang.RuntimeException: java.net.SocketException: No such file or directory
        at com.icegreen.greenmail.imap.ImapServer.run(ImapServer.java:53)
Caused by: java.net.SocketException: No such file or directory
        at java.net.PlainSocketImpl.socketBind(Native Method)
        at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
        at java.net.ServerSocket.bind(ServerSocket.java:336)
        at java.net.ServerSocket.<init>(ServerSocket.java:202)
        at com.icegreen.greenmail.AbstractServer.openServerSocket(AbstractServer.java:48)
        at com.icegreen.greenmail.imap.ImapServer.run(ImapServer.java:51)


By Default, the file /etc/authbind/byuid/107 contained: 

0.0.0.0/32:1,1023

The fix is changing this to:

X.X.X.X/32:1,1023

where x.x.x.x is your local IP address which resolves to your systems hostname.

---

### Post by fusz on 2011-10-07
I have a related problem but your fix don't work for me. 

I've also tried to add an address attribute to the connector element specifying the same address as in /etc/authbind/byuid/103

```

    <Connector port="80" protocol="HTTP/1.1" address="10.33.12.73"
               connectionTimeout="20000"
               URIEncoding="UTF-8"
               redirectPort="8443" />


```

and

```

10.33.12.73/32:1,1023

```

Still no luck. Works like a charm in Natty...

---

