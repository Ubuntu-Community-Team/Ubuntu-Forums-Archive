---
title: "Strange Wine behaviour (simple app)"
date: 2009-02-15
forum: Wine
---

### Post by oleksus on 2009-02-15
Hi everyone. I've been using a simple text proggie with Cyrillic letters (which I got working with the simple script)

Then something got updated and now that proggie is gone weird, giving me such message:
```
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
fixme:imagelist:ImageList_DrawIndirect ILS_ALPHA: unimplemented!

```
It won't react to pressing Enter, and does glitchy interaction with keyboard.

I wonder, how could this happen, and what could've been the wrong thing?

---

### Post by oleksus on 2009-02-15
:confused:

---

### Post by Dizzle7677 on 2009-02-16
"something got updated"? 

Wine or the app got updated? Either way you can always reinstall the version that did work before, right?

---

### Post by oleksus on 2009-02-17
No, something *else* got updated, not wine or the app. (that small app works without install, it was made with Borland C++Builder and it's a simple sort of text editor).

Should I try purging and reinstalling wine? The error message says something about richedit. What's that? Could the installation of microsoft fonts be the cause of the error?

---

### Post by oleksus on 2009-02-17
bumpy-bump!
anyone got any idea about the code posted above?
still the proggie doesn't work properly, and its frustrating.

What's that 'richedit' thing it says?
:(

---

### Post by david_kt on 2009-02-18
> **oleksus said:**
> bumpy-bump!
anyone got any idea about the code posted above?
still the proggie doesn't work properly, and its frustrating.

What's that 'richedit' thing it says?
:(

May be you could try:

```
WINEDLLOVERRIDES="riched20=n,b" wine your_program.exe
```

DK

---

### Post by oleksus on 2009-02-22
Thanks for advice, tried it, the console says less this time,
```
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub

```

BUT the problem with editing (no reaction to ENTER key) still remains.

Maybe there's some other option? Too bad I don't quite understand what it wants.:(

---

### Post by david_kt on 2009-02-22
> **oleksus said:**
> 
BUT the problem with editing (no reaction to ENTER key) still remains.

Maybe there's some other option? Too bad I don't quite understand what it wants.:(

Open terminal and follow below series of commands one by one, according to the sequence:

```
wget http://www.kegel.com/wine/winetricks

chmod +x winetricks

./winetricks riched20
```

If the above 3 commands completed successfully, try again to run your program normally:

```
wine your_program.exe
```

I hope that will help.

DK

---

### Post by oleksus on 2009-02-22
:D Yippeee!!! It worked! 

Thank you! I've heard about winetricks but never knew how to use them. 
Now the issue is solved!

Thanks a million! 
Bless this community. :KS

---

