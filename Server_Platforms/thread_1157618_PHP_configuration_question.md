---
title: "PHP configuration question"
date: 2009-05-12
forum: Server Platforms
---

### Post by pytheas22 on 2009-05-12
On an old Red Hat server that I had, I could embed PHP code into html pages using syntax like this:

```
<html>
<p>Some html text</p>
**<? echo 'some text' ?>**
</html>

```
On Ubuntu with the default LAMP setup, however, my code has to look like this in order for the server to recognize it as PHP:

```

<html>
<p>Some html text</p>
**<? _php_ echo 'some text'; ?>**
</html>
```

(Notice that I have to declare the code as 'php' explicitly after the '<?' tag.)

I assume that there's a configuration option somewhere in Apache that tells it to interpret '<? ... ?>'  as PHP code even if there's no 'php' string mentioned.  Does anyone know where I could find and change that option?  I've tried asking Google, but it's hard to come up with a good search query for this type of thing.

---

### Post by Zeosa on 2009-05-12
> **pytheas22 said:**
> On an old Red Hat server that I had, I could embed PHP code into html pages using syntax like this:

```
<html>
<p>Some html text</p>
**<? echo 'some text' ?>**
</html>

```
On Ubuntu with the default LAMP setup, however, my code has to look like this in order for the server to recognize it as PHP:

```

<html>
<p>Some html text</p>
**<? _php_ echo 'some text'; ?>**
</html>
```

(Notice that I have to declare the code as 'php' explicitly after the '<?' tag.)

I assume that there's a configuration option somewhere in Apache that tells it to interpret '<? ... ?>'  as PHP code even if there's no 'php' string mentioned.  Does anyone know where I could find and change that option?  I've tried asking Google, but it's hard to come up with a good search query for this type of thing.



Head over to /etc/php5/apache2/php.ini and open it in your favorite editor, check the value of 'short_open_tag' -Make sure it's set "On" ...Don't forget to restart apache after making any changes in the file.

---

### Post by pytheas22 on 2009-05-13
> Head over to /etc/php5/apache2/php.ini and open it in your favorite editor, check the value of 'short_open_tag' -Make sure it's set "On" ...Don't forget to restart apache after making any changes in the file.

Many thanks for your response.  Unfortunately, the short_open_tag value is set to 'On' (apparently by default), but the code still doesn't work, even after restarting apache.  Any other places where I might look?  If not, I at least have a Google term to work with now--I didn't know these were called short_open_tags.

---

### Post by cdenley on 2009-05-13
Try this, and post the output
[PHP]
<?php
header('Content-type: text/plain');
echo "long tag\n";
echo "short_open_tag=\"".get_cfg_var('short_open_tag')."\"\n";
?>
<? echo "short tag\n"; ?>
[/PHP]

---

### Post by pytheas22 on 2009-05-13
> **cdenley said:**
> Try this, and post the output
[PHP]
<?php
header('Content-type: text/plain');
echo "long tag\n";
echo "short_open_tag=\"".get_cfg_var('short_open_tag')."\"\n";
?>
<? echo "short tag\n"; ?>
[/PHP]

Thanks for the response.  This is the output:
```

long tag
short_open_tag="1"
short tag
```

So the short tag worked in this code, which was run from mysite.com/~user/php-test.php.  However, the short tags in the main page of the site, at mysite.com, are still not working.  I'm suspecting this has to do with the way the server has virtual hosts set up.  I'll look into this and report back if I figure out what's going on.

---

### Post by cdenley on 2009-05-13
> **pytheas22 said:**
> Either way, short tags don't seem to be working in my scripts, even though they are enabled in php.ini.

That's weird, because the short tag in the script you just ran worked fine.

---

### Post by pytheas22 on 2009-05-13
> That's weird, because the short tag in the script you just ran worked fine.

My apologies, I've made more observations about what's going wrong, and I don't think the short or long tags have to do with the problem.

What's happening is that PHP code embedded into html files is not running at all, whether the code uses short or long tags.

However, PHP code works fine when used in scripts with the .php extension.

Is there any reason why the default LAMP setup on Ubuntu would ignore PHP when it's embedded into html, even though it works in .php files themselves?

Thanks to all for the replies so far.

---

### Post by pytheas22 on 2009-05-13
Aha, that was easy: I just need to add this line to /etc/apache2/apache2.conf:
```

AddType application/x-httpd-php .html
```

Then restart Apache.

Problem solved.  Thanks for the help, and sorry for asking a question that ultimately was kind of stupid.

---

### Post by Zeosa on 2009-05-13
As of php => 5.3.0 it can be set on a per directory basis. Is it possible that there's a .htaccess file in there somewhere setting the php_flag off? (it could also be in the main configuration) ...it would look something like this: 

```
php_flag short_open_tag Off
```

---

### Post by pytheas22 on 2009-05-13
> **Zeosa said:**
> As of php => 5.3.0 it can be set on a per directory basis. Is it possible that there's a .htaccess file in there somewhere setting the php_flag off? (it could also be in the main configuration) ...it would look something like this: 

```
php_flag short_open_tag Off
```

I think that none of the embedded code was working before--it wasn't a question of certain directories working while others didn't--but since I edited apache2.conf as described in my last post, everything works fine now.  I'm surprised that Ubuntu's LAMP doesn't set up Apache to parse html-embedded PHP by default, but now I know.

Thanks for all the quick help.  Our old Red Hat web server got hacked and needed to be rebuilt on Ubuntu as fast as possible; because the original server had tons of cruft to sift through and was configured in weird, non-standard ways, it was hard to track down some of the glitches that were preventing the web applications from working as expected.  I assumed that the PHP issues were due to a weird configuration left by the last system administrator, but I guess it came down just to changing a default setting in Apache's configuration.

---

### Post by Gimpy_Rob on 2009-05-13
Ah, I'm sorry I missed this, I had the problem pegged from post#1.  Subtle with the "html"

I've ALWAYS seen this setup on servers.  The reason is security, and executable code.  By default, HTML is static, so things like <? might be something else.

Glad you've got it solved

---

