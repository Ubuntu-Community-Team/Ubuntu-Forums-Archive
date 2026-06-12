---
title: "Tomcat and some problems"
date: 2007-10-25
forum: Server Platforms
---

### Post by michalwu on 2007-10-25
Hi
I'm using Kubuntu 7.04. I need to install Tomcat server on my machine.

Everything goes fine, untill I try to start Tomcat. 
```
root@tomcat2:/# /usr/share/tomcat/bin/catalina.sh start
Using CATALINA_BASE:   /usr/share/tomcat
Using CATALINA_HOME:   /usr/share/tomcat
Using CATALINA_TMPDIR: /usr/share/tomcat/temp
Using JRE_HOME:       /usr/share/jdk

```

and then

```
root@tomcat2:/# /usr/share/tomcat/bin/catalina.sh stop
Using CATALINA_BASE:   /usr/share/tomcat
Using CATALINA_HOME:   /usr/share/tomcat
Using CATALINA_TMPDIR: /usr/share/tomcat/temp
Using JRE_HOME:       /usr/share/jdk
2007-10-25 12:36:22 org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop:
[COLOR="Red"]java.net.ConnectException: Connection refused[/COLOR]
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
        at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
        at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
        at java.net.Socket.connect(Socket.java:516)
        at java.net.Socket.connect(Socket.java:466)
        at java.net.Socket.<init>(Socket.java:366)
        at java.net.Socket.<init>(Socket.java:179)
        at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:395)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:344)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:435)

```


Connection refused is because catalina never started, I suppose.

And now strange thing. When I'm in debug mode (catalina.sh -debug) all I need to do is type "run", and catalina is starting without any problems.

I'm using JDK1.5.0, apache/2.2.3,

What is wrong? I did some research, but found nothing useful.

Best regards
mike

---

### Post by sgordon on 2007-10-26
Hi.

Think I'm missing something

When in normal (non-debug), Tomcat starts up ok, it's when you go to STOP tomcat that you have trouble (connect refused).

But then you say it starts ok in debug mode. But it looks like it starts ok without debug.

Er, perhaps it's me, the tea is still kicking in!

After you start Tomcat (non debug), what does a netstat -an | grep <port> show? anything listening? I think it's 8180. (usually 8080)

  Si

---

### Post by michalwu on 2007-10-27
Thanks for reply.


My mistake! Huge one. When I'm trying to start it in normal mode (non-debug), it is not starting really. There is no messages about failure. Logs are empty. But Tomcat is not working.

Then, when I type "stop" it shows same message 
"SEVERE: Catalina.stop:
java.net.ConnectException: Connection refused". No matter how many times I try to stop it (without starting, sic!).

All I have to do is type "tomcat debug", then run and tomcat is up and running. I tried all scripts via http - working fine.
It must be something simple and stupid :)

I can't check netstat now. I had terrible week - started with Tomcat, ended with my brand new motherboard broken :/ 
So my tomcat problem is solved ;) for now. I will have new MB within week.

Regards
mike

---

### Post by sgordon on 2007-10-29
Wow, what a nightmare!

Well, a further thought on the Tomcat issue you are having would be to use this line to 'start' Tomcat:

/usr/share/tomcat/bin/catalina.sh run
(note, run instead of start)

This will run Tomcat in the current shell, rather than spawn a new one. Hence any errors to stdout/stderr will be visible. Just paste them here, (unless that gives you all the info you need!). Anyhow, let me know.

Good luck with the new mobo.

  Si

---

### Post by fergalicious on 2007-11-01
Just to say that I am experiencing the same problem on ubuntu 7.04 with tomcat 5.5.

---

### Post by sgordon on 2007-11-02
Well, what console output do you get from:

/usr/share/tomcat/bin/catalina.sh run

(instead of /usr/share/tomcat/bin/catalina.sh start)

  Si

---

### Post by nucleo on 2007-11-06
Having the same issue

runnin Ubuntu 6.x, install tomcat 5.5 via apt-get.

I see the logs shows the address is already in use but as far as I know the only other server running is apache ans it's running on port 80.

Any one can help me out? 

also, even though I ran apt-get remove tomcat5 I still get a lot of files for it. any tips on how to remove everything form an old version?

