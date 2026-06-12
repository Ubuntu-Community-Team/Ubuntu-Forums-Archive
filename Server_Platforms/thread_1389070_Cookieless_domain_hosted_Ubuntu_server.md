---
title: "Cookieless domain hosted Ubuntu server"
date: 2010-01-23
forum: Server Platforms
---

### Post by wattaman on 2010-01-23
Hi!
I was wondering if any of you knows how to set up a cookieless domain to serve static content of other sites hosted on the same server. As far as I've (recently) learned using the Yslow tools from Yahoo, it is better to serve static content from a separate domain which doesn't send cookies to the browser (therefore the name, *cookieless domain*)
So, what I've done was to create a subdomain of my main site and I'm planning to move there all the static content (css, js, jpg etc). That part I've got it.
However, I don't know about the 'cookieless' thing. Do I have to change something in the apache config. file for that subdomain so it won't send cookies, never. Or I must add a few lines in the htaccess file, maybe? Or maybe, because the subdomain will server only static content, there's no need to change anything 'cause the static content don't need cookies !?! :confused:
Can somebody advice me on this, please?
Thank you!

---

### Post by BkkBonanza on 2010-01-24
AFAIK Apache doesn't send cookie headers at any time unless they are set by the script returning content. You may not do it in your code overtly but languages like PHP will set one automatically for session support.

You can use Firefox, Tools, Page Info, Security, View cookies to see what cookies are being set on a page. For checking images and content embedded in pages you can use the Firebug "Net" panel. By clicking on each content item listed you can see it's request and response headers to check if a cookie is present.

---

### Post by wattaman on 2010-01-24
> **BkkBonaza said:**
> AFAIK Apache doesn't send cookie headers at any time unless they are set by the script returning content. You may not do it in your code overtly but languages like PHP will set one automatically for session support.

You can use Firefox, Tools, Page Info, Security, View cookies to see what cookies are being set on a page. For checking images and content embedded in pages you can use the Firebug "Net" panel. By clicking on each content item listed you can see it's request and response headers to check if a cookie is present.

OK, just to make sure I've understood: cookies are send back to the browser only by dynamic pages and not by static files like images or css files, right? Therefore, I don't have to do any settings to the cookieless domain, all I must do is make sure it is hosting static files.
Please confirm this.
Thanks for your help!

---

### Post by Ryan Dwyer on 2010-01-24
Javascript can set cookies.

But really, this isn't worth changing unless you have a huge amount of traffic like Facebook. You're only saving a couple of bytes per request. And you need prior knowledge of how cookies work and which of your scripts are setting them.

---

### Post by BkkBonanza on 2010-01-24
> **wattaman said:**
> OK, just to make sure I've understood: cookies are send back to the browser only by dynamic pages and not by static files like images or css files, right? Therefore, I don't have to do any settings to the cookieless domain, all I must do is make sure it is hosting static files.
Please confirm this.
Thanks for your help!

I believe this to be correct. You should use Firebug to check yourself because for all I know your config is different in some way. In my experience images and such don't have cookie headers. I checked on my pages here and that's what I see, so it's likely the norm since I didn't make any special changes for this.

---

### Post by wattaman on 2010-01-24
Thanks everyone! I'm starting to understand now :)

---

### Post by Vegan on 2010-01-24
Cookies are used by the web application not the Apache server. phpBB uses them a lot to track user names and last read messages etc.

Not unlike the way this forum works.

---

### Post by ICEB3AR on 2010-01-24
already said. sorry for post.

---

### Post by HighCommander540 on 2010-01-25
Yeah, like everyone else has said. Your scripts need to set the cookies for them to be served. So things like CSS, Images, pure HTML, and stuff like that don't create cookies.

So for instance websites like myspace and facebook for that matter. Have all the images and stuff like that on another server with a different subdomain. To make it a bit faster.

---

