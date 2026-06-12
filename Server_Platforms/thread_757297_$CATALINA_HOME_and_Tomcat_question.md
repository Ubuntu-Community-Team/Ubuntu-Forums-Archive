---
title: "$CATALINA_HOME and Tomcat question"
date: 2008-04-16
forum: Server Platforms
---

### Post by AndrewTheArt on 2008-04-16
Hey all - 

I have successfully installed Apache Tomcat 5.5 from the Ubuntu repositories on my school's server machine, and after some minor fixes, it seems to be up and running. 

Typing in [http://localhost:8180](http://localhost:8180), however, produces a blank page. This makes sense though, as there are obviously no files in the Tomcat root directory ($CATALINA_HOME) for the JSP engine to display.

I assumed that /usr/share/tomcat5.5/webapps is the directory that I would put such files, but after dropping some test files in there, obviously my intuition is wrong.

I was reading some forum posts and it seems that installing the tomcat5.5-webapps package sets $CATALINA_HOME to /usr/share/tomcat5.5-webapps for you automatically.

My question is, where the heck is $CATALINA_HOME defined/set by default if you install tomcat5.5 from the repositories? Also, how can I change this default - I can't figure out how to set it statically to a directory of my own choosing.

Thanks!!!!

PS - echoing $CATALINA_HOME from Bash shows nothing.

---

### Post by AndrewTheArt on 2008-04-16
Any ideas? :lolflag:

---

### Post by juan@forum on 2008-04-16
in the source package, it is set on a script called catalina.sh
and it gets executed when you run startup.sh

---

