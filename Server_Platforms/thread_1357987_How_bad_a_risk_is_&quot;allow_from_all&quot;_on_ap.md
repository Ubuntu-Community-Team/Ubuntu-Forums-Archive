---
title: "How bad a risk is &quot;allow from all&quot; on apache2"
date: 2009-12-17
forum: Server Platforms
---

### Post by volkswagner on 2009-12-17
I am trying to setup a new server 8.04 VPS.  I heard how easy Citadel was and decided to give it a go.  I want mail and apache on the same server for $cost reasons.

According to Citadel docs the following config is needed for the webcit frontend Vhost file.

```
<VirtualHost mydomain.com:443>
	#here some of your config stuff like logging, serveradmin...
	NameVirtualHost www.mydomain.com
    <location />
         allow from all
    </location>
    ProxyPass / http://127.0.0.1:2000/
    ProxyPassReverse / http://127.0.0.1:2000/
# The following line is optional.  It allows WebCit's static content
# such as images to be served directly by Apache.
    alias /static /var/lib/citadel/www/static
</VirtualHost>
```

What kind of hole am I creating with <location /> allow from all?

Is this really opening my root directory to the world?

If so, is there a more secure way to run webcit and apache on the same physical server....without requiring using alternate ports int the urls?

Without the allow from all, I get a 403 Forbidden error.

---

### Post by TwiceOver on 2009-12-17
I think you are just allowing logon from any IP address.  Not positive, but you could probably use "Allow from {yourIP}" or "Allow From x.x.x.0/24" for a range....

Again, not positive.

---

