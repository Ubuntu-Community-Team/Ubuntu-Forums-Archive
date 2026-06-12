---
title: "phpwiki"
date: 2008-01-07
forum: Server Platforms
---

### Post by orgrimdoom on 2008-01-07
I have set up phpwiki, and it is running however (icafedcgaming.com/phpwiki) however, when you actually use the wiki,it redirects to the site icafedcgaming.com/phpwikihttp://icafedcgaming.com/phpwiki/index.php

etc etc. so it adds it AFTEr the current address, which is just weird . . . 

anyone know where i can go to fix this in the scripts???

ty ^^

---

### Post by cdenley on 2008-01-07
I've never used phpwiki before, but looking at the html source code, I'm guessing that for some reason, it uses full url's instead of relative url's, and there is a configuration setting for the server's url where you put "www.icafedcgaming.com/phpwiki" instead of "http://www.icafedcgaming.com/phpwiki", probably in config.php.

---

### Post by orgrimdoom on 2008-01-07
i checked through config.php but couldnt find anything >< i dont know php amazingly well so i guess that is a slight handicap :( but from what i knew i couldnt find anything

---

