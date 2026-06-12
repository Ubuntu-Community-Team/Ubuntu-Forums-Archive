---
title: "are web proxies beatable?"
date: 2010-05-18
forum: Security
---

### Post by ulao on 2010-05-18
I tried this common script. 


```
RewriteCond %{HTTP:VIA}                 !^$ [OR]
RewriteCond %{HTTP:FORWARDED}           !^$ [OR]
RewriteCond %{HTTP:USERAGENT_VIA}       !^$ [OR]
RewriteCond %{HTTP:X_FORWARDED_FOR}     !^$ [OR]
RewriteCond %{HTTP:PROXY_CONNECTION}    !^$ [OR]
RewriteCond %{HTTP:XPROXY_CONNECTION}   !^$ [OR]
RewriteCond %{HTTP:HTTP_PC_REMOTE_ADDR} !^$ [OR]
RewriteCond %{HTTP:HTTP_CLIENT_IP}      !^$ [OR]
RewriteRule ^(.*)$ - [F]
```

Even got a list of 5000 ips but most of the google first hits are not on there. Anyone know how to prevent web proxies?

---

### Post by Agent ME on 2010-05-19
Not all proxies announce themselves in HTTP headers, so checking those won't block all.

Why do you want to block people from accessing your web site with a proxy? (I'm assuming this is what you're trying to do.)

To stop automatic spammers? A CAPTCHA would be more appropriate.

To stop people from registering many separate accounts? Make the registration process require an email address. Maybe make it so a certain number of quality posts is needed before a "trial" user can be promoted to a full user.

---

### Post by ulao on 2010-05-19
its just a web site not a registration site. Yeah my situation is a bit unique I will admit, just was hopping to ban proxy hits.

---

### Post by Agent ME on 2010-05-19
If the web site isn't even interactive, why would you want to ban proxies? You're just possibly stopping people from seeing your site.

---

### Post by ulao on 2010-05-20
Its based on a particular threat and figured anyone using a proxy its not that important and probly a good idea to keep them away as well.

---

### Post by ulao on 2010-05-25
I installed good 'ol php and figure I could beat it this way. I found something interesting but dont think its full prof yer.  I may block non proxy users..

```

<?php
if (substr($_SERVER['REMOTE_ADDR'],0, 3) != substr($_SERVER['SERVER_ADDR'], 0,3) ) 
{
	echo(" your using a proxy,leave now...");
    die();
}
?>
```

I found that the server ip should be the same domain up as your ip if you are coming form a normal server.

good (i.e ) IP:97.x.x.x SERVER IP:97.x.x.x

bad  (i.e ) IP:67.x.x.x SERVER IP:97.x.x.x

May come up with something better but so far it kills all proxies for sure ( except for a coincidence ). Also if you ID starts with a 1-9, it may have issues.

xxx. OK
xx.  OK
x.   Maybe not  OK

but regular expression could fix that.

---

### Post by Agent ME on 2010-05-25
Wait, you're going to ban everyone that doesn't have the same first octet as you in their IP? That's definitely not right. My IP doesn't even start with 97.

---

### Post by ulao on 2010-05-25
Uh, did I do that? whoops.. Back to the drawing board.. 

I though it was the proxies ip and the clients ip, but I see your point, that is not right at all.

This seems to get most

if ( $_SERVER['HTTP_CONNECTION'] == "" ||
     $_SERVER['HTTP_CONNECTION'] == "1" || //hide my a$$ did this..
     $_SERVER['HTTP_CONNECTION'] == "0" ||
     $_SERVER['HTTP_ACCEPT_ENCODING'] == "" ) //kproxy did this

Not really sure how to control these from a client point of view but most people pass this check.

---

