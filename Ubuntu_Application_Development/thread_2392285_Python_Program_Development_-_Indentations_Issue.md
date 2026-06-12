---
title: "Python Program Development - Indentations Issue"
date: 2018-05-19
forum: Ubuntu Application Development
---

### Post by sniper8752 on 2018-05-19
I am writing a Python script in notepad++ on win10 to be copied onto my Ubuntu server machine via ssh (copy n paste).  I set the EOL conversion in notepad++ to Unix.  When I try to run my script, it complains about the tabbing, which looks fine in notepad++.  What is the best way to develop like this, if the server does not have a gui?
Error:
```
    if os.path.isfile(snortRulesFileName+filename):                                                  ^
IndentationError: unindent does not match any outer indentation level

```
Graphical images of what the code looks like on both platforms.  You can see the indentation does not properly get copied over.

[ATTACH=CONFIG]279741[/ATTACH]

[ATTACH=CONFIG]279742[/ATTACH]

---

### Post by oldfred on 2018-05-19
Do not know notepad++.

But with Ubuntu I use geany.
But first thing is to change from tabs to 4 spaces in both preferences & projects. And set default to python. And a save file using spaces to replace all tabs.

You might be able to set up geany for python, like mine, and import & save file to see if spacing is corrected.

---

### Post by Carl H on 2018-05-21
Notepad++ is good for Windows but I've found the same issue with EOL when moving between OS. 

I find Geany to be much better for cross-platform development.   As Oldfred says, set the tabs to 4 spaces.

---

### Post by Skaperen on 2018-05-22
notepad will put in tabs for indentations long enough that tabs can be used.  generally this is 8 positions.  the python world prefers spaces instead of tabs because tabs make the indentation harder to work with, such as moving a block of code over because of things like a "for" clause or "if" clause being added or removed.  i am not surprised that it is now necessary in python.  the Windows version of python may still allow tabs.

there is a command called "expand" in Ubuntu which converts tabs to the proper number of spaces.  do "man expand" in a command line terminal to read more about it. it can read filenames given to it as arguments but always writes the file to standard output, so the way to use it (after the file is on Ubuntu) is:
```
expand mything.py > mything.tmp
mv mything.tmp mything.py
```

---

### Post by spjackson on 2018-05-22
I would suggest copying the file from Windows to Ubuntu rather than using copy & paste. e.g. use WinSCP.

---

