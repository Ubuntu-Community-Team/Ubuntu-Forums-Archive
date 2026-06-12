---
title: "Faking response from missing mysql with Apache?"
date: 2010-01-19
forum: Server Platforms
---

### Post by Rallg on 2010-01-19
I have two installations of Ubuntu 9.10. One installation is for doing useful things, and the other (smaller, with less software) is a playground for my own experiments.

On the useful partition, I have a good working version of LAMP that I can use with things such as blog software, if I wish.

On the playground partition I have Apache with PHP, but NOT mysql. I don't want to put mysql there.

Currently I'm testing some software that calls mysql. Not having mysql in the playground, I get a "cannot contact mysql" error, and none of the test page is rendered.

Is there a way to fake a response, so that when the server attempts to contact mysql, it gets an actual response without generating an error? It could be the same response regardless of the query, such as "Hello from fake database!" The idea is that the rest of the page, which does not rely on mysql, will be able to render.

I can do simple no-brainer code manipulation, but I am not a programmer.

---

### Post by gombadi on 2010-01-19
> 
Is there a way to fake a response, so that when the server attempts to contact mysql, it gets an actual response without generating an error? It could be the same response regardless of the query, such as "Hello from fake database!" The idea is that the rest of the page, which does not rely on mysql, will be able to render.


Yes and no

Yes - you could write something that to apache looks like a mysql server and returns the same response to any query. But if you need this running then why not just run mysql.

No - My guess is even with the above working you will not get the effect you want. For example if the software does a query and asks for the number of widgets to display on the page. Your fake response returns "Fake Response" but the code will not understand that answer and fail and therefore not display the page.

---

### Post by Rallg on 2010-01-20
The "playground" partition can be used by others, so I don't want access to my real mysql database there. I guess it would be easiest to install a copy of mysql, but with dummy entries.

The only thing mysql return is local text, not widgets. Everything other than text is hard-coded into the surrounding web pages.

---

