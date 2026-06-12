---
title: "Apache and vhosts + mod_rewrite"
date: 2012-09-13
forum: Server Platforms
---

### Post by MadsRC on 2012-09-13
I've recently aquired a Ubuntu server, with one IP attached, that I'm going to turn into a web server.

Apache is installed an configured, but I've got a question about how I should go about this.

I have a domain (Say example.com) that is a vhost. There I want to run:
phpmyadmin
blog
regular site
wiki

I want to be able to go to, say the blog, by typing blog.example.com

And then there's the kicker: I want to be able to use SSL

What is the best to with to do the URL?
Is it to have one vhost, with subfolders (ie. example.com/blog/) and then use .htaccess to translate blog.example.com to example.com/blog OR should I go with different vhosts?

I know the last one is the easiest/best way to set it up, but that won't allow me to use SSL on each site. Since I only got one IP, I can only set up one SSL site.

What should I do?

---

### Post by Bachstelze on 2012-09-13
> **MadsRC said:**
> Since I only got one IP, I can only set up one SSL site.

Not at all. With recent Apache versions it is perfectly possible to have name-based SSL virtual hosts.

---

### Post by MadsRC on 2012-09-13
From what I read it's not something that would be perfectly supported by all browsers, as not all support SNI perfectly?

That info is a few years old though, so don't know if it's still true?

---

### Post by Bachstelze on 2012-09-13
Well, if you want something that's perfectly supported by all browers, you can forget about SSL altogether...

---

