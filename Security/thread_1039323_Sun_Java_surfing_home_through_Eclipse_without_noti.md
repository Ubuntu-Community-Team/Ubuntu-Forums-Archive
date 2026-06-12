---
title: "Sun Java surfing home through Eclipse without notifying the user"
date: 2009-01-14
forum: Security
---

### Post by Percolator on 2009-01-14
I hava Interpid Ibex installed and through apt-get installed sun-java6-jdk, sun-java6-doc and eclipse (actually Build id: M20070212-1330 (Ubuntu version: 3.2.2-5ubuntu2)). (I downloaded the jdk-6u10-docs.zip file, renamed it, copied it to /tmp and so on so it was well installed.)

Now when I turn on EtherApe and Wireshark I noticed that my computer was going to the Sun website (72.5.124.55) for no apparent reason. First I thought I had cought Sun red handed doing a plain call home secretely transmitting personal data but maybe it's more harmless, I'm not sure. Anyway what causes the connection in this case is auto-complete in Eclipse.

Now my question is, why is my Eclipse secretely going to the Sun website instead of looking at locally installed documentation so should I report this as a bug?

Also, how do I fix this and stop Eclipse from going to the Sun website and only look at local information?

---

### Post by andrewc6l on 2009-01-14
Eclipse will go to the web for javadoc if yours isn't set up right. See [https://bugs.eclipse.org/bugs/show_bug.cgi?id=117740](https://bugs.eclipse.org/bugs/show_bug.cgi?id=117740) for more details.

The workaround is to attach source or delete the javadoc location of rt.jar. (Alternately, you could block java.sun.com in your /etc/hosts file, but that seems a bit extreme.)

---

### Post by Percolator on 2009-01-27
Thanks for your reply Andrew. Apparently there is another post related to my problem and gave me the solution, it's the same solution but more elaborate:
       [http://ubuntuforums.org/showthread.php?t=851678](http://ubuntuforums.org/showthread.php?t=851678)



In Eclipse, go to Window / Preferences / Java / Installed JREs.

Click on the installed JRE and click Edit...

Select rt.jar from the list and click Javadoc Location...;

And then make it point to the API-docs.


A pitty apt-get wasn't smart enough to do that for me :D

---

