---
title: "Find what modules Apache doesn't need"
date: 2010-04-15
forum: Server Platforms
---

### Post by wattaman on 2010-04-15
This is a really noob question. I'm trying to figure out what modules I don't need so I can uninstall them. I know some I need, like rewrite, geoip, deflate (those activated by me, basically) but hey're others I have no idea if I use them or not.
I know is a hard question to answer because if I don't know what my site's needs ... how can I ask you? :)
However, I'm hoping there's somewhere a log file with the last used Apache modules, something that (for example) will say: *module fcgid last time used: 01-01-2007* - then I'll know I don't need it.
So, is there something like that?!
Also, is there a way I can find out what other programs I don't (never used) need?

---

### Post by Ryan Dwyer on 2010-04-16
You could disable all the ones you're suspicious about, see what breaks, then enable the ones needed to make it work properly again.

Of course, if this is a production server then you'll want to do this in a development environment.

---

### Post by wattaman on 2010-04-16
> **Ryan Dwyer said:**
> You could disable all the ones you're suspicious about, see what breaks, then enable the ones needed to make it work properly again.

I was thinking of this as an ultimate solution. I have many sites each running its own script and it will take a little time to check them all by disabling module after module :(
So, I suppose there's no log with the last used modules :)

---

