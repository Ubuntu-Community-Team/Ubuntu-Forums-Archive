---
title: "Tomcat 5.5 + Eclipse + WDT issues on Edgy"
date: 2006-12-30
forum: Server Platforms
---

### Post by munkay on 2006-12-30
I'm having issues with the tomcat5.5 package from the edgy repo. After installing tomcat5.5 and eclipse and all the necessary stuff, I can't add tomcat5.5 as one of the server runtimes. 

The complaint is that "/usr/share/tomcat5.5/conf cannot be accessed".

Also, starting tomcat5.5 from "/etc/init.d/tomcat5.5 start" results in no error msg.
But running "/etc/init.d/tomcat5.5 status" says "no tomcat running, but found pid".

Any help would be appreciated.

Thanks

---

### Post by pliscante on 2007-02-12
hi,
i had the same problem.
seems to be an error in the config file.
in /etc/default/tomcat5.5 i had the following line:

JAVA_HOME=usr/lib/jvm/java-1.5.0-sun-1.5.0.08

(no absolut path)
i replaced it by 

JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08

and also put after this

export JAVA_HOME

that solved it for me.

philipp

---

