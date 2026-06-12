---
title: "Cache or History ?"
date: 2007-05-18
forum: Server Platforms
---

### Post by blmartin777 on 2007-05-18
Can someone explaine this to me. I have been testing an apache2 server. If you change files for your website. Why does a computer that has pulled that website up a lot show files that aren't there anymore, but if I log onto the site from a totally new computer it shows that new changed files. I tried erasing all the cookies, cache, history and restarting, but still shows the old files.

---

### Post by heimo on 2007-05-18
> **blmartin777 said:**
> I tried erasing all the cookies, cache, history and restarting, but still shows the old files.

Let me guess. Is this browser by any chance Internet Explorer?

---

### Post by blmartin777 on 2007-05-18
Actually it is happening on the main three computers that I have been using. One is a Mac/Safari, on is a Ubuntu/Firefox, and the third yes is a XP/IE6. I have not tried rebooting the Mac or the Ubuntu but I have reset the browsers, but I have reset the browser and rebooted the XP machine. But aal other computers pull up the right web pages.

---

### Post by heimo on 2007-05-18
At least in IE you can try hitting CTRL+F5, which should force refresh. Browser caches... What can I say. You can try setting headers and meta headers to minimize too strong caching if it causes problems.
[http://www.mnot.net/cache_docs/](http://www.mnot.net/cache_docs/)

---

### Post by blmartin777 on 2007-05-18
Thanks that did it. Now I know what to do.

---

### Post by blmartin777 on 2007-05-18
How do I do that in Firefox. I just tried a few different refreshes that I got from a google search, but still no luck.

---

### Post by ricrac on 2007-05-18
cntrl + shift + del
 
tools, clear private data

---

### Post by blmartin777 on 2007-05-18
> **ricrac said:**
> cntrl + shift + del
 
tools, clear private data

The ctrl + f5 worked on the XP/IE6 but that computer is outside of my network. The mac/safari and ubuntu/firefox are inside my network at home and I have tried to force refresh them but still no luck. Any other ideas. I even installed another browser on the ubuntu laptop and still the same thing. It is displaying the parked page from the company I bought the domain name from. But any computer outside my network shows the website I have set up?

---

### Post by ricrac on 2007-05-18
Sounds like there could be a proxy cache between you and the net. Could this be the case?

Could also be a dns cache issue. Double check your dns.  Do a dns lookup from inside and outside your net and make sure they're resolving to the same ip.

---

### Post by blmartin777 on 2007-05-18
I don't think it is the dns but am not 100% sure. How can I clear proxy cache between me and the net. I have not done that before?

I don't know if this is worth mentioning. I have dhcp so I am using zoneedit I made and alias saying [www.example.com](www.example.com) and example.com are the same thing just without the www. If I use example.com the site comes up but if I do [www.example.com](www.example.com) I get a parked page from the company I bought the domain name from.

---

