---
title: "Apache and PHP: dowloads file instead of displaying. Why?"
date: 2009-08-26
forum: Server Platforms
---

### Post by lduperval on 2009-08-26
Hi,

What causes apache to try and download a php file instead of parsing it? It looks to me like everything is installed and configured correctly, yet, it doesn't work.

Can anyone help?

Thanks,

L

---

### Post by Sporkman on 2009-08-26
Does the file end in .php ?

---

### Post by lduperval on 2009-08-26
Yes. But instead of displaying the index.php file, it opens it in my text editor. It's probably a minor config issue but I can't figure it out.

Thanks,

L

---

### Post by Sporkman on 2009-08-26
How are you accessing the file? Is it on a remote computer, which you are navigating to in a browser via URL?

---

### Post by lduperval on 2009-08-26
No it's on my local computer: [http://localhost/index.php](http://localhost/index.php)

L

---

### Post by Sporkman on 2009-08-26
Sorry, no idea.

You could try putting an html file in the same directory & see if that's served up correctly, don't know where to go from there.

Also, maybe try a different browser.

---

### Post by lduperval on 2009-08-26
HTML works correctly. I tried Chrome and Epiphany and it works in both. So I guess it's something with my FF installation. Well, the workaround is enough for me for the time being. I'll figure out the rest some other time.

Thanks!

L

---

