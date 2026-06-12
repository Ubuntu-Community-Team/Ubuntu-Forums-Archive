---
title: "Editing Large Txt Files (100mb)"
date: 2009-02-18
forum: The Cafe
---

### Post by Johnsie on 2009-02-18
Hi, I'm trying to open a 100mb text file to see how many lines there are in it.

Gedit doesn't handle things too well (probably because I only have 500mb ram). Can anyone suggest a text editor that would help me do this or another way to find out how many lines are in the text file?

Thanks,

John

---

### Post by Johnsie on 2009-02-18
Nevermind, I got someone in the data department to do it using Visual Fox.

---

### Post by Kvark on 2009-02-18
Quickest way to count the lines in a text file, so you know for next time:
```
wc -l file.txt
```
You can also do wc -w to count number of words and wc -m to count number of characters. Just wc file.txt without options prints 3 numbers without explanation, the first is lines, the second is words and third is file size in bytes.

---

### Post by Johnsie on 2009-02-18
Nice, I ran that and it worked almost instantly.

+1 for Linux

---

### Post by rax_m on 2009-02-18
Also, if you ever do need to actually open such a large file, I find the vi works great (or cream, if you're looking for a gui version).

---

