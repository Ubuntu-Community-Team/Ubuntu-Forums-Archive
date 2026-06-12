---
title: "Password-protecting files and folders"
date: 2013-08-15
forum: Ubuntu One (CLOSED)
---

### Post by Andy3142 on 2013-08-15
One problem with Dropbox is that you can't password-protect files and folders. 

Can I password-protect folders or files in Ubuntu One? I would be using it on both Linux and Windows, so Ubuntu pw-protected folders probably aren't the whole answer.

Many thanks

Andy

---

### Post by Y^2om&amp;#7sgP on 2013-08-15
Have you looked at something like

[http://www.gnupg.org/](http://www.gnupg.org/)

It has front-ends for just about every system there is :P

---

### Post by sudodus on 2013-08-15
> **hattpa said:**
> Have you looked at something like

[http://www.gnupg.org/](http://www.gnupg.org/)

It has front-ends for just about every system there is :P
+1

---

### Post by Andy3142 on 2013-08-15
Thank you, that's interesting, I'll look into it. I'm also still interested in Ubuntu One's native security.

---

### Post by Andy3142 on 2013-08-15
No, that's waaaaay to complex!

---

### Post by sudodus on 2013-08-16
If you want something simpler (but also less secure), you can use zip to make a compressed file and at the same time encrypt it. See ```
man zip
```

       ```
-e
       --encrypt
              Encrypt  the contents of the zip archive using a password which is entered on the termi&#8208;
              nal in response to a prompt (this will not be echoed; if standard error is  not  a  tty,
              zip  will  exit  with  an error).  The password prompt is repeated to save the user from
              typing errors.
```

---

