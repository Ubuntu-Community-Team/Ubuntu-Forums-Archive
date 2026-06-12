---
title: "Ultra5 Java/Flash Questions"
date: 2007-08-15
forum: Sun Sparc Users
---

### Post by mthornto88 on 2007-08-15
I recently installed Dapper on my Sparc Ultra 5. Everything works great except a few things. I was hoping to get the forums opinion on things. It seems there is no java for this version of Linux. The Blackdown java project has stopped a while ago. So what are people using for Java? Java is a big deal and there must be something I am missing. It doesn't look like Sun is porting over a version for linux and sparc as well.

Also, what are people using for flash support? Adobe doesn't have a plugin for sparc at this time either. 

Thanks...

---

### Post by mthornto88 on 2007-08-17
No one has any information?? What are people doing for Java?? Or do they not need it?

---

### Post by psychicist on 2007-08-17
They don't do anything because they are all on x86 :).

I have ported Slackware 12.0 to MIPS and the company that released the computer containing the Loongson processor has managed to port JDK 1.5 to MIPS and they are porting 1.6 now. They have also ported OpenOffice.org. I am at the moment porting Slackware 12.0 to SPARC and I hope to be able to rework their Java MIPS patch for SPARC. I will probably have to gain some SPARC assembly knowledge for that so don't expect too much too soon :).

For Flash there is nothing but Gnash but it doesn't work yet, not even 0.8.0 on MIPS at least. There is nothing that can be done about this except for improving Gnash or abandoning Flash altogether.

---

