---
title: "PHP in html not working?"
date: 2012-03-12
forum: Server Platforms
---

### Post by MG&amp;TL on 2012-03-12
Hello everyone! First visit to the server platforms area.

Anyway, I'm trying to setup Apache and PHP, as described by the ubuntu wiki page on LAMP.

My problem being that php in itself works (if I have a .php file), but if I have a .html file like this:

[HTML]
<html>
<body>

<?php
echo "Hello World";
?>

</body>
</html>  [/HTML]then absolutely nothing shows up in the web page. 

What am I doing wrong?

---

### Post by CharlesA on 2012-03-12
You need to create or modify the .htaccess file to allow php to parse and run any php it finds in html files because it doesn't do that be default.

[http://php.about.com/od/advancedphp/p/html_php.htm](http://php.about.com/od/advancedphp/p/html_php.htm)

Sidenote: To be complaint to HTML standards, you still need <head> </head> and <title> </title> tags.

---

### Post by MG&amp;TL on 2012-03-12
Thank you, Charles A. Most kind.

Unfortunately, the .htaccess file does not work. I am assuming it has to be in the same directory as the source (?) html files?

But thank you for your explanations, I may just use .php from now on. More of a learning project than an actual site.

Sidenote: I realise, just an example, but thank you for the hint. :)

---

### Post by CharlesA on 2012-03-12
I tried what you are doing now, but decided just to use.php instead of html. I'm not sure why .htaccess isn't working, is this a shared webhost or your own?

---

### Post by MG&amp;TL on 2012-03-13
> **CharlesA said:**
> I tried what you are doing now, but decided just to use.php instead of html. I'm not sure why .htaccess isn't working, is this a shared webhost or your own?

It's my own local webserver. Just learning, really.

---

### Post by mcduck on 2012-03-13
Have you added the "AllowOverride All" -option in your web site configuration? Apache doesn't accept overriding settings with .htaccess file by default, you need to specifically allow it.

---

### Post by MG&amp;TL on 2012-03-13
> **mcduck said:**
> Have you added the "AllowOverride All" -option in your web site configuration? Apache doesn't accept overriding settings with .htaccess file by default, you need to specifically allow it.

Ahah! That worked. I'll probably just stick with .php as Charles A suggested, but thanks everybody! Thread solved.

---

