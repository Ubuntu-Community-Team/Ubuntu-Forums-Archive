---
title: "&quot;sudo&quot; user not find JDK"
date: 2010-03-30
forum: Server Platforms
---

### Post by Archimede on 2010-03-30
Dear Forum,
i have Ubuntu 9.10 with JDK 1.6 and Eclipse Galileo installed. All work good. I have see, when i by terminal start Tomcat or Eclipse ("/opt/apache-tomcat..." and "/opt/eclipse/...") all work good. I have see, when i make this action with "sudo" user ("sudo /opt...") i see an error message; by this message, is not possible my JDK find. Is this normal? Why, with "sudo" user, is not possible my JDK find, and without "sudo" all work good? I post here the error message. Very very thank. 


With Eclipse (i see this in popup)
```

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/opt/eclipse/jre/bin/java
java in your current PATH

```With Tomcat (i see this in terminal)
```

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```

---

