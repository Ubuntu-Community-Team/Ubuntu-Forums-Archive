---
title: "Is it possible to run two Tomcat servers (one on 8080 and other on 9090)"
date: 2007-05-29
forum: Server Platforms
---

### Post by ishaqmalik on 2007-05-29
Hello

         Is it possible that I could run to separate tomcat servers on different ports on the same machine e.g. one of them running on 8080 and the other on 9090?

Regards,

---

### Post by craigp84 on 2007-05-29
Yes. Setup each instance's server.xml appropriately.

-c

---

### Post by ishaqmalik on 2007-05-30
Hi,

       Well that's what I thought, I have replaced every instance of '8080' with '9090' in server.xml (inside conf dir of tomcat), and restarted the server, here's the out put:

```
[root@servername bin]# ./startup.sh
Using CATALINA_BASE: /usr/bin/tomcat
Using CATALINA_HOME: /usr/bin/tomcat
Using CATALINA_TMPDIR: /usr/bin/tomcat/temp
Using JRE_HOME: /usr/bin/j2sdk1.4.2_06
```

However, when I try to access localhost:9090 it says 'Connection Refused'. Below is my server.xml

```
<!-- Note:  A "Server" is not itself a "Container", so you may not
     define subcomponents such as "Valves" at this level.
     Documentation at /docs/config/server.html
 -->
<Server port="8005" shutdown="SHUTDOWN">

  <!--APR library loader. Documentation at /docs/apr.html -->
  <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />
  <!--Initialize Jasper prior to webapps are loaded. Documentation at /docs/jasper-howto.html -->
  <Listener className="org.apache.catalina.core.JasperListener" />
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
    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
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
         Define a non-SSL HTTP/1.1 Connector on port 9090
    -->
    <Connector port="9090" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               redirectPort="8443" />
    <!-- A "Connector" using the shared thread pool-->
    <!--
    <Connector executor="tomcatThreadPool"
               port="9090" protocol="HTTP/1.1" 
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
    <Engine name="Standalone" defaultHost="localhost" jvmRoute="jvm1">         
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
           available for use by the Realm.  -->
      <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
             resourceName="UserDatabase"/>

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
```

Any ideas where I have gone wrong?

Regards,

---

### Post by craigp84 on 2007-05-30
See the catalina.out, it'll probably complain about not being able to bind to certain ports.

You've changed one set of ports, your mission, should you choose to accept it, is to find out what ports you missed, what they're used for, and report back here why tomcat couldn't start up :)

Google indexes these pages, so do post back the answers (it's easy, honest!).

Hope this helps,

-c

---

### Post by ishaqmalik on 2007-05-31
Nope :), the problem was somewhat more basic... One doesn't have to change the whole set of ports, one has to upgrade the JVM (in my case we were running 1.4.2), I just upgraded it to latest (JDK6) and now everything works fine..

Regards,

---

### Post by craigp84 on 2007-05-31
Does starting up and shutting down each instance work?

Because you have both instance's shutdown connectors set to listen on the default 8005.

Also the SSL enabled connector in the 9090 config is at the default 8443, if the other one is the same you'll get issues.

Read that catalina.out and see what's going on.

Otherwise, you must have already changed the shutdown ports etc?

-c

---

### Post by ishaqmalik on 2007-06-01
yes, there are problems with shutdown, it shuts down both servers implicitly... However, I have configured my applications to run on the same server, and so the initial requirement for running two Tomcats has been resolved...

I don't know if changing the startup and shutdown ports would be enough, I guess there would be some changes to startup.sh and shutdown.sh as well, however I am not totally sure of that...

Regards,
MI

---

