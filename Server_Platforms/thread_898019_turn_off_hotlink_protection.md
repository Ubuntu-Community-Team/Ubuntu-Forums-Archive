---
title: "turn off hotlink protection"
date: 2008-08-22
forum: Server Platforms
---

### Post by Meph1st0 on 2008-08-22
Can someone help me turn off hotlink protection in a subdirectory of my web root?  I read an article [Here]("http://perishablepress.com/press/2007/11/28/three-ways-to-allow-hotlinking-in-specific-directories/") talking about creating an .htaccess file in the directory that I want to enable hotlinking from.  So I did that but it's not working.

Can anyone hotlink to [http://www.thebrowndomain.com/noduhzone/images/border.jpg](http://www.thebrowndomain.com/noduhzone/images/border.jpg) ?


I put a .htaccess file in the images folder so that I could hotlink to my pics there on a different web site.  

The file has the following code in it:
```
# disable hotlink protection
RewriteEngine off
```

I then restarted my server just in case I needed to restart the apache service.

Am I missing something else I need to do?

---

### Post by windependence on 2008-08-23
I'm sorry, I'm not sure what you are referring to as "hot linking". Are you pulling in remote images from a php script or something similar?

-Tim

---

### Post by Meph1st0 on 2008-08-23
No, I'm not using any sort of php script or anything of the sort.

I'm just hosting my images on my own personal apache web server.

Then at a different web site, (we could even say myspace or whatever) I'm trying to display those images by using an img tag.  <img src="mywebserver.com/images/theimageIwanttodisplay.jpg"/>

"hotlinking" is direct linking to a web site's files (images, video, etc.). An example would be using an <img> tag to display a JPEG image you found on someone else's web page so it will appear on your own site, eBay auction listing, weblog, forum message post, etc. 


Another example of hotlinking is what's done at Photobucket.com.  You can upload your images and then hotlink to them to display them on a different site.  

Apache web server has hotlinking disabled by default.  And I can understand the reasoning behind it but I just want to permit hotlinking for a certain folder, not necessarily for my entire web site.

---

### Post by windependence on 2008-08-23
OK, now that I know what you are doing, I think you might be able to put the directive in an .htaccess file inside the directory instead of turning it on globally. What do you think about that? 

-Tim

---

### Post by Meph1st0 on 2008-08-24
Well that is actually what I've done.  I placed an .htaccess file containing the following code in my images folder.

```
RewriteEngine on
RewriteCond %{HTTP_REFERER} .
RewriteCond %{HTTP_REFERER} !^http://([^.]+\.)?thebrowndomain\. [NC]
RewriteCond %{HTTP_REFERER} !^http://21601.synsport.com\. [NC]
RewriteCond %{HTTP_REFERER} !google\. [NC]
RewriteCond %{HTTP_REFERER} !search\?q=cache [NC]
RewriteCond %{REQUEST_URI} !^/hotlink\.png$
RewriteRule \.(gif|jpg|png)$ /hotlink.png [NC,L]

```

The [http://21601.synsport.com](http://21601.synsport.com) is the url that I want to give access to hotlink to these images.

I'd rather not turn off hotlink protection globally if I don't have to.  Can you see anything wrong with my .htaccess file?  By the way, I really do appreciate you helping me with this.

---

