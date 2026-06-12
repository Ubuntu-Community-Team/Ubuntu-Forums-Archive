---
title: "Indicator session Restart menu not appear in HUD."
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by serdotlinecho on 2012-09-17
Hi, i'm using HUD to shutdown my pc. Press Alt, type in sh, enter, enter. Done. That's how i did on Precise Pangolin.
(Am I the only one who uses HUD to turn off the pc?). 
But on Quantal Quetzal, now i need to type off, Enter, Enter.  
There is new menu in indicator session which is Restart, but i found that the Restart menu is not appear on HUD? :confused:

---

### Post by dino99 on 2012-09-17
changelog of one of the latest version:

indicator-session (12.10.2-0ubuntu1) quantal; urgency=low

  * New upstream release:
    - Add an 'Online Accounts' menuitem (lp: #1044464)
    - Add disposition highlighting to the indicator icon (lp: #1044015)
    - Remove the Restart button from the shutdown dialog (lp: #1027952)

 -- Sebastien Bacher <seb128@ubuntu.com>  Fri, 31 Aug 2012 19:38:05 +0200

---

### Post by serdotlinecho on 2012-09-20
Here some screenshots:

---

### Post by jbicha on 2012-09-21
dino99, that changelog is referring to the pop-up shutdown confirm dialog showing a restart button.

serdotlinecho, please file a bug about that issue: ubuntu-bug indicator-session

---

### Post by fluteflute on 2012-09-28
> **jbicha said:**
> dino99, that changelog is referring to the pop-up shutdown confirm dialog showing a restart button.

serdotlinecho, please file a bug about that issue: ubuntu-bug indicator-session

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1058148](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1058148)

---

