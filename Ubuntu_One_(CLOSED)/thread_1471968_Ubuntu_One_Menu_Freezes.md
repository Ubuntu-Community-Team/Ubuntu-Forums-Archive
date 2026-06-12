---
title: "Ubuntu One Menu Freezes"
date: 2010-05-04
forum: Ubuntu One (CLOSED)
---

### Post by gomab2k4 on 2010-05-04
I had Ubuntu One working like a charm prior to upgrading to 10.04. Now, when I select the Ubuntu One icon, the tabbed menu pops up, but it is frozen. When I force it to close and try to restar, it does not re-open. The website with my Uuntu One information pops up, but thats it...I can't even add my computer. I have uninstalled it and reinstalled the program numerous times, but to no avail. Any ideas?

---

### Post by duanedesign on 2010-05-04
there has been a bug that was affecting some people when upgrading to Lucid that prevented them from adding there computer.

   1. close the Ubuntu One Preferences application window (if it's already open)
   2. open your Terminal (located in Applications >> Accessories)
   3. and type the following: 

```
 u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

This should force a web browser to open and put you at [step 2 of the process.]("https://one.ubuntu.com/support/installation/")

---

