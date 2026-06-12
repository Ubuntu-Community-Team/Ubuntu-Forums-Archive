---
title: "[SOLVED] Why windows why!"
date: 2008-07-05
forum: Server Platforms
---

### Post by majikhotline on 2008-07-05
Hello ubuntu country,

My super simple web site works only on the local machine, all the links, photos, and a background photo appears normal on the web server.  Now my problem is, only the index page shows on the windows computer that's on the local network.  None of the links work, photo has an empty window with a red X in the top left corner, and the background photo does not show. 

1. What do can I do to fix this 
2. Is this preventable for future sites?
3. How did this happen?

Thanks:)

---

### Post by damis648 on 2008-07-05
Do the links point to a directory on your server computer? You have to specify that it is in the same directory, and not a full path.
Example for a link on the index page to "otherpage":
```
./otherpage.html
```

---

### Post by windependence on 2008-07-05
Unless of course the page IS located somewhere else and it would have to be under the document root to be visible. In those situations you must use the absolute path to the pages. 

For example, if you have pictures in a directory called /pics, you cannot nake a link directly to /pics on your web site because that directory is not under your root directory, typically /var/www. So you could create a directory /var/www/pics and place the pics there or you may be able to create a symlink to the /pics directory also.

-Tim

---

### Post by majikhotline on 2008-07-06
my index page is under /var/www and my pix are in /var/www/images

---

### Post by majikhotline on 2008-07-07
for some strange reason i had to change the permissions on the all website folders

---

### Post by windependence on 2008-07-07
Not a great idea to make them world writable. You should at least try 755.

-Tim

---

