---
title: "Apache or Ubuntu Image Caching"
date: 2012-01-19
forum: Server Platforms
---

### Post by renaudclarke on 2012-01-19
Hello,

I've been using ubuntu and apache for ages, although my knowledge of this server is very limited. So that's a credit to how good it is.

I've setup Apache, MySQL & PHP with Webmin. I have recently built a new server using Ubuntu Desktop 10.04 with a 64Bit system.

I'm not sure why but now Apache seems to cache all the images in the website. It doesn't matter which site or why, but we can't stop it from caching.

I've looked in my Apache modules and the cache module isn't on!! I don't really know what to do now??

Can anyone provide any advice?

thanks in advance.

Ren

---

### Post by SeijiSensei on 2012-01-19
> **renaudclarke said:**
> I'm not sure why but now Apache seems to cache all the images in the website. It doesn't matter which site or why, but we can't stop it from caching.

What evidence do you have for this?  Caching usually happens at the browser or in a proxy like Squid.

Take a look at /var/log/apache2/access.log.  Do you see a lot of [304]("http://en.wikipedia.org/wiki/List_of_HTTP_status_codes") replies?  These indicate requests from the browser for objects it already has cached.  The browser asks Apache if the image on the server is newer than the one it has cached and downloads the server version only if its newer or the cached version has reached its end-of-life.

Take a look at [this document]("http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html") for details on how HTTP caching is implemented.

If you want to prevent caching by browsers, you can configure Apache to add custom HTTP headers to control caching behavior.

---

### Post by renaudclarke on 2012-01-19
I actually wanted to update this thread in case anyone else comes across this problem. SeijiSensei's repsonse got me thinking it might not be the Apache causing the issue and infact it might be something else.

I did ommit that I was running the Ubuntu machine as a VM using Virtual Box. The file storage was being served via a shared folder, which was on a Windows Server. 

I moved the files from the shared folder in virtual box onto the local linux machine which then fixed the caching issue. So it must have been the Virtual Box shared folder.

I didn't really want this as a long term solution so I google around a bit to see if I could find a fix:

I then found this post: 
[https://www.virtualbox.org/ticket/819](https://www.virtualbox.org/ticket/819) which has a lead to turning off 'EnableSendfile Off' which is simple enough by adding the line

'EnableSendfile Off' at the very bottom of the apache2.conf. That's it, just add that!

Restart Apache, done.

thanks to SeijiSensei for making me think outside the box. 

Love Ubuntu and the Community. :-)

---

