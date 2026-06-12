---
title: "Zen cart: no page style unless .htaccess is renamed"
date: 2007-07-09
forum: Server Platforms
---

### Post by robk86 on 2007-07-09
I installed Zen Cart on my server and the problem is the following:  My cart had messed up style and missing images in the pages.  Apparently the page displays normally if I rename the .htaccess file in the "zen-cart/includes" folder to something arbitrary like ".htaccess-b".  I would really appreciate it if someone could tell me if it is a problem to have no .htaccess file or what I should put in it.

Right my .htaccess  file(now renamed) contains:
```

<Files *.php>
Order Deny,Allow
Deny from all
</Files>

```

 I searched online and found similar topics with no definite solution.  Here is a site given as an example in the zen cart forum topics to show the problem: [http://www.zapink.co.uk](http://www.zapink.co.uk)

---

### Post by Darth Arturito on 2008-02-17
Same problem here.

---

### Post by robk86 on 2008-02-17
Wow, this is an old thread. I don't have zen-cart installed anymore, but I think I just left it without a .htaccess file.

Here is a tutorial I just found on how to fix the problem:
[http://tutorials.zen-cart.com/index.php?article=235]("http://tutorials.zen-cart.com/index.php?article=235")

Also look at the Apache Tutorial for .htaccess files: 
[http://httpd.apache.org/docs/1.3/howto/htaccess.html]("http://httpd.apache.org/docs/1.3/howto/htaccess.html")

I am not that good with configuring Apache, so I don't think I can help much more than that.

---

