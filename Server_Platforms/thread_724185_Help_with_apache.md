---
title: "Help with apache"
date: 2008-03-14
forum: Server Platforms
---

### Post by seepage87 on 2008-03-14
I think this may be a problem with apache, I'm not sure, but every time I got to mysite.org/blog/ (where I've installed wordpress) it forwards me to 192.168.1.103/blog/ (the local address of my server). 

 If I'm in my network than the blog works fine because 192.168.1.103/blog is a reasonable place, so I don't think it's wordpress.  If I'm not in my network I get nothing because 192.168.1.103/blog doesn't exist.  Note that [www.mysite.org/](www.mysite.org/) works fine, it's only /blog that is messing up.

I've tried on a different computer on a different network and the problem persists.  I've also tried reinstalling wordpress with no luck.  Any ideas?  Please help

---

### Post by PmDematagoda on 2008-03-14
This thread has been moved to the Server Platforms section.

---

### Post by seepage87 on 2008-03-14
I thought maybe it was  a weird DNS thing, so I tried visiting my.ip.add.ress/blog/ to the same effect, it just changes it to 192.168.1.103/blog.  Is there some apache config file that would handle forwards like that?  Thanks.

---

### Post by seepage87 on 2008-03-14
I moved wordpress to a new folder and am having the same problem, so maybe it is wordpress since every other folder works well.  Is there a config file that would stick around after I deleted the wordpress folder and extracted a new copy into it?

---

### Post by Dr Small on 2008-03-14
Is there a .htaccess file in the wordpress directory allowing access only from a certain address and denying everything else?

Dr Small

---

