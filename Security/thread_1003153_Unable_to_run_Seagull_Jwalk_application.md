---
title: "Unable to run Seagull Jwalk application"
date: 2008-12-05
forum: Security
---

### Post by barcodenow on 2008-12-05
I've just install Ubuntu Intrepid on a test machine.  I'm a relatively 'green' linux user, but have moderate sco experience.  First experience with Ubuntu.  I'm impressed!

I've had (almost) no problems, even setting up a Verizon Wireless card.  However, when attempting to run a Seagull Jwalk app in firefox, I get the following permissions error(s).

Any suggestions?  Please give relatively complete responses to keep me from googling my mind out!

Thanks in advance!

Java Plug-in 1.6.0_10
Using JRE version 1.6.0_10 Java HotSpot(TM) Client VM
User home directory = /home/tom




----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

Minium Version as specified in html file = 4.79.2424
Sun Microsystems Inc.
LINUX
1.6.0_10
This seems to be a 1.1 browser/viewer!
1.1 Compliant check passed! GO for it
Load : ./jwalkframes.html?jvmven=Sun+Microsystems+Inc.&jvmver=1.6.0_10&msjvmver=0
Version: 4,566,1,101(WJ40C11_RELEASE)
Using lightweight controls
java.security.AccessControlException: access denied (java.util.PropertyPermission user.home read)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:323)
	at java.security.AccessController.checkPermission(AccessController.java:546)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
	at java.lang.SecurityManager.checkPropertyAccess(SecurityManager.java:1285)
	at java.lang.System.getProperty(System.java:652)
	at com.seagullsw.jwalk.c.q.<init>(Unknown Source)
	at com.seagullsw.jwalk.c.s.a(Unknown Source)
	at com.seagullsw.jwalk.ois.JWalkSession.createSession(Unknown Source)
	at com.seagullsw.jwalk.JWalk.a(Unknown Source)
	at com.seagullsw.jwalk.JWalk.createSession(Unknown Source)
	at com.seagullsw.jwalk.JWalk.a(Unknown Source)
	at com.seagullsw.jwalk.JWalk.start(Unknown Source)
	at sun.applet.AppletPanel.run(AppletPanel.java:464)
	at java.lang.Thread.run(Thread.java:619)

---

### Post by jamesstansell on 2008-12-05
A java applet normally is not allowed to read the user.home property.  So either the applet needs to be signed, or possibly you could configure some JRE setting to relax the restriction.

Do the jwalk docs talk about anything like this?

Sorry, to be more complete I'd have to go googling myself. :)

-james.

---

### Post by barcodenow on 2008-12-06
James:

Thanks!  This gives me something to search for!  I had looked at Ubuntu a couple of years ago when it was new.  It's definitely grown up!

---

