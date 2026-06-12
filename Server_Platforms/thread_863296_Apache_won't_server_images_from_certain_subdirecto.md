---
title: "Apache won't server images from certain subdirectory"
date: 2008-07-18
forum: Server Platforms
---

### Post by Deicist on 2008-07-18
Hi All,

I have a Hardy server setup, and Apache serving a VirtualHost setup from a webroot of /home/myname/Web/

This all works fine, apart from a really weird problem.

I have two folders:

/Web/Sitename.com/Style 

and

/Web/Sitename.com/Ajaxwrapper

Images from the first folder work fine.  Images from the second give a  500 error.  for example, if I have this:

/Web/sitename.com/Style/image.jpg

and

/Web/sitename.com/Ajaxwrapper/image.jpg 

this:

[http://sitename.com/Style/image.jpg](http://sitename.com/Style/image.jpg) displays fine

this:

[http://sitename.com/Ajaxwrapper/image.jpg](http://sitename.com/Ajaxwrapper/image.jpg) gives me a 500 error.

Anyone know what's causing this?

---

### Post by soulresin on 2008-07-18
Hi.

Check /var/log/apache2/error.log for any errors (or wherever you have the error log set for that virtual host).

At first glance, I'd think permissions problem on the Ajaxwrapper directory, but that usually shows up as a 403 rather than 500.  Is there a .htaccess file in that directory that maybe has an error in it?

---

### Post by mbeach on 2008-07-19
is there some other directive doing some extra work on everything in ajaxwrapper?  Perhaps something that wraps the content in a xml tag or two for ajax type calls?

---

### Post by Deicist on 2008-07-19
It was the misconfigured .htaccess :)

Cheers guys.

---

### Post by Kolipoki on 2008-08-19
> **Deicist said:**
> It was the misconfigured .htaccess :)

Cheers guys.

Would be nice to know what you found. Having a hard time right now with a similar issue. I'm testing the photo gallery from the **[Jaws]("http://www.jaws-project.com/")** cms. Works absolutely great and superfast from an intranet, but when I try to access from outside it has a hard time rendering the images, up to the point of not publishing any or any of the page styles. 

Already tried changing different permissions and disabling Rewrite, with no success.

I might be wrong but this suggests a probable htaccess or Apache issue. Any lead will be greatly appreciated. I'd like to give Jaws a chance, before I get stuck and decide to move on to another solution.

Thanks in advance. K.

---

