---
title: "Ubuntu, Glassfish &amp; Magnolia - perfect together..."
date: 2007-05-31
forum: Server Platforms
---

### Post by huggy77 on 2007-05-31
I have been trying to add as may open source apps to my glassfish setup as possible.  So far i have my little ubuntu/glassfish box runnig
[B]
- pebble
- jforum
[/B]

both installed pretty easy... I now wanted to add magnolia - which is a java based, open source, content management system....

I put on a large pot of coffee and prepared for a long night of hacking around...  


What a waste of coffee- i am happy to say that it could not be easier.  all you have to do is download the Magnolia war files from:
[http://www.magnolia.info/en/products/community-edition.html](http://www.magnolia.info/en/products/community-edition.html)   (link is to the right)

then you can hop into your glassfish admin  console and install 2 wars to Applications > web applications (this is very easy. 2 clicks of a mouse

lastly edit /domain1/config/login.conf  and add:
magnolia {
info.magnolia.jaas.sp.jcr.JCRAuthenticationModule requisite;
info.magnolia.jaas.sp.jcr.JCRAuthorizationModule required;
};
Jackrabbit {
org.apache.jackrabbit.core.security.SimpleLoginModule required;
};

and thats it... took all of 5 minutes after i figured out how to config the login.conf....

this is really great... i cant believe how easy it is...  I highly recommend glassfish...

btw glassfish is an open source java server, it rocks...

---

