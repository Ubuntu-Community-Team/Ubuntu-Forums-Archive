---
title: "[Solved] Rdesktop mouse pointer disappears"
date: 2015-09-24
forum: Ubuntu, Linux and OS Chat
---

### Post by dan-bolser on 2015-09-24
Thought I'd post this as I couldn't find the answer here. Basically this fixed it for me:
[http://www.paperstreetonline.com/2015/04/09/server-2012-rdesktop-fix-disappearing-mouse-cursor-with-group-policy/](http://www.paperstreetonline.com/2015/04/09/server-2012-rdesktop-fix-disappearing-mouse-cursor-with-group-policy/)

I'm connecting to Windows 8, so I went to the control panel and searched 'mouse', clicked 'Change mouse settings' then clicked "Enable pointer shadow". Hey presto! My mouse pointer is fixed!

I should point out my mouse pointer was 'intermittent' i.e. sometimes gone, sometimes stuck on the 'resize window pointer', etc. Removing the shadow fixed it :-)

---

