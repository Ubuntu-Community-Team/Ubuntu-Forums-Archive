---
title: "Display humanclock.com images on my desktop?"
date: 2008-04-10
forum: The Cafe
---

### Post by martinquested on 2008-04-10
Apparently there is a little Windows app that would allow me to see the  current image from humanclock.com on my desktop.

It must be possible to create a similar kind of thing to run every minute and display a/the current image on my Kubuntu desktop.  And, if it fails to connect, to display some pretty image from my own files, so that an incorrect clock is not shown.

Does anyone have any idea how to go about this?  I bet it's really simple so I'm happy just to be given pointers and to figure the details out myself!

---

### Post by elmer_42 on 2008-04-10
I guess you could set up a cron job to wget the image and then set it as the desktop every minute. I can't think of another way, though there probably is. Ubuntu - Linux for Human Clocks.

---

### Post by martinquested on 2008-04-10
Cool.  That's a good start.  Thank you.  What file would I get?  The site seems to need to refer to a cookie with my timezone and other settings stored in it, but I imagine there's a single URL or php call which results in the image I need?  Or do I wget the web page, then parse it for the URL of the current image?  Ideas anyone?

Also, who has some pointers on how to set the KDE desktop image and other settings (e.g. scale&crop)?

Thanks guys!

---

### Post by elmer_42 on 2008-04-10
I have no idea about what file to get. Sorry. Good luck!

---

### Post by Sporkman on 2008-04-10
> **elmer_42 said:**
> Ubuntu - Linux for Human Clocks.

:lol:

---

### Post by martinquested on 2008-04-10
Cool.  I have already made some progress...

Two files needed (could possibly be made into one, but modular was never a bad thing!):

**listimageurls.sed**
```
#! /bin/sed -nf

# Join lines if we have tags that span multiple lines
:join
/<[^>]*$/ { N; s/[      *]\n[   *]/ /; b join; }

t loop
# Print an URL, remove it, and loop
:loop
h
s/.*name="btn" src="\([^"]*\)".*$/\1/p
t loop
```
**get-humanclock**
```
#! /bin/sh
wget --load-cookies=/home/mq/scripts/humanclockcookies.txt http://www.humanclock.com/jsclock.php -O /home/mq/scripts/currenthumanclock.txt
wget `listimageurls.sed /home/mq/scripts/currenthumanclock.txt` -O humanclock.jpg
```

Obviously, you will need sed installed, but it seemed to be there by default for me.  I don't really understand the full sed syntax, but this seems to work.

I copied my mozilla firefox cookies file to humanclockcookies.txt and deleted the irrelevant lines.  (If you haven't been to the site and collected a cookie, you can't look at the clock.)

So all this works and you'd just need to find a way to put it on the desktop as a wallpaper.  However, it's at this point that I discover how small the images are.  That won't look nice at full size!

Maybe I won't bother after all.  Unless someone has a neat idea about how to put it on part of the desktop?


Linux for human clocks indeed!  :)  Well, that was a fun way to procrastinate for an hour.  Better start some work now though.

---

