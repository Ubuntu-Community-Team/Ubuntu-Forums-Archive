---
title: "Wine 1.0.1 Issue with menu text"
date: 2009-04-13
forum: Wine
---

### Post by andy17299 on 2009-04-13
Hi Everyone,

I'm new to the forums and new to ubuntu/linux. Anyways I'm having an issue with Wine 1.0.1 I installed it and when I load the configuration for wine I don't see any menu text. Refer to my images. I also had issues with open office where i had a similar issue and it was because of anti-lacing with the font. I don't know if both correlated. Thanks in advance for any help.

---

### Post by cogadh on 2009-04-13
From [this thread]("http://ubuntuforums.org/showthread.php?t=244623#8"):
1) Create a "settings.txt" file with your favorite text editor (vi, emacs or the Gnome Text Editor under Acessories) with the following three lines:

```
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"
"ClientSideWithCore"="N"
```

(there should be no extra spaces - for example, a space before or after the equal (=) symbol will cause you trouble).
2) Execute the following command:

    regedit settings.txt

3) Run a wine app, for example:

    winecfg

---

### Post by andy17299 on 2009-04-13
oh wow cool thanks.

---

### Post by gatorbrit on 2009-04-23
I have a similar problem.  I can get the fonts to show correctly in winecfg, but when I load a document in to word 2007 the document fonts are garbled just like how they are described above.
I added the lines
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"
"ClientSideWithCore"="N"
to the registry and without these the fonts in winecfg are messed up to.  So these seem to solve part of the problem.  But not the document fonts in word.   

Any ideas?

---

