---
title: "Something like Yahoo Groups..."
date: 2012-12-31
forum: Server Platforms
---

### Post by sanric on 2012-12-31
Hi everybody,

sorry for bothering you with this post but I'm installing Ubuntu Server for the very first time and I'm in need of your help. ;)
I was wondering whether it could be possible to install a service that may resemble in some way Yahoo Groups.
I need this for the local section of my political party, so it's not adviced to use a global method like Yahoo or whatsoever: better keep files and conversations inside a server of property.

For my use, this service must cover:

1) username/password for login
2) mailing list
3) file repository
4) database
5) calendar

What do you suggest?
Happy New Year!

---

### Post by volkswagner on 2013-01-01
I'm not aware of any software package containing all your requirements.

You may want to start with a CMS and build from it.  Perhaps starting with Wordpress, Drupal, Joomla, Mambo, Xoops, etc. will get the ball rolling.

---

### Post by sanric on 2013-01-02
I've been thinking about it but it seemed a rather unorthodox solution.
Something like ownCloud, maybe?

---

### Post by lisati on 2013-01-02
[Mailman]("https://help.ubuntu.com/community/Mailman") might be of some help with the email side of things. One of its options is to have an online archive available.

Edit: If you're not so worried about ineracting via email, an online forum, such as [MyBB]("http://mybb.com") or [PhpBB]("http://phpbb.com") might be what you're after. You will, however, probably need to check the plugins that are available to help you prevent spammers making a nuisance of themselves.

---

### Post by volkswagner on 2013-01-02
> **sanric said:**
> I've been thinking about it but it seemed a rather unorthodox solution.
Something like ownCloud, maybe?


I have been known to over complicate the simple :D

What is the purpose of the "database" in your list of requirements?

I think OwnCloud will get you most all on your list.  Again, not sure what you're looking to get from the database.  I'm also not sure how OwnCloud will handle the mailing list.

I just thought a CMS would be very scalable and highly flexible (with large lists of available plugins/modules, etc).

---

