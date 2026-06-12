---
title: "[SOLVED] apache2 phpmyadmin problem?!?!"
date: 2008-03-05
forum: Server Platforms
---

### Post by sevenearths on 2008-03-05
Before I start with the problem I have to tell you that I have installed ruby on rails from this tutorial:

[http://www.urbanpuddle.com/articles/2007/11/16/install-ruby-rails-on-gutsy-gibbon-nginx-version]("http://www.urbanpuddle.com/articles/2007/11/16/install-ruby-rails-on-gutsy-gibbon-nginx-version")

The problem is I have installed apache2 (for php devlopment) as well (the tutorial installs nginx, I think!). So every time i type 'localhost' in to address bar I get phpmyadmin for my mysql database.

How do I get apache to work so I can start doing some php stuff?

BTW(the ruby and rails stuff should interfere with any of the phpmyadmin/apach2 stuff because i do all my development on [http://0.0.0.0:3000/](http://0.0.0.0:3000/))

---

### Post by sevenearths on 2008-03-06
no worries

I found the solution. Apache was on localhost:8080

So I jst made the following html file to access it


```
<html><body><center>
<style>
A
{
	font-size: 24;
}
</style>

<h1>It works!2</h1><br /><br /><br />
<a href="http://0.0.0.0:3000" >Ruby-on-Rails</a>
<br /><br /><br />
<a href="http://localhost" >phpMyAdmin</a>
<br /><br /><br />
<a href="http://localhost:8080/phpscripts/" >phpscripts</a>
</center></body></html>
```

---

