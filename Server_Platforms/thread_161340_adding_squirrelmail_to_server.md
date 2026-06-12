---
title: "adding squirrelmail to server"
date: 2006-04-16
forum: Server Platforms
---

### Post by mofojones on 2006-04-16
This may be a silly question, but I'm awfully new to running apache, so bear with me.  I've been running a test server with a few basic html pages.  I just recently added squirrelmail as per the tutorial in the ubuntu howtos.  (or maybe it was wiki.  Can't remember)  Currently, all I see is my default web page.  I don't know how to ... separate the website and webmail into two separate sites.  I use dynamic dns and don't really care if they use the same domain name.  I suppose that mysitename.xyz.com/webmail would be the preffered way of doing things.

Any quick pointers?

---

### Post by fdoving on 2006-04-17
Add
```

Include /etc/squirrelmail/apache.conf

```

to your /etc/apache2/apache2.conf file.

Now reload apache.
```

/etc/init.d/apache2 reload

```

You can now access squirrelmail from yoursite.com/squirrelmail
To edit the apacheconfig for squirrelmail edit /etc/squirrelmail/apache.conf

- Frode

---

### Post by mofojones on 2006-04-17
Thanks, that did the trick!

---

### Post by fdoving on 2006-04-18
Great :)

---

