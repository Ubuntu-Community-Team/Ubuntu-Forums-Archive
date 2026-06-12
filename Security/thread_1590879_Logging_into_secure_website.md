---
title: "Logging into secure website"
date: 2010-10-08
forum: Security
---

### Post by jwh02017 on 2010-10-08
A friend of mine has a private forum setup so he and I can communicate back and forth so we don't have to send emails.  The link is a "https://" so I'm assuming it's secure.  I'm a newbie to ubuntu and I have already switch 3 of my computers at home to ubuntu and I LOVE IT!!!

I'm using Ubuntu 10.04 and google chrome as my browser. 

When I log into his forum it pops up with a screen saying "The site's security certificate is not trusted" and I always click proceed anyways.  I'm not worried about this because I'm 110% sure that it's his website that I'm trying to access.  My question/problem is it also pops up with a little box telling me to enter my Username and Password every time.  When I was using WindowsXP, I had to enter this info once and then I wouldn't have to enter it again.  So is there a way I can tell ubuntu/chrome to save this username and password so I don't have to enter it every time I log into his forum?

I've tried to search the forums, but I really don't know what I should search for.

Thanks,
Justin

---

### Post by The Cog on 2010-10-08
On chrome, click the spanner and under Preferences > Personal Stuff, make sure you have selected "Offer to save passwords". If that doesn't do it, maybe it's because it doesn't trust the site certificate. I don't know how to get a site certificate trusted on Chrome.

---

### Post by jwh02017 on 2010-10-08
> **The Cog said:**
> On chrome, click the spanner and under Preferences > Personal Stuff, make sure you have selected "Offer to save passwords". If that doesn't do it, maybe it's because it doesn't trust the site certificate. I don't know how to get a site certificate trusted on Chrome.Thanks for the reply.  The setting was already set to "save passwords".  I will try it in firefox to see if it'll work in that browser.  

Thanks,
Justin

---

### Post by The Cog on 2010-10-08
On further thoughts, it occurs to me that there is one site (my employer's webmail) that never gets its username/password remembered in either firefox or chrome (never offers to remember). I think it's because the site uses javascript rather than the more normal "basic authentication" for web pages. If that's the case then I don't think there's much you can do about it at all.

---

### Post by jwh02017 on 2010-10-08
I tried it in ubuntu/firefox and it works.  It asked me if I wanted to allow this untrusted exception and I said permanently add the exception.  As I said before it also works in XP/chrome.  

I just done some comparing between the two computers (XP and ubuntu) and it seems I need to add an exception in chrome.  In XP/chrome under the options "Under the Hood" tab there is a button to "Manage Certificates" but in ubuntu/chrome there is no button in this location and there is only a link to this website... [http://code.google.com/p/chromium/wiki/LinuxCertManagement]("http://code.google.com/p/chromium/wiki/LinuxCertManagement")  I'm new to ubuntu so I don't really understand how to add the certificate this way. :confused:

---

