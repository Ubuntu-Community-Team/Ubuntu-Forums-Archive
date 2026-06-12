---
title: "serveralias not working in apache2"
date: 2008-05-19
forum: Server Platforms
---

### Post by roderashe on 2008-05-19
Hi. Webserver working great if I type in [www.example.com](www.example.com). If I type in example.com all I get is a web page that says "It Works". So my 'serveralias' doesn't seem to work. Here's my [www.example.com](www.example.com) file:

```
<VirtualHost *>
        ServerAdmin admin@example.com
        ServerName  www.example.com
        ServerAlias example.com

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/www.example.com/

</VirtualHost>
```

Any thoughts? Thanks!

---

### Post by spiderbatdad on 2008-05-19
DocumentRoot is pionting to /var/www which contains the index.html apache2 is looking for. 
My understanding of the ServerAlias directive is that it allows path names to be appended to the virtual host file. For example if "localhost" in the address bar brings up the default page, then "localhost/example.com" should bring up the page you are trying to see...assuming you have localhost as a ServerName in httpd.conf

EDIT: the above is probably not correct. You still would need the appropriate .html in /var/www. It seems like what you want is a redirect.

---

### Post by roderashe on 2008-05-19
how would I redirect? here's the real url's:

[http://www.bretography.com](http://www.bretography.com)

[http://bretography.com](http://bretography.com)

---

### Post by windependence on 2008-05-20
> **roderashe said:**
> Hi. Webserver working great if I type in [www.example.com](www.example.com). If I type in example.com all I get is a web page that says "It Works". So my 'serveralias' doesn't seem to work. Here's my [www.example.com](www.example.com) file:

```
<VirtualHost *>
        ServerAdmin admin@example.com
        ServerName  www.example.com
        ServerAlias example.com

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/www.example.com/

</VirtualHost>
```

Any thoughts? Thanks!

Try this:

```
<VirtualHost *>
        ServerAdmin admin@example.com
        ServerName  www.example.com
        **ServerAlias *example.com**

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/www.example.com/

</VirtualHost>
```

-Tim

---

### Post by MJN on 2008-05-20
Have you turned name-based virtual hosting on?
 
i.e. **NameVirtualHost ***
 
(it needs to go outside of any <Virtualhost> container, e.g. the line above in your posed config)
 
Mathew

---

### Post by windependence on 2008-05-20
MJN is correct here, you must turn on named based vitual hosting.

Also, your alias line should be 

ServerAlias *.example.com

Notice the dot. My bad, sorry.

-Tim

---

### Post by MJN on 2008-05-20
Unless sub-domain matching is required, **ServerAlias example.com** will match example.com as it stands.
 
Mathew

---

### Post by windependence on 2008-05-20
> **MJN said:**
> Unless sub-domain matching is required, **ServerAlias example.com** will match example.com as it stands.
 
Mathew

You are absolutely correct, however, if he wants to reach the site using [http://example.com](http://example.com) or [www.example.com](www.example.com) he will need the wild card for sub-domain matching.

-Tim

---

### Post by MJN on 2008-05-20
The ServerName directive takes care of that - there is no need to duplicate it in the ServerAlias.
 
Not that it matters (assuming the OP wants all sub-domain matching, not just [www.)](www.)) - I was just pointing out that in this particular case the ServerName and ServerAlias directives are already configured correctly for the situation.
 
Mathew

---

### Post by roderashe on 2008-05-20
Thanks, everyone. Turns out there was an erroneous ip address in my DNS zone file. Works fine now. Thanks!

---

