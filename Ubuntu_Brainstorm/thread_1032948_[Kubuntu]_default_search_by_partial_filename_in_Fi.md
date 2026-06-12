---
title: "[Kubuntu] default search by partial filename in Find File tool"
date: 2009-01-06
forum: Ubuntu Brainstorm
---

### Post by skullmunky on 2009-01-06
In Dolphin, the Find File dialog uses wildcard matching for finding files, as in the underlying 'find' command.  That's really handy for people who know about wildcards; but it's not intuitively obvious that you have to search for 

"*.jpg" 

and that searching for 

".jpg"

will give no results.

What about making the default behavior be for the Find dialog to automatically include *'s around the search string, so that entering 'foo' will translate behind the scenes to 

find . -name '*foo*' 

and then include a checkbox to turn wildcards back on?  

I started using KDE with about 10 years as a unix user/coder/admin ... for a very long time I was convinced that the Find File dialog in KDE just didn't work, because I wasn't using the wildcards.  :)

---