```

Using CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun
6-Nov-2007 2:11:49 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib
6-Nov-2007 2:11:49 PM org.apache.coyote.http11.Http11BaseProtocol init
INFO: Initializing Coyote HTTP/1.1 on http-8180
6-Nov-2007 2:11:49 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 648 ms
6-Nov-2007 2:11:49 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
6-Nov-2007 2:11:49 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5
6-Nov-2007 2:11:49 PM org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
6-Nov-2007 2:11:50 PM org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8180
6-Nov-2007 2:11:50 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
6-Nov-2007 2:11:51 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/22  config=null
6-Nov-2007 2:11:51 PM org.apache.catalina.storeconfig.StoreLoader load
INFO: Find registry server-registry.xml at classpath resource
6-Nov-2007 2:11:51 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1303 ms
6-Nov-2007 2:11:51 PM org.apache.catalina.core.StandardServer await
SEVERE: StandardServer.await: create[8005]:
java.net.BindException: Address already in use
        at java.net.PlainSocketImpl.socketBind(Native Method)
        at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:359)
        at java.net.ServerSocket.bind(ServerSocket.java:319)
        at java.net.ServerSocket.<init>(ServerSocket.java:185)
        at org.apache.catalina.core.StandardServer.await(StandardServer.java:373)
        at org.apache.catalina.startup.Catalina.await(Catalina.java:615)
        at org.apache.catalina.startup.Catalina.start(Catalina.java:575)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:294)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:432)

```

---

### Post by nucleo on 2007-11-06
I managed to kill the java process that was giving me the error "address already in use". I restarted the server and here is the code I get:

```
Using CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun
6-Nov-2007 4:10:00 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib
6-Nov-2007 4:10:00 PM org.apache.coyote.http11.Http11BaseProtocol init
INFO: Initializing Coyote HTTP/1.1 on http-8180
6-Nov-2007 4:10:00 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 647 ms
6-Nov-2007 4:10:00 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
6-Nov-2007 4:10:00 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5
6-Nov-2007 4:10:00 PM org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
6-Nov-2007 4:10:01 PM org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8180
6-Nov-2007 4:10:01 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
6-Nov-2007 4:10:01 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/21  config=null
6-Nov-2007 4:10:01 PM org.apache.catalina.storeconfig.StoreLoader load
INFO: Find registry server-registry.xml at classpath resource
6-Nov-2007 4:10:01 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1306 ms

```

My issue might be a bit different then the original one. I can start the server but when I check the opened port I see the port for AJP13 but not the one for Tomcat... any help would be appreciated :)

---

### Post by sgordon on 2007-11-08
Ok, well you're getting closer anyhow!

When you say checking the tomcat port, how are you doing this?

My suggestion is:

$ netstat -an | grep 8180

Any useful output from that?

  Si

---

### Post by nucleo on 2007-11-08
$ netstat -an | grep 8180
gives me this
```

tcp6       0      0 :::8180                 :::*                    LISTEN

```

and 
# nmap -sT localhost 

gives me 

```

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-08 12:06 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 1690 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3306/tcp open  mysql
8009/tcp open  ajp13

```

---

### Post by nucleo on 2007-11-15
sgordon any ideas?

---

### Post by sgordon on 2007-11-21
Was stumped for a while to be honest!

Had a similar problem on a hosted server that had tomcat installed upon it. The problem seemed to be a firewall by the hosting provider!

Ah, one more thought!!

If you only install the package tomcat5.5, you don't get any webapps. It's an odd situation you get into as well...if you go to [http://localhost:8180/](http://localhost:8180/) you seem to get a blank page returned (even view-source on your browser gets no content). But that's correct since no apps are installed.

If you install something in your web browser which shows HTTP traffic, such as livehttpheaders: [http://livehttpheaders.mozdev.org/](http://livehttpheaders.mozdev.org/)

you can see the response from your working Tomcat server! Mine shows:

```
HTTP/1.x 400 No Host matches server name www.mydomain.com
Transfer-Encoding: chunked
Date: Wed, 21 Nov 2007 15:02:55 GMT
Server: Apache-Coyote/1.1

```

If you install package tomcat5.5-webapps you get the docs (and more).

So [http://localhost:8180/tomcat-docs/](http://localhost:8180/tomcat-docs/) should work.

Do you have tomcat5.5-webapps  ?

  Si

---

