---
title: "Best solution for serving images on webserver"
date: 2013-01-27
forum: Server Platforms
---

### Post by tep200377 on 2013-01-27
Hi! I'm to set up a server for hosting only images.It's about 2 million small images, ranging from 10k to 1mb. What is the best setup on a ubuntu server for this?

Should I use:

apache or lighttp?

any suggestions on caching? etc..

Appreciate any help on this matter.

Ps: allso, should i use SSD disk for best performance on files like these, or just depend on cache images in the server memory?

---

### Post by Lars Noodén on 2013-01-27
If you're looking at Apache, then I would read up on [mod_expires](http://httpd.apache.org/docs/2.2/mod/mod_expires.html) and [mod_cache](https://httpd.apache.org/docs/2.2/mod/mod_cache.html).  

There is also a third option for web servers, nginx.  It is the smallest and lightest.

---

### Post by thnewguy on 2013-01-27
Since you're only hosting images, not dynamic content, then I don't think it will make a whole lot of difference which web server you use. Any web service with caching should do the trick just fine.

---

### Post by Jonathan L on 2013-01-27
> **tep200377 said:**
> Hi! I'm to set up a server for hosting only images.It's about 2 million small images, ranging from 10k to 1mb. What is the best setup on a ubuntu server for this?

Should I use:

apache or lighttp?

any suggestions on caching? etc..

Appreciate any help on this matter.

Ps: allso, should i use SSD disk for best performance on files like these, or just depend on cache images in the server memory?

Hi

If you're new to this, my recommendation would be to use the most ordinary configuration first, and only become more exotic if you find it doesn't work out how you need it.

In this particular situation, I'd recommend a completely stock 10.04 or 12.04 server, tick 'LAMP server' during installation, and see how you get on with a straight Apache installation.

With 2 million images, I'd pay a little attention to your file structure -- you don't want 2 million files in one directory.  Without knowing more about your application it's hard to give more than general advice, but a tree of directories organised to give about 1000 images in the bottom directory is pretty usual: 00/11/22/filename.jpg or 2010/01/01/filename.jpg for example.

Who are you serving to?  I wouldn't worry about SSD versus hard disk until you have something working. 

Hope that helps.

Kind regards,
Jonathan.

---

### Post by tgalati4 on 2013-01-27
If you want comments, the ability to add photos, and other plug-ins, then you are looking for a content management system such as [http://drupal.org](http://drupal.org).  I agree, I wouldn't use an SSD because your internet bandwidth will be much slower than any disk drive you use.  CPU and RAM may be important depending on how many simultaneous users you expect to be pulling photos from the site.

---

### Post by anonymouschief on 2013-01-31
You should consider using CDN if you have a high traffic website.

---

