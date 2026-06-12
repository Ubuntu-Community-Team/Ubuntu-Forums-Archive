---
title: "Can you help me with XAMPP?"
date: 2010-04-18
forum: Server Platforms
---

### Post by JoeyF on 2010-04-18
First off. I'm not using Ubuntu Server. But I'm trying to get XAMPP set up so I can test Wordpress themes I make.  Using 9.10

Anyway:

I got XAMPP installed using the Instructions from Apache Friends.

When I went to Localhost I got the language page. Selected English but nothing happened.  

Here's my Index.php:
```
<?php
	if (!empty($_SERVER['HTTPS']) && ('on' == $_SERVER['HTTPS'])) {
		$uri = 'https://';
	} else {
		$uri = 'http://';
	}
	$uri .= $_SERVER['HTTP_HOST'];
	header('Location: '.$uri.'/xampp/');
	exit;
?>
Something is wrong with the XAMPP installation :-(
```

I searched and found a couple Index.php files. Deleted one. And now when I go to localhost I get a "Index of" page.

I removed the XAMPP folder, Deleted Apache, PHP from Synaptic(They got reinstalled when i reinstalled XAMPP btw). Installed LAMP but it still does it.


Any ideas what I should do?.

Maybe reinstall XAPP and copy the index.php files from another Comp?.

Thanks.

---

### Post by eppo10 on 2010-04-18
... so you've got empty broser window... and deleted something somewhere... That shouldn't help much.

If you have XAMPP installed check if that's working (see if u have ~/lampp/ folder around), try 'sudo ~/lampp/lampp restart' in terminal. That should show you what's going on. You could even put this command as a starter on your desktop. Helps later on. Then try to open [http://localhost/xampp](http://localhost/xampp) in browser. By defaults username is '**lampp**'.

Then again your web content should go under **/opt/lampp/htdocs** where you can make folders containing, say, wordpress, joomla, drupal or u name it what. 
Files and folders under /opt/lampp/htdocs should be owned by user 'nobody' group 'nogroup'. See help on permissions. 

To see if it works put file named index.html containing "Hello me!" surrounded by html tags in /opt/lampp/htdocs and open browser to [http://localhost](http://localhost) 
That should do the trick.

---

### Post by JoeyF on 2010-04-18
Something I should add:

I'm trying to get to PhpMyAdmin so I can create a Database for Wordpress.

I'll try copying the file over from another computer to see if that works.


Thanks.

---

### Post by eppo10 on 2010-04-18
If apache is running for you and you are able to access [http://localhost/xampp](http://localhost/xampp) you just have to log in to it using 'lampp', 'password_you_set_when_installed_xampp'. Main xampp page pops up where phpMyAdmin is one of given links. It's installed by default.
Good luck.

---

