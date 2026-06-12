---
title: "filename w/date &amp; time in ubuntu/windows"
date: 2008-09-08
forum: Windows
---

### Post by magicmt on 2008-09-08
in ubuntu i want to have filenames with the date and time added to them. i know i can do this by doing filename-$(date +%F-%T).mpg

the result looks nice in ubuntu
TV_Recording-2008-09-08-18:04:47.mpg

but not so nice in windows...
THMZAH~O.MPG

this is probably because windows doesn't understand -$(date +%F-%T). how do i adjust the filename so it'll also work in windows?

---

### Post by iaculallad on 2008-09-08
Duh, why not try asking that question on windoze forum. As you could see, you're logged onto Ubuntuforums.org w/c tackles more on Ubuntu/*Linux questions.

---

### Post by overdrank on 2008-09-08
> **magicmt said:**
> in ubuntu i want to have filenames with the date and time added to them. i know i can do this by doing filename-$(date +%F-%T).mpg

the result looks nice in ubuntu
TV_Recording-2008-09-08-18:04:47.mpg

but not so nice in windows...
THMZAH~O.MPG

this is probably because windows doesn't understand -$(date +%F-%T). how do i adjust the filename so it'll also work in windows?

Hi and welcome, 
Moved to windows discussion. :)

---

### Post by ilrudie on 2008-09-09
> **magicmt said:**
> in ubuntu i want to have filenames with the date and time added to them. i know i can do this by doing filename-$(date +%F-%T).mpg

the result looks nice in ubuntu
TV_Recording-2008-09-08-18:04:47.mpg

but not so nice in windows...
THMZAH~O.MPG

this is probably because windows doesn't understand -$(date +%F-%T). how do i adjust the filename so it'll also work in windows?

I have done something like this with windows server 2003.  The problem I came across is the date/time format in windows is stored in the registry (wouldn't be windows if it wasn't), contains a delimiter that is not valid in a filename (my file was just cut off after the first instance of the delimiter), and I could not find a way to modify the format anywhere other than the registry.  I don't recall the final solution I worked out but it changed the date/time format for the whole server so I imagine its in hklm.  I just searched around on google for a while and found where the format lives.

---

### Post by magicmt on 2008-09-09
i got it. windows doens't like colons in the filename. so the solution is to just use another date function for the time that doesn't have colons, like:

TV_Recording_$(date +%m.%d.%Y_%I.%M%P).mpg

looks uglier, but it works

---

