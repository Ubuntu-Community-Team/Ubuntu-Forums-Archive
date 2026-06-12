---
title: "Error Installing Tomcat 6"
date: 2007-06-12
forum: Server Platforms
---

### Post by codefinder on 2007-06-12
Hi Guys,

I am trying to install Tomcat 6 as per the following guide:

[http://ubuntuforums.org/showthread.php?p=2561912]("http://ubuntuforums.org/showthread.php?p=2561912")


I have downloaded Tomcat and when I run the following command:

**[COLOR="Red"]sudo tar zxvf apache-tomcat-6.0.13.tar.gz[/COLOR]**

I get this:

[COLOR="Red"]tar: apache-tomcat-6.0.13.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/COLOR]

Hope someone can help. Thanks in advanced.

---

### Post by AlexThomson_NZ on 2007-06-12
Well that error is saying that is can't find the file apache-tomcat-6.0.13.tar.gz

Can you confirm that is it in the directory you are running this from, and appears EXACTLY as apache-tomcat-6.0.13.tar.gz?

---

