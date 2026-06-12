---
title: "Forcing a server cache update"
date: 2010-12-06
forum: Server Platforms
---

### Post by jhsu802701 on 2010-12-06
I'm working on a web site.  I'm sometimes finding that when I update a file, some mysterious force intercepts my changes and refuses to let me see them.  I have confirmed that this mysterious force is a server cache.  By adding a "?" to the end of the URL, I can see the changes I've made.  Is there a way to somehow force my Internet provider to update the server cache?

---

### Post by cariboo on 2010-12-06
Moved to Server support subform, and jailed way offtopic post.

---

### Post by tgalati4 on 2010-12-06
Are you sure it's your provider's cache and not your local browser cache?  Try clearing your cache on your browser and see if the updated pages show up correctly.

I'm not sure what triggers a stale page on a browser's cache, but minor changes to a page on the server won't often show up until you either clear the browser cache or start a new tab or new browser session.

---

### Post by SeijiSensei on 2010-12-07
> **tgalati4 said:**
> Are you sure it's your provider's cache and not your local browser cache?  Try clearing your cache on your browser and see if the updated pages show up correctly.

I'm not sure what triggers a stale page on a browser's cache, but minor changes to a page on the server won't often show up until you either clear the browser cache or start a new tab or new browser session.

In PHP, I use these commands to stop browsers from caching when needed:

```

header("Pragma: no-cache");
header("Cache-Control: no-cache; must-revalidate");
header("Expires: -1");  

```

You can also tell [Apache]("http://httpd.apache.org/docs/2.2/mod/mod_headers.html") to send custom HTTP headers like these.

---

