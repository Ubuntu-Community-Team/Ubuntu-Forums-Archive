---
title: "Creating a start page for epiphany..."
date: 2007-05-14
forum: The Cafe
---

### Post by kragen on 2007-05-14
I want to make myself a start page for epiphany - the default one is getting boring... but I want it to read my epiphany bookmarks and place them on the screen for me nicely.

I've done some ASP development in the past, and so I'm figuring I could pick up php just as easily, which leaves me with one question:

How do I access the bookmarks? I figure there's not going to be a way to access them from inside the browser itself for security reasons, so that leaves somehow accessing someones home directory... I'm probably going to run into some security issues there as well... any ways around them?

Once I can read the file I figure its a simple matter of figuring out the format and learning enough java / php to display them nicely :)

---

### Post by ThinkBuntu on 2007-05-14
Why not just make an HTML page, save it locally, and link it?

---

### Post by kragen on 2007-05-14
Because I change my bookmarks and wanted my homepage to update as well - basically I just want a challenge! :D

Besides, I think its a good idea - whenever you load up your browser you either want to go somewhere you go regularly (so its probably bookmarked), search for something (so I'd find a way to deal with epiphany's search bookmarks), or you want to see the news or something like that (so have RSS feeds shown on there as well)

---

### Post by Mateo on 2007-05-14
The epiphany bookmarks are saved in an XML file in the ~/.gnome2/epiphany directory.  So make a page that displays the XML file and you're good to go.

---

### Post by kragen on 2007-05-14
Wouldn't I have problems accessing that file? Presumably Apache is run under some sort of web process...

Also, would there be any way of telling who was logged in, so I got the right bookmarks? (i'm thinking not...)

---

### Post by qamelian on 2007-05-14
> **kragen said:**
> Wouldn't I have problems accessing that file? Presumably Apache is run under some sort of web process...

Also, would there be any way of telling who was logged in, so I got the right bookmarks? (i'm thinking not...)

Assuming all you want is a local page, presumably saved in your home folder, Apache isn't needed. I've done something similar by creating my own locally stored "portal" with the most common sites I visit linked from that page. Mine isn't linked to my bookmarks, though and doesn't update automatically, because the list of sites doesn't change often.

---

### Post by ThinkBuntu on 2007-05-14
> **Mateo said:**
> The epiphany bookmarks are saved in an XML file in the ~/.gnome2/epiphany directory.  So make a page that displays the XML file and you're good to go.

Just make an xsl page. Contrary to common knowledge, you can load an XSL page on its own without using PHP or anything else to process it, and that's the route to take since this is just one page.

---

### Post by kragen on 2007-05-14
> **ThinkBuntu said:**
> Just make an xsl page. Contrary to common knowledge, you can load an XSL page on its own without using PHP or anything else to process it, and that's the route to take since this is just one page.

Awesome, thanks for the help - I hadn't heard of XSL before now, looks like I've got a lot of reading to do! :D

---

### Post by Dragonbite on 2007-05-14
Epiphany saves it as XML? I know Firefox saves it as HTML.

---

### Post by ThinkBuntu on 2007-05-14
> **Dragonbite said:**
> Epiphany saves it as XML? I know Firefox saves it as HTML.

HTML is now XHTML. XHTML is XML.

---

### Post by ThinkBuntu on 2007-05-14
> **kragen said:**
> Awesome, thanks for the help - I hadn't heard of XSL before now, looks like I've got a lot of reading to do! :D

Not too hard to do. I wish I had a sample handy. Maybe I'll make one for my Firefox Bookmarks this evening. Don't go to Borders (or your local bookstore if you're cool) yet! I have my XSLT book at home and, frankly, I need to brush up on my for-each skills.

---

### Post by Dragonbite on 2007-05-15
> **ThinkBuntu said:**
> Not too hard to do. I wish I had a sample handy. Maybe I'll make one for my Firefox Bookmarks this evening. Don't go to Borders (or your local bookstore if you're cool) yet! I have my XSLT book at home and, frankly, I need to brush up on my for-each skills.For startes you can look at [[COLOR="Blue"]w3schools[/COLOR]]("http://www.w3schools.com/"), they have an [[COLOR="Blue"]XSLT tutorial [/COLOR]]("http://www.w3schools.com/xsl/default.asp")(and a whole mess of other lessons) all for free!

---

### Post by kragen on 2007-05-15
yeah, w3schools is my first port of call for things like this - it's an awesome site.

---

