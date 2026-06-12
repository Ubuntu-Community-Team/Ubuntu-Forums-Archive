---
title: "Control via internet"
date: 2011-01-02
forum: The Cafe
---

### Post by nice_like_rice on 2011-01-02
Hi all, hopefully someone here can point me in the right direction!

In short, what is the best way for me to control stuff on my computer via an online webpage? Eg. Shut down my computer from a webpage running on my computer?

I found a way to do this by having a php script save a file, then a different  script access it every 10s. It's a horrible hack.


LONG STORY below, don't have to read this it's not entirely relevant

------------------------------------------------------------
I'm actually trying to control an arduino via a webform. I managed to do this by setting up apache to run a little server, with php parsing and saving the contents of POST to a text file. Then a python script read this file every 10s, and sent commands to the arduino. This is obviously a very basic way of doing this. What if, for example, I wanted to use a slider on the webpage to control, eg. my lights? Javascript? Is there different way other than accessing a file repeatedly, it seems a bit silly? I have to run it like 10 times a second if I want the response to be instant.

Thanks,

David

---

### Post by earthpigg on 2011-01-02
webmin?

edit: removed large image from post, it breaks the thread. [link]("http://upload.wikimedia.org/wikipedia/commons/a/a5/Webmin1420.png").

---

### Post by nice_like_rice on 2011-01-02
Thanks for the link, yes that's exactly the sort of interface I'm looking for, but am trying to write one myself... maybe I'll have a look through the source code and see if I can figure some of it out :)

---

### Post by samalex on 2011-01-03
> **earthpigg said:**
> webmin?

I second this... Webmin is amazing and you can control about everything on your box using it.  Also if WWW isn't a requirement I'd suggest just using SSH.  You can get a Java-based SSH client for a website if you wanted to go that way.

---

