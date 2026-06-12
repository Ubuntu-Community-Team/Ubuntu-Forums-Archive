---
title: "Squirrel with MSSQL"
date: 2009-03-04
forum: Server Platforms
---

### Post by mistypotato on 2009-03-04
Hello :KS

Has anyone setup Squirrel to work wit the MSSQL JDBC driver?

If so, do you know of a good resource (tutorial) for doing that?


thx

---

### Post by kuson on 2011-07-20
You may have found out a solution by now, but here's my contribution:
1. Download & Install from SQuirrel Client (at the moment 3.1.2)-- download the jar file, and run java -jar <install filename>
2. Open the GUI. You will notice the Drivers are all marked X. You will need to configure the MSSQL one by editing it, and fixing the connection string (a matter of putting in the <SERVER> and <DATABASE>), and the most important one is the EXTRA CLASS PATH.
3. You will need to google "MSSQL JDBC DRIVERS" and as attached pix, will go to the Evil Empire's Website. Download the Drivers in the zipped .tar.gz file, and unzip the "sqljdbc4.jar" to where you need it to be. Note I unzipped it to the plugin/mssql directory under my installation directory.
4. From where we left off at #2, press 'add' and point it to the file in #3. And voila, the driver turns from X to "Correct".
5. Now you configure the alias, Add a new one, choose the driver you just configged in #4, put in the username and passwords, and you should be done; Try connecting and you should be done!

---

### Post by marvelousvts on 2012-12-11
thanx!!!):P

---

