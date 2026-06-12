---
title: "Viewing directories containting images."
date: 2009-03-22
forum: Server Platforms
---

### Post by robfindlay on 2009-03-22
I have apache2 setup on ibex and i have a script that moves and renames my webcam images to a "history" directory. 

Thing is, I can see the images if I specify the absolute path and file name to a jpg, but when I try to view the bare directory i get a permission denied. 

Do I just need to chmod 777 the history directory and restart apache?  Or better yet does anyone know of a way to dynamically create an html index page that updates or reindexes all of the images?  

I wonder if Gallery can do it?


-Rob

---

### Post by windependence on 2009-03-22
Gallery is very good. 

Word of caution. It's not good practice to just chmod everything you can't get into to world writable. It's more likely an ownership issue than it is a permissions issue.

When you say "view the bare directory", what do you mean? Exactly how are you displaying the directory in each case? I'm a bit confused, but then again I have been known to do that. :)

-Tim

---

### Post by robfindlay on 2009-03-22
> **windependence said:**
> Gallery is very good. 

Word of caution. It's not good practice to just chmod everything you can't get into to world writable. It's more likely an ownership issue than it is a permissions issue.

When you say "view the bare directory", what do you mean? Exactly how are you displaying the directory in each case? I'm a bit confused, but then again I have been known to do that. :)

-Tim

example:

[http:///url.com/history/](http:///url.com/history/) 

I would like to just see a plain list of everything in "history." from my browser.

---

### Post by windependence on 2009-03-22
Where is your document root for this directory?

So what you are saying is you can view the directory from the command line, but not from a web browser, correct?

-Tim

---

### Post by robfindlay on 2009-03-22
> **windependence said:**
> Where is your document root for this directory?

So what you are saying is you can view the directory from the command line, but not from a web browser, correct?

-Tim

The document root in /etc/apache2/sites-available/default is 

/home/slag/www/

So the directory in question is: /home/slag/www/history with: drwxr-xr-x settings. 

I can read and write in that directory, i can even specify a filename inside the history dir and it will display it.  What it wont do is display JUST the contents from that directory via the browser.

Does that make sense?

-Rob

---

### Post by robfindlay on 2009-03-22
> **windependence said:**
> Where is your document root for this directory?

So what you are saying is you can view the directory from the command line, but not from a web browser, correct?

-Tim

An example: 
[http://phundlecam.dyndns.org/history/](http://phundlecam.dyndns.org/history/) = 403 Forbidden
You don't have permission to access /history/ on this server.

however: [http://phundlecam.dyndns.org/history/03.22.09-08.14.43.jpg](http://phundlecam.dyndns.org/history/03.22.09-08.14.43.jpg)

Opens just fine.  I'm trying to get rid of the 403, i've chmod 777 the history and www directories and restarted the server with no change.

-Rob

---

### Post by windependence on 2009-03-22
You need to turn on directory listings in your apache2.conf file. You may also want to turn on fancy indexing to make it look good. 

BTW, the first link brings me up a page full of thumbnails. The second one directly to the jpg gives me a 404 error. 

You will definitely want to change those directories back to 755 or maybe even tighter because you are inviting yourself to be seriously hacked. 777 is a no no unless you are on your private LAN. Even then, I usually do 775. I don't want just anyone to be able to have write access and that's what you are doing, opening it to the world.

-Tim

---

### Post by robfindlay on 2009-03-22
> **windependence said:**
> You need to turn on directory listings in your apache2.conf file. You may also want to turn on fancy indexing to make it look good. 

BTW, the first link brings me up a page full of thumbnails. The second one directly to the jpg gives me a 404 error. 

You will definitely want to change those directories back to 755 or maybe even tighter because you are inviting yourself to be seriously hacked. 777 is a no no unless you are on your private LAN. Even then, I usually do 775. I don't want just anyone to be able to have write access and that's what you are doing, opening it to the world.

-Tim

I found a proggy that will create nice HTML structures for me on the fly, I guess I'm good.

I chmod'd everything back :-) 

Thanks again!

-Rob

---

