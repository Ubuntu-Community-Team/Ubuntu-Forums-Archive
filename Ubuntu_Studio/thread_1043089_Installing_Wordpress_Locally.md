---
title: "Installing Wordpress Locally"
date: 2009-01-18
forum: Ubuntu Studio
---

### Post by Crackity Jones on 2009-01-18
I'm wanting to do some theme development for my site before it moves from wordpress.com to an independent host. For this I need Wordpress installed locally, which requires a local installation of PHP, MySQL etc. This can be easily done with packages such as XAMPP.

The problem is that installing [XAMPP]("http://www.apachefriends.org/en/xampp.html") for Linux only comes with support for x86 computers and there is no 'XAMPP Lite' version for download - something that just has the bare essentials.

Any suggestions?
Would installing the Windows XAMPP Lite version work under Crossover-office?

---

### Post by stmiller on 2009-01-18
No need to do that xampp thing, or other mess. Just do this:

```
sudo apt-get install wordpress
```

Wordpress is Linux/Unix only. It does not require anything windows. :)

---

### Post by javaholic5 on 2009-09-27
But why xampp?

I have one on howto install it on (k)ubuntu with PHP, MySQL, etc. here:

[http://www.ludisoft.com/knowledgebase/?p=3](http://www.ludisoft.com/knowledgebase/?p=3)

---

