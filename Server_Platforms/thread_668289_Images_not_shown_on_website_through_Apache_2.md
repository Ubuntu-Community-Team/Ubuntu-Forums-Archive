---
title: "Images not shown on website through Apache 2"
date: 2008-01-15
forum: Server Platforms
---

### Post by lucas4ce on 2008-01-15
I have apache 2 running on unbuntu desktop 7.10.  Initially I had a problem with php not being parsed, but thanks to these forums I've solved that one.

My current problem is that images are not showing up on one of my sites.  The images are sized correctly and in the right place etc, but it's as if the images (in this case some gif files) don't exist.

Everything for the site, html, css, images etc is in the var/www folder.

Any help would be great.

---

### Post by MJN on 2008-01-15
Can you show us the output of **ls -l /var/www/** and the relevent portion of the Apache error log?
 
Mathew

---

### Post by lucas4ce on 2008-01-15
Hi,

looked up the permissions as you asked and everything is... 

          -rwxrwxrwx 1 1001 1001 

..except the apache default folder which is

           drwxrwxrwx 2 root root

Will there be an error log for this?  If so where might I find that?

Thank you.

---

### Post by MJN on 2008-01-15
It depends on the ErrorLog directive in your Apache config. I think the default something like /var/log/apache2/error.log

Mathew

---

### Post by crouton on 2008-01-17
Check to make sure your image filenames are in the correct case - upper or lower.  image.jpg is not the same as image.JPG. :)

---

### Post by lucas4ce on 2008-01-17
GENIUS GENIUS GENIUS!!!

Thank you both that did it!!

The error log said file does not exist, and the file extensions were in uppercase, I'm guessing that happened when I copied the images across from a windows computer?!

Replaced the GIF with gif and it all works great now.

Thanks again!!!

---

