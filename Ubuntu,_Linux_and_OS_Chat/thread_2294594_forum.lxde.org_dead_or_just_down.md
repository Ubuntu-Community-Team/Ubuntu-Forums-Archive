---
title: "forum.lxde.org dead or just down?"
date: 2015-09-11
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-09-11
>  It's not just you! [http://forum.lxde.org](http://forum.lxde.org) looks down from hereDoes anyone know? It had a lot of useful posts about lxde and openbox :(

---

### Post by mc4man on 2015-09-12
On the site the blog,wiki & forum don't work, rest do so I'd say down

---

### Post by vasa1 on 2015-09-12
It seems there's a migration in progress ...> Hi List,

I am going to migrate our websites to our new server provided by
GPLHost, also move the current main site (lxde.org) to GitHub by
making the website static to eliminate the effort of maintaining an
old CMS.

Here is my plan:

1. Announce read-only status on wiki and forums.
2. Make a copy of website content and database.
3. Use HTTrack to snapshot lxde.org main site.
4. Move the blog, forums and wiki onto the new server.
5. Upload lxde.org main site onto GitHub.
6. Set the DNS for the websites respectively.

If there's any objections please tell me.

Thanks,
-- 
Yao Wei[http://sourceforge.net/p/lxde/mailman/message/34283370/](http://sourceforge.net/p/lxde/mailman/message/34283370/) from two months ago (From: Yao Wei <mwei@lx...> - 2015-07-10 08:44:04)

---

### Post by vasa1 on 2015-09-22
Here's a post from 20150920 by PCMan (LXDE/LXQt dev):> Dear LXDE/LXQt project members,
As some of you might have noticed, some of our web services, such as wiki, blog, and forum are not accessible for weeks. I'll briefly report what happened and discuss with you about the future of our web hosting.
Previously, these lxde web services are lxc containers running on the server donated by GPLHost.
(The homepages of lxde and lxqt are on github so they are not affected.)
Some time ago, after some system upgrades, the containers are broken because of systemd and kernel related incompatibilities. We are not able to restore the services at the moment without fixing the containers. In addition, we transferred the domain name lxde.org to Gandi and initially the DNS zonefile was not fully updated. (But this has been fixed already)
So the basic plan is re-constructing the lxc containers and restore the services using our backup data, which is very time consuming. 
Luckily, Debian developer Daniel Baumann (dba) who mastering virtualization technologies is willing to help. He has been maintaining thousands of containers at work. ([http://daniel-baumann.ch/](http://daniel-baumann.ch/))
In addition, he also want to donate free hosting to us.
If there are no objections, it seems to be a good idea to move some of our lxde web services to his hosting. He'll help the restoration and future maintenance of the web services.
Please let me know if there are any different opinions or better suggestions.

Thank you!

---

### Post by vasa1 on 2015-11-09
It's back online.

---

