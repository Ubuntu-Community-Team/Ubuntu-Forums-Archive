---
title: "Apache2: Cannot access files through Virtual Host"
date: 2006-03-22
forum: Server Platforms
---

### Post by krokodil on 2006-03-22
I have setup Apache2 to allow me to access a folder in my home directory called public_html through:

http://localhost/~krokodil/

Using "UserDir public_html" in my apache2.conf file.

I also have setup 2 virtual hosts that both point to folders inside public_html, and both seem to work, ie. take me to what seems to be the correct place.

Example of one of my Virtual hosts:

<VirtualHost *>
ServerName bricks.test
ServerAlias www.bricks.test
DocumentRoot /home/krokodil/public_html/bricks/site/work/root
</VirtualHost>

My problem is I have copied files into the above directory but when I access it through the virtual host (http://bricks.test/) I see the correct directory structure but no files.

When I access it through localhost, http://localhost/~krokodil/bricks/_project/work/root/ I see all the files. It even opens up on my index.htm file.

I have no idea what's wrong.

---

### Post by dragonfyre13 on 2006-03-22
make sure that www-group has read permissions. for testing purposes, you can turn on read permissons for "other" but make sure to change them back once it gets fixed.

---

### Post by krokodil on 2006-03-22
[QUOTE=dragonfyre13]make sure that www-group has read permissions.[/QUOTE]

I did a "chmod -R a+rwx ~/public_html" and now all my files are -rwxrwxrwx, unfortunately this hasn't made any difference.

---

### Post by peanut butter on 2006-03-22
try the following code (just an idea) (works for me)

	<VirtualHost *>
		ServerName bricks.test
		DocumentRoot /home/krokodil/public_html/bricks/site/work/root
	</VirtualHost>

also is the dns for "bricks.test" pointed to the server (if bricks.test is a domain)

---

### Post by krokodil on 2006-03-23
[QUOTE=peanut butter]also is the dns for "bricks.test" pointed to the server (if bricks.test is a domain)[/QUOTE]

I tried the virtual host as you suggested but it doesn't seem to make a difference.

I have setup my /etc/hosts file to point bricks.test to 127.0.0.1. bricks.test is never meant to be seen beyond my local network it's just there to simplify local development and testing.

---

### Post by dragonfyre13 on 2006-03-27
Errrr, Set it to the IP address of the computer, not localhost, I thought. I could be wrong though.

---

