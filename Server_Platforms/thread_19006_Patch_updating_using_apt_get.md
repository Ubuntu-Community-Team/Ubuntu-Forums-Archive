---
title: "Patch updating using apt get"
date: 2005-03-09
forum: Server Platforms
---

### Post by user_stu on 2005-03-09
I'm test driving Ubuntu having previously dabbled in Mandrake and Suse. Bother these have an automatic update facility somewhat akin to windows xp.

I want to have no bugs/security issues patched. How do I do this? ie. how do I know what packages I need to update in Ubuntu? Is everything that appears in the list already installed (and therefore I should update everything)?

---

### Post by KLineD on 2005-03-10
It's as easy as 
```
sudo apt-get update
sudo apt-get dist-upgrade
``` 
And that's it.

In hoary, there's the Ubuntu Update Manager that somewhat resembles those services you mentioned, but in the end it's just another, very convenient, frontend to apt with Ubuntu specific functionality.

Also note that if you are running Hoary, the updates are very frequent (and large) since it's in development. In Warty once upgraded you get the usual security updates.

Hope this helps.

---

