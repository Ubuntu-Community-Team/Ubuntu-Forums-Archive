---
title: "Default HTTP upload location"
date: 2010-05-22
forum: Server Platforms
---

### Post by matt79 on 2010-05-22
I have been trying to make it possible to upload images on my website via a web browser. I have created the HTML form, I can browse to my desktop and upload an image. But my question is, where is it on my server after I upload it? I am running 8.04 on my server.:confused:

---

### Post by Alkaif on 2010-05-22
most likely in the tmp folder.

---

### Post by v1ad on 2010-05-22
if u upload from the web page then its probably in /var/www/html/ and somewhere in there

---

### Post by matt79 on 2010-05-24
In mine I only have /var/www/ and I looked. I used the command "find / -name FILE.JPG" to try to find the file but could not. I also searched the /tmp, /var/tmp locations.

---

