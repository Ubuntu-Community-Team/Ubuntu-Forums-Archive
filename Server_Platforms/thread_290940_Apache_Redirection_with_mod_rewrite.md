---
title: "Apache Redirection with mod_rewrite"
date: 2006-11-01
forum: Server Platforms
---

### Post by DannyG on 2006-11-01
Hello,

I am trying to setup my webserver to do a simple bit of redirection. Adding the following code to apache2.conf ```
Options +FollowSymLinks 
RewriteEngine on
RewriteRule (.*/webmail) https://www.mydomain.com/webmail [R]
``` successfuly results in [http://www.mydomain.com/webmail/](http://www.mydomain.com/webmail/) being redirected to [https://www.mydomain.com/webmail/](https://www.mydomain.com/webmail/).

However, I am trying to set up a redirection so that anyone going to [http://www.mydomain.com/](http://www.mydomain.com/) will be redirected to [http://mydomain.com/blog/](http://mydomain.com/blog/) but I cannot seem to get it to work. I have added these lines of code to apache2.conf ```
RewriteRule (.*/) http://www.mydomain.com/blog/ [R=permanent,L]
``` however when I try and access [http://www.mydomain.com](http://www.mydomain.com) Firefox gives me the message:


The page isn't redirecting properly

Firefox has detected that the server is redirecting the request for this address in a way that will never complete.

*This problem can sometimes be caused by disabling or refusing to accept cookies.


Now I know for a fact there is nothing wrong with my cookies. Can anyone tell me what the problem is? And is there anything I can do to optimize my current code for SEO, because I'm fairly sure there is.

I'm quite new to Apache and mod_rewrite, so go easy on me.

Thanks,

Daniel.

---

### Post by kidders on 2006-11-02
Hi there,

I'm no mod_rewrite expert either ... I've only needed to use it a handful of times ... but it seems to me that your redirect will apply to any URL with a '/' anywhere in it (ie every URL). I may be wrong, but it looks as though ".*//" would behave exactly the same way, for instance.

In any case, protocol changes like your http -> https are best solved with URL rewriting, but redirection of a specific URL to another is usually done with server-side scripting. If it were me, I would have used...

```

<?php
header("Location: /blog/");
exit();
?>

```

... or it's equivalent in another language. You'd save it as /index.php. Aside from the simplicity factor, handling your redirect this way also means you won't have to restart your web server to change it.

I hope this helps.

---

### Post by DannyG on 2006-11-02
That piece of code worked perfectly.

Many thanks.

---

### Post by kidders on 2006-11-02
Great :-)

Just for the benefit of anyone else reading this post though, my code breaches the HTTP/1.1 specification. Oops! :-? So, I'll try again...

```

<?php
header("Location: http://{$_SERVER['HTTP_HOST']}/blog/");
exit();
?>

```

---

