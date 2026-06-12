---
title: "Apache vs SQL vs PHP"
date: 2007-07-20
forum: Server Platforms
---

### Post by eagleeyes on 2007-07-20
So, I am planning on starting my own server to make some documents/photos available on the web. I was originally going to install the whole LAMP package but i was reading the installation methods of the individual packages; apache, SQL, php.  What are the major differences between the three server formats? I do want to be able to put up a website and I have a java based ssh portal to upload on the server (I already have it thanks to a friend of mine).

Thanks

---

### Post by LaRoza on 2007-07-20
> **eagleeyes said:**
> So, I am planning on starting my own server to make some documents/photos available on the web. I was originally going to install the whole LAMP package but i was reading the installation methods of the individual packages; apache, SQL, php.  What are the major differences between the three server formats? I do want to be able to put up a website and I have a java based ssh portal to upload on the server (I already have it thanks to a friend of mine).

Thanks

Apache2 is the server, SQL is a database query language, and php is an interpreter for a scripting language. Usually Apache2, MySQL, PHP and Perl are installed together.

If you are using Ubuntu, "sudo tasksel" will install everything, (select Lampp).

---

### Post by az on 2007-07-20
> **eagleeyes said:**
> So, I am planning on starting my own server to make some documents/photos available on the web. I was originally going to install the whole LAMP package but i was reading the installation methods of the individual packages; apache, SQL, php.  What are the major differences between the three server formats? I do want to be able to put up a website and I have a java based ssh portal to upload on the server (I already have it thanks to a friend of mine).

Thanks

I would stay away from a java-based ssh terminal.  It would be far more secure to just ssh into your box from a linux console, or use putty in windows.

A static website just requires apache.  Apache is the webserver and will serve the pages.  A dynamic site uses a scripting language to get the server to render the page on the server before it is sent out to the client.  Usually, the data for a dynamic site is stored in a database.  Mysql has fewer bells and whistles than other database engines, but it has better performace (and you don't need fancy features for a dynamic website.)

Another word for dynamic website is web application.  Examples of web applications include CMSs (Content Management Systems) Wikis, Forums, etc...

In summary, your web application runs on the LAMP stack.  Apache, Mysql and Php (or perl, or python) are stacked together.

---

### Post by eagleeyes on 2007-07-20
thanks,

I am starting the learning process on this stuff. That helps

:)

---

