---
title: "sed usage"
date: 2008-10-29
forum: The Cafe
---

### Post by maclenin on 2008-10-29
[B][update]

I will be adding lessons learned to this posting with [update]...stay tuned.[/B]

I would like to take full(er) advantage of sed....

I have already used it in this way...

```
sed -i 's/night/day/g' *.html
```

...to search and replace text within hundreds of similar files.

However, I was wondering whether sed might also be used in these ways:

1. To rename a set of files (while retaining a sequential integrity/format)...

...from:

abc_001.html
abc_002.html
...
abc_999.html

...to:

def_001.html
def_002.html
...
def_999.html

[B][update]

...one could use the rename command, and in this manner:

```
rename 's/abc/def/' *.html
```[/B]

2. To copy a single file, multiple times, while retaining/creating a definable sequential integrity/format...

...starting with:

xyz_000.html

...and ending up with:

xyz_000.html
xzy_001.html
xyz_002.html
...
xyz_999.html

3. To rename a group of differently-named files...

...from:

abc_001.jpg
water54.JPG
0004.jpg
...
xyz.gif

...to:

abc_001.jpg
abc_002.jpg
abc_003.jpg
...
abc_999.jpg

[B][update]

...I first use the "Rename" function within the Thunar file manager (though I would rather find a terminal-based option), by...

```
1. Selecting the group of files I wish to rename...
2. Right-clicking on the group of files and choosing "Rename"...
3. Selecting "Numbering" from the first drop-down menu...
4. Selecting "Name and Suffix" from the second drop-down menu...
5. Selecting "001, 002, 003" from the Number Format menu...
6. Selecting "Text - Number" from the Text Format menu...
7. Entering a Start With number - in this case: "1"...
8. Entering a Text name - in this case: "abc"...
9. Clicking on "Rename Files"...
```

...to create a standard and sequential naming convention.

...I then use the rename command in the terminal (from within the directory your files reside) to fine-tune the file names and append a relevant extension...

```
rename 's/abc_ (\d{3})/abc_$1\.jpg/' *
```

...et voila!


[/B]
 
Thanks for whatever advice you might provide.

---

### Post by maclenin on 2008-11-07
I have added an **[update]** or two....

---

### Post by Gamma746 on 2008-11-07
> **maclenin said:**
> 2. To copy a single file, multiple times, while retaining/creating a definable sequential integrity/format...

...starting with:

xyz_000.html

...and ending up with:

xyz_000.html
xzy_001.html
xyz_002.html
...
xyz_999.html


I would try ```
for i in `seq -w 1 999`; do cp xyz_000.html xyz_$i.html; done
```

---

### Post by conehead77 on 2008-11-07
Here is an excellent tutorial:

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

