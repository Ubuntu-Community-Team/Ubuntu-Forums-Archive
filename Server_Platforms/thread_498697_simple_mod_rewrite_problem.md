---
title: "simple mod_rewrite problem"
date: 2007-07-11
forum: Server Platforms
---

### Post by kitman420 on 2007-07-11
I have a simple mod rewrite problem going on and I can't find the answer anywhere.

I have a webpage named [http://home/test.php](http://home/test.php),  When I go there, I want it to say [http://home/test](http://home/test)

That's easy, I make a rule like this:

```
RewriteRule ^test$ /test.php
```

Now, I have page called test2.php that reads the variables using $_GET. I want to hide those variables. So, if I go to [http://home/test2/123](http://home/test2/123) it redirects me to [http://home/test2.php?hello=123](http://home/test2.php?hello=123). I do it like this:

```
RewriteRule ^/test2/([0-9]+)$ /test2.php?hello=$1
```

So now in my php script, I should be able to use $_GET['hello'] to read whatever numerical value I passed in on the URL line.

But, this isn't working properly, I can go to the webpage test2/123, but there is nothing in the $_GET variable.

Any help?

Thanks,
km

---

### Post by jtc on 2007-07-12
Using that second rewrite you should get a numeric value in $_GET['hello']
Actually, tested it myself and it worked just fine.

In what scope have your put your Rewriterule? Directly inside <Virtualhost....>?
How about the superglobal $_GET in general? Does it work for you when rewrites are not involved?

---

### Post by Footballkid4 on 2007-07-12
PHP Version?
Anything > 4 should work, but if you're working on PHP 3 for some reason (please upgrade), it may be in $HTTP_GET_VARS.

Easiest thing to do for simple debugging on your page is to try:
```
<?php
print '<pre>' . print_r($_REQUEST, true) . '</pre>';
?>
```
That'll spit out cookies, sessions, post, and get data.

Also, you should try changing:
```
RewriteRule ^/test2/([0-9]+)$ /test2.php?hello=$1
```
To this:
```
RewriteRule ^/test2(?:/([0-9]+))$ /test2.php?hello=$1
```

That way yourdomain.com/test2 will redirect to test2.php?hello=, whereas with your regex, yourdomain.com/test2 will not be captured and therefore not directed

---

### Post by kitman420 on 2007-07-12
I had to turn off Multiviews in apache to get this to work. The description of the problem that I traced it down to is in [this thread]("http://ubuntuforums.org/showthread.php?p=3009212")

---

