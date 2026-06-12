---
title: "Apache + Mod_jk + Tomcat"
date: 2011-03-29
forum: Server Platforms
---

### Post by steryd_net on 2011-03-29
Hello, I've been trying to configure Tomcat to work with apache serwer, but with no effect. I tried different configurations and can't figure out what is wrong. This is my actual configuration:
/etc/apache2/mods-enabled/jk.conf
```
JkMount /*.jsp ajp13_worker
JkMount /*/servlet/ ajp13_worker
```/etc/apache2/httpd.conf
```
JkWorkersFile    /etc/libapache2-mod-jk/workers.properties
JkLogFile     /var/log/apache2/mod_jk.log
JkLogLevel     info
JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories
JkRequestLogFormat "%w %V %T" 
```/etc/libapache2-mod-jk/workers.properties
```
workers.tomcat_home=/usr/share/tomcat6
workers.java_home=/usr/lib/jvm/java-gcj
ps=/
worker.list=ajp13_worker
worker.ajp13_worker.port=8009
worker.ajp13_worker.host=localhost
worker.ajp13_worker.type=ajp13
worker.ajp13_worker.lbfactor=1
worker.loadbalancer.type=lb
worker.loadbalancer.balance_workers=ajp13_worker
```/etc/tomcat6/server.xml
```
<?xml version='1.0' encoding='utf-8'?>
<Server port="8004" shutdown="SHUTDOWN">
  <Listener className="org.apache.catalina.core.JasperListener" />
  <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
  <Listener className="org.apache.catalina.mbeans.ServerLifecycleListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />

  <GlobalNamingResources>
    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
  </GlobalNamingResources>
  <Service name="Catalina">

    <!-- Define an AJP 1.3 Connector on port 8009 -->
    
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
    

    <Engine name="Catalina" defaultHost="localhost">
      <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
             resourceName="UserDatabase"/>
      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true"
            xmlValidation="false" xmlNamespaceAware="false">

      </Host>
    </Engine>
  </Service>
</Server>
```

Please help.

---

### Post by hawkmage on 2011-03-29
Personally I prefer to use mod_proxy, mod_proxy_ajp and mod_proxy_balancer.  

By using a few simple lines in your Apache config you can front Tomcat with Apache.
First you need to include the modules:
```
LoadModule proxy_module modules/mod_proxy.so
LoadModule ajp_module modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
```

Then you define what you want to pass to Tomcat:
```
<Location />
    ProxyPass balancer://tomcat/ stickysession=JSESSIONID|jsessionid
</Location>
```

Then you define the proxy balancer:
```
<Proxy balancer://tomcat>
    BalancerMember ajp://localhost:8009 route=jvmRoute smax=5 max=20 ttl=120 retry=300
</Proxy>
```
The "route=jvmRoute" would be used if you are balancing between multiple Tomcat instances and you would replace the "jvmRoute" with the value of the jvmRoute element in the Engine element from the server.xml.

---

