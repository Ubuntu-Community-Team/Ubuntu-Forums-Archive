---
title: "Error with Maven var in environment"
date: 2014-12-16
forum: Ubuntu/Debian BASED
---

### Post by cjsartorif on 2014-12-16
I Have a problem with Apache Maven in EOS Luna, when I run:
 ```
mvn -v 
Error: Could not find or load the main class org.codehaus.plexus.classworlds.launcher.Launcher

```

But if I run the following first:  ```
source /etc/environment
```

Maven works. 
Why /etc/environment is not auto-loaded?

The content of environment file is:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/apache-maven-3.2.3/bin/"
JAVA_HOME="/usr/lib/jvm/java-8-oracle/"
M2_HOME=”/usr/local/apache-maven/apache-maven-3.2.3&#8243;
MAVEN_HOME=”/usr/local/apache-maven/apache-maven-3.2.3&#8243;
M2=”/usr/local/apache-maven/apache-maven-3.2.3/bin”
```

---

