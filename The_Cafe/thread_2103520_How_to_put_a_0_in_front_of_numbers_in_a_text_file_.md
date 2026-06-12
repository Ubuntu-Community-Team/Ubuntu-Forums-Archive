---
title: "How to put a 0 in front of numbers in a text file in cygwin"
date: 2013-01-10
forum: The Cafe
---

### Post by YourSurrogateGod on 2013-01-10
Hi.

Basically, I have CSV file.  The contents of the file might look like this:
```

"08-41M",43,5,83,"M01",,
"08-41G",43,56,3,"M01",,
"08-41T",3,15,83,"M01",,

```
But I want it to look like this (notice the prepended 0s):
```

"08-41M",43,05,83,"M01",,
"08-41G",43,56,03,"M01",,
"08-41T",03,15,83,"M01",,

```
How would I do this?  And this has to work for numbers in those 3 columns only.  I'd do this by hand, but there are over 60,000 records :) .

---

### Post by steeldriver on 2013-01-10
well you could use 'awk' and print the specific fields with fixed width / zero-padding

```
$ awk -F"," '{ printf "%s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }' file.csv
"08-41M",43,05,83,"M01",,
"08-41G",43,56,03,"M01",,
"08-41T",03,15,83,"M01",,
```

---

### Post by YourSurrogateGod on 2013-01-10
> **steeldriver said:**
> well you could use 'awk' and print the specific fields with fixed width / zero-padding

```
$ awk -F"," '{ printf "%s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }' file.csv
"08-41M",43,05,83,"M01",,
"08-41G",43,56,03,"M01",,
"08-41T",03,15,83,"M01",,
```
This is what I got when I ran the command:
```
$ awk -F"," '{ printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }' MIRIAM-only-output.txt
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:          ^ syntax error
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:             ^ syntax error
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:                  ^ syntax error
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:                       ^ syntax error
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:                            ^ syntax error
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:                               ^ syntax error
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:                                  ^ backslash not last character on line
awk: cmd. line:1: { printf %s,%02d,%02d,%02d,%s,%s,\n", $1, $2, $3, $4, $5, $6 }
awk: cmd. line:1:                                  ^ syntax error

```

[edit]

Yeah, I got that error because I typed in the command by hand and made a stupid error somewhere.  When I copied and pasted, it worked fine.

Thanks for your help!

---

### Post by steeldriver on 2013-01-10
OK glad that worked for you - just be aware it is hard-coded for only the 6 fields per record shown in your snippet - so if your files can have more fields than that you will need to modify it

---

### Post by YourSurrogateGod on 2013-01-10
> **steeldriver said:**
> OK glad that worked for you - just be aware it is hard-coded for only the 6 fields per record shown in your snippet - so if your files can have more fields than that you will need to modify it

Yup, well aware.  Thanks for your help!

Now trying to get phpMyAdmin to not give me an Internal Server Error (runs on Apache) every time I try to upload the file :) .

---

