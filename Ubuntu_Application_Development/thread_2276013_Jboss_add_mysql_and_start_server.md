---
title: "Jboss add mysql and start server"
date: 2015-04-29
forum: Ubuntu Application Development
---

### Post by cdb10 on 2015-04-29
I cannot configure Jboss. I want to add module MySQL to  JBoss.
 There is a written in my handbook that I have add the following lines:
```

<subsystem xmlns="urn:jboss:domain:darasource:1.0">
    <datasources>
        <datasource jta="false" jndi-name="java:jboss/datasource/jbossas7development" pool-name="jbossas7development" enabled="true">
            <connection-url>
                jdbc:mysql://localhost:3306/ticketsystem
            </connection-url>
            <driver-class>com.mysql.jdbc.Driver</driver-class>
            <driver>mysql</driver>
            <security>
                <user-name>jboss</user-name>
                <password>jboss</password>
            </security>
        </datasource>
        <drivers>
            <driver name="mysql" module="com.mysql"/>
        </drivers>
    </datasources>
</subsystem>

```
I have a proper file structure:
```

pioflor@pioflor-IdeaPad-S210-Touch:~$ cd wildfly-8.0.0.Final/modules/com/mysql/main/
pioflor@pioflor-IdeaPad-S210-Touch:~/wildfly-8.0.0.Final/modules/com/mysql/main$ ls
module.xml  mysql-connector-java-5.1.35-bin.jar
pioflor@pioflor-IdeaPad-S210-Touch:~/wildfly-8.0.0.Final/modules/com/mysql/main$ cat module.xml 
<module xmlns="urn:jboss:module:1.0" name="com.mysql">
        <resources>
                <resource-root path="mysql-connector-java-5.1.35-bin.jar"/>
        </resources>
        <dependencies>
                <module name="javax.api"/>
                <module name="javax.transaction.api"/>
        </dependencies>
</module>pioflor@pioflor-IdeaPad-S210-Touch:~/wildfly-8.0.0.Final/modules/com/mysql/main$

```
But when I run ./standalone.sh, I see in the console:
```

23:31:45,324 ERROR [org.jboss.as.server] (Controller Boot Thread) JBAS015956: Caught exception during boot: org.jboss.as.controller.persistence.ConfigurationPersistenceException: JBAS014676: Failed to parse configuration
        at org.jboss.as.controller.persistence.XmlConfigurationPersister.load(XmlConfigurationPersister.java:112) [wildfly-controller-8.0.0.Final.jar:8.0.0.Final]
        at org.jboss.as.server.ServerService.boot(ServerService.java:331) [wildfly-server-8.0.0.Final.jar:8.0.0.Final]
        at org.jboss.as.controller.AbstractControllerService$1.run(AbstractControllerService.java:256) [wildfly-controller-8.0.0.Final.jar:8.0.0.Final]
        at java.lang.Thread.run(Thread.java:745) [rt.jar:1.8.0_31]
Caused by: javax.xml.stream.XMLStreamException: ParseError at [row,col]:[157,9]
Message: Unexpected element '{urn:jboss:domain:darasource:1.0}subsystem'
        at org.jboss.staxmapper.XMLMapperImpl.processNested(XMLMapperImpl.java:108) [staxmapper-1.1.0.Final.jar:1.1.0.Final]
        at org.jboss.staxmapper.XMLExtendedStreamReaderImpl.handleAny(XMLExtendedStreamReaderImpl.java:69) [staxmapper-1.1.0.Final.jar:1.1.0.Final]
        at org.jboss.as.server.parsing.StandaloneXml.parseServerProfile(StandaloneXml.java:1131) [wildfly-server-8.0.0.Final.jar:8.0.0.Final]
        at org.jboss.as.server.parsing.StandaloneXml.readServerElement_1_4(StandaloneXml.java:458) [wildfly-server-8.0.0.Final.jar:8.0.0.Final]
        at org.jboss.as.server.parsing.StandaloneXml.readElement(StandaloneXml.java:145) [wildfly-server-8.0.0.Final.jar:8.0.0.Final]
        at org.jboss.as.server.parsing.StandaloneXml.readElement(StandaloneXml.java:107) [wildfly-server-8.0.0.Final.jar:8.0.0.Final]
        at org.jboss.staxmapper.XMLMapperImpl.processNested(XMLMapperImpl.java:110) [staxmapper-1.1.0.Final.jar:1.1.0.Final]
        at org.jboss.staxmapper.XMLMapperImpl.parseDocument(XMLMapperImpl.java:69) [staxmapper-1.1.0.Final.jar:1.1.0.Final]
        at org.jboss.as.controller.persistence.XmlConfigurationPersister.load(XmlConfigurationPersister.java:104) [wildfly-controller-8.0.0.Final.jar:8.0.0.Final]
        ... 3 more

23:31:45,328 FATAL [org.jboss.as.server] (Controller Boot Thread) JBAS015957: Server boot has failed in an unrecoverable manner; exiting. See previous messages for details.
23:31:45,457 INFO  [org.jboss.as] (MSC service thread 1-1) JBAS015950: WildFly 8.0.0.Final "WildFly" stopped in 11ms
pioflor@pioflor-IdeaPad-S210-Touch:~/wildfly-8.0.0.Final/bin$ ./standalone.sh 



```

---

