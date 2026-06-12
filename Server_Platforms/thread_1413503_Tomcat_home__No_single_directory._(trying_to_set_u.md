---
title: "Tomcat home?  No single directory. (trying to set up mod_jk)"
date: 2010-02-22
forum: Server Platforms
---

### Post by mazz0 on 2010-02-22
I've got Apache, Tomcat and the Apache module mod_jk all installed from Universe.  I'm trying to use mod_jk to forward from Apache to Tomcat as described [here]("http://www.howtoforge.com/apache2_tomcat5_mod_jk_p3") so that I don't have to specify a port in my URL for either server.

When setting up my workers.properties I have to specify a tomcat_home directory, which according to the comments in workers.properties should > point to the location where you installed tomcat. This is where you have your conf, webapps and lib directories..

The problem is I don't have a single directory that has conf, webapps and lib!  Webapps are in /var/lib/tomcat6 along with links to conf, logs and work, but lib is only in /usr/share/tomcat6.  I tried creating a link to /usr/share/tomcat6/lib in /var/lib/tomcat6 and using /var/lib/tomcat6 as tomcat_home, but Tomcat still fails fails to start, with nothing in the log to explain why.  Commenting out the reference in the Tomcat config to workers.properties allows Tomcat to start up, so the problem must be in there, and I'm guessing it's what I've identified.

Can anyway offer any advise on this subject?  Has anyone got mod_jk working in Ubuntu?

---

### Post by Vegan on 2010-02-22
I have Apache and Tomcat both running. I use them both for web development. I can then use mixed documents in any user folder.

---

### Post by mazz0 on 2010-02-22
Yeah, I have both running fine, I just don't want to specify a port all the time, I want to have [http://localhost/thing.php](http://localhost/thing.php) work from Apache, but [http://localhost/myapp](http://localhost/myapp) work from Tomcat.

---

