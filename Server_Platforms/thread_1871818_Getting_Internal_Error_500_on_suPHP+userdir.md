---
title: "Getting Internal Error 500 on suPHP+userdir"
date: 2011-10-29
forum: Server Platforms
---

### Post by kustomjs on 2011-10-29
Hey Guys
I am getting internal error 500 on suPHP+userdir and I checked apache2 error log and its showing me this:  SoftException in Application.cpp:350: UID of script "/home/tzm/public_html/index.php" is smaller than min_uid

but if I go /var/www I get the page saying it It Works!

how do I fix that?

---

### Post by kustomjs on 2011-10-29
I got it fix what I did was delete the old file in public_html and uploaded a new file.

---

### Post by vasile002 on 2011-10-30
the file ownership was wrong probably
The "it works!" appears when there's a forbidden error, it's the default page

---

