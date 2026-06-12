---
title: "Palette mismatch"
date: 2017-11-03
forum: Ubuntu, Linux and OS Chat
---

### Post by hamiljf on 2017-11-03
This is something odd.  I set the colour of a pane using Python/tkinter to 'navy' and it came out bright blue (unexpectedly).  I checked the X-window definition and it was 0 0 128.  So I checked the CSS colours under Firefox and sure enough 'navy' is #000080 and is a dark blue.  As expected, exactly the same numbers.  So I tried bypassing the X-window definition and set the tkinter pane to #000080.  It looked just the same as before.  Side by side #000080 looked quite different in tkinter and Firefox.  A bit of experiment (it was quite late at night by the time) and I got tkinter #000028 to look about the same as Firefox #00080.

Who is messing with me?  And how are they doing it??  And why???

BTW, I chose a chat forum because I don't really expect 'support', just sympathy.

---

