---
title: "access files on web server (local machine)"
date: 2009-03-17
forum: Server Platforms
---

### Post by b-boy on 2009-03-17
Hi


I am learning HTML and I would like to know how to I access a file on my local machine. I have apache install and I can view text and images the have put in my page.html


What I want is a link that will take me to a directory on my local machine such as /home/user/picture

how can I do this?

---

### Post by askreet on 2009-03-17
HTML links point to locations on the current webserver.

Let's say you have a web site configured in the default location:

/var/www

Going to [http://localhost/index.html](http://localhost/index.html) displays the contents of /var/www/index.html.

If you had a folder called /var/www/pictures/, you could get to it by going to [http://localhost/pictures/](http://localhost/pictures/).  However, if you have some images in a location outside of the web root (/var/www), you cannot browse to that location.  This is, of course, for security reasons.

Where is your web root?  What URL are you using to get there?  Where are the pictures you want to link to?  If you give these answers we can help you understand if/why/how to link to them.

Good luck, and I hope this is helpful!

-askreet

---

### Post by b-boy on 2009-03-18
ok thanks for the info askreet 

My webroot is default /var/www/ and I would like to access a image outside the web root like /home/user/Pics

---

