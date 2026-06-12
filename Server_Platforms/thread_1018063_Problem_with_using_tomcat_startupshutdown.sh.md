---
title: "Problem with using tomcat startup/shutdown.sh"
date: 2008-12-21
forum: Server Platforms
---

### Post by r1ch on 2008-12-21
Hi,
Is anyone able to offer some help with the following problem please?

I have installed tomcat6 from synaptic and after viewing [http://localhost:8080](http://localhost:8080) it shows the "it works" screen and shows my catalina variables as being...

CATALINA_HOME=/usr/share/tomcat6
CATALINA_BASE=/var/lib/tomcat6

...however running the shutdown script gives the following error...

[B]Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6[/B]
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr
21-Dec-2008 23:24:39 org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:137)
	at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:407)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:337)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:415)


...this shows the catalina base and home being the same. I'm not worried whether I have a seperate instance or not but have been unable to either find a way to change the CATALINA_BASE value to be what it should be or to change the installation so that it does not have the seperate instance.

Any ideas and suggestions or pointers to a solution would be very gratefully received.

---

### Post by Drezard on 2008-12-21
Read this error here:

> 
java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml (No such file or directory)


Thats all you should need :-)

---

### Post by r1ch on 2008-12-22
Thankyou for your reply Drezard. Unfortunately I do already have the file and directory structure mentioned by the java exception, but it is present in the previously mentioned CATALINA_BASE=var/lib/tomcat6 directory whereas the actual value for C_BASE in the server instance is the same as CATALINA_HOME which is =usr/share/tomcat6.

I suspect that your suggestion that I copy the folder/files over from one place to the other may solve this problem but as I don't know what other dependencies I may be affecting if I do this, I was hoping to alter the 'BASE value to be the 'correct' one mentioned by the server on its welcome page, which would presumably do the trick.

Does anyone know how I can change such a variable please?

---

### Post by wsfulton on 2009-01-12
I had the same problem, but using the new way to start/stop services introduced in Intrepid Ibex works nicely:

[FONT="Courier New"]
$ sudo service tomcat6 stop
 * Stopping Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ sudo service tomcat6 start
 * Starting Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ 
[/FONT]

or of course the more traditional way:

[FONT="Courier New"]
$ sudo /etc/init.d/tomcat6 stop
 * Stopping Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ sudo /etc/init.d/tomcat6 start
 * Starting Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ 
[/FONT]

---

### Post by nikhilbhardwaj on 2009-06-29
thanks a lot 
the method of starting up services worked for me

---

### Post by eazyigz on 2010-01-08
This worked for me too.  Thank you.

---

### Post by Tricia Bowen on 2010-01-26
> **wsfulton said:**
> I had the same problem, but using the new way to start/stop services introduced in Intrepid Ibex works nicely:

[FONT="Courier New"]
$ sudo service tomcat6 stop
 * Stopping Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ sudo service tomcat6 start
 * Starting Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ 
[/FONT]

or of course the more traditional way:

[FONT="Courier New"]
$ sudo /etc/init.d/tomcat6 stop
 * Stopping Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ sudo /etc/init.d/tomcat6 start
 * Starting Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ 
[/FONT]
Thanks, this worked.

---

### Post by pwiggins on 2011-03-22
I spent a couple of hours searching for a fix and figure I'll post what I found here.

Beware... Mgmnt type dusting off nonexistent skill; 6hours into creating a Ubuntu Virtualbox guest for webapp testing... in other words don't trust a thing I type.

My hack fix was to create a link where tomcat wanted it to the existing server.xml file.
- create a conf directory in /usr/share/tomcat6
- create the link server.xml and point it to the existing /etc/tomcat6/server.xml

That solved my start/stop with:
- startup.sh
- shutdown.sh
- ./catalina.sh [run/stop]

BUT.. I had a severe cannon find /usr/share/tomcat6/tmp... yup... 2nd manual hack, simply created that directory. All is well so far.
-Paul

---

