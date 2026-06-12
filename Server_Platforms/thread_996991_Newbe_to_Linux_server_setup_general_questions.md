---
title: "Newbe to Linux server setup general questions"
date: 2008-11-29
forum: Server Platforms
---

### Post by wlbragg on 2008-11-29
Ubuntu 8.10 -(Intrepid Ibex)
Apache 2. mod-jk
Tomcat 6  jdbc
PHP5
MySQL

Amazing software installation system in Ubuntu but leads to questions.

I have a fairly advanced ajax (DWR) app that ran well in Windows using almost identical server software. I just moved the files over and changed some paths and it all works except the DWR calls. In Windows I had to install and configure jk-connector (workers.properties) to send everything to Tomcat except php. In Ubuntu it seemed to handle the configuration and just sends the java to Tomcat automatically.
 I tried a test program I had made using ajax calls through HTML/JS to a server side PHP file pulling data out of the same MySql database the DWR program is using and it worked fine. So I think the problem is with the DWR servlet. 
The DWR.jar file is placed in the WEB-INF folder but I think the program isn't finding the class. Does anyone have any experience with this and maybe help me out?

Any help greatly appreciated!

---

### Post by wlbragg on 2009-02-22
This question has been SOLOVED It wasn't a Servlet issue at all. It was an entirely different issue that was masking as a DWR problem.

---

### Post by gnicko on 2009-02-27
Well....now that you've "SOLOVED" your problem, how about sharing the "SOLOUTION" with the rest of us--just in case someone else is having the same problem but doesn't know how to fix it??

Thanks!

---

### Post by wlbragg on 2009-02-27
Sorry, I would have posted more but it didn't really apply as it wasn't a servlet problem at all. But for continuities sake the solution to the real problem which was a dbcp connector problem

[http://ubuntuforums.org/showthread.php?p=6779005](http://ubuntuforums.org/showthread.php?p=6779005)

What I first saw was my DWR servlet just hung with no error messages at all. Least none I could find. What clued me in was when I made commons-logging.jar visible to the app it allowed the program to continue execution to the underlying dhcp problem. There never was a servlet or DWR problem other than commons-logging.jar was not seen by the app. Commons.logging.jar was put into TOMCAT_HOME/lib

---

