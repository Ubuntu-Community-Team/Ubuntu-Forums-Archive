---
title: "Resin can't find JAVA_HOME?"
date: 2010-08-21
forum: Server Platforms
---

### Post by Qure on 2010-08-21
Hi,

I've been following the instructions to install Resin, and all seems to go well until I try to run the /bin/httpd.sh file. It simple says:

```
exec: 40: -jar: not found
```I suspected this was something to do with my JAVA_HOME variable not being set, so I looked up how to do this and added it to my /etc/bash.bashrc file. Saying "echo $JAVA_HOME" does indeed return the correct path so I don't think this is the problem.

Am I missing something else?

Thanks

---

### Post by Qure on 2010-08-22
I've tried getting a different version of Resin and even installed Java and set up JAVA_HOME again, but I'm still getting the same message mentioned above...

I'm not convinced the "make install" part worked correctly because it happens in a split second, unlike the "./configure" and "make" commands. So, when running "/usr/local/resin/resin-4.0.9/bin/httpd.sh" I still get 
```
exec: 40: -jar: not found
```

Can anyone think what this might be?

---

### Post by madverb on 2010-08-22
So JAVA_HOME is pointing to /usr/bin ?

---

### Post by Qure on 2010-08-22
> **madverb said:**
> So JAVA_HOME is pointing to /usr/bin ?

I've had it pointing to "/usr/bin", "/usr/lib/jvm/java-6-sun", "/usr/lib/jvm/java-6-sun-1.6.0.20", even tried the /bin/ folders inside those too, but always the same result. 

I logged out and in again between those changes.

It's this really a Java issue, or maybe something else? It's resin-3.1.9 I'm using if this helps

---

### Post by Qure on 2010-08-27
Is there another section on these forums where I should try asking this question? Maybe I'm in the wrong place...

Thanks

---

### Post by madverb on 2010-08-27
I know what your problem is. I am pretty sure there are some configuration files you need to modify. It's in the instructions for setting up Resin. Make sure you read through the instructions properly.
I think there is a file called 'profile' under the resin directory. You need to change some small bits at the start of the file.
Should look something like this:
```
# Java Location
JAVA_HOME=/<installdir>/jdk1.4
export JAVA_HOME
```

---

