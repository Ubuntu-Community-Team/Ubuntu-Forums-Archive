---
title: "How to link to a php file ?"
date: 2007-09-09
forum: Server Platforms
---

### Post by seshomaru samma on 2007-09-09
I have apache 2 running on Dapper. I installed gallery2 and hosted pictures there that other people could watch by putting my IP into their browsers like this:
[http://XX.XX.XXX.XXX/gallery/albums.php](http://XX.XX.XXX.XXX/gallery/albums.php)
recently I got a domain name with no-ip
when i point my browser at my new domain I get the apache test page but when I point it at [http://my.new.domain/gallery/albums.php](http://my.new.domain/gallery/albums.php) Firefox asks me what do I want to do with the php file.
I thought I'll try a different way and created a hyperlink on the apache test page to the albums.php in usr/share/gallery but I keep getting "the file cannot be found on the server".
What can I do?

---

### Post by lsmobrian on 2007-09-09
check to see if php is installed,  easy way is create a index.php with "<?php phpinfo(); ?>" as the contents, then in your browser goto the directory you created that file in or the file itself.  if it still asks what to do with a php file, make sure everything is installed.

are you using LAMP (linux, apache, mysql, php)
there are lots of good tutorials setting this up if you do a search

---

### Post by seshomaru samma on 2007-09-10
It's not LAMP
just Apache on Dapper , I have PHP installed cause that is one of Gallery's dependencies

The thing is that I got Gallery's pix albums in my var/www directory but its albums.php file is in usr/share/gallery. This is the way it installs by default. 

I'm not sure what you mean by :
> create a index.php with "<?php phpinfo(); ?>" as the contents, then in your browser goto the directory you created that file in or the file itself
what is the purpose ? anyway I will try and let you know.

(EDIT> oh I get it , <?php phpinfo(); ?> is to see if PHP is working.....yes it's working....)

thanks for the help
:

---

### Post by quatre.sushis on 2007-09-13
I read your post.
  I think I can understand PHP (if the manual is at my side). But I don't use it so well, so I only can answer you some good way of programming or similar things with Perl. I also don't know what "gallery2" is.
  Anyway I think <?php phpinfo(); ?> lets you know what the parameter of your php enviroment. I remember I also checked some of its parameter from this command. But I don't remember so clearly. Bad memory...

---

### Post by Drunky on 2007-09-13
I would imagine that your computer will not locally server php files unless they are in the /var/www directory.

Try moving the php file to the /var/www directory.

I think this is a common difficulty with gallery2.

---

### Post by hobbestec on 2007-09-13
You could create a virtual host that has a DocumentRoot of the Gallery folder.  You'll probably need to also add the filename albums.php to the index files list so it loads automatically when going to your domain.

Basically you would add a new virtual host entry to your httpd.conf file:
 <VirtualHost www.mydomain.com>
ServerName [www.domain.com](www.domain.com)
DocumentRoot /var/www/gallery
</VirtualHost>

More details are available from apache:
[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

---

