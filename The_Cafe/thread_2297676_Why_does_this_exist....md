---
title: "Why does this exist..."
date: 2015-10-05
forum: The Cafe
---

### Post by The_Forgotten_King on 2015-10-05
[http://us.archive.ubuntu.com/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/](http://us.archive.ubuntu.com/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/ubuntu/)
Adding another /ubuntu gives a Forbidden Error. But, why so many /ubuntu's

---

### Post by yoshii on 2015-10-06
it must be some kind of script error.  these days a lot of HTML addresses are generated algorithmically so wierdness like that can happen.

---

### Post by Bucky Ball on 2015-10-06
You could try asking Canonical ...

---

### Post by mcduck on 2015-10-07
Most likely it doesn't actually exist, but the server does a rewrite to map different nice-looking URLs into actual addresses, and the regexp used to do it just happens to do the same thing regardless of how many extra "ubuntu"s you add to the end. Up to certain limit, like you found. All of them are just one and the same real address on the server anyway. Take a look at [.htaccess]("http://httpd.apache.org/docs/current/howto/htaccess.html") and Apache's [mod_rewrite]("http://httpd.apache.org/docs/current/mod/mod_rewrite.html") for more details.

So no, nobody created that address, it just happens that the system used to create pretty web addresses allows you to type in something like that and still maps it into same place.

edit:
For example in the url for Ubuntuforums you'll see lots of complicated stuff after the showthread.php part. All those things provide the server information it can then use to decide what content to send back to you. Most web pages work like that these days, instead of having static web pages for everything the server creates a page for you dynamically. The downside is that you end with url's that are difficult to type and pretty much impossible for humans to remember. So often the server then uses mod_rewrite (or similar system) to create some simpler url's for people to use, for example automatically creating a mapping from *[http://www.someserver.com/firstpage](http://www.someserver.com/firstpage)* (which doesn't really exist) to *[http://www.someserver.com/index.php?page=firstpage](http://www.someserver.com/index.php?page=firstpage)* (which is the real address, with *index.php* being the php script dealing with the content and *page=firstpage* the variable that tells it what content to display.

---

