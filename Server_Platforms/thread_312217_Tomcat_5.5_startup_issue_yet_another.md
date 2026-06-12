---
title: "Tomcat 5.5 startup issue /yet another/"
date: 2006-12-04
forum: Server Platforms
---

### Post by GSMD on 2006-12-04
I've installed Tomcat 5.5 using apt-get.
It would start by /etc/init.d/tomcat5.5 start but not at system startup. There are symlinks in rc*.d folders presented.
I've changed the ownership of /usr/share/tomcat5.5 to tomcat5.5:nogroup, but still no result /while TOMCAT5_USER=tomcat5.5 in /etc/default/tomcat5.5/.
I don't see anything related to tomcat startup at syslog as well...
It's not a good thing to run tomcat under the root account at startup /though this can be done/.
Anyone, could you please give me a hint on what am i doing wrong?

Thanks.

---

### Post by Jere Retzer on 2006-12-04
Did you look at the Tomcat log in /var/log/tomcat5.5? The Ubuntu package also uses port 8180 as opposed to 8080 like most. Point your browser to localhost:8180 if you haven't.

---

### Post by GSMD on 2006-12-06
Yeah, nothing special there. Nothing at all!
Sure thing i've been accessing :8180!

Thanks.

---

### Post by fabiodasoghe on 2007-11-10
> **GSMD said:**
> 
I've changed the ownership of /usr/share/tomcat5.5 to tomcat5.5:nogroup, but still no result /while TOMCAT5_USER=tomcat5.5 in /etc/default/tomcat5.5/.

Is it EXACTLY what you're written? I mean, TOMCAT5_USER=tomcat5.5? If this is the case, maybe it's the error: the right username is tomcat55.

Cheers,

Fabio

---

### Post by GSMD on 2007-11-10
My bad, it was tomcat55 naturally. That was a well-known bug fixed later.

---

