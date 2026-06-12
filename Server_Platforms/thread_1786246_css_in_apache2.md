---
title: "css in apache2"
date: 2011-06-19
forum: Server Platforms
---

### Post by Jugg on 2011-06-19
I have put together a personal website. I am trying to use apache2 as my server however when i go to [http://localhost](http://localhost) it does not display correctly. Neither the .css or .js files seem to be getting read. Any help would be appreciated.

---

### Post by Lars Noodén on 2011-06-19
It's probably a mistake in the HTML.  Try installing HTML Tidy or using another HTML validator.  That's the first step.  Tidy is like a spellchecker for your HTML.

---

### Post by Jugg on 2011-06-19
I checked my error logs (I should have done that immediately), it says that permission to the directory with my styles is denied. How can I fix that?

---

### Post by craigcrawford114 on 2011-06-19
Check the permissions on the directories.

---

### Post by Jugg on 2011-06-19
thanks, that did the trick

---

### Post by crispy_420 on 2011-06-22
Solved? I just replied to your other thread...

---

