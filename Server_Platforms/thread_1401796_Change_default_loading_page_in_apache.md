---
title: "Change default loading page in apache"
date: 2010-02-08
forum: Server Platforms
---

### Post by overtone on 2010-02-08
Im not using the server edition right now but this is server related and seemed more suited too this part of the forum than the general help.

im using lamp right now and have php and apache set up right (i think)

but ive two problems. 

1st: The first is how do i change the default page on load up of localhost.
eg when i enter the [http://localhost/](http://localhost/) i get the usual it works symbol.

this is because its loading the index.html file in my var/www/ folder.

i dont want too create another index file, but how do i change the configuration too load up a different one like home.html

2nd: i tried installing sudo apt-get install phpmyadmin 
and for the most part it worked.

but nothign comes up when i go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

how do i change this? what am i doing wrong?

---

### Post by gobbledigook on 2010-02-08
maybe check your apache config file for if there is an option for this... ?

---

### Post by noway2 on 2010-02-08
Certain pages, like index.html and index.php are programmed to automatically load when they are present in a directory.  To load a different file you can specify it as [http://localhost/xxx.html](http://localhost/xxx.html), where xxx is the file name.

It has been a long time since I set up the phpmyadmin, but I seem to recall that there are a few things that you need to configure in one of the files before you can bring up the page.  if I recall correctly, the documentation has pretty clear instructions on what those settings are.

---

