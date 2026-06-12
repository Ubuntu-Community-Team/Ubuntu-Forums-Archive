---
title: "Tomcat Server + CMD BUILD"
date: 2009-12-10
forum: Server Platforms
---

### Post by Diubidone on 2009-12-10
Hi all...

So I have this issue about installing a specific war application on my tomcat server.

I installed the Tomcat Server following [these]("http://kmtk.cs.ait.ac.th/knowledge-center/how-to/install-tomcat-6-on-ubuntu-server-8.0.4") instructions (the page is sometimes very slow).

I chose to install the Tomcat Server like this following an advice given me by the support personnel from Tecnoteca, which is the italian company that has the CMDBUILD project that I need to deploy ([link to the project]("http://www.cmdbuild.org/")).

This beeing said the tomcat server works great, I deployed the sample applications and they work perfectly.

But when it comes to deploy the cmdbuild.war application I have some serious problems. As instructions say I copied the jdbc driver for the postgresql database (which I installed during the installation of the OS) into the tomcat/libs directory. I then copied the cmdbuild.war applications into the tomcat/webapps directory but when I connect to the server I get "NO JDBC DRIVER" message.

(I haven't installed the jdbc drivers for postgresql from synaptic because I'm affraid I might get confused on conflicting jdbc drivers).

The guys from tecnoteca have [kind of surrendered]("http://www.cmdbuild.org/supporto/forum/tecniche/886898933") (problably because they have no idea about Ubuntu's Tomcat platform). The italian [forum]("http://forum.ubuntu-it.org/index.php/topic,345100.0.html") hasn't responded.

 Anyone here can help me?

---

### Post by craigp84 on 2009-12-10
Hi,

From what you say, it seems like tomcat cannot see your JDBC drivers, and your instructions have been to install the driver at the tomcat container level.

You could try putting the jdbc driver .jar file in the web application's lib dir.

I'd install the tomcat admin application (see tomcat.apache.org) and explore the configuration from there. Can you see the postgresql driver jar / lib mentioned?

---

