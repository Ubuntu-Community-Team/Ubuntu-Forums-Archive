---
title: "Wine Shortcuts"
date: 2009-12-20
forum: Wine
---

### Post by freestyleren on 2009-12-20
Is it possible to create shortcuts to wine programs, say in Applications > Office, or on the top panel?

I just succeeded in installing Microsoft Office, and I would like some shortcuts. There is no Wine > Programs option.

Thanks

---

### Post by akoskm on 2009-12-20
> **freestyleren said:**
> Is it possible to create shortcuts to wine programs, say in Applications > Office, or on the top panel?

I just succeeded in installing Microsoft Office, and I would like some shortcuts. There is no Wine > Programs option.

Thanks

Yes, it's possible. Create a "Launcher" on the desktop fill out the name and for command hit Browse and search for the office's executable (.exe). You'll find your office directory under
```

~/.wine/drive_c/Program Files/

```. If you found the exe file select it and click to the open.
Now in your Command area should be something like:
```

"/home/<username>/.wine/drive_c/Program Files/<patch to your office installation's exe>.exe".

```
, you need to write **wine** at the beginning of this text. So finally you have:
```

wine "/home/<username>/.wine/drive_c/Program Files/<patch to your office installation's exe>.exe".

``` in your Command box.
Click to OK.

---

### Post by freestyleren on 2009-12-20
Thanks man. Worked perfectly. :)

---

### Post by freestyleren on 2009-12-20
Do anyone know how I can make Word open files by doubleclicking them? At the moment opening files from word works fine, but I'd like to open files simply by doubleclicking them.

Edit: No worries I figured it out.

---

### Post by freestyleren on 2009-12-20
How do you set custom commands as default for opening files? I made a custom command that links to a script, so that when I double click the file it opens in word. I'd like it to do that with all .doc and .docx files.

---

### Post by akoskm on 2009-12-20
> **freestyleren said:**
> Do anyone know how I can make Word open files by doubleclicking them? At the moment opening files from word works fine, but I'd like to open files simply by doubleclicking them.

Edit: No worries I figured it out.

Great! I've just finished with my answer. :D
Good luck!

---

