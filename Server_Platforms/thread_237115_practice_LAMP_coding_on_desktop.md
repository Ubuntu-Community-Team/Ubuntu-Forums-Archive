---
title: "practice LAMP coding on desktop"
date: 2006-08-15
forum: Server Platforms
---

### Post by qiemem on 2006-08-15
How can I set up my desktop so I could practice coding for websites using LAMP? Is this possible?

---

### Post by kebes on 2006-08-15
Yes it's possible. All you need to do is install a full LAMP stack (Linux Apache Mysql Php (or Perl/Python/etc.)). So you would install them the usual way, using "Synaptic" (or "Adept" on Kubunut), of via the commandline using:
```

sudo aptitude install apache2
sudo aptitude install mysql-server
sudo aptitude install php5

```

Then you can access pages you put in your web-folder "/var/www/" by going to:
[http://localhost/](http://localhost/)

So you'll be able to make sample pages, php scripts, databases, etc. and test them all.

For detailed instructions on setting up LAMP on Ubuntu, see:
[http://www.howtoforge.com/node/1388](http://www.howtoforge.com/node/1388)

Or do a search in the "howto" section of the ubuntuforums.

---

### Post by qiemem on 2006-08-15
awesome! thanks very much!

---

### Post by kebes on 2006-08-16
Also worth looking at:
[http://www.ubuntuforums.org/showthread.php?t=223410](http://www.ubuntuforums.org/showthread.php?t=223410)

It's a guide for setting up XAMPP, which will give you a LAMP-like development and testing environment.

---

### Post by qiemem on 2006-08-16
Giving XAMPP a try, and so far tis working great! Very easy to set up! But I've run into some troubles...

I've been working through the PHP tutorial off php.net: [http://us2.php.net/manual/en/tutorial.php]("http://us2.php.net/manual/en/tutorial.php")

Anyway, the hello world page worked fine, but when I try:
```

<html>
	<head>
		<title>What browser are you using?</title>
	</head>
	
	<body>
		<?php echo $_SERVER['HTTP_USER_AGENT']; ?> 
	</body>
</html>

```

I get:
```


Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/opt/lampp/htdocs/bryanh/PHP/browser.php' for inclusion (include_path='.:/opt/lampp/lib/php') in Unknown on line 0

```

I'm a total noob at this stuff so I have no idea where to begin on this one. Anyone know what I should do?

---

