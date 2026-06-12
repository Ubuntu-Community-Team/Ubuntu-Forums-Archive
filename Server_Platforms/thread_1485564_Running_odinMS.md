---
title: "Running odinMS"
date: 2010-05-17
forum: Server Platforms
---

### Post by clone11 on 2010-05-17
I'm having a bit of trouble getting it running, I think it's releated to java not finding the jar files
```
CLASSPATH=".:dist/arberms.jar:dist/mina-core.jar:dist/slf4j-api.jar:dist/slf4j-jdk14.jar:dist/mysql-connector-java-bin.jar"
export CLASSPATH
java -Darberms.recvops=config\recvops.properties \
-Dnet.sf.odinms.sendops=config\sendops.properties \
-Dnet.sf.odinms.wzpath=wz \
-Djavax.net.ssl.keyStore=filename.keystore \
-Djavax.net.ssl.keyStorePassword=passwd \
-Djavax.net.ssl.trustStore=filename.keystore \
-Djavax.net.ssl.trustStorePassword=passwd \
-Xmx150M \
net.sf.odinms.net.world.WorldServer
```

That's the orginal start up, it throws and error saying "': not a valid identifierexport: `CLASSPATH", i've changed it to -classpath ".:dist/arberms.jar:dist/mina-core.jar:dist/slf4j-api.jar:dist/slf4j-jdk14.jar:dist/mysql-connector-java-bin.jar", and that just says command not found. Sorry if this is the wrong section, was not sure where to post this.

FIXED - I was saving the file in DOS format and it wasn't parsing right.

---

