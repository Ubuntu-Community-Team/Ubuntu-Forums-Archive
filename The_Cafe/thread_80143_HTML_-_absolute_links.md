---
title: "HTML - absolute links"
date: 2005-10-21
forum: The Cafe
---

### Post by Steve Smith on 2005-10-21
Within my webspace, I have two separate websites.  If you say do href="/photos.html", it obviously refers to [www.mydomain.com/photos.html](www.mydomain.com/photos.html), rather than [www.mydomain.com/site1/photos.html](www.mydomain.com/site1/photos.html).  I don't want to use href="/site1/photos.html" in case I rename one of the sites.

I tried using

<base href="http://www.mydomain.com/site1/">

along with href="photos.html", which works, but isn't really what w3.org says base is for (see [http://www.w3.org/TR/html401/struct/links.html#h-12.4](http://www.w3.org/TR/html401/struct/links.html#h-12.4)).  In any case, I'm using SSI, which ignores base.

Can anyone think of a way I can make href="/photos.html" point to site1/photos.html or site2/photos.html?

---

### Post by Kvark on 2005-10-21
<a href="photos.html">photos</a> refers to photos.html in the same directory as the current document.

So if you put that link in http://www.mydomain.com/site1/vacation.html then it refers to http://www.mydomain.com/site1/photos.html.

If you on the other hand put it in http://www.mydomain.com/site2/products.html then it refers to http://www.mydomain.com/site2/photos.html.

But isn't this kinda the wrong forum for this?

---

### Post by Steve Smith on 2005-10-21
The probelm is that within each site, I have several subdirectories, and I don't want to go for the whole ../../ thing because if I move a page to a different level in the directory heirarchy, then I have ot update it.

[QUOTE=Kvark]But isn't this kinda the wrong forum for this?[/QUOTE]
Yes - thought I'd just try to pick  someone's brains, that's why I stuck it in chat, hope no one minds!

---

