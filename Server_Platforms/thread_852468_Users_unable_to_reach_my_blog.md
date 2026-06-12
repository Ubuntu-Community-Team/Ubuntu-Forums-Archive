---
title: "Users unable to reach my blog"
date: 2008-07-07
forum: Server Platforms
---

### Post by Shaoline on 2008-07-07
As titled, any user trying to enter my subfolder "wp01" gets a
```

Not Found

The requested URL /wp01/ was not found on this server

```

Strange thing is, they can reach my /var/www folder (the index.html file telling "it works!"), so things can't be all that bad..

But this is out of my knowledge.. :(

And from my workstation, I can surf without any problems at all, to both blog-folder and www root.

---

### Post by hrod beraht on 2008-07-07
So are you saying that [COLOR="Blue"]http://youripaddress[/COLOR] shows /var/www, but [COLOR="Blue"]http://youripaddress/wp01[/COLOR] is completely unreachable?

Bob

---

### Post by Shaoline on 2008-07-07
Only unreachable for external computers, that is.
Strange thing though .. they can access, let's say /var/www/temp - should I create such a folder.

I'm beginning to think there's something wrong or missed with my install of WordPress.
There are a couple of lines one should modify pre-install, and one of them consists of a "localhost" word. Is that maybe what's causing this? The comment says something similar to "In 99% of the cases, you shouldn't need to modify this.."

I'll need to poke more into this tomorrow after work..

---

