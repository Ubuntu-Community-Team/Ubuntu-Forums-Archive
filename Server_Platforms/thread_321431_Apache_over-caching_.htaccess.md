---
title: "Apache over-caching .htaccess"
date: 2006-12-18
forum: Server Platforms
---

### Post by Burgresso on 2006-12-18
It seems that apache2 is caching my changes to various .htaccess files. This can be great for production, but I'm constantly tweaking these files in development. Is there a way to force apache to see and do these changes instantly?

I've tried restarting apache. I even restarted the computer just to see...and yep, it still caches. I usually end up having to create a new folder rather, rather wait for apache to make the changes.

thanks,

burgresso

---

### Post by tturrisi on 2006-12-19
It's probably your browser that is saving form input.

---

### Post by Burgresso on 2006-12-20
Thanks tturrisi, but even if the  .htaccess does things like redirect and rewrite the url?

---

### Post by tturrisi on 2006-12-20
By default, when htaccess is enabled on apache, caching of htaccess occurs, but apache is supposed to also check for changes in the htaccesss files anyway.  If yours does not do that then your htaccess probably has conflicting rules somewhere or they are not written correctly.  Firefox, unlike IE, has no setting to disable using the cached temp internet files, which, imho, is a pita when doing any type of development work.  Clear your temp files in firefox each time you make htaccess changes and see if things are any different.

---

