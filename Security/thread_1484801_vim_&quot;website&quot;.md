---
title: "vim &quot;website&quot;"
date: 2010-05-16
forum: Security
---

### Post by l3ecl on 2010-05-16
so what exactly happens when i type "vim google.com"?

i know it opens up google.com's source page via vim, but im just curious  on what other subtleties happen. 

-did my machine effectively visit the website? if there was a visitor  count would it +1 or if there was a picture, would my computer have stored it in its cache as a .jpeg?
-would that website's cache be saved in some temporary folder that i'd  have to delete ?
-what out of the box usefulness can u get from doing a "vim website"?

please treat them as rhetorical questions, as im interested in security point of view answers.

---

### Post by Bachstelze on 2010-05-16
Basically, vim uses wget to download the page source to /tmp and then opens that.

> **l3ecl said:**
> if there was a visitor  count would it +1

Depends on how the visitor count is implemented. If it's Javascript, probably not. If it's PHP, yes.

> **l3ecl said:**
> or if there was a picture, would my computer have stored it in its cache as a .jpeg?

No.

> **l3ecl said:**
> -would that website's cache be saved in some temporary folder that i'd  have to delete ?

No.

> **l3ecl said:**
> -what out of the box usefulness can u get from doing a "vim website"?

In most modern websites, none, because the code if often obfuscated with Javascript nonsense. However, it can be used for simple HTML email, for example

---

### Post by OpSecShellshock on 2010-05-16
Sounds like it would be a handy way to be able to look at the source of a page without having to browse to it and render its scripts first.  Probably not necessary for most people, but if you want to check a page for injected scripts (like if you go to a site a lot, but know it's been compromised and want to see if it's been cleaned before going to it again, or if someone you know gets a drive-by and you want to figure out how it happened).

---

