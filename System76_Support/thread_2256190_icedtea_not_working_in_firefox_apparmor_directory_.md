---
title: "icedtea not working in firefox apparmor directory denied"
date: 2014-12-10
forum: System76 Support
---

### Post by riomacho on 2014-12-10
I purchased a System76 Kudu Professional laptop in July.  My only issue so far was that I need Java to access my online banking site in Costa Rica. I installed Java 7 jdk using the software center, but the browser did not recognize the plugin at the bank. 

I tested the installation here [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)  and got the same error, when verifying java only a blank screen (nothing happened)  I purged and reinstalled java several times with no luck.  

I was able to find what the error was using the system logs in terminal: 
```
tail -f /var/log/syslog 
```

Then I found this message: 

```
Dec 10 11:53:53 russell : IcedTea-Web c-plugin - for more info see itweb-settings debug options or console. See http://icedtea.classpath.org/wiki/IcedTea-Web#Filing_bugs for help.
Dec 10 11:53:53 russell : IcedTea-Web c-plugin error manual log:
Dec 10 11:53:53 russell : Failed to create data directory /run/user/1000/icedteaplugin-russell-XXXXXX, Permission denied
```

There were also several messages like :
```
Dec 10 11:53:53 russell kernel: [ 1082.039640] type=1400 audit(1418234033.910:82): apparmor="DENIED" operation="ptrace" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" pid=3166 comm="firefox" requested_mask="read" denied_mask="read" peer="unconfined"

```

I searched for instructions about using app armor and found this line in the readme at /etc/apparmor.d/local README

```

# For example, if the shipped /etc/apparmor.d/usr.sbin.smbd profile has:
#   #include <local/usr.sbin.smbd>
#
# then an administrator can adjust /etc/apparmor.d/local/usr.sbin.smbd to
# contain any additional paths to be allowed, such as:
#
#   /var/exports/** lrwk,
```

So I tried the following:
```
sudo nano /etc/apparmor.d/local/usr.bin.firefox
```

I added this line to the file:
```
/run/user/1000/** lrwk,
```

Then:
```
sudo /etc/init.d/apparmor restart
```

This worked, and now I get the pop up window asking for permission to run the applet at Java.com  

My only doubt is about the /run/user/1000/**  permissions, I used lrwk  just like in the example and I would wonder if that is too permissive or just right.

---

### Post by riomacho on 2014-12-13
When I closed the browser and reopened it, the error came back.  Running 
```
sudo /etc/init.d/apparmor restart
```
Fixed the problem.  Now I have restarted the computer and the plugin works as expected straightaway.

---

