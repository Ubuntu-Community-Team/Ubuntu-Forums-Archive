---
title: "how to bypass googles cookie &amp; if use proxomitron a rule to set all to Zeroes"
date: 2007-09-03
forum: The Cafe
---

### Post by nowshining on 2007-09-03
Moved to [http://www.freewebs.com/gutsygibbon/](http://www.freewebs.com/gutsygibbon/)

---

### Post by RAV TUX on 2007-09-03
> **nowshining said:**
> EDIT: to disable google from setting ANY cookies in firefox



EDIT - preferences - privacy - exceptions



type google.com and or [www.google.com]("http://www.google.com") and click block







1st clear all your cookies...
 
if you want 100 pages - all English + Safe search off use this one I already made up:
 
[http://www.google.com/search?as_q=%7E&hl=en&ie=ISO-8859-1&num=100&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=lang_en&as_ft=i&as_filetype=&as_qdr=all&as_nlo=&as_nhi=&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=off](http://www.google.com/search?as_q=%7E&hl=en&ie=ISO-8859-1&num=100&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=lang_en&as_ft=i&as_filetype=&as_qdr=all&as_nlo=&as_nhi=&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=off)
 
you can copy it to your home button when presses it will put a ~ so remove that before inserting a search term and you can disable googles' cookie from hitting your harddrive... :)
 
to do your own do the following
 
Go to google.com
 
set your preferences and when back to the main page put a ~ in the search box, hit search  now copy the url and paste it to your home button in the firefox prefs, etc.. useful and quick if you chose to open last times tabs, etc.. if not just bookmark it.. now go disable cookies from google.. :)
 
for the proxomitron rule if you want the same results / prefs I had do this below - if want other prefs just let me know for now and i'll set em' up for u guys.. :)
 
copy
 
```

[HTTP headers]
In = TRUE
Out = FALSE
Key = "Set-Cookie:"
Match = "PREF=ID="
Replace = "PREF=ID=0000000000000000:FF=4:LR=lang_en:LD=en:NR=100:TM=1115409441:LM=1186961856:S=3-cjb0XZNOmZV8Nu"
 
 

```now open up proxomitron file - merge config files and now at the very bottom check mark merge data from clipboard and now save and you are all set.. :) just do a google search and NO MATTER news/images/web the cookies will go to all zeroes ;)sounds interesting but isn't there a Firefox extension that does this?

I think it's called "Kill Google" or something of that nature?

---

### Post by nowshining on 2007-09-12
yes but if you don't want it installed also this works universally not just for firefox in other words - NOT EVERYONE uses firefox..

---

