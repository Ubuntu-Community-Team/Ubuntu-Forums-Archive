---
title: "Apache &quot;It Works!&quot; page keeps coming up"
date: 2010-08-20
forum: Server Platforms
---

### Post by swraman on 2010-08-20
Hi,

I have a problem when I try to view my root directory of my website.

if I go to [http://localhost/](http://localhost/) on my computer, it always loads the "It Works!" page.  I deleted the original index.html page, and even replaced it - but if I go to [http://localhost/](http://localhost/) it KEEPS coming up!

If I specify the page I want to view, ie. [http://localhost/index.html](http://localhost/index.html) it loads the right file.

Is there a setting in the conf file that Im missing?

Thanks

Raman

---

### Post by Queue29 on 2010-08-20
Did you try refreshing your browser/ deleting saved history etc.?

---

### Post by Project_Pat on 2010-08-20
I HAD THE EXACT SAME PROBLEM!
go to etc/apache2/sites-enabled and rename that 000-default file to something for you (mywebpage for example) and that seemed to fix it and inside that file has all the info for where the files are and stuff liek that

---

### Post by swraman on 2010-08-21
Wow.  Now I feel dumb.

Clearing the browser history did the trick.

Im surprised the file was so presistant though.

Thanks

Raman

---

