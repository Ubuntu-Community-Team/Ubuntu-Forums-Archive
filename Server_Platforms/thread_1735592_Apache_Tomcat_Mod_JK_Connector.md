---
title: "Apache Tomcat Mod_JK Connector"
date: 2011-04-21
forum: Server Platforms
---

### Post by rhyobit on 2011-04-21
Hi All,

I've been banging my head against a brick wall with this one for some time now so I'm really hoping that somebody can point me in the right direction.

I'm trying to setup apache tomcat with mod_jk so that requests for jsp/jsf content can be forwarded to tomcat transparently. I understand that there may be simpler ways of doing this such as mod_proxy, I am stuck with having to do this using mod_jk however.

Ok, so now to some basics the versions of everything I'm using are as follows:
OS Ubuntu Server 10.10
Apache: 2.2.16
Tomcat: 6.0.32
Java: 1.6.0_21
Mod_JK: 1.2.31

The issue I'm currently having is that I've setup a worker tomcat1 which is mounted at serverroot/docs

When I'm browsing to this I'm getting a 404.  My apache logs advises 404 with the logs stating that /var/www/docs doesn't exist.  As a result apache doesn't seem to be forwarding anything to mod_jk at all.

Follows are the contents of server.xml, workers.properties and httpd.conf

**workers.properties:**
```
pete@ubuntu:/etc/apache2$ cat /etc/apache2/workers.properties 
worker.list=tomcat1
worker.tomcat1.type=ajp13
worker.tomcat1.host=localhost
worker.tomcat1.port=8009
# worker "tomcat1" uses up to 150 sockets, which will stay no more than
# 10 minutes in the connection pool.
worker.tomcat1.connection_pool_size=150
worker.tomcat1.connection_pool_timeout=600
# worker "tomcat1" will ask the operating system to send a KEEP-ALIVE
# signal on the connection.
worker.tomcat1.socket_keepalive=1
# mount can be used as an alternative to the JkMount directive
worker.tomcat1.mount=/docs /docs/*
# Update this path to match your local state directory or logs directory
JkShmFile     /var/log/httpd/mod_jk.shm

```
[B]server.xml:
[/B]```
pete@ubuntu:/$ cat /opt/tomcat/tomcat6/conf/server.xml
<?xml version='1.0' encoding='utf-8'?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<!-- Note:  A "Server" is not itself a "Container", so you may not
     define subcomponents such as "Valves" at this level.
     Documentation at /docs/config/server.html
 -->
<Server port="8005" shutdown="SHUTDOWN">

  <!--APR library loader. Documentation at /docs/apr.html -->
  <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />
  <!--Initialize Jasper prior to webapps are loaded. Documentation at /docs/jasper-howto.html -->
  <Listener className="org.apache.catalina.core.JasperListener" />
  <!-- Prevent memory leaks due to use of particular java/javax APIs-->
  <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
  <!-- JMX Support for the Tomcat server. Documentation at /docs/non-existent.html -->
  <Listener className="org.apache.catalina.mbeans.ServerLifecycleListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />

  <!-- Global JNDI resources
       Documentation at /docs/jndi-resources-howto.html
  -->
  <GlobalNamingResources>
    <!-- Editable user database that can also be used by
         UserDatabaseRealm to authenticate users
    -->


   <!-- <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
   -->

  </GlobalNamingResources>

  <!-- A "Service" is a collection of one or more "Connectors" that share
       a single "Container" Note:  A "Service" is not itself a "Container", 
       so you may not define subcomponents such as "Valves" at this level.
       Documentation at /docs/config/service.html
   -->
  <Service name="Catalina">
  
    <!--The connectors can use a shared executor, you can define one or more named thread pools-->
    <!--
    <Executor name="tomcatThreadPool" namePrefix="catalina-exec-" 
        maxThreads="150" minSpareThreads="4"/>
    -->
    
    
    <!-- A "Connector" represents an endpoint by which requests are received
         and responses are returned. Documentation at :
         Java HTTP Connector: /docs/config/http.html (blocking & non-blocking)
         Java AJP  Connector: /docs/config/ajp.html
         APR (HTTP/AJP) Connector: /docs/apr.html
         Define a non-SSL HTTP/1.1 Connector on port 8080
    -->
    <Connector port="8080" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               redirectPort="8443" />
    <!-- A "Connector" using the shared thread pool-->
    <!--
    <Connector executor="tomcatThreadPool"
               port="8080" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               redirectPort="8443" />
    -->           
    <!-- Define a SSL HTTP/1.1 Connector on port 8443
         This connector uses the JSSE configuration, when using APR, the 
         connector should be using the OpenSSL style configuration
         described in the APR documentation -->
    <!--
    <Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true"
               maxThreads="150" scheme="https" secure="true"
               clientAuth="false" sslProtocol="TLS" />
    -->

    <!-- Define an AJP 1.3 Connector on port 8009 -->
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />


    <!-- An Engine represents the entry point (within Catalina) that processes
         every request.  The Engine implementation for Tomcat stand alone
         analyzes the HTTP headers included with the request, and passes them
         on to the appropriate Host (virtual host).
         Documentation at /docs/config/engine.html -->

    <!-- You should set jvmRoute to support load-balancing via AJP ie :
    <Engine name="Catalina" defaultHost="localhost" jvmRoute="jvm1">         
    --> 
    <Engine name="Catalina" defaultHost="localhost">

      <!--For clustering, please take a look at documentation at:
          /docs/cluster-howto.html  (simple how to)
          /docs/config/cluster.html (reference documentation) -->
      <!--
      <Cluster className="org.apache.catalina.ha.tcp.SimpleTcpCluster"/>
      -->        

      <!-- The request dumper valve dumps useful debugging information about
           the request and response data received and sent by Tomcat.
           Documentation at: /docs/config/valve.html -->
      <!--
      <Valve className="org.apache.catalina.valves.RequestDumperValve"/>
      -->

      <!-- This Realm uses the UserDatabase configured in the global JNDI
           resources under the key "UserDatabase".  Any edits
           that are performed against this UserDatabase are immediately
           available for use by the Realm.  
      <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
             resourceName="UserDatabase"/>
      -->

      <Realm className="org.apache.catalina.realm.JDBCRealm"
             driverName="com.mysql.jdbc.Driver"
             connectionURL="jdbc:mysql://localhost:3306/tomcat_realm"
             connectionName="realm_access" connectionPassword="realmpass"
                userTable="tomcat_users" userNameCol="user_name" userCredCol="password"
                userRoleTable="tomcat_users_roles" roleNameCol="role_name" />


      <!-- Define the default virtual host
           Note: XML Schema validation will not work with Xerces 2.2.
       -->
      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true"
            xmlValidation="false" xmlNamespaceAware="false">

        <!-- SingleSignOn valve, share authentication between web applications
             Documentation at: /docs/config/valve.html -->
        <!--
        <Valve className="org.apache.catalina.authenticator.SingleSignOn" />
        -->

        <!-- Access log processes all example.
             Documentation at: /docs/config/valve.html -->
        <!--
        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"  
               prefix="localhost_access_log." suffix=".txt" pattern="common" resolveHosts="false"/>
        -->

      </Host>
    </Engine>
  </Service>
</Server>

```[B]httpd.conf:
[/B]```
pete@ubuntu:/$ cat /etc/apache2/httpd.conf
#Load mod_jk module
LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so
# Where to find workers.properties
JkWorkersFile /etc/apache2/workers.properties
# Where to put jk logs
JkLogFile /var/log/httpd/mod_jk.log
# Set the jk log level [debug/error/info]
JkLogLevel info
# Select the log format
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
# JkOptions indicate to send SSL KEY SIZE,
JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories
# JkRequestLogFormat set the request format
JkRequestLogFormat "%w %V %T"
# Send servlet for context /docs to worker named tomcat1
JkMount /docs/* tomcat1
#set thispath to match your local state directory or logs directory
JkShmFile     /var/log/httpd/mod_jk.shm

```I hope somebody can point me in the right direction, my head may asplode otherwie :(

Cheers in advance.

---

### Post by Thyagaraj on 2011-06-12
I know it's a late response and I'm trying if I could help you as I have already setup apache tomcat with mod_jk.

You did not tell me what site you are accessing, is the root directory for jsp is under tomcat_home/webapps?

Did you do virtual hosting in both apache and tomcat and if not here is the example of both:

apache2.conf virtual hosting:
```

<VirtualHost *:80>
ServerName station1.mydomain.com
DocumentRoot /usr/share/tomcat/webapps/myapps
        JkMount /* tomcat1
        JkUnMount /*.html tomcat1
</VirtualHost>

```

Tomcat server.xml virtual hosting example:

```

--------------------
----------------
------------
</Host>


<Host name="station1.mydomain.com" debug="0" appBase="webapps" unpackWARs="true">
<Logger className="org.apache.catalina.logger.FileLogger"
directory="logs" prefix="virtual_log1." suffix=".log" timestamp="true"/>
<Context path="" docBase="/usr/share/tomcat/webapps/myapps" debug="0" reloadable="true"/>
</Host>


    </Engine>
  </Service>
</Server>

```

Restart apache and tomcat

If you just want to check whether apache and tomcat are working on the port 80, just try or cross check with this link
[http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html]("http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html")

---

### Post by hawkmage on 2011-06-13
Personal I prefer to use mod_proxy_ajp with mod_proxy and mod_proxy_balancer instead of mod_ajp.  Mod_proxy_ajp is much easier to configure than the mod_ajp.

---

