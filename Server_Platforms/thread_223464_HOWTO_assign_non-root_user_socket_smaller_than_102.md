---
title: "HOWTO assign non-root user socket smaller than 1024"
date: 2006-07-26
forum: Server Platforms
---

### Post by BrianB2 on 2006-07-26
Sorry if this is an old question, but I've really tried hard to find the solution. It is difficult for me to think of search terms that cover my question without also hitting loads of irrelevant stuff.

I've used tomcat for years, but only with a manual install and running it as root. I've just installed the package on my new 6.06 system with synaptic. This version runs chrooted as a system user called tomcat5.

When I configure server.xml to listen on port 8080, it works fine. However, I want/need it to run as a standalone web server (i.e. without an apache front-end) by listening on port 80. In this case, it fails with java.netBindException: Permission denied:80.

I realise that processes running as root are allowed to open any socket number smaller than 1024. I also realise that some programs have special configurations for opening/using their specific sockets while chrooted (e.g. mysql, hamachi).

Is there a general technique for assigning permission to a non-root user for access to a specific port or set of ports below the 1024 "water line", or am I dealing with a specific tomcat deficiency or configuration issue?

---

### Post by killernurd on 2006-07-27
Actually, it's generally safer to let Apache handle the front end. For that matter, it's also generally less of a pain to let Apache handle the front, since you have a little more control over what servlets are available where.

I suppose that if you really wanted to, you could change Tomcat's ownership and permissions, but I couldn't say where (I use the Apache method).

---

### Post by LordHunter317 on 2006-07-27
There is no general way.

---

### Post by Gustavo Orair on 2006-09-26
The rigth way to create these permissions are creating a file your-webapp.policy and puting this on /etc/tomcat5/policy.d/ then restarting the Tomcat.
When you do this you will note that the content of this file will be concatenated on catalina.policy (/usr/share/tomcat5/conf/catalina.policy).
To know how to create the content of this file you can access the Tomcat documentation or try to get the idea from the files already existing on /etc/tomcat5/policy.d/ directory!!!

---

