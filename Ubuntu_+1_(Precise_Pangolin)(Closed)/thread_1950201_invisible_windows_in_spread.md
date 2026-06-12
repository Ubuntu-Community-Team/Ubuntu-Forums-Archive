---
title: "invisible windows in spread"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ppd on 2012-03-31
I have been using Precise for a few months now. Although it was always pretty stable I continued facing a severe problem. 
When working with multiple windows I often ended up with a spread where some windows were invisible.

I created a bug report which did not receive any feedback so far. As I'm very much concerned that such a severe bug might get into a final lts release, I wondered if anyone here could confirm this bug.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963164](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963164)

Thanks
ppd

---

### Post by ppd on 2012-04-07
Can anybody who has a spare minute please follow these very simple steps to reproduce on his/her hardware configuration and then add a "affects me too" for the above mentioned bug? This bug is driving me insane...

Steps to reproduce (by Pablo Almeida from the bug report):

> Just have an application with multiple windows opened.
Have them both maximized.
Type Super+Ctrl+D to minimize all windows.
Click the previously maximized application icon. This will bring it up front maximized again.
Click the icon again, to alternate to the other window of the same app.

There you go: invisible window.

Thanks a lot in advance.

---

### Post by mc4man on 2012-04-07
If you are referring to something like in screen where a minimized window shows up blank in the spread then here is an active bug on
(the emblems aren't related, just added to see what they look like in use, in this case Documents was min'ed
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778)

At least here this issue was re-introduced with the upgrade of compiz* from 0.9.7.2-... to 0.9.7.4- ...
Atm on my _using_ install I've reverted all the compiz related packages back to 0.9.7.2-0ubuntu4 & minimized windows are handled correctly in spread

---

### Post by ppd on 2012-04-07
It is not quite the same here. The window is entirely invisible in spread. However the upgrade to the unity 5.10 testing version seems to have fixed this issue. (at least for me)

---

