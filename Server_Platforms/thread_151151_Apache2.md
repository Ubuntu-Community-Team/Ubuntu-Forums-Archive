---
title: "Apache2"
date: 2006-03-27
forum: Server Platforms
---

### Post by gymsmoke on 2006-03-27
I just finished setting up an Ubuntu 5.10 server.  Looking in the error log, I see this:

[Mon Mar 27 07:03:14 2006] [error] [client xxx.yyy.zz.ww] File does not exist: /var/www/favicon.ico

It seems that this happens every time I access the default page.  Is there a way to clean this up?

Thanks for any assistance you can provide.  I appreciate the help.

---

### Post by invalid on 2006-03-27
How about creating a favicon for the server :)

---

### Post by gymsmoke on 2006-03-27
Umm - okay.  I guess a better question is - what is a favicon and what is its purpose in life?  where is it stored?  you know, the usual n00b queries...

---

### Post by invalid on 2006-03-27
[QUOTE=gymsmoke]Umm - okay.  I guess a better question is - what is a favicon and what is its purpose in life?  where is it stored?  you know, the usual n00b queries...[/QUOTE]
favicon is the little icon in your address bar next to the URL. It's a small image in .ico format that is stored as /var/www/favicon.ico. There are many programs available that will allow you to design one, try a google search and you will get countless resources.

---

### Post by gymsmoke on 2006-03-28
I~
Thanks.  I found a google on this, and setup a favicon.ico and put it in the root dir.  The message is taken care of, but the favicon doesn't show up  (at least not on firefox on my Ubuntu box)... I did read where this seems to be available only under M$ IE and some versions of Netscape.  If that's true, I wonder why Apache would bother even looking for it?

---

### Post by kpgalligan on 2006-03-28
[QUOTE=gymsmoke]I~
I did read where this seems to be available only under M$ IE and some versions of Netscape.[/QUOTE]

This works for firefox too.  Your browser might not be trying for the file since it didn't find one the first time.  Close and open all the browser windows.  Possibly flush the cache or even restart the machine.

[QUOTE=gymsmoke]If that's true, I wonder why Apache would bother even looking for it?[/QUOTE]

To answer this, its the browser thats asking for the file.  The server is just responding.  M$ or not.

---

### Post by gymsmoke on 2006-03-28
K~
Thanks.  I'll give that a shot...

---

### Post by invalid on 2006-03-28
[QUOTE=gymsmoke]K~
Thanks.  I'll give that a shot...[/QUOTE]
Or I think I remember seeing once that you could just add it to your favorites, and refresh the page.

---

### Post by gymsmoke on 2006-03-30
Nada... refreshed the page, reloaded the page, loaded the page in a new instance of firefox... still no icon

---

