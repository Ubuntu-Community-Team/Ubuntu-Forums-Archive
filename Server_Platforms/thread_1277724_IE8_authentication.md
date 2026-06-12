---
title: "IE8 authentication"
date: 2009-09-28
forum: Server Platforms
---

### Post by cdenley on 2009-09-28
There are a few directories in apache which I require SSL and basic authentication. This was working fine, but recently I noticed that IE8 will not authenticate. Firefox works fine. IE8 gets a 401 response, just like FF does, but instead of prompting the user for a username and password, it displays a page "Internet Explorer cannot display the webpage". Anyone else have a problem like this?

---

### Post by Vegan on 2009-09-28
IE8 changed the way it works with certificates, go visit the MS forums over here at [http://social.technet.microsoft.com/Forums/en-US/categories/]("http://social.technet.microsoft.com/Forums/en-US/categories/")

---

### Post by cdenley on 2009-09-28
> **Vegan said:**
> IE8 changed the way it works with certificates, go visit the MS forums over here at [http://social.technet.microsoft.com/Forums/en-US/categories/]("http://social.technet.microsoft.com/Forums/en-US/categories/")

It's not a certificate problem. It still happens without SSL. IE8 simply won't do a basic authentication for some reason.

---

### Post by cdenley on 2009-09-29
I just tried with another windows computer, the same version of IE8, nearly identical software entirely, and it works fine. No users have been complaining about any problems, either, so my IE8 must be broken somehow.

---

