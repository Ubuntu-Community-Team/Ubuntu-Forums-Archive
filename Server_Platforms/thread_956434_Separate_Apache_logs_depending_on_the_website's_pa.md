---
title: "Separate Apache logs depending on the website's path"
date: 2008-10-23
forum: Server Platforms
---

### Post by tengblad on 2008-10-23
Hey folks,
Not sure if this is the right sub-forum to post in, but I thought I'd give it a shot.

I've got a small problem regarding Apache web server logs. The site's general access-log has been configurated to not display requests made for images files. 

However, we want all image request made to one specific path to show up in the log. An example

[http://site.com/test](http://site.com/test)  - This path should not have images logged
[http://site.com/images](http://site.com/images) - This path should have images logged

Is there any easy way to achieve this?

---

### Post by StickyStyle on 2008-10-23
What you want should be possible with conditional logs.

[http://httpd.apache.org/docs/2.0/logs.html#conditional](http://httpd.apache.org/docs/2.0/logs.html#conditional)

Something like...
```

SetEnvIf Request_URI "^/images/.*(\.jpg|\.gif|.jpeg)$" logit
CustomLog logs/images common env=logit

```

may need some playing with since I'm just writing this off the cuff, and don't really know your exact requirements.  But this example would log all image requests into a separate log file, I know its not exactly what you asked for, but it's a start in the right direction.

---

### Post by tengblad on 2008-10-24
Thanks! That looks to be exactly what I was looking for. :) I'll play around some with it and see if I can get it to do what I want.

---

