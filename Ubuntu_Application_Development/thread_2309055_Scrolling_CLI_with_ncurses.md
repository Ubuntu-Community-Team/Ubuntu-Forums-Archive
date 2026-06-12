---
title: "Scrolling CLI with ncurses"
date: 2016-01-07
forum: Ubuntu Application Development
---

### Post by os2 on 2016-01-07
Is there a way to scroll the contents of an ncurses pad or window without putting the contents into a buffer and then rewinding and forwarding the buffer?

Buffer usage seems expensive.

What is the typical way to scroll the contents in a CLI using ncurses especially when the contents fill the screen? I want to scroll the text which is off the standard screen viewport.

---

### Post by ajgreeny on 2016-01-07
If I want to do what you are trying to do in CLI I use ```
less filename
``` Repeat use of Enter goes to the end of the file and allows you to scroll up and down with the cursor keys.

Does that help, or perhaps you were aware of that and it is not what you need?  Maybe you have a good reason for wanting to use an ncurses interface?

---

