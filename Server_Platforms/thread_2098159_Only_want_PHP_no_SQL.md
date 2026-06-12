---
title: "Only want PHP no SQL"
date: 2012-12-25
forum: Server Platforms
---

### Post by mrhobbeys on 2012-12-25
I have a website that uses no SQL only php. But after I have setup PHP trying to use phpmyadmin it seems I need mysql for that to work :(. How do I setup my site with no SQL?

---

### Post by littlegreiger on 2012-12-25
If you're not using any SQL then you won't need phpmyadmin because all it does is administer SQL databases.

---

### Post by Vegan on 2012-12-25
You can use the standard LAMP stack and ignore the database.

Then when you find you do need a database its there ready for use.
:popcorn:

---

### Post by volkswagner on 2012-12-26
What type of website are you setting up?

When you say "no SQL" so you mean "without MySQL" or "no database server"?  Or do you mean noSQL like [MongoDB]("http://www.mongodb.org/") or [CouchDB]("http://couchdb.apache.org/"), etc.?

As mentioned, having MySQL idle in the background will not be a significant resource hit, so just install it and use it when necessary.  Also mentioned, there will be no need for phpmyadmin without MySQL installed.

---

