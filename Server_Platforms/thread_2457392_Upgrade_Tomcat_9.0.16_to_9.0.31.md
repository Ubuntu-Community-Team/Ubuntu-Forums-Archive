---
title: "Upgrade Tomcat 9.0.16 to 9.0.31"
date: 2021-02-01
forum: Server Platforms
---

### Post by LeBabe on 2021-02-01
Hi,

I'm using Tomcat 9.0.16 on and Ubuntu 18.04.

This morning a threat analyzer triggered an alert asking to upgrade to 9.0.31 because a critical issue.

Unfortunately 18.04 does not seems to have natively tomcat 9.0.31 repo. (Whereas 20.04 have it)

What is the best and simplest way to get this upgrade without killing the current conf.

I found the sources on Tomcat website  but I don't know how to compile it correctly to match the Ubuntu repo default settings.

Many thanks by advance for any help.

---

### Post by ajgreeny on 2021-02-01
I can not help you with 18.04, but 20.04, if you are able to upgrade, has tomcat 9.0.31, the version you need.

---

### Post by LeBabe on 2021-02-01
I know that 20.04 has the right version. But I can't upgraded the to server to 20.04 without taking risk to break other services.

So I have to stay on 18.04. 

Then 18.04 is an LTS, 9.0.31 is one year old, the last stable release is 9.0.40. As 9.0.31 correct a sever issue, why there is no package for this?

---

### Post by howefield on 2021-02-01
> **LeBabe said:**
> Then 18.04 is an LTS, 9.0.31 is one year old, the last stable release is 9.0.40. As 9.0.31 correct a sever issue, why there is no package for this?

When Ubuntu release a new version, the repository packages are frozen to those versions at time of release. They will get security updates but not version updates. That being said there are a few packages such as Firefox which do get version updates, there may be one or two more but those are the exception to the rule.

Might be that a PPA is your best bet given you cannot upgrade to 20.04.

---

### Post by ajgreeny on 2021-02-01
A PPA repository was my first thought but I did not find one in my fairly quick search using my own CSE search engine at Google which you're very welcome to use if it might help.
Give it a try at [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao)

---

### Post by LeBabe on 2021-02-02
Hi, 

But this is a security issue. 

[https://ubuntu.com/security/CVE-2020-1938](https://ubuntu.com/security/CVE-2020-1938)

They talked about patches on this site but I don't know if they are related to the 9.0.31 or if we have to apply them to be at the same level of security as 9.0.31

---

### Post by LeBabe on 2021-02-11
Hi,

I found a way to update my server to 9.0.41 without updating Ubuntu to 20.04.
The solution is easy to apply but it has been hard to find as I did nearly not found any info about how upgrading this product.

This solution is working for a migration from 9.x to 9.x on Ubuntu server.

So this is how I did it : 
-Download and deflate required package here : [https://tomcat.apache.org/download-90.cgi](https://tomcat.apache.org/download-90.cgi) (For a 9.x)
-Stop tomcat
-Copy apache-tomcat-9.0.41/lib/* to /usr/share/tomcat9/lib/
-Copy apache-tomcat-9.0.41/bin/*.jar /usr/share/tomcat9/bin/
-Start your tomcat server and everyhting should be OK.

That's all. 

I hope this will help someone else later.

Bye.

---

