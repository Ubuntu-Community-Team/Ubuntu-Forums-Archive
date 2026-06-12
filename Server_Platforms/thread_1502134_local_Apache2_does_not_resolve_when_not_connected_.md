---
title: "local Apache2 does not resolve when not connected to the internet, and other issues"
date: 2010-06-05
forum: Server Platforms
---

### Post by ftaylor on 2010-06-05
When I navigate to [http://localhost/](http://localhost/) in my browser, everything works fine regardless of whether or not the internet is connected.

When I navigate to [http://localhost/some_directory_that_exists/](http://localhost/some_directory_that_exists/) without the internet connection, it does not resolve. What could the problem be?

Also, I want to create aliases for [http://localhost/some_directory/](http://localhost/some_directory/) so I can type something like [http://somewebsite.dev/](http://somewebsite.dev/) in browser and it will resolve to that location. How can I achieve this?

Thanks,

Finbarr

---

### Post by wojox on 2010-06-05
> **ftaylor said:**
> 
without the internet connection, it does not resolve. What could the problem be?

Don't you need an Internet connection to access sites?

---

### Post by ftaylor on 2010-06-05
Well that would seem very stupid to me if that is the case, why should I need an internet connection to access a website that is on my hard drive?

---

### Post by wojox on 2010-06-05
Yeah my bad. I thought you had a server on a Lan. :redface:

What if you type your ip address?

You said > without the internet connection does it connect with the connection?

---

### Post by ftaylor on 2010-06-05
It would appear that this is a chrome bug. I got it to work in firefox without difficulty. Thanks for your help.

You don't by any chance know anything about the aliases do you?

---

### Post by wojox on 2010-06-05
> **ftaylor said:**
> It would appear that this is a chrome bug. I got it to work in firefox without difficulty. Thanks for your help.

You don't by any chance know anything about the aliases do you?

Did you get it using the ip address or the 127. ?

Aliases sure what do you want to due ?

---

### Post by ftaylor on 2010-06-05
Google Chrome browser wouldn't resolve it using ip or localhost without connection. Firefox resolved both without internet connection.

What I want to do is have an alias like [http://site.dev](http://site.dev) => [http://127.0.0.1/some_directory/](http://127.0.0.1/some_directory/)

---

### Post by wojox on 2010-06-05
Here's a How To for setting up a free domain name [http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

---

### Post by jarnik on 2010-07-12
> **ftaylor said:**
> Google Chrome browser wouldn't resolve it using ip or localhost without connection. Firefox resolved both without internet connection.

Confirmed - Chromium 5.0.375.86 does not resolve local URLs, Firefox 3.6.6 (at least with my settings).

---

