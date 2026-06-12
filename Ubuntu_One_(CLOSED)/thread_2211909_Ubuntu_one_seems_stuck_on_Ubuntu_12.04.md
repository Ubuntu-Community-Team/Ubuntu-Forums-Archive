---
title: "Ubuntu one seems stuck on Ubuntu 12.04"
date: 2014-03-18
forum: Ubuntu One (CLOSED)
---

### Post by poum2 on 2014-03-18
Ubuntuone had been working on my Ubuntu 12.04 install but for         the last weeks it was giving an "Auth fail" message. Before         anything I just completely uninstalled it, then re installed it.
       Well now it doesn't give me any error message any more, but is         now stuck on "File sync starting...". After a few investigations,         I tried to check the cue and the result is :
       ```
poum@poumbuntu:~$ u1sdtool --waiting | wc -l
129
poum@poumbuntu:~$ u1sdtool --waiting-metadata | wc -l
70
poum@poumbuntu:~$ u1sdtool --waiting-content | wc -l
61
```       
Which would be OK, except that this result has been the same         for 2 days, so I guess there's something wrong here.
       Any tips?
       Thanks in advance!

---

### Post by Irihapeti on 2014-03-18
When you reinstalled, did you also remove the password (in passwords and keys) and the machine name from Devices ("My account" on the U1 website)?

---

### Post by poum2 on 2014-03-20
I just did what granny suggested, but this is now getting weirder, as Ubuntuone wouldn't let me log in. The thing is I know my email / pwd are correct as I log in with them on the Web.
WTF???

---

### Post by kostkon on 2014-03-20
Try [this]("https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/") from the U1 faq, it worked for me.

---

