---
title: "Tomcat 6 help"
date: 2008-11-12
forum: Server Platforms
---

### Post by Lex-Man on 2008-11-12
I've installed Tomcat 6.

I want to set up netbeans to run with Tomcat 6 but I can't find the Catalina home. Where is the base file located.

Also I'm not sure I've set it up right.

---

### Post by praxis1949 on 2008-12-06
Try "usr/share/tomcat6" if you loaded Tomcat from outside of Ubuntu. I fear that the Netbeans version from Ubuntu does not work with Tomcat (but the Windows version does). Could be wrong but...

Regards

John S

---

### Post by praxis1949 on 2008-12-06
I was wrong about Netbeans, but you have to install plug ins from within Netbeans. Watch for permission problems with your Tomcat files (i.e. mine were owned by "Root" and invisible (in effect) to Netbeans.)

---

