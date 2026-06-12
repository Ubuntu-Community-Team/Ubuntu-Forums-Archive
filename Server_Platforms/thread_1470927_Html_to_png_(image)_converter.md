---
title: "Html to png (image) converter"
date: 2010-05-03
forum: Server Platforms
---

### Post by fMads on 2010-05-03
Hey

I'm looking for a program (or script), that can convert html to an image (png)..
I've searched a lot on google, but haven't found anything that actually worked..

Is the anyone that know of a converter, that works on ubuntu server?

I use php, so it could be nice if php could use the program :)

regards
fMads

---

### Post by Ryan Dwyer on 2010-05-03
I doubt there's any software that does it all through PHP. It would need to contain the entire HTML and CSS specification for a start.

One way is to have a machine with a GUI load up the page in a browser and take a screenshot. Some sites do this. They have their main frontend server and a bunch of worker servers to take the screenshots. I imagine that just involves a technical person manually configuring everything.

---

### Post by fMads on 2010-05-03
You probably right.
Hmm, it could be smart if it could be done on my server (without GUI) .. Have you ever heard of anything that could do that?

---

### Post by Ryan Dwyer on 2010-05-03
Nope. Unless Webkit or another rendering engine has the ability to be run from command line and generate an image file.

---

### Post by smeerbartje on 2010-05-04
You can create a virtual machine running XP or a very light-weight Windows installation (do they exist?? ;)) and run [IECAPT]("http://iecapt.sourceforge.net/") from the command line; must do the job from within PHP.

There is another [possibility]("http://code.google.com/p/wkhtmltopdf/"), but I have no experience with that....

---

