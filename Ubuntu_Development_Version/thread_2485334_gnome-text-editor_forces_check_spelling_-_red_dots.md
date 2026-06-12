---
title: "gnome-text-editor forces check spelling - red dots underscore"
date: 2023-03-27
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-03-27
Editing a .txt document i see many words underlined by red dots. Red dots disappear if I disable check spelling but after saving the documents next time red dots reappear.
I find no way to permanently disable Check Spelling.
[https://bugs.launchpad.net/ubuntu/+source/gnome-text-editor/+bug/2012931](https://bugs.launchpad.net/ubuntu/+source/gnome-text-editor/+bug/2012931)

---

### Post by jbicha on 2023-03-27
Does this still happen with gnome-text-editor 44.0?

---

### Post by zebra2 on 2023-03-28
[SIZE=4]**it's 44rc**[/SIZE]

---

### Post by corradoventu on 2023-03-28
after last updates i still have: 
```
corrado@corrado-n5-ll-0224:~$ apt policy  gnome-text-editor
gnome-text-editor:
  Installed: 44~rc-1
  Candidate: 44~rc-1
  Version table:
 *** 44~rc-1 500
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-n5-ll-0224:~$ 

```

---

### Post by BBQdave on 2023-03-28
> **corradoventu said:**
> Editing a .txt document i see many words underlined by red dots. Red dots disappear if I disable check spelling but after saving the documents next time red dots reappear. I find no way to permanently disable Check Spelling.

Might be missing the problem, but (Gnome) Text Editor 43.2 under the *view* tab you can disable spell check for the document you are viewing and that remains off after closing and opening the text document.

Not sure about Text Editor 44, is that a beta? Perhaps a bug?

---

### Post by corradoventu on 2023-03-28
gnome-text-editor:   Installed: 44~rc-1
I disable check spelling and save the document, next open check spelling is again active.

---

### Post by jbicha on 2023-04-02
Could you try again now that gnome-text-editor 44.0 is in Lunar? There have been some other updates too.

It works for me.

---

### Post by corradoventu on 2023-04-02
After removing check spelling and save next time check spelling is again active.
tested on 2 different installations on 2 partitions of the same PC

---

### Post by jbicha on 2023-04-02
Try looking at what's going on with gsettings:

```

gsettings get org.gnome.TextEditor spellcheck

```

You don't happen to have a different version of gnome-text-editor installed also, do you? As a snap or Flatpak?

Are you able to duplicate the issue from a Lunar live session using the Beta or a later daily ISO?

---

### Post by zebra2 on 2023-04-02
@jbicha
I'm using a default ubuntu re-installed in the past week 3/28/2023 (Ubuntu/Gnome 44.0/Wayland).  My Text Editor v44 correctly saves spell checker preference and survives a reboot. The dots do not appear when the spell checker is unchecked. The changes persist.  FYI

---

### Post by jbicha on 2023-04-02
Yeah, it works for me too.

---

### Post by corradoventu on 2023-04-03
same problem with system installed from Beta ISO on a different machine: Dell Inspiron 3793
on all my machines i'm using language english but italian keyboard, may affect?

Edit: NO, changing keyboard does not change problem

Edit: same problem with a live session from ISO dated 0402

---

### Post by corradoventu on 2023-04-04
```
corrado@corrado-n4-ll-beta:~$ gsettings get org.gnome.TextEditor spellcheck
true
corrado@corrado-n4-ll-beta:~$ 
```
It seems I can disable check spelling only on documents with size over 1MB

I created a document document slightly smaller than 1 MB, spellcheck is forced and i can't disable it. Added some lines to exceed 1 MB, now spellcheck disappear, I can enable it but is not saved.

---

