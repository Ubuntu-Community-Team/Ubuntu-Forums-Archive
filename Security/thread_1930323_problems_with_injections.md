---
title: "problems with injections"
date: 2012-02-23
forum: Security
---

### Post by isecore on 2012-02-23
So, I recently launched a webserver with Ubuntu Server 11.10 running on it. I would've wanted LTS release, but 10.04 felt too old and 12.04 isn't ready yet.

Almost immediately I've been having problems with file injections and modifications through PHP. I've tried to harden it as much as possible, but whenever the Apache user (www-data) owns files or folders they immediately get corrupted and have code snippets, files or other alterations made that cause spam-emails and redirects to porn-sites.

Any ideas on how to patch this up? It's driving me nuts!

---

### Post by CharlesA on 2012-02-23
www-data shouldn't have write access to files.

---

### Post by roelforg on 2012-02-23
> **CharlesA said:**
> www-data shouldn't have write access to files.
Charles is right.
EDIT: Though you might wanna patch up your php-scripts as well, if they can do this now, they might find a way to execute an exploit later.

---

### Post by isecore on 2012-02-23
Yes, I agree with that. However, I then need to know how I can implement functions securely which my users depend on. Most of them run Wordpress-blogs, and it is a _huge_ inconvenience for them not being able to use the built-in upgrade function.

I'm thinking about implementing a solution with suexec, is this a good idea?

---

### Post by Lars Noodén on 2012-02-23
Also, if PHP has a [taint mode](https://wiki.php.net/rfc/taint), use it.  Treat all data acquired from outside the program as suspect until it has been validated or sanitized.  When I worked with PHP, I used to import everything from the web forms into a separate array/namespace and transferred after cleaning. 

When working with MySQL use [prepare and execute](http://dev.mysql.com/doc/refman/5.5/en/sql-syntax-prepared-statements.html) statements, with placeholders, to interact with the database.  Not only will this make your code more secure, it will also increase performance in some cases.  Unfortunately it is not taught often, though it should be obligatory in any course covering PHP and databases.  Here is one article on the topic:

[http://www.ultramegatech.com/2009/07/using-mysql-prepared-statements-in-php/](http://www.ultramegatech.com/2009/07/using-mysql-prepared-statements-in-php/)

---

### Post by isecore on 2012-02-23
> **Lars Noodén said:**
> *loads of text*

Yeah, thanks for your input but I have no knowledge or intention of writing PHP. I want it running for prefab things like Wordpress, forums, whatnot.

---

