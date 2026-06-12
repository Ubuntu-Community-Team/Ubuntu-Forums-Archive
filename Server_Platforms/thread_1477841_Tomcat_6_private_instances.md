---
title: "Tomcat 6 private instances"
date: 2010-05-09
forum: Server Platforms
---

### Post by tonabnehmer on 2010-05-09
Hello,

I was install Tomcat 6 "apt-get install tomcat6-user" on a multi user host and the users can create their own instances via "tomcat6-instance-create my-instance".

I have a few questions about the instances:

[LIST=1]
[*]Do the private instances realy run in fully independent JVMs?
[*]If one instance for example receives a heap space error or crashes, will the other instances be fine?
[*]How can I make sure that one private instance dosn't allocate all the available memory of the machine? As far as I understood, the user can configure JAVA_OPTS="-Xmx<too much memory>" in bin/setenv.sh. Can I set a quota or do I need to ask them to be fair?
[*]Are there any other things which I need to keep an eye of when running a multi user Tomcat host?
[/LIST]
Thank you very much!
tonabnehmer

---

### Post by tonabnehmer on 2010-05-12
anyone?

---

