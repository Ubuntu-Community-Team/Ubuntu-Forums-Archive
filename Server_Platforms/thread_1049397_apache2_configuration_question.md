---
title: "apache2 configuration question"
date: 2009-01-24
forum: Server Platforms
---

### Post by silbermm on 2009-01-24
Does any one have any idea how to configure apache2 to allow urls without extensions? 
Example: 
Instead of this -> [www.example.com/new_page.pl](www.example.com/new_page.pl) 
use this        -> [www.example.com/new_page](www.example.com/new_page)

Thanks

---

### Post by geforce123 on 2009-01-24
Mod rewrite is exactly doing what you need.
The official docs are a bit hard to understand if you're not familiar with regex and apache inner working.

I suggest you read this (including the comments):

[http://www.workingwith.me.uk/blog/software/open_source/apache/mod_rewriting_an_entire_site](http://www.workingwith.me.uk/blog/software/open_source/apache/mod_rewriting_an_entire_site)

and


[http://www.workingwith.me.uk/articles/scripting/mod_rewrite](http://www.workingwith.me.uk/articles/scripting/mod_rewrite)

The first one has a good example file.

Phil

---

