---
title: "Apache2 and ASP"
date: 2006-12-16
forum: Server Platforms
---

### Post by LightShear on 2006-12-16
Hey all,

I have a question about setting up apache2 to support asp files. I followed the howto's I found by searching on this topic and installed mono-server2 and that lib thing, but I still can't get it to work. All the howto's talk about virtual hosts and stuff. I not running a dot com, I just have a no-ip account and use /var/www or the deafult directory for webpages. I'm not sure how to set up the config files. Anyone know of a general/default setup for supporting asp files?

Thanks,
Chris

PS- I'm using 6.06

---

### Post by LightShear on 2006-12-16
Actually, I think I'm doing stuff I don't need to do. All I want is to be able to "include", for example .asp or .html files, in html documents. I don't really understand apache's howto. Any ideas?

-Chris

---

### Post by chrisfay on 2006-12-17
> All I want is to be able to "include", for example .asp or .html files, in html documents.

I'm not sure I understand what you're trying to do. Could you elaborate?


**EDIT:**

If all you're trying to do is 'include' external files within a page, such as SSI or PHP includes, you need to decide which method to use.  Assuming that is what you're trying to do, I prefer using PHP over Apache's 'server side includes'. All you would need to do is create a file, for example test.txt, and enter whatever you want to include into it.

Then in your main page, instead of saving it with a .html extension, use .php. Inside the main page you would add:

<?php include 'path/to/text.txt' ;?>

This would esentially take whatever is in test.txt and place it within your .php file. This also assumes that you have a working PHP installation on the server and that your web server is not configured to parse .txt files. If it is, you can save the file containing the info you want to include as a .php file instead of a .txt file.

This link may help:
[http://us3.php.net/function.include](http://us3.php.net/function.include)

If this isn't what you're trying to do, then again, elaborate.....:-D

---

### Post by LightShear on 2006-12-17
What you are describing is exactly what I'm trying to do. Sorry, I wasn't more clear; I thought that include stuff was just for asp. I'm a little outdated in web development, and that's what my job is now, so I figured the best way to understand what we're doing at work is to experiment with it at home. Thanks for your help, though. I'll try that today.

---

### Post by LightShear on 2006-12-17
Turns out I had PHP installed already and doing what you said did the trick. Thanks so much!

-Chris

---

