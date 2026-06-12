---
title: "Extremely frustrated"
date: 2009-02-04
forum: Wine
---

### Post by pete44444444 on 2009-02-04
Ok I changed the dpi on wine to a really big#. I can't change it back because when I open the wine settings, the window is huge and it will not let me resize it. Since it is so ****** big I can't even click apply changes to change the ****** back. PLEASE HELP. 
Ps I don't speak geek. No offense.
:<
:(
:-(
:-<

---

### Post by BlackMeTaL on 2009-02-04
Open the file ~/.wine/system.reg

Try changing the line that starts with "LogPixels" so it looks like this:
"LogPixels"=dword:00000060

---

### Post by pete44444444 on 2009-02-05
> **BlackMeTaL said:**
> Open the file ~/.wine/system.reg

Try changing the line that starts with "LogPixels" so it looks like this:
"LogPixels"=dword:00000060

Ok I'm new to Ubuntu so i don't know how to navigate to the file. I ran a search and no files were found.

---

### Post by Tony Flury on 2009-02-05
1) Open a terminal - click the icon that should be in your top Panel or goto the menu Applications -> Accessories.

2) in the terminal type :
```

gedit ~/.wine/system.reg

```

3) Make the changes suggested by BlackMeTaL

4) Save the file

5) close the editor - and try running the wine thing again.

---

### Post by vtikha on 2009-02-05
This is a hidden file. Go to your home directory, do ctrl+h to show the hidden files, find .wine and do the required changes to the system.reg file using a text editor of your choice.

---

### Post by pete44444444 on 2009-02-05
I got it! Thanks to everyone!:p:p:p:):):D:D;)

---

