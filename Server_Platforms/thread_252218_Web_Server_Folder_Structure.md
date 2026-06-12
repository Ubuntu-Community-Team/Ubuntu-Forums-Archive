---
title: "Web Server Folder Structure"
date: 2006-09-06
forum: Server Platforms
---

### Post by Low-Key on 2006-09-06
I have been trying to install serendipity and gallery2 on my server, but some of the people on the forums mention that my folder structure isnt appropriate and that I should ask on ubuntu forums for the best setup.

I currently use /var/www/ as my root dir, as this is where it defaulted to. But people are saying this isnt secure and that I should use /srv/ for everything:
/srv/domain.com/ftp/
/srv/domain.com/htdocs/
and on and on. Is this the best practice to place all web related things in /srv ?

I am new to all of this and am trying to learn. 

If I should be changing stuff around, do I do so in apache? Where would I look for more information in settings this up properly?

Thanks!

---

### Post by Jussi Kukkonen on 2006-09-06
Maybe you could link to the discussion you had, so people would see what the problem is (just changing the directory can't really make anything more secure...)

---

### Post by Low-Key on 2006-09-06
This is the forum:
[http://gallery.menalto.com/node/54095#comment-198003](http://gallery.menalto.com/node/54095#comment-198003)

is there a standard directory structure that should be used?

Thanks!

---

### Post by Jussi Kukkonen on 2006-09-07
Ah, I see. What they mean is not that you should use a certain directory structure (or that /var/www/ is a bad place for your website). The point is that Gallery2 files should *not* be in your web-accessible dir (/var/www/ in default ubuntu), but somewhere else. I'm guessing this is what the ubuntu packages for gallery2 do by default...

---

