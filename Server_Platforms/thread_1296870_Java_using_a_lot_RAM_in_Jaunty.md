---
title: "Java using a lot RAM in Jaunty"
date: 2009-10-21
forum: Server Platforms
---

### Post by Krijk on 2009-10-21
On of my servers (jaunty with GUI) is using a lot of Java.

According to top it uses 1200m. 
I don't use any heavy Java-applications that I'm aware of. I run tomcat for an administrative interface that I hardly ever use. How can I find out what it is using it?

---

### Post by linux-hack on 2009-10-21
you can controle the resorces for a process with **nice **and **renice**

---

### Post by gabore on 2009-10-24
For me netbeans (6.7.1) gets really sluggish after some time, then I check the running processes with System Monitor and it shows >600MB. How could I use [COLOR="DeepSkyBlue"]nice[/COLOR] or [COLOR="RoyalBlue"]renice[/COLOR] to prevent that amount of java usage? I know that for eclipse there was a startup parameter to set the ram allocation maximum, but that was on win and a really long time ago.

Okay, I figured it was an -Xmx option for setting the heap-size for eclipse, and there is the option to use it for Netbeans, too, in the etc/netbeans.conf file in the netbeans installation directory.  I wonder how should it be set though - very big (like 600m) or very small (like 128m or less)...

---

