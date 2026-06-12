---
title: "Java EE 6 w Glassfish on Ubuntu Server (Console only)"
date: 2010-03-18
forum: Server Platforms
---

### Post by jinliew on 2010-03-18
Hi All,

I'm attempting to install Java EE6 on Ubuntu 8.04 server (only has command line access) but when I try to run the installer I get the following error message: 

```
This program requires DISPLAY environment variable to be set.
Please re-run after assigning an appropriate value to DISPLAY.
```
Has anyone installed Java EE6 on Ubuntu server?  Do I need to install X / VNC or is there another way?

AFAIK, there are no Ubuntu packages for Java EE6 at this stage.

Cheers,

Jin

---

### Post by n0dix on 2010-03-18
Set the environment variable GF_HOME to where you installed GlassFish.
See [this]("http://blogs.sun.com/enterprisetechtips/entry/datasource_resource_definition_in_java").

---

