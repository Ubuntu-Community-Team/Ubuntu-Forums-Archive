---
title: "Deleted my old Ubuntu One account made new one and Ubuntu One will not start or sync"
date: 2010-12-02
forum: Ubuntu One (CLOSED)
---

### Post by MechaMechanism on 2010-12-02
EDIT:  Solved by purging One from the computer and deleting all traces of One from home.


Deleted my old Ubuntu One account and made new one and now Ubuntu One will not start or sync.  Always says disconnected.

---

### Post by duanedesign on 2010-12-02
These instructions are for Lucid and Maverick.

**1.** Close the Ubuntu One Preferences if open
**2.** Open (Maverick)
*System -> Preferences -> Password and Encryption Keys*
(Lucid)
*Applications->Accessories->Passwords and Encryption Keys*
**3.** Click on the arrow next to "Passwords"
**4.** Right-click on the Ubuntu One token and select "Delete"
**5.** Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
**6.** Click on the checkbox next to your computer
**7.** Click the "Remove selected computers" button
**8.** Open a Terminal and run the following command:
(Maverick)
```
killall ubuntu-sso-login; u1sdtool -q; u1sdtool -c
```
(Lucid)
```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```
**9.** a ((Maverick)window *or* (Lucid)web page) should open, prompting you to add your computer to your Ubuntu One account
**10.** Add your computer

let us know how it goes,
duanedesign

---

### Post by MechaMechanism on 2010-12-02
It added my computer alright.  It's just not syncing.  I included a screen shot that says disconnected.  Nothing in the Ubuntu One dir syncs as well as dir that I right clicked selected for sync.

---

### Post by r.osmanov on 2011-01-11
Thank you, [[COLOR=#D40000]**duanedesign**[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/member.php?u=686748")! That helped me :)

---

