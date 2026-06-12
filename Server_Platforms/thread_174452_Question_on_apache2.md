---
title: "Question on apache2"
date: 2006-05-11
forum: Server Platforms
---

### Post by acheun on 2006-05-11
I've installed and started apache2, so far so good.  The default apache page shown up in my browser.

But when I put my own index.html into /var/www/apache2-default, I got a permission forbidden error when I entered the url: [http://localhost/apache2-default/](http://localhost/apache2-default/) or [http://localhost/](http://localhost/).  Pls note that, I was using sudo command to move the file, so the index.html was belongs to root, which was same as other apache2 default html file.

I also thought I might fool apache by renaming my index.html to index.html.en, which was the page that successfull shown to me for the first time.  But it looked like the fool was me.  I still got 401 file permission error.

I haven't changed any default configuration under Ubuntu.

I know I should dig deep about the doc, but I appreciate if there is anyone can give me the direction so I can quickly see my page successfully.  Thanks.

**********************
Sorry, I figure it myself.  The problem is nothing to do with apache, I just forget to do chmod 644 index.html.

---

### Post by und3rtug4 on 2006-05-12
Hi there!

The /var/www/apache2-default folder is only to show that your instalation of apache went good!

On terminal, delete the apache2-default folder, typing:

sudo rm -r /var/www/apache2-default


Then, you might want to add new content to your /var/www (that is your www document root location, You may change it if you want, but, its quite good on /var/www)

Then, I usually change the ownership of the /var/www folder, to my user:usergroup, and then apply the proper permissions!

Dont forget to give 'r' & 'x' permissions for 'others', so that apache2 could read your /var/www/ content!

Hope it helps :mrgreen:

---

