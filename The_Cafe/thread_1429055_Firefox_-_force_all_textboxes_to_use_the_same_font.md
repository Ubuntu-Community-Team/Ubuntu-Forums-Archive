---
title: "Firefox - force all textboxes to use the same font color?"
date: 2010-03-13
forum: The Cafe
---

### Post by Yes on 2010-03-13
I'm using a kind of dark GTK theme and some textboxes in Firefox use a dark font on a dark background font that's kind of hard to see, but then others use a light font that's easy to read (pictures below).  Is there anyway I can force all textboxes to use the same font color?

In Firefox 3.6, that is.

Thanks!

[img]http://img15.imageshack.us/img15/5104/ex1p.png[/img] [img]http://img651.imageshack.us/img651/1763/ex2.png[/img]

---

### Post by lovinglinux on 2010-03-13
You can either change [userChrome.css](http://ubuntuforums.org/showthread.php?t=503508) or use [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108).

Similar threads: [http://www.google.com/search?q=Firefox+dark+theme+site%3Aubuntuforums.org](http://www.google.com/search?q=Firefox+dark+theme+site%3Aubuntuforums.org)

---

### Post by Yes on 2010-03-13
Thanks, but I've tried all of that.  The closest I can get is using Stylish to change the background color of the textbox in the first picture to white.  But it leaves the second textbox the same color and that looks odd.

---

### Post by jrarrmy on 2011-09-12
Hey, I've looked everywhere, and ended up adding to my userChrome.css ... this:

```
menubar, menubutton, menulist, menu, menuitem {
  color: black !important; 
}



/* Single line text fields */
input {
  /* Set font size and family of text fields */
  color: black !important; 

  /* Set background color to something a little prettier */
  background-color: rgb(200, 255, 220) !important;
}

/* Multi-line textareas */
textarea {
  background-color: rgb(200, 255, 220) !important;
  color: black !important; 
}

```

yet I still have msgboxes that I can barely see the font in...

[http://farm7.static.flickr.com/6210/6140833101_3d48bcdaf9_b.jpg]("http://farm7.static.flickr.com/6210/6140833101_3d48bcdaf9_b.jpg")

any ideas?
thanks

---

