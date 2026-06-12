---
title: "optimizing tomcat web server"
date: 2009-09-07
forum: Server Platforms
---

### Post by bilal_jan on 2009-09-07
**Please consider the following details:**

**Scenario:** We put load on tomcat (basically a simple http request) and in response an http response sends 1 to show success.

> 
Executor and Connector configuration (TOMCAT 6) with java version 1.4.2:

<Executor name="tomcatThreadPool" namePrefix="catalina-exec-" 

        maxThreads="300" minSpareThreads="100" maxIdleTime="120000" />

 

<Connector executor="tomcatThreadPool" port="8080"  protocol="HTTP/1.1" 

               acceptCount="100"

               acceptorThreadCount="2"

               processCache="-1"

               enableLookups=”false”

               connectionTimeout="120000"

               socket.tcpNoDelay="true" 

               redirectPort="8443" />
 

Now I have tried many other configurations but I think this basic configuration should work.**What we eventually want is TPS around 1000.**I have tried the  version where we don’t use the executor and have useExecutor=”false” in connector settings and define maxthread and minspare thread count in connector.In all cases TPS seems pretty much the same. More so I have also tried using different protocol protocol=”org.apache.coyote.http11.HTTP11NioProtocol” as well. We have heap size increased to 1GB.

> 
Load  Testing and results:

100 users hit once we get  23 tps at max

100 users hit thrice with no gap we get 250 tps.


But as we go to increase the number of users and not iterations we get a bottleneck of 25 tps at max and not more.As minSpareThread count is 25 by default. I thought that it may very well explain the bottleneck but increasing the minsparethread count doesn’t help at all we get same results.

What i want is a simple configuration that ensures high tps .

I am stuck here would really appreciate your help.Would be waiting for your response.

---

