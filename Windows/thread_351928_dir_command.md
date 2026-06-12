---
title: "dir command"
date: 2007-02-02
forum: Windows
---

### Post by lucia_engel on 2007-02-02
This is more a question than discussion.

In MS-DOS, typing this will get me the names of all the excel files output to list.txt (the /B option removes the dates and other details)
```
dir /B *.xls > list.txt
```

The problem is, the output will always include the extension:
ie.

A.xls
B.xls
B1.xls
etc.

Is there a way I can get a list of dir output without extension? Or do I need a script to delete the .xls part afterward :confused:

---

### Post by linuchsan on 2007-02-02
ls  *.xls |sed 's/.xls//g' >list.txt

---

### Post by lucia_engel on 2007-02-02
I guess I should clarify...I'm trying to do this in MS-DOS

---

### Post by linuchsan on 2007-02-03
Wrong forum then !!

---

### Post by kevinf311 on 2007-02-03
Actually this is the most correct forum on the site. Windows Discussions is for the discussion of windows. MS-DOS is decidedly windows. 

I wish I wasn't so rusty on the dos prompt.

There's a flag to supress parts of results isn't there? Or is it a flag to supress entire results?

How many files are we talking about here? You could just do it manually if it is only a few files.

The script idea might work. I imagine it would scan for '.xls' and delete the four characters including the '.' then look for the next one. Kinda a search and destroy script.

I wish I could be more helpful, but it's been years since I wrote a script for DOS. Good luck.

---

### Post by erlyrisa on 2007-02-04
R u making a joke?

-you can't realy do hard core things with a dos prompt alone - you need extra tools..

-forget cmd.exe and look into PowerShell - that should be able to format your output. -still technically hard though (there isn't a grep or anything like that but you can make your own scripts or fully fledged apps)

This and a freely modifiable kernel is why linux is king

---

### Post by erlyrisa on 2007-02-04
actually here is how ya do it.. 

A use wsh script or.

c:>

dir > text
start notepad text
alt e r
xls tab
alt 255
enter

---

### Post by lucia_engel on 2007-02-04
> **erlyrisa said:**
> R u making a joke?

-you can't realy do hard core things with a dos prompt alone - you need extra tools..


I don't really use dos much other than for ipconfig or ping so never really aware of its commands...or lack of.

I saw my supervisor at work doing it (without the /B flag) manually and just wanted to know if there's an easier way.

> c:>

dir > text
start notepad text
alt e r
xls tab
alt 255
enter

Hmm, that's replacing all xls with a null character right? I didn't even think of that. I'll try that out when I'm on Windows.

---

### Post by Phatfiddler on 2007-02-06
Wouldn't you need to use ".xls" instead of "xls" to remove the decimal as well?  The method posted above seems to work, but leaves the deciaml point.  Just a thought.

Also, try "dir /B > text" to keep the details out of the file as originally requested.

---

### Post by erlyrisa on 2007-02-08
whoops - forgot the dot! - which bring me to a pun:

.net would be easier - you just need to learn it.

---

