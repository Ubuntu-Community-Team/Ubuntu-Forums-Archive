---
title: "Images not appearing under localhost"
date: 2010-06-20
forum: Server Platforms
---

### Post by .Daniel on 2010-06-20
Hey guys, I recently set up an Apache web server with PHP and MySQL on my desktop and it's all going great apart from the fact that standard HTML <img src='etc'> won't appear... any ideas?

---

### Post by Ryan Dwyer on 2010-06-20
You're not linking to the images properly. Please provide the src attributes you're using (ie. the HTML) as well as your directory structure.

---

### Post by kenada on 2010-06-21
I had this prob too.

Following this fixed it
[http://ubuntuforums.org/showthread.php?t=555804](http://ubuntuforums.org/showthread.php?t=555804)

---

### Post by .Daniel on 2010-06-21
> **Ryan Dwyer said:**
> You're not linking to the images properly. Please provide the src attributes you're using (ie. the HTML) as well as your directory structure.

Surely you can get all you need from viewing source?

And the thread that the other guy linked didn't solve anything :(

---

### Post by Diabolis on 2010-06-21
Common errors that you should check:
1.- The files have the correct permissions? Apache can read them?
2.- The files are visible to the server? Is your apache root placed at /var/www and your image is at ~/images/etc ?

---

### Post by .Daniel on 2010-06-21
Well, I've pointed it to 'public_html' which is located in the Home folder and then the images are stored under 'public_html/images' - do the images need to also be under 'public_html'?

---

### Post by Diabolis on 2010-06-21
How did you 'pointed' it to public_html? Apache can only see files under the root folder, **/var/www/** by default. Thats where you must place them, unless you changed that location through **/etc/apache2/sites-available/default**.

---

### Post by .Daniel on 2010-06-21
I followed this:

[http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#createNewVirtualHost](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#createNewVirtualHost)

...and changed it from the default location...

---

### Post by Ryan Dwyer on 2010-06-21
> **.Daniel said:**
> Surely you can get all you need from viewing source?

I could if you provided a link to your website.

---

### Post by .Daniel on 2010-06-21
*facepalm* Sorry, I'm getting mixed up with another thread I started elsewhere, here's the code of index.html:

[HTML]<html>
<head>
<title>ETC</title>

<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<meta name="title" content="">
<meta name="keywords" content="">
<meta name="description" content="">
<link rel='stylesheet' media='screen' type='text/css' href='style.css'>
</head>
<body>

<center>

<img style='position:relative; right:480px' src='images/title.png'>

<table style='position:relative; right:486px; top:-11px'>
<tr class="sharing-cl"> 
	<td><a class="sh-mail" href=""></a></li> 
	<td><a class="sh-feed" href=""></a></li> 
	<td><a class="sh-face" href=""></a></li> 
</tr>
</table>

<ul id='menu'>
<li><a href='index.php'>Home</a></li>
<li><a href='upcoming_gigs.php'>Upcoming Gigs</a></li>
<li><a href='gallery.php'>Gallery</a></li>
<li><a href='contact.php'>Contact</a></li> 
</ul>
<p class='content'>ETC</p>
</body>
</html>[/HTML]

and the css for it...

[HTML]A:link {text-decoration: none; color: #ffffff; font-family:arial,sans-serif;}
A:visited {text-decoration: none; color: #ffffff; font-family:arial,sans-serif;}
A:active {text-decoration: none; color: none; font-family:arial,sans-serif;}
A:hover {text-decoration: none; color: #005aff; font-family:arial,sans-serif;}

body {
background-color: #161719;
background-image: url('images/banner.png');
background-repeat: no-repeat;
background-position: center top;
}

p {
font-family: arial,sans-serif;
color: #777777;
font-size:80%;
}

#menu {
position: relative;
top: -21px;
}

#menu li {
display: inline;
margin: 100;
font-family: arial,sans-serif;
color: #ffffff;
font-size: 13;
}

.content {
position: relative;
top: 55px;
width: 960px;
}

.sharing-cl{
	  overflow:hidden;
	  margin:0;
	  padding:0;
	  list-style:none;
	}
	.sharing-cl a{
	  overflow:hidden;
	  width:75px;
	  height:30px;
	  float:left;
	  margin-right:-10px;
	  text-indent:-200px;
	  background:url("images/share-sprite.png") no-repeat;
	}
	a.sh-feed{background-position:-70px -40px;}
	a.sh-mail{background-position:0 -40px;}
	a.sh-face{
	  margin-right:0;
	  background-position:-350px -40px;
	}
	a.sh-mail:hover{background-position:0 1px;}
	a.sh-feed:hover{background-position:-70px 1px;}
	a.sh-face:hover{
	  background-position:-350px 1px;
	}[/HTML]

---

### Post by Diabolis on 2010-06-21
Use this url: [http://localhost/images/title.png](http://localhost/images/title.png)

If you can't see it in your browser, then:
a) the path is wrong
b) the image doesn't have read permissions

---

### Post by Ryan Dwyer on 2010-06-22
> **Diabolis said:**
> Use this url: [http://localhost/images/title.png](http://localhost/images/title.png)

Or if your site is in a folder like [http://localhost/mysite/](http://localhost/mysite/), look at [http://localhost/mysite/images/title.png](http://localhost/mysite/images/title.png).

---

### Post by .Daniel on 2010-06-22
Mkay... I get:

'Forbidden

You don't have permission to access /images/title.png on this server.'

...when I go directory to it. How can I change the permissions so that I'm allowed to access the pictures?

---

### Post by Ryan Dwyer on 2010-06-22
Type ls -l to view the files in that directory and see what the current permissions are. Paste them here.

---

### Post by .Daniel on 2010-06-22
> **Ryan Dwyer said:**
> Type ls -l to view the files in that directory and see what the current permissions are. Paste them here.

I'm not sure what that means but if I go to the file and then right-click --> properties --> permissions, I get the following:

Owner: daniel - Daniel
Access: Read and write
Group: daniel
Access: Read-only
Others
Access: Read-only
Execute: Allow executing file as program (this box is ticked)
SELinux context: unknown
Last changed: ETC

I'm going to need more info if you want me to do as you just asked I'm afraid, sorry...

---

### Post by Diabolis on 2010-06-22
Check:
```
man chmod
```
and
```
man chown
```

Your file has the correct permissions (644), but the Apache user can't access it.

---

### Post by sf-it-services on 2010-06-22
sudo chmod xxx /var/www/images

xxx is your choice in three octal numbers  related to the rwxrwxrwx in the ls -l

my images directory is set at :-

drwxr-xr-x 2 root root 4096 2010-06-17 16:49 images


that would make the octal 755

is 644 more propererer

---

### Post by .Daniel on 2010-06-22
Guys, I'm pretty new to Ubuntu so I'm not sure what you just said at all... I pumped this into the console:

sudo chmod /home/daniel/public_html/images

and got:

chmod: missing operand after `/home/daniel/public_html/images'

Sorry, I need an uber-simple explanationv :S

---

### Post by Diabolis on 2010-06-22
You don't need to do that, however this is the explanation:

You would do it like this for the image:
```
chmod 644 /home/daniel/public_html/images/title.png
```
and for the folder:
```
chmod 755 /home/daniel/public_html/images
```

The numbers are the permissions:
4 read
2 write
1 execute

We use a 3 digit representation for the 3 access levels (user, group and others). So a 644 means:
the user, you, has a 6 (4 + 2) meaning read and write permission.
the group has a 4 meaning read only permission.
others have a 4 meaning read only permission.

The problem you have is not file permissions. The user with which Apache runs is not allowed to read your home folder. You have to add it, with the chown command, to your group.

Since you are new to this, you should stick to the defaults and leave the files under /var/www.

---

### Post by Ryan Dwyer on 2010-06-22
No, no, no... Apache should be able to read that file. Why would it be able to read the index and not the image?

Daniel, please open /var/log/apache2/error.log and scroll to the bottom. There should be some lines explaining why Apache served up a forbidden page. If you don't see the lines, open your browser and request the image again, then check the log again.

---

### Post by .Daniel on 2010-06-22
Contents of 'error.log':

[HTML][Sun Jun 20 00:36:44 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 20 01:42:52 2010] [notice] caught SIGTERM, shutting down
[Sun Jun 20 10:49:18 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 20 10:51:48 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 20 12:25:33 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:25:33 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:25:33 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:25:33 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:25:36 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:25:36 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:25:36 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:25:36 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:27:19 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:27:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:27:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:27:20 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:27:21 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:27:21 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:27:21 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:27:22 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:28:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:28:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:28:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:28:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:29:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:29:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:29:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:29:13 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:32:16 2010] [notice] caught SIGTERM, shutting down
[Sun Jun 20 12:33:06 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 20 12:50:53 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:50:53 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:50:53 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:50:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:51:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:51:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:51:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:51:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:52:15 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:52:16 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:52:16 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:52:16 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:52:49 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:52:49 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:52:49 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:52:49 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:56:42 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:56:43 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:56:43 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:56:43 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:11 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:59:11 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:59:11 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:59:11 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:12 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/upcoming_gigs.html, referer: http://localhost/
[Sun Jun 20 12:59:12 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:14 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:48 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 12:59:48 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 12:59:48 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 12:59:48 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:50 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 12:59:50 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 12:59:50 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 12:59:50 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:52 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/gallery.php
[Sun Jun 20 12:59:52 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/gallery.php
[Sun Jun 20 12:59:52 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/gallery.php
[Sun Jun 20 12:59:52 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:53 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/contact.php
[Sun Jun 20 12:59:53 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/contact.php
[Sun Jun 20 12:59:53 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/contact.php
[Sun Jun 20 12:59:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:54 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/gallery.php
[Sun Jun 20 12:59:54 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/gallery.php
[Sun Jun 20 12:59:54 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/gallery.php
[Sun Jun 20 12:59:54 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 12:59:56 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 12:59:56 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 12:59:56 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 12:59:56 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:05:09 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:05:10 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:05:10 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:05:10 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:30:56 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:30:57 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:30:57 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:30:57 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:34:59 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:34:59 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:34:59 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:34:59 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:35:43 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:35:43 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:35:43 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:35:43 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:35:44 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:35:44 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:35:44 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:35:44 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:35:49 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:36:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:36:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:36:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:36:21 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:37:00 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:00 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:00 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:37:02 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:37:02 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:37:02 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:37:02 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:37:16 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:37:16 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:37:16 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/upcoming_gigs.php
[Sun Jun 20 13:37:16 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:37:17 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:17 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:17 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:17 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:37:46 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:46 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:46 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:37:46 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:38:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:13 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:38:19 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:19 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:19 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:20 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:38:27 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:27 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:27 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:38:28 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:39:28 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:39:28 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:39:28 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:39:28 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:41:21 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:41:21 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:41:21 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:41:21 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:41:22 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:41:22 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:41:22 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:41:22 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:42:09 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:09 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:09 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:10 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:42:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:20 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:20 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:42:37 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:37 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:38 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:38 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 13:42:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/index.php
[Sun Jun 20 13:42:39 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 14:08:41 2010] [notice] caught SIGTERM, shutting down
[Sun Jun 20 19:18:09 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 20 20:04:01 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Sun Jun 20 20:04:01 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Sun Jun 20 20:04:01 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Sun Jun 20 20:04:01 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 00:37:06 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 00:37:06 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 00:37:06 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 00:37:06 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 00:38:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 00:38:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 00:38:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 00:38:14 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 00:59:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 00:59:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 00:59:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 00:59:39 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 00:59:51 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 00:59:51 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 00:59:51 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 00:59:52 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:00:07 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:00:07 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:00:07 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:00:08 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:00:24 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:00:24 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:00:24 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:00:25 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:00:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:00:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:00:39 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:00:39 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:01:03 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:01:03 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:01:03 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:01:03 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:01:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:01:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:01:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:01:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:01:29 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:01:29 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:01:29 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:01:30 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:02:09 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:02:09 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:02:09 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:02:10 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:02:45 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:02:45 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:02:45 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:02:46 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:02:54 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:02:54 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:02:54 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:02:55 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:02:56 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 01:02:56 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 01:02:56 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 01:02:56 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 01:06:28 2010] [notice] caught SIGTERM, shutting down
[Mon Jun 21 10:37:49 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 21 10:39:42 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 21 11:01:51 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 11:01:51 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.PNG denied, referer: http://localhost/
[Mon Jun 21 11:01:51 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.PNG denied, referer: http://localhost/
[Mon Jun 21 11:01:52 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 11:02:14 2010] [notice] caught SIGTERM, shutting down
[Mon Jun 21 14:04:29 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 21 15:10:06 2010] [notice] caught SIGTERM, shutting down
[Mon Jun 21 15:59:27 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 21 16:05:06 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 21 16:29:42 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 16:29:42 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 16:29:42 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 16:29:44 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 16:46:59 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 16:49:27 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:14:55 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:17:31 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:18:18 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:20:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:22:03 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:53:07 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:54:22 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 17:57:06 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 18:02:16 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 18:25:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Mon Jun 21 18:33:20 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 21 20:09:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied, referer: http://localhost/
[Mon Jun 21 20:09:13 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/top.png denied, referer: http://localhost/
[Mon Jun 21 20:09:14 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/share-sprite.png denied, referer: http://localhost/
[Mon Jun 21 20:09:14 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Mon Jun 21 20:18:47 2010] [notice] caught SIGTERM, shutting down
[Mon Jun 21 21:34:53 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 21 21:36:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Tue Jun 22 03:48:23 2010] [notice] caught SIGTERM, shutting down
[Tue Jun 22 13:21:48 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Tue Jun 22 13:42:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 13:42:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 13:42:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 13:43:01 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 13:44:46 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied
[Tue Jun 22 13:44:47 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Tue Jun 22 13:45:16 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/public_html
[Tue Jun 22 13:45:17 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Tue Jun 22 13:45:21 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Tue Jun 22 13:46:06 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /images/title.png denied
[Tue Jun 22 13:46:06 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Tue Jun 22 13:50:58 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Tue Jun 22 14:10:46 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 14:12:31 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 14:40:56 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 14:43:56 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 15:09:22 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 15:13:10 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 15:41:46 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 15:46:17 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Tue Jun 22 16:01:34 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Tue Jun 22 23:11:36 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations[/HTML]

Contents of 'error.log.1':

[HTML][Wed Jun 16 01:26:41 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Wed Jun 16 01:26:43 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 16 01:26:43 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Wed Jun 16 01:31:18 2010] [notice] Graceful restart requested, doing restart
Warning: DocumentRoot [/desktop/public_html] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 16 01:31:18 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 16 01:36:05 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:36:32 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:36:32 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:36:35 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:42:53 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:46:23 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:46:35 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:46:35 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:48:38 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:48:38 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:48:52 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:48:55 2010] [error] [client 127.0.0.1] File does not exist: /desktop
[Wed Jun 16 01:50:09 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jun 16 01:50:09 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 16 01:50:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 01:50:39 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 01:51:07 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 01:51:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 01:59:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:04:54 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE in /home/daniel/public_html/index.php on line 6
[Wed Jun 16 02:04:54 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:06:11 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE in /home/daniel/public_html/index.php on line 6
[Wed Jun 16 02:06:11 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:06:12 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE in /home/daniel/public_html/index.php on line 6
[Wed Jun 16 02:06:12 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:08:36 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE in /home/daniel/public_html/index.php on line 6
[Wed Jun 16 02:08:36 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:08:37 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE in /home/daniel/public_html/index.php on line 6
[Wed Jun 16 02:08:37 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:09:09 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:09:38 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:10:29 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:10:31 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:10:59 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:10:59 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:11:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:15:29 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:15:44 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/daniel/public_html/index.php on line 12
[Wed Jun 16 02:15:45 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:15:45 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/daniel/public_html/index.php on line 12
[Wed Jun 16 02:15:45 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:15:54 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 12
[Wed Jun 16 02:15:55 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:15:55 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 12
[Wed Jun 16 02:15:55 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:15:55 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 12
[Wed Jun 16 02:15:55 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:16:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:16:54 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:17:21 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:17:31 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:17:36 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:18:54 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:19:02 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:19:48 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:19:57 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:24:49 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING in /home/daniel/public_html/index.php on line 11
[Wed Jun 16 02:24:49 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:24:50 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING in /home/daniel/public_html/index.php on line 11
[Wed Jun 16 02:24:50 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:24:51 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING in /home/daniel/public_html/index.php on line 11
[Wed Jun 16 02:24:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:25:18 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING in /home/daniel/public_html/index.php on line 11
[Wed Jun 16 02:25:18 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:25:18 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING in /home/daniel/public_html/index.php on line 11
[Wed Jun 16 02:25:18 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:25:38 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING in /home/daniel/public_html/index.php on line 11
[Wed Jun 16 02:25:38 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:26:04 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_STRING in /home/daniel/public_html/index.php on line 10
[Wed Jun 16 02:26:04 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:26:35 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:28:23 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:28:24 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:28:26 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:28:46 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:30:33 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 11
[Wed Jun 16 02:30:33 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:32:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:32:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:32:10 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 02:42:18 2010] [notice] caught SIGTERM, shutting down
[Wed Jun 16 13:49:42 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 16 14:07:16 2010] [notice] caught SIGTERM, shutting down
[Wed Jun 16 17:50:39 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 16 18:10:34 2010] [notice] caught SIGTERM, shutting down
[Wed Jun 16 18:12:11 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 16 18:16:24 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 18:48:58 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 18:49:12 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 18:49:13 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 18:49:14 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 18:51:44 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:08:28 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:08:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:21:17 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 19:24:47 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:36:11 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:36:12 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:36:12 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:36:16 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:38:11 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 19:50:09 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/scrape
[Wed Jun 16 19:52:58 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 20:20:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/scrape
[Wed Jun 16 20:24:52 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 20:50:20 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/scrape
[Wed Jun 16 20:53:26 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 20:53:34 2010] [notice] caught SIGTERM, shutting down
[Wed Jun 16 20:54:31 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Jun 16 20:55:46 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Wed Jun 16 20:55:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 20:58:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/scrape
[Wed Jun 16 21:24:59 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 21:28:58 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/scrape
[Wed Jun 16 21:55:35 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 21:59:03 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/scrape
[Wed Jun 16 22:17:22 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Wed Jun 16 22:17:23 2010] [notice] caught SIGTERM, shutting down
[Thu Jun 17 00:44:11 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 17 08:38:36 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 17 08:54:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Thu Jun 17 08:54:53 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Thu Jun 17 08:55:16 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/announce
[Thu Jun 17 14:09:19 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 17 16:33:57 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Thu Jun 17 18:31:38 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 17 23:11:17 2010] [notice] caught SIGTERM, shutting down
[Thu Jun 17 23:12:08 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 17 23:33:35 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Fri Jun 18 00:17:17 2010] [notice] caught SIGTERM, shutting down
[Fri Jun 18 08:00:58 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 18 08:25:01 2010] [notice] caught SIGTERM, shutting down
[Fri Jun 18 17:58:21 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 18 18:39:25 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Fri Jun 18 21:02:19 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 01:12:16 2010] [notice] caught SIGTERM, shutting down
[Sat Jun 19 01:13:07 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Jun 19 13:26:08 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:01:06 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 42
[Sat Jun 19 14:01:06 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:01:07 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 42
[Sat Jun 19 14:01:08 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:01:28 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 43
[Sat Jun 19 14:01:28 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:01:28 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 43
[Sat Jun 19 14:01:29 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:01:51 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:01:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:02:12 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:02:12 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:02:29 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:02:55 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:02:56 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:03:36 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:03:47 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:06:35 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:06:59 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:07:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:08:48 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:09:13 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:09:28 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 48
[Sat Jun 19 14:09:28 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:09:43 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:13:01 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 45
[Sat Jun 19 14:13:01 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:13:02 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 45
[Sat Jun 19 14:13:02 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:13:28 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 45
[Sat Jun 19 14:13:28 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:13:29 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 45
[Sat Jun 19 14:13:29 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:14:00 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 14:14:00 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:14:45 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_ENCAPSED_AND_WHITESPACE in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 14:14:45 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:14:46 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_ENCAPSED_AND_WHITESPACE in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 14:14:46 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:16:40 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_ENCAPSED_AND_WHITESPACE in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 14:16:40 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:17:24 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 14:17:24 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:17:25 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 14:17:25 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:17:42 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 14:17:42 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:18:36 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:18:36 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:18:57 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: d in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:18:57 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:48:06 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: d in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:48:07 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:48:38 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: d in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:48:38 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:49:02 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '.' in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:49:02 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:49:09 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: d in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:49:09 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:49:18 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:49:18 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:49:40 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected ';' in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:49:41 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:49:41 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected ';' in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:49:41 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:49:42 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected ';' in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:49:42 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:49:51 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: d in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 14:49:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:55:34 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: b in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:55:34 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:55:45 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:55:45 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:56:32 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:58:14 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:58:14 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:58:15 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:58:15 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:58:24 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:58:24 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:58:24 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:58:24 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:58:58 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:59:08 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:59:30 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:59:30 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:59:31 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '=' in /home/daniel/public_html/index.php on line 44
[Sat Jun 19 14:59:31 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 14:59:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:00:28 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 15:00:28 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:00:29 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 15:00:29 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:00:44 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 15:00:44 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:00:51 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 15:00:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:00:51 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 15:00:51 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:01:02 2010] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected T_VARIABLE, expecting ',' or ';' in /home/daniel/public_html/index.php on line 46
[Sat Jun 19 15:01:02 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:01:17 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:01:31 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:02:25 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: b in /home/daniel/public_html/index.php on line 47
[Sat Jun 19 15:02:26 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:02:39 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 15:45:22 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Jun 19 16:44:29 2010] [error] [client 127.0.0.1] File does not exist: /home/daniel/public_html/favicon.ico
[Sat Jun 19 20:44:15 2010] [notice] caught SIGTERM, shutting down
[Sat Jun 19 20:45:07 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Jun 19 20:59:32 2010] [error] [client ::1] File does not exist: /home/daniel/public_html/favicon.ico
[Sun Jun 20 00:23:56 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 20 00:26:19 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 20 00:36:43 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/HTML]

---

### Post by .Daniel on 2010-06-22
> **Diabolis said:**
> You don't need to do that, however this is the explanation:

You would do it like this for the image:
```
chmod 644 /home/daniel/public_html/images/title.png
```
and for the folder:
```
chmod 755 /home/daniel/public_html/images
```

The numbers are the permissions:
4 read
2 write
1 execute

We use a 3 digit representation for the 3 access levels (user, group and others). So a 644 means:
the user, you, has a 6 (4 + 2) meaning read and write permission.
the group has a 4 meaning read only permission.
others have a 4 meaning read only permission.

The problem you have is not file permissions. The user with which Apache runs is not allowed to read your home folder. You have to add it, with the chown command, to your group.

Since you are new to this, you should stick to the defaults and leave the files under /var/www.

Well, it's working now - might have been those two commands you gave... whatever - all I care about is that it works now - thanks for the help everyone :)

---

### Post by Diabolis on 2010-06-22
> **Ryan Dwyer said:**
> Apache should be able to read that file. Why would it be able to read the index and not the image?

Thats true, but the index file is not inside the same folder as the images. Maybe the trouble is in the images folder permissions. 

Once I had a weird problem. I had image A.png and B.png, both in the same folder. I could see image A.png, but not B.png and the browser reported permissions problems. I checked them with ls -l and both had identical permissions. So I deleted B.png and then copied it again from the original source and that fixed it...

---

### Post by sf-it-services on 2010-06-23
file permissions can work recursively

---

### Post by sf-it-services on 2010-06-23
> **Diabolis said:**
> You don't need to do that, however this is the explanation:

You would do it like this for the image:
```
chmod 644 /home/daniel/public_html/images/title.png
```and for the folder:
```
chmod 755 /home/daniel/public_html/images
```The numbers are the permissions:
4 read
2 write
1 execute

We use a 3 digit representation for the 3 access levels (user, group and others). So a 644 means:
the user, you, has a 6 (4 + 2) meaning read and write permission.
the group has a 4 meaning read only permission.
others have a 4 meaning read only permission.

The problem you have is not file permissions. The user with which Apache runs is not allowed to read your home folder. You have to add it, with the chown command, to your group.

Since you are new to this, you should stick to the defaults and leave the files under /var/www.

rwx rwx rwx 
7 7 7


r-x r-x r-x 
5 5 5
 
rw- r-x -wx
6 5 3

its octal numbering system, simples

---

### Post by koenn on 2010-06-23
> **sf-it-services said:**
> Truley I believe you are a ****wit.....
rwx rwx rwx 
8 8 8 


its octal numbering system, simples
yeah, it's octal, meaning "base 8" so you could never get an '8' -> you'd get '10'.  Compare binary = 'base 2' : 00  01 10 11 .... you never get '2'


rwx = 7 ;  rwx rwx rwx = 777

---

### Post by Diabolis on 2010-06-23
> **sf-it-services said:**
> file permissions work recursively

False, unless you specify it with the -R option.

> **sf-it-services said:**
> Truley I believe you are a ****wit.....
rwx rwx rwx 
8 8 8 
its octal numbering system, simples

:confused:

Don't forget to mark this thread as solved.

---

