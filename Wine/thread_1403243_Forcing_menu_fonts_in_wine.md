---
title: "Forcing menu fonts in wine"
date: 2010-02-10
forum: Wine
---

### Post by oldmankit on 2010-02-10
I have successfully run and installed a Thai-English dictionary using wine version 1.0.1.  Fonts are displayed correctly, and I'm even able to select different fonts to display the English and Thai in each dictionary entry.

The only problems are that I cannot input words using Thai (question marks are displayed instead of characters), and that any menu items using Thai are displayed incorrectly.  I've attached a screenshot.  I need to be able to enter using Thai in order to search.

If I use the following command to start wine, I don't even get question marks when I enter Thai characters using the keyboard, I get nothing.  
```
LANG=th_TH.utf-8 wine ~/.wine/drive_c/thai_dictionary/dsdic.exe 
```

I can paste Thai from another program.  It displays correctly, however, it is not 'recognised' and found, it says ?????? not found.

The folder /usr/share/fonts/truetype contains both msttcorefonts and thai truetype fonts.  I can use these fonts successfully within the dictionary program to change the display font of the dictionary entries only, not menu items or keyboard input.

I have searched for over an hour but have not found any solutions.  I would be really grateful for a solution, as this would save me hours of page turning  in my paper dictionary!

---

### Post by dino99 on 2010-02-10
3 ways to go aheah:

- first: wine 1.0.1 is so old, better to install the last one
      [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

- second: add all your MS Windows fonts into wine fonts folder

- third: your problem is maybe related to one of your programs, not wine itself (workaround: progam+thai on google)

note: if you have personal work inside wine, back it up first, then erase /.wine before installing the new wine.

---

### Post by oldmankit on 2010-02-15
Thanks for the advice.   Following the instructions on the wine website, I've upgraded to version 1.1.38.  This did not fix it, but I've got some more information.

I tried running the dictionary on windows XP, and had the same error, with the notable difference that I was able to copy Thai words from an external application in to the dictionary, and it would successfully find the words and display the translation.  The difference is that under wine, I cannot type in Thai (squares display instead of characters), and if I paste from an external application, the word DISPLAYS properly in the search box, but it does not actually FIND the word in the dictionary and show the translations.  It says: "cannot find ?????"

What fixed everything in windows was running Microsoft AppLocale, which is used to display non-unicode programs (which this dictionary clearly is) under a specified character set.

So when I was calling LANG=th_TH.utf-8, that was actually the wrong idea.  The program doesn't use unicode (at least for its menus).

Trying this, unfortunately, doesn't help:
```
LANG=th_TH.tis-620 wine /media/cdrom/dsdic.exe
```I have not added my MS windows fonts to my wine folder because as stated in the OP the program clearly has access to them already.  Perhaps I misunderstand the rationale for copying the fonts across.

It looks like I might be facing two issues: one, how to display menus etc. in a Thai characterset, and two, how to actually input Thai words into the dictionary.

---

### Post by oldmankit on 2010-03-08
The reason 

```
LANG=th_TH.tis-620 wine /media/cdrom/dsdic.exe
```
did not work is because I hadn't properly added the Thai locale to my system.  It's now working well. :p

First I added the locale (th_TH TIS-620) using the instructions here: [http://code.google.com/p/winelocale/wiki/AddLocalesToDebian](http://code.google.com/p/winelocale/wiki/AddLocalesToDebian)

Then the following was successful:

```
LC_ALL=th_TH wine ~/.wine/drive_c/windows/notepad.exe
```Hey presto, notepad with Thai menus! How it translates from English to Thai I don't know, but it's very clever.

I am also finally able to use my dictionary, including searching and everything.  Lovely!

---

