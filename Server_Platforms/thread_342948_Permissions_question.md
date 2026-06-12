---
title: "Permissions question"
date: 2007-01-20
forum: Server Platforms
---

### Post by PCSpectra.com on 2007-01-20
Can someone explain the workings of file permissions in the context of a PHP script and a end user accessing a web site from an web browser.

For instance, a user accessing your web site won't be able to do much other then retreive files as Apache and more specifially (HTTP) doesn't allow for much more - correct? So even with a file/folder permission such as 777 an end user via the web can't do much with a properly configured/updated (epxloit free) system???

Secondly, in trying to wrap my head around permissions...

Can a linux system have users but no groups? When you FTP and CHMOD you can't change the user or the group of a file (chown, etc?) just the permissions.

Apache runs (typically) as user: **nobody** could it also be run as group "everybody" and thus override it's user specific permisisons?

When I CHMOD a file/folder on a shared host as 777 it doesn't pose any risk to the outside world as Apache (HTTP) only allows for so many things to happen. But on a shared host users of that host could write a PHP script which could operate on files in your folder - correct? This is when permissions become important in a web development environment???

Assuming a shared host then, and ignoring PHP security such as open_basedir, etc...what are considerations to make?

Does PHP get executed as user: **nobody** as well when nivoked through Apache - I would think so...

Is there anything you can do from the Apache/Linux level to prevent other users of that shared host from traversing into your space? Is this where Users and Groups come in?

---

### Post by kidders on 2007-01-20
Hi there,

> **PCSpectra.com said:**
> For instance, a user accessing your web site won't be able to do much other then retreive files as Apache and more specifially (HTTP) doesn't allow for much more - correct?Strictly no ... the various HTTP specifications are quite extensive. In any case, that's not the usual reason for maintaining a sensible permissions policy. It's difficult to make a case for deliberately assigning badly designed permissions on the grounds that you haven't provided a means for anyone to alter your files.

Two observations:
[LIST]
[*]You still need to protect your web pages from processes (and people) other than your web server.
[*]There's no accounting for bugs in apache that may allow (or inadvertently cause) file modifications. You should never consider a system to be "exploit free".
[/LIST]

> **PCSpectra.com said:**
> Can a linux system have users but no groups?Again, strictly not. You *could* achieve the same effect by using only one group system-wide, but why would you want to?

> **PCSpectra.com said:**
> Apache runs (typically) as user: **nobody** could it also be run as group "everybody" and thus override it's user specific permisisons?This would have extremely serious security implications that would make apache extremely unpopular.

---

