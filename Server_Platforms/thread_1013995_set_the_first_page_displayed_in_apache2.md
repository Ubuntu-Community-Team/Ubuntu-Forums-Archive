---
title: "set the first page displayed in apache2"
date: 2008-12-17
forum: Server Platforms
---

### Post by herbert tamayo on 2008-12-17
I'm coding an app using LAMP, my first page is called="inicio.html" I want that the user can type: [http://localhost/bank](http://localhost/bank) and the page inicio.html is displayed, but if I do that, another page -nologin.php- is displayed.

Now, checking my apache2.conf the line that I change is this:
[PHP]
DirectoryIndex login.php index.php inicio.html
[/PHP]

But still, inicio.html is not recognized as a valid start page -the user has to type: [http://localhost/nomina/inicio.html](http://localhost/nomina/inicio.html)

My question is:
How should I do to tweak apache and it recognize inicio.html as a valid automatic start page?

Regards

---

### Post by doobiest on 2008-12-17
You did restart apache after right?  other than that I'm not sure why it would work

One thing you could do is a redirectmatch which goes in your site's config file in /etc/apache2/sites-enabled, in the Directory section

<Directory /var/www/bank/>
 RedirectMatch ^/$ inicio.html
</Directory>

Something like that.

---

### Post by MJN on 2008-12-17
It certainly should be working.

Indeed, it shouldn't be serving nologin.php as you haven't included that in the DirectoryIndex at all.

Are you sure you haven't specified (and hence overwritten) DirectoryIndex elsewhere in your config?

What happens if you delete nologin.php from the bank/ directory?

Mathew

---

