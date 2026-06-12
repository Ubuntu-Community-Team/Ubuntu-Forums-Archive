---
title: "Need help changing short date format"
date: 2006-08-15
forum: Ubuntu System Panel
---

### Post by trenths on 2006-08-15
How do I change the short date format from dd/mm/yy to mm/dd/yy? I live in the states and this is what I'm used to. It throws me off when I'm viewing the dates of my emails to see them posted with the day first. Currently, I have the time zone designated as Los Angeles/America as I live on the west coast of USA.

Steve

---

### Post by Uncle Spellbinder on 2006-08-15
Hmmm.  Mine seems to be set to *mm/dd/yy* by default.

---

### Post by Seryozha on 2006-09-02
did you figure this out?  I would like toi change mine from mm/dd/yy to dd/mm/yyyy

---

### Post by bulldog on 2006-09-02
Look here and read post 511 on the last page.
[http://www.ubuntuforums.org/forumdisplay.php?f=156](http://www.ubuntuforums.org/forumdisplay.php?f=156)

I think this is what your looking for.

---

### Post by Seryozha on 2006-09-02
> **bulldog said:**
> Look here and read post 511 on the last page.
[http://www.ubuntuforums.org/forumdisplay.php?f=156](http://www.ubuntuforums.org/forumdisplay.php?f=156)

I think this is what your looking for.


i dunno if that is a wrong link or im retarded.  probably the latter.  The link just brings up the forum.  i looked at the last page but dont see anything related

---

### Post by Seryozha on 2006-09-02
> **Seryozha said:**
> i dunno if that is a wrong link or im retarded.  probably the latter.  The link just brings up the forum.  i looked at the last page but dont see anything related

thanks to this [thread]("http://www.ubuntuforums.org/showthread.php?t=205383&highlight=date+time+format") i have figured out to change my date format to dd/mm/yy all i have to do is date +%d/%B/%Y from a terminal :D

---

### Post by bulldog on 2006-09-03
> **Seryozha said:**
> i dunno if that is a wrong link or im retarded.  probably the latter.  The link just brings up the forum.  i looked at the last page but dont see anything related

Yep wrong link sry.

[http://www.ubuntuforums.org/showthread.php?t=222546](http://www.ubuntuforums.org/showthread.php?t=222546)
post 511

Hope this will work.

---

### Post by Peebo on 2007-01-04
To make a permanent change to your date format system wide edit /etc/environment

Look for the line that starts with
LANG="

For DDMMYYYY change it to

LANG="en_GB.UTF-8"

For the very stupid USA format    MMDDYYYY

LANG="en_US.UTF-8"

There are other formats e.g.      YYYYMMDD

LANG="en_DK.UTF-8"

Hope this helps

](*,)

---

### Post by sizzlor on 2007-01-27
> **Peebo said:**
> To make a permanent change to your date format system wide edit /etc/environment

Look for the line that starts with
LANG="

For DDMMYYYY change it to

LANG="en_GB.UTF-8"

For the very stupid USA format    MMDDYYYY

LANG="en_US.UTF-8"

There are other formats e.g.      YYYYMMDD

LANG="en_DK.UTF-8"

Hope this helps

](*,)

wouldn't this change 'everything' to the language you pick (e.g. names of days, etc.) ?

---

### Post by Malac on 2007-01-28
> **sizzlor said:**
> wouldn't this change 'everything' to the language you pick (e.g. names of days, etc.) ?
Yes it would but I think that is what the O.P. was after. Even though it was posted in this forum I think it was actually a general enquiry about Gnome.

---

