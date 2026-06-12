---
title: "Help with Web development."
date: 2011-04-28
forum: The Cafe
---

### Post by Jonny87 on 2011-04-28
I've recently been teaching myself HTML CSS and now starting on Javascript. But I'm looking for a something in particular at the moment and thought that theres bound to be someone on her who can help.

I after a vistor counter that will count all visitors except the Webmaster/Owner of the page.

Also a counter that will keep track of how many times a file downloaded from the site.

---

### Post by RiceMonster on 2011-04-28
A visitor counter needs to be done with a server side language such as PHP.

---

### Post by SeijiSensei on 2011-04-28
You can count the number of downloads of an object from the command line using the Apache logs:

```
grep 'file.name' /var/log/apache2/access.log | wc -l
```

returns the number of times "file.name" appears in the access log.

If your logs are rotated (so you have files like /var/log/apache2/access.log.1 and so forth) you'll need to replace "access.log" with "access.log*" in the command above.

If you want to display this value on a web page, you'll again need to use a scripting language like PHP.

---

