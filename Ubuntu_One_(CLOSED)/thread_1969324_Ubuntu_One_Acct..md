---
title: "Ubuntu One Acct."
date: 2012-04-29
forum: Ubuntu One (CLOSED)
---

### Post by rosswmcgee on 2012-04-29
When I set up my wife's Ubuntu One acct. I misspelled the account name. So I 

went to account info and edited it on line. The changes are fine there but 

when I open Ubuntu One the misspelled name still appears. How to correct?

---

### Post by hakermania on 2012-04-30
Hm, I searched this a little bit, as it seems, ubuntu one - and it's logical - only once check for account name and then it stores it locally.
I searched the code of ubuntuone so as to discover where this name is being saved but I wasn't so lucky (I searched for the string 'Hi' that it displays before the name, e.g. 'Hi Fotis Maloukis', and I found that the name in fact is stored in a variable called 'user_display_name' but I searched the file and -being a noob in python- I couldn't find where it was defined or how (there was simply not other reference to the same file for this variable, so it was probably defined in other file which I couldn't find).

---

### Post by rosswmcgee on 2012-04-30
Gee Whiz thanks for taking the time to research it. I guess I would have to do an entire re- install just to fix a spelling error.

---

### Post by nothingspecial on 2012-04-30
*Thread moved to **Ubuntu One**.*

---

