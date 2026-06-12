---
title: "apt-get install tomcat7 - what about java?"
date: 2014-06-05
forum: Server Platforms
---

### Post by Danny_R on 2014-06-05
After a few issues with a previous install of Server 12.04. i flattened the server an reinstalled 12.04

i ran 

```
apt-get install tomcat7
```

aswell as 

```

apt-get install default-jre 
apt-get install default-jdk
```

im trying to install another application (Queuemetrics) within its install guide it mentions

> 
[LIST]
[*] Complete the set-up
  update-alternatives --install /usr/bin/java java /opt/jre1.7.0_40/bin/java 
[/LIST]


but i dont know where the java "stuff" went to when i automatically installed it with apt-get install etc...

Basically how do i set the environment config to java

does this all make sense!?

thanks

---

### Post by slickymaster on 2014-06-05
Moved to the **Server Platforms** sub-forum.

Edit the system Path file **/etc/profile**
```
gksudo gedit /etc/profile
```Add following lines in end```
JAVA_HOME=/usr/lib/jvm/<your version of java>
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export JRE_HOME
export PATH
```

---

