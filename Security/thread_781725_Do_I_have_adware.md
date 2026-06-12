---
title: "Do I have adware?"
date: 2008-05-04
forum: Security
---

### Post by yit on 2008-05-04
This is weird, using firefox 3 beta 5, on some sites like wikipedia, google and ubuntuforums, when I click on a search button with my middle mouse button, instead of doing a search in a new tab, it redirects me to one of various advertising sites. In the address bar it often includes an address that includes some term I have searched for recently. So if I have searched for the town of kolberg recently, it goes to what it claims to be [www.kolberg.com](www.kolberg.com) but it is an IT website called qmatics or a box comes up saying the the url is invalid. I seems to be trying lots of different urls.  This is seems like adware to me but that doesn't make a whole lot of sense. Any thoughts?

---

### Post by aysiu on 2008-05-04
Middle-click pastes whatever's in your clipboard.

---

### Post by yit on 2008-05-04
I thought my middle click was set to open the link in a new tab.  Ha! Thanks!

---

### Post by aysiu on 2008-05-04
> **yit said:**
> I thought my middle click was set to open the link in a new tab.  Ha! Thanks!
It is if you click exactly on the link. But if you happen to slip and click on some empty space by accident, Firefox will attempt to take you to whatever's in your clipboard.

You can disable this behavior by going to about:config and searching for middlemouse.contentLoadURL and double-click it.

---

### Post by lemming465 on 2008-05-04
The other thing that can be going on is that your upstream DNS provider may be playing games which redirect failed URLs to ad sites.

---

