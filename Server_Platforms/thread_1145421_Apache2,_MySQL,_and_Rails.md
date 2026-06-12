---
title: "Apache2, MySQL, and Rails"
date: 2009-05-01
forum: Server Platforms
---

### Post by BenjaminKohl on 2009-05-01
I have been searching all over the internet for instructions on how to get Rails working with Apache2 and MySQL in Ubuntu.  I find detailed lists of instructions, but none of them seem to work.  Each list I find specifies varying libraries that are "required", but no two lists match.

Does anyone out there actually know what I really need to do and what libraries are truly required?  I'd like detailed instructions, if possible.  Being vague won't help me because I generally know what I am doing anyway.  Thank you for any help you can offer.

I am currently using Ubuntu 9.04.

---

### Post by TheR on 2009-05-03
> **BenjaminKohl said:**
> I have been searching all over the internet for instructions on how to get Rails working with Apache2 and MySQL in Ubuntu.  I find detailed lists of instructions, but none of them seem to work.  Each list I find specifies varying libraries that are "required", but no two lists match.

Does anyone out there actually know what I really need to do and what libraries are truly required?  I'd like detailed instructions, if possible.  Being vague won't help me because I generally know what I am doing anyway.  Thank you for any help you can offer.

I am currently using Ubuntu 9.04.

I would REALLY like to suggest you Ruby Enterprise edition. It has everything packed together, Ruby, Rails, Gems, Apache mod_rails and most common gems in debian package.

[http://rubyforge.org/projects/emm-ruby/](http://rubyforge.org/projects/emm-ruby/)



by
TheR

---

### Post by ejschaefer on 2009-05-03
Hello, 

Here are some instructions for configuring Apache and Mongrel using mod_proxy_balancer: [http://mongrel.rubyforge.org/wiki/Apache](http://mongrel.rubyforge.org/wiki/Apache)

This article offers a step by step approach to configuring both sides of the equation. 


If you're having problems with RoR and MySQL, here's an article covering those details: 
[http://www.bin-co.com/blog/2009/04/error-connection-mysql-ruby-rails-linux-solution/](http://www.bin-co.com/blog/2009/04/error-connection-mysql-ruby-rails-linux-solution/)

Let me know if you have any problems.

Edward Schaefer
Support Center Manager
[http://www.hostmysite.com/?utm_source=bb](http://www.hostmysite.com/?utm_source=bb)

---

### Post by BenjaminKohl on 2009-05-11
Thank you, very much!  All of this information is helpful.

---

