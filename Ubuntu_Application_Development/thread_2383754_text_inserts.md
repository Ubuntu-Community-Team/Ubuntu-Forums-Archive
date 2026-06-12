---
title: "text inserts"
date: 2018-01-29
forum: Ubuntu Application Development
---

### Post by rimidalv on 2018-01-29
Hello.
It is needed for my app to insert text in any opened window in system (in current position of the cursor). I tried xdotool (lib and console program) and xvkbd, but both of them work bad with big texts and special characters.
My app is wrote with Python 3. Used system - Ubuntu 14.
I would be glad any ideas and decisions.

---

### Post by TheFu on 2018-01-29
Welcome to the forums.

Suggestion: Make a CLI version of "your app" that accepts either a FIFO, named pipe or stdin for input.

IMHO, trying to playback text entry via an external program is a hack and will always be prone to errors.

You can also check "alternativeTo.net" for other options.

---

