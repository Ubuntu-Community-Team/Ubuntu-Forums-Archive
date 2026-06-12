---
title: "OGV to MPG/AVI conversion script help"
date: 2009-06-17
forum: Ubuntu Studio
---

### Post by TheBuzzSaw on 2009-06-17
[http://ubuntuforums.org/showthread.php?t=665836](http://ubuntuforums.org/showthread.php?t=665836)

```
mencoder -idx input.ogv -ovc lavc -oac mp3lame -o output.avi
```
This code has helped out immensely, but I have a few questions.

Can I convert to mpg instead? What would I have to change in this line besides the file extension?

Also, could someone help me convert this into a bash script? I know some basic bash scripting, but I've not worked with script parameters before.

---

### Post by raboofje on 2009-06-17
> **TheBuzzSaw said:**
> ```
mencoder -idx input.ogv -ovc lavc -oac mp3lame -o output.avi
```

Can I convert to mpg instead? What would I have to change in this line besides the file extension?

Check out the section on '-lavcopts' in the manpage

> Also, could someone help me convert this into a bash script? I know some basic bash scripting, but I've not worked with script parameters before.

What do you need to know? Most bash tutorials probably show you how to use script parameters.

---

