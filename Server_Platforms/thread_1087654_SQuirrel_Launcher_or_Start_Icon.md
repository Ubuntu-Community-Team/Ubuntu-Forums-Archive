---
title: "SQuirrel Launcher or Start Icon"
date: 2009-03-05
forum: Server Platforms
---

### Post by mistypotato on 2009-03-05
Hello,

I installed SQuirrel and it works but it didn't install any way to start it and it's a booger to launch.

How would I create a launch icon for this application which is a jar file?

Currently, the only way I can start it is navigate to the folder it is in which it is located
**/usr/local/SQuirrel\ SQL\ Client/**
and run THIS command.........
**java -jar squirrel-sql.jar**


thx

---

### Post by JanvL on 2009-03-07
Hi I have the same problem.

The spaces in the Directory-name brake the .sh file.
Maybe someone can give a hint what to do so bash accepts these spaces.

Jan

---

### Post by mistypotato on 2009-03-07
I'm still experimenting with this.

If we could ONLY get someone with a desktop Icon to give us the link code for that icon we'd be set.

The lack of responses might indicate we're gonna have to come up with a launch icon all on our own.  <biting nails>

---

### Post by hansdown on 2009-03-07
Good news guys.

The developer has a site that should help.

[http://www.nabble.com/Re:-Launcher-Icon-in-Ubuntu--p20784174.html](http://www.nabble.com/Re:-Launcher-Icon-in-Ubuntu--p20784174.html)

---

### Post by mistypotato on 2009-03-07
Hi hansdown,

I took a look at the link you provided.

It appears to be a video of his installation of Squirrel and HIS icons on HIS desktop.... and it's very nice and all......but alas....I failed to see where that will help the OP or myself find a solution to getting a shortcut for our systems which did not create such an icon during installation?

Did I miss something?

---

### Post by hansdown on 2009-03-07
Yes mistypotato. Sorry about that.

I was hoping for an easy solution, but all my searches have turned up alot of problems with the default launcher, with no solution.

---

### Post by JanvL on 2009-03-08
The solution is simple.

1 - rename the directory "SQuirrel SQL Client" to "SQuirrel_SQL_Client"

2-  open squirrel-sql.sh with Kate or Gedit or any editor.

go to line 21

20 else 
21        SQUIRREL_SQL_HOME='/your/jdirctory/SQuirreL_SQL_Client'
22 fi

and change the "SQuirrel SQL Client" to "SQuirrel_SQL_Client"

save the changes and the command ./squirrel-sql.sh
will start Squirrel as planned.

hope it works for you as well.

Problem is that bash has trouble working with spaces in a path.

Jan

---

### Post by mistypotato on 2009-03-09
Hi Jan,

Thanks for the assist.  Unfortunately it did'nt work for me :(

It now returns this error instead of running SQuirrel.........

Exception in thread "main" java.lang.NoClassDefFoundError: net/sourceforge/squirrel_sql/client/Main
Caused by: java.lang.ClassNotFoundException: net.sourceforge.squirrel_sql.client.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268 )
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: net.sourceforge.squirrel_sql.client.Main. Program will exit.



Also, when I navigate into the directory and try to run it I also get an error.

engineer@SYSTEM1:/usr/local/SQuirrel_SQL_Client$ sudo squirrel-sql.sh
sudo: squirrel-sql.sh: command not found

Not even this will work.........
sudo /usr/local/SQuirrel_SQL_Client/java -jar squirrel-sql.jar


The ONLY line thus far that has ever successfully launched SQuirrel is this one........
java -jar squirrel-sql.jar
and that's ONLY if I'm inside the SQuirrel_SQL_CLient folder

---

### Post by JanvL on 2009-03-11
There is something very strange happening, you are right.

If I open a terminal I cannot CD into the directory,
if I use Crusader (as root), doubleclick on the file squirrel.sh it starts
I reset the permissions for the directory several times but I still cannot cd into the directory.

I will search further, but this is very very strange!

Jan

---

