---
title: "how to undo changes made with a script in a text file (changes are marked)"
date: 2012-05-28
forum: Server Platforms
---

### Post by legolas_w on 2012-05-28
I am wondering how can I undo changes I made to a text file using a script in case the user decides that s/he does not like my changes.

Let's say my changes are in a block that starts with ## story ## and ends with ## end story ##. Can you help me with an awk or sed or perl script that can locate such a block and remove it from the give file?

Thanks.

---

### Post by rubylaser on 2012-05-28
This should do it.  Here's your original file + edits.
```
Rubylasers-MacBook-Pro ~: cat input.txt
This is the original story...
isn't it great?
## story ##
Appended stuff in here...
Great stuff...
## end story ##
original story continues here...
```

To remove those blocks + the lines between them.
```
sed '/## story ##/,/## end story ##/d' input.txt > output.txt
```

Here's the result.
```
Rubylasers-MacBook-Pro ~: cat output.txt 
This is the original story...
isn't it great?
original story continues here...
```

---

