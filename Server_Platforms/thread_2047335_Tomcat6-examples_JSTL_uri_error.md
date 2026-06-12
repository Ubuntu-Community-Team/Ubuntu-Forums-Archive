---
title: "Tomcat6-examples JSTL uri error"
date: 2012-08-24
forum: Server Platforms
---

### Post by jsbiff on 2012-08-24
I installed Ubuntu 12.04, and during installation, also installed Tomcat.

When installation finished, I went to localhost:8080, and the "intro" page for Tomcat provided links for examples (among other things). I selected the examples, selected "JSP" examples, and when I clicked on the "Implicit Objects" execute link, received an error:

> 
org.apache.jasper.JasperException: The absolute uri: [http://java.sun.com/jsp/jstl/functions](http://java.sun.com/jsp/jstl/functions) cannot be resolved in either web.xml or the jar files deployed with this application


It would seem like this should already work, since it was installed as part of the basic tomcat package? Anyhow, does anyone know how to fix it? I thought maybe I needed to install a JSTL package, and tried two of them (one from apache, one which claims to be the reference implementation), but it still didn't work after installing either of those.

---

### Post by angryfirelord on 2012-08-24
I don't use Tomcat, but judging from the error, it looks like that URI has changed from when the example was built. If you can find another Tomcat basic tutorial, I'd load the WAR and see if it works.

---

### Post by hawkmage on 2012-08-24
There are multiple Tomcat packages.  Not all of them are installed by default, you need to have the tomcat7-examples package installed for the examples to work.

The default page in the main Tomcat package has links to the examples but not the examples themselvs.

---

