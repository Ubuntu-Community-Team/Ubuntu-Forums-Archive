---
title: "htpasswd, htaccess not working with firefox"
date: 2010-07-21
forum: Security
---

### Post by warda on 2010-07-21
hi,

I have created htpasswd and htaccess to restrict access to the part of the website.

so htpasswd is hidden away on ubuntu and htaccess within the protected directory and configured to use htpasswd.

now, it does work for Interne Explore and Safari but on firefox it goes streight to:

**Not Found**

 The requested URL /secret\sam.html was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at myserver.com Port 80

I googled it and looked up firefox settings but can't work out where the problem lies...

I believe it is firefox side issue as it works for 2 others browsers.

does anyone happend to have similiar problem or knows any solution?

thanks..

---

### Post by anomie on 2010-07-21
[QUOTE=warda]The requested URL /secret\sam.html was not found on this server.[/QUOTE]

Use forward slashes (/) for your URL path.

---

### Post by warda on 2010-07-21
hi thanks that worked!
 
I would think it was firefox fault though it turned up html code issue.
 
anyway why Firefx could not read the site while 2 other webbrowsers could? isnt it kind of on (-) for FF in terms of comatibility and flexibility?
 
thanks

---

### Post by anomie on 2010-07-21
IMO, it demonstrates the opposite. :) Apparently IE and Safari thought it prudent to tweak a mistyped URL, and actually *change* a character. Firefox did what it was told without acting unexpectedly. (I obviously prefer the latter behavior.)

---

### Post by cdenley on 2010-07-21
> **anomie said:**
> IMO, it demonstrates the opposite. :) Apparently IE and Safari thought it prudent to tweak a mistyped URL, and actually *change* a character. Firefox did what it was told without acting unexpectedly. (I obviously prefer the latter behavior.)

+1
Especially when a "\" can be a valid character in a filename, there is no reason for it to be assumed it should be "/".

---

### Post by warda on 2010-07-21
i havan't thought of that this way...
 
i see your points
 
thanks

---

