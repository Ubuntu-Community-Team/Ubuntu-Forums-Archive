---
title: "how to add images on squid error pages?"
date: 2010-04-26
forum: Server Platforms
---

### Post by X1R1 on 2010-04-26
well, title says it all. I want that squid error pages have the company logo. I edited the page called ERR_ACCESS_DENIED but the image doesn't show (image its in the same directory as ERR_ACCESS_DENIED).

I tried png and gif formats to no avail.

Any tips?

Also I found this but I don't get what the writer is saying so I cant do it.

[http://www.creative.net.au/evil/squid_error_image_pages.shtml](http://www.creative.net.au/evil/squid_error_image_pages.shtml)

regards and thanks in advance for the help

---

### Post by Ilalmi on 2010-04-27
As I understand it, you have to do the following:

[LIST]
[*]Put your image file into /usr/share/squid/icons/
[*]Add the following line to /usr/share/squid/mime.conf:
```
\.uwaicon1$     application/uwa-image-1         yourimagefile.gif
```
[*]Put the link into the html code of your error page:
```
<img src="http://proxy.server:3128/squid-internal-static/icons/yourimagefile.gif" />
```
[*]restart squid
[/LIST]

---

### Post by X1R1 on 2010-04-27
hi, thanks for the help, I will try it out and come back with results

---

### Post by X1R1 on 2010-05-04
Best Way I found out to do it is to get the image on a image hosting website like tinypic, imageshack, photobucket etc. 

Once the image is uploaded edit html code of the page and in the place you had the path to your image saved locally, put the absolute path of the image you just uploaded. eg.

```
src= "http://img266.imageshack.us/img266/548/companylogo.png"
```

I will leave this thread open for a while if you have questions, then mark it as solved.

cheers

---

### Post by ghost_ryder35 on 2010-05-04
awesome

---

