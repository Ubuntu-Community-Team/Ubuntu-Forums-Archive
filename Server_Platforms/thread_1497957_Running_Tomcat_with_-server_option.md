---
title: "Running Tomcat with -server option"
date: 2010-05-31
forum: Server Platforms
---

### Post by jonchase on 2010-05-31
I'm trying to get a Tomcat server running using the Java VM -server option on Ubuntu Karmic 9.10 (I'm using the official Karmic AMI on EC2: ami-bb709dd2)


I install Tomcat:

```
sudo apt-get -y install tomcat6
```

I set up a bit of configuration in /etc/default/tomcat6:
```
JAVA_OPTS="-Djava.awt.headless=true -Xms1024m -Xmx1024m -XX:PermSize=384m -XX:MaxPermSize=384m"
```

I can start Tomcat with no problems:
```
sudo /etc/init.d/tomcat6 restart
```


However, if I add the -server option into the JAVA_OPTS variable, like so:
```
JAVA_OPTS="-server -Djava.awt.headless=true -Xms1024m -Xmx1024m -XX:PermSize=384m -XX:MaxPermSize=384m"
```

I get this:

```
$ sudo /etc/init.d/tomcat6 restart
 * Stopping Tomcat servlet engine tomcat6
   ...done.
 * Starting Tomcat servlet engine tomcat6
Invalid option -server
Cannot parse command line arguments

```
How do I set the -server option correctly?  I'm stumped!!

---

### Post by jonchase on 2010-06-07
*bump*

---

