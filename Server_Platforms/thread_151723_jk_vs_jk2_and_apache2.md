---
title: "jk vs jk2 and apache2"
date: 2006-03-28
forum: Server Platforms
---

### Post by kpgalligan on 2006-03-28
Looking at the documentation on apache's site, [http://tomcat.apache.org/faq/connectors.html](http://tomcat.apache.org/faq/connectors.html), it looks like 'jk' is the connector to use instead of jk2.  However, doing 'apt-cache search jk' returns ...

libapache-mod-jk - Apache 1.3 connector for the Tomcat Java servlet engine
libapache2-mod-jk2 - Apache 2.0 connector for the Tomcat Java servlet engine
(many other rows)

I originally installed 'libapache2-mod-jk2'.  After reading up, however, I went back and installed 'libapache-mod-jk'.  This actually installed apache 1.3 as well.  I've had to disable that, and tried to add jk to apache2, which failed on startup with ...

Cannot load /usr/lib/apache/1.3/mod_jk.so into server: /usr/lib/apache/1.3/mod_jk.so: undefined symbol: ap_table_get

At this point I'm thinking I'll have to build jk to work against apache2.  Any thoughts/similar experiences?

---

### Post by kpgalligan on 2006-03-28
Answering my own question, I found this which seems to cover the topic...

[http://www.crazysquirrel.com/computing/debian/tomcat55.jspx](http://www.crazysquirrel.com/computing/debian/tomcat55.jspx)

---

### Post by kpgalligan on 2006-03-28
In case anybody is looking for this in the future, just follow along with that website.  I personally had no troubles building from source (other than the fact that I didn't have g++ installed, as on this server I have built nothing from source until this point).

Seems to be working pretty well so far...

---

