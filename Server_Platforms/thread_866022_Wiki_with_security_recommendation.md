---
title: "Wiki with security recommendation"
date: 2008-07-21
forum: Server Platforms
---

### Post by matthewboh on 2008-07-21
I'm looking for a wiki that has at least site security - so that people have to sign on.  So far, I've installed a few - but they are coming up short.  

Mediawiki - recommends that you do NOT use it as a secure Wiki.  This was my first choice.

Dspace - basically takes over your root directory, and you can't place it in another one.

JSPWiki - has the security, but seems like it's missing some functionality.

The things that I would really like are:

[LIST=1]
[*]Site security - just a simple web login
[*]Versioning - especially if I could get it for attachments like Word Documents
[*]Access based on groups[/LIST]

Any ideas?

---

### Post by Titan8990 on 2008-07-21
Anything wrong with Apache's .htaccess for security?

---

### Post by windependence on 2008-07-21
[http://twiki.org/](http://twiki.org/)

-Tim

---

### Post by Endwin on 2008-07-21
I use dokuwiki  it has ACL with group view and edit. Use it in an IT shop where we have a public section employees can only read. Private IT only section, and readable but only editable by cetain logged in users sections. You can lock it down or have it as open as you like. It moves great, no need for a database backend. Reason being if you need to get to the wiki to read how to save the database it is not helpful to have the database hold the wiki. It is all done in text documents you can move around on the server and view. Also has a decent list of plugins. One I used was to add mediawiki like tables to it for my own use.

[http://wiki.splitbrain.org/wiki:dokuwiki](http://wiki.splitbrain.org/wiki:dokuwiki)

---

### Post by matthewboh on 2008-07-22
That's what I love about computers - always something new to learn!

All right - I read up about .htaccess and it looks like I can use it with a user and group file - but does it also include mechanisms to allow people to register / sign-up /etc?  Is there a really simple mechanism which allows people to take on the registration workflow so I don't have to be involved once installation happens?

---

