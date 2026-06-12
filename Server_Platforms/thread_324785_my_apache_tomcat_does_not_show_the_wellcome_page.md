---
title: "my apache tomcat does not show the wellcome page"
date: 2006-12-24
forum: Server Platforms
---

### Post by ajana_pothik on 2006-12-24
hello everybody,
i am very new in ubuntu family, infact i am very new in linux environment, 
i am trying to install apache tomcat webserver into my machine, 
i installed jdk 1,5 and i also set JAVA_HOME
and i also installed apache tomcat version 5.5.20 and when i run startup.sh command it shows me this output 

Using CATALINA_BASE:   /opt/tomcat
Using CATALINA_HOME:   /opt/tomcat
Using CATALINA_TMPDIR: /opt/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun

which seem to be correnct but when i try [http://localhost:8080](http://localhost:8080) it doesnt show me the 
wellcome page. i also set up classpath for jsp-api.jar and servelt-api.jar.

so anybody please help me, i am looking forward your answer.

---

### Post by ajana_pothik on 2006-12-26
please give me new idea , to install tomcat correctly from the very begining m that will also helpfull for me
bye

---

### Post by bikeboy on 2006-12-26
I don't know tomcat specifically, but is there a config file you could post for us? It might help.

---

### Post by not_cool on 2006-12-26
what about if you just type localhost, without the 8080?

---

### Post by pmasiar on 2006-12-28
IIRC tomcat on ubuntu uses port 8180. check: gedit usr/local/tomcat/conf/server.xml, <Connector port="8080" ... I gathered some resources here: [http://www.ubuntuforums.org/showthread.php?p=1911505](http://www.ubuntuforums.org/showthread.php?p=1911505)

---

