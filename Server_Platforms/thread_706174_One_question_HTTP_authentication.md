---
title: "One question HTTP authentication"
date: 2008-02-24
forum: Server Platforms
---

### Post by danielsbrewer on 2008-02-24
I am running gallery (gallery.menalto.com) on an ubunutu gutsy server using apache as my http server.  What I would like to do is allow to be viewed by my friends and family but no-one else.  I was looking into some sort of http authentication, but from what I can see is that they all need a username and password.  I don't want to create usernames for everyone I know who possibly might want to see the gallery, but rather use some knowledge that they would have about me.  What I would like to have is just a single question that if you get right then you can get access to the gallery for example, What is the name of my wife?

I know this could easily be bypassed probably with a google search, but I would like a small wall to prevent casual access.

Is anything like this possible?  Any other suggestions for this low level protection

Thanks

---

### Post by k_grdn on 2008-02-24
Hi,

You could use htaccess to restrict access but you'll need usernames + passwords, why not just create a simple generic set and share with your family.

[http://httpd.apache.org/docs/1.3/howto/htaccess.html#what](http://httpd.apache.org/docs/1.3/howto/htaccess.html#what)

If you want something more personalised why not knock up a simple php auth frontend to your site.

Also I'm sure you could use gallery to restrict access to certain albums.

Regards,

k_grdn

---

### Post by danielsbrewer on 2008-02-24
The username+password route isn't what I am after as I want to make it as easy as possible for my friends and family to access.

I had thought of a simple php frontend, but I would not know how to make this so it interoperates with gallery.  The only thing they suggest is username+password authentication

---

