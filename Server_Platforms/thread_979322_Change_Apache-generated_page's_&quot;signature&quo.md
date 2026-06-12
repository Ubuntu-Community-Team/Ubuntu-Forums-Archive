---
title: "Change Apache-generated page's &quot;signature&quot;"
date: 2008-11-11
forum: Server Platforms
---

### Post by jamieh on 2008-11-11
At the bottom of every Apache-generated page, it says:

> Apache/2.2.8 (Ubuntu) DAV/2 PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at xxxxx.org Port xxxx

I know how to change it to display more or less information, but how can I display a completely custom string of text, such as my favorite quote?

PS: Don't give me that "Apache doesn't let you display a custom string of text because you could lie about your server's specs" crap that Mac Forums gave me because Apache is open-source and I'll lie all I want.

---

### Post by Thirtysixway on 2008-11-11
You could use mod_headers to send the Server header as your own

[http://httpd.apache.org/docs/2.2/mod/mod_headers.html](http://httpd.apache.org/docs/2.2/mod/mod_headers.html)

---

### Post by jamieh on 2008-11-11
> **Thirtysixway said:**
> You could use mod_headers to send the Server header as your own

[http://httpd.apache.org/docs/2.2/mod/mod_headers.html](http://httpd.apache.org/docs/2.2/mod/mod_headers.html)

I'm a server n00b. Can you dumb that down a bit? :KS

Do I just need to add a line to httpd.conf/apache2.conf or is it harder than that?

---

### Post by Thirtysixway on 2008-11-11
You may have to run this as sudo, but in terminal type in


**a2enmod**


And type in **headers**  when it asks which module to enable.  Then just reload apache

sudo /etc/init.d/apache reload

and it should be enabled.  As far as configuring it (changing the server tag) try either the httpd.conf or apache2.conf file, I'm not sure which one the settings need to be entered into..

---

### Post by jamieh on 2008-11-11
> **Thirtysixway said:**
> You may have to run this as sudo, but in terminal type in


**a2enmod**


And type in **headers**  when it asks which module to enable.  Then just reload apache

sudo /etc/init.d/apache reload

and it should be enabled.  As far as configuring it (changing the server tag) try either the httpd.conf or apache2.conf file, I'm not sure which one the settings need to be entered into..

Okay thanks :)

---

### Post by MJN on 2008-11-12
I've never used mod_headers so am unable to comment on its use (although I didn't think it could do this sort of stuff, not least given that the server signature is not sent as part of the HTTP headers) however I can point you in the direction of the [ServerTokens]("http://httpd.apache.org/docs/2.0/mod/core.html#servertokens") directive (available from v2.0.44 onwards) which enables you to choose from a pre-defined set of verbosity with regards to the signature.
 
I am not aware of a way of actually 'customising' the displayed text beyond this, although there might be a way with the setenv directive in the mod_env module - the variable you'd be looking at playing with is SERVER_SIGNATURE.
 
Mathew

---

