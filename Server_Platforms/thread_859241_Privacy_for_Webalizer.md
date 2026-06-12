---
title: "Privacy for Webalizer"
date: 2008-07-14
forum: Server Platforms
---

### Post by Kolipoki on 2008-07-14
Hihi,

I installed Webalizer last week on a Hardy H. and just realized that the reports seem to be visible to anyone by browsing to the basic URL of the site, plus the /webalizer directory.

Is this supposed to be like that? Or is there a way to block this open view and restrict it only to an authenticated user? I'm still learning the trades for this awesome operating system, so maybe there is something obvious that I haven't taken into consideration.

Thanks in advance for any suggestion.

---

### Post by mrmonday on 2008-07-14
This is the expected behaviour. If you want to only allow certain users to access the pages, you need to protect the /webalizer directory using one of the mod_auth apache modules and a .htpasswd file. I don't know much about this, but have a look at one of the mod-auth* modules at [http://httpd.apache.org/docs/2.2/mod/](http://httpd.apache.org/docs/2.2/mod/) to see what needs doing. Someone else may be able to help more with this.

---

