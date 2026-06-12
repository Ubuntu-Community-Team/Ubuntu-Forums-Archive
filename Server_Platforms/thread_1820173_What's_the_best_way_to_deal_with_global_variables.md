---
title: "What's the best way to deal with global variables"
date: 2011-08-07
forum: Server Platforms
---

### Post by ki4jgt on 2011-08-07
I started my website on my own computer (due to the ISP unable to service my area, I had to switch it to an online host, thinking domain.com or godaddy) I had originally set the site up to use sockets to manage a single variable. Just 1 variable was all I needed. Now, I don't want to use a database for just one variable. What's the best way to do it?

The site is written in PHP. Is there a way to have a global variable for PHP?

---

### Post by SeijiSensei on 2011-08-07
What kind of "global variable" are you talking about?  A variable within PHP?  An environment variable in the shell?  What do you mean by "global?"

I'm afraid it's going to be hard to help you without a lot more detail on what you're trying to do.

In PHP, you can [declare variables as global]("http://php.net/manual/en/language.variables.scope.php") and make them accessible to user-defined functions.  Is that what you mean?  There's also the $GLOBALS array as described in that link.

If you want to change an environment variable, you might be able to set them using exec("export VARIABLE='value'"), but you might run afoul of permissions.

You might also be talking about the PHP settings themselves.  You can change those in [a variety of ways]("http://www.php.net/manual/en/ini.list.php").

---

### Post by Wim Sturkenboom on 2011-08-07
If it needs to be persistent between sessions, possibly a file to store it in. If it's sensitive, place the file outside the document root so visitors can't read it.

If it just for the session, you can use a session variable.

PS
I don't understand how sockets can be used as a global variable; do you mind to enlighten me?

---

### Post by ki4jgt on 2011-08-07
> **Wim Sturkenboom said:**
> If it needs to be persistent between sessions, possibly a file to store it in. If it's sensitive, place the file outside the document root so visitors can't read it.

If it just for the session, you can use a session variable.

PS
I don't understand how sockets can be used as a global variable; do you mind to enlighten me?

OK, the variable is a number which is incremented by session. Like, if a user logs on, the variable increases by 1. I used Python to create a socket server on localhost. The socket server then returned the variable to the page as it was being loaded. This is what I meant by sockets. That is what I was meaning by Global Variable.

---

### Post by SeijiSensei on 2011-08-07
There are lots of ways to do this, but you'll need a method of identifying the user.  I'd just put a persistent cookie in their browsers with the number.  You read the cookie, increment the counter, and write the cookie back to the browser.

---

### Post by ki4jgt on 2011-08-08
> **SeijiSensei said:**
> There are lots of ways to do this, but you'll need a method of identifying the user.  I'd just put a persistent cookie in their browsers with the number.  You read the cookie, increment the counter, and write the cookie back to the browser.

On the server side though, what would be the best way to keep up with the number? Like, I just opened site xyz.com;

I want to count the page views. for each user, I want the count increased by 1. True, client side, I could use cookies, but server side, I don't want to create an entire database for just 1 number, but that seems to be what everyone else tells me to do all over the web.

---

### Post by lisati on 2011-08-08
Some kind of [visitor counter]("http://inobscuro.com/tutorials/simple-php-unique-visitors-counter-30/")?

---

### Post by SeijiSensei on 2011-08-08
If you don't use cookies, how are you identifying individual users?  If users have to log in, you could just keep a plain-text file with login IDs and the number you want to store.  Read it into an array at startup, increment the counter for the login in question, then write it back to disk.  A slightly speedier solution would use a [Berkeley DB]("http://www.php.net/manual/en/intro.dba.php") key/value database.

---

### Post by ki4jgt on 2011-08-08
That's the thing, they don't login. It just counts them. Currently, I'm doing it in memory with Python. I was wondering if PHP could put it directly in memory, so I wouldn't have read and write to a file every time the page was loaded.


Example:

a = 0

Bob loads the page:

a = 1

cindy loads the page:

a = 2

Rod loads the page:

a = 3

Bob loads the page again:

a = 4

The way it is currently setup, (through python sockets) the python program stores the variable in memory and gives it to the php page when it's called. There is no file read or written. If I created a file for this, wouldn't it be slower than accessing it from memory?

---

### Post by SeijiSensei on 2011-08-08
That seems like a very complicated way to count total page views.  How about something like:

```
grep 'GET /index' /var/log/apache2/access.log | wc -l
```

Better yet, use a log analysis program like [analog]("http://www.analog.cx/").

---

