---
title: "Request: Mozilla Sunbird 0.2"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by benplaut on 2005-06-03
i really have no idea why it's not in the repos already  :? 

[http://www.mozilla.org/projects/calendar/](http://www.mozilla.org/projects/calendar/)

---

### Post by jdong on 2005-06-03
Nobody has made Debian / Ubuntu packages for it yet :(

File an "enhancement" bug with Ubuntu or Debian (probably Debian will be a better bet) about this.

---

### Post by benplaut on 2005-06-03
[QUOTE=jdong]Nobody has made Debian / Ubuntu packages for it yet :(

File an "enhancement" bug with Ubuntu or Debian (probably Debian will be a better bet) about this.[/QUOTE]

OK, will do!  :)

---

### Post by BimberiDreamer on 2005-06-04
Hi,

Another (ubuntuforums) thread had this:

[http://www.asoftsite.org/s9y/categories/5-Debian-Sunbird](http://www.asoftsite.org/s9y/categories/5-Debian-Sunbird)

Thought it might help (or at least be of interest).

BTW my attempt to install it under Hoary had dependency issues.

```
Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
```Cheers, Dave.

---

### Post by jdong on 2005-06-04
> 
Though, sunbird is still not ready to go in the debian archives I will provide regular snapshot builds from now on in my experimental archive (be aware that this is nothing for production use; for serious things don’t use packages in there).


So, there's a guy who's making steady progress towards stabilizing it enough to be in Sid.


Considering how Sid's an "unstable" branch anyway, I don't want to officially offer experimental-quality packages, though I welcome someone to try using ubp-build.py to make their own packages ;)


P.S. Bring this up again when you see Sunbird in Sid or Breezy.

---

