---
title: "[SOLVED] how I got PHP5 to work in Apache2"
date: 2008-04-20
forum: Server Platforms
---

### Post by brook adams on 2008-04-20
I'm writing this post for the benefit of anyone who has had trouble getting php5 to do it's thing when running apache2. I looked at a lot of posts while solving my problem (and a book or two) and here's what I got...

PHP is supposed to be 'invisible' to the end user, that is, the code embedded in the HTML should be processed by the server and the results sent to a browser so the browser never sees any php code.

After I set up Apache and PHP I tried a little 'hello world' script in an HTML file and the result was disappointing. First the browser didn't show any of the PHP generated text and worse, the view source revealed the php script there in the HTML code.

I tore my hair out for several days, starting and stopping Apache and reading over the same pages in my reference books. (I highly recommend 'Practical Guide to Ubuntu Linux' by Mark Sobell). Finally while looking at my /etc/apache2/mods-enabled/php5.conf I found my problem:

This is what I had in mine...
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

The second line appears to define the file extensions which the php5 module will process. Notice that .html ain't in there. I tried copying my index file with a .php extension instead of .html and IT WORKED! My cries of joy frightened the pets.

I opened an editor and added .html to the list like this:

  AddType application/x-httpd-php .php .phtml .html .php3

 and restarted Apache. It worked... Now the PHP in my web pages gets processed correctly.

I hope this will help someone having a similar problem.

Brook Adams

---

### Post by Dr Small on 2008-04-20
Hrm, I never heard of proccessing Php through a Html file, but it looks to me as if you figured out how to do it :D

---

### Post by Oldsoldier2003 on 2008-04-20
the usual solution would be to just add it in .htaccess :)

@DrSmall: its a common hack used to allow people to use ssi and php in html files. Makes it a lot easier for novice webmasters as they dont have to remember to name files with different extensions.

---

