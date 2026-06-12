---
title: "how to open Truecrypt volume on other computer?"
date: 2008-05-11
forum: Security
---

### Post by grashdur on 2008-05-11
Truecrypt users: When I open Truecrypt and "browse" for an encrypted volume file to open, I don't have the option of looking through my network to my other computer. How to do this? 

If I can't open a volume on another computer, then I have to copy the same volume back and forth between computers, which could lead to a copying or editing mistake and thus a loss of new data, or perhaps to a corrupted file to do copying it many times over. I think opening on a different computer shouldn't be a problem, because Cryptainer (which works on Windows) doesn't raise any fuss about doing this.

---

### Post by chewearn on 2008-05-12
> **grashdur said:**
> Truecrypt users: When I open Truecrypt and "browse" for an encrypted volume file to open, I don't have the option of looking through my network to my other computer. How to do this? 

If I can't open a volume on another computer, then I have to copy the same volume back and forth between computers, which could lead to a copying or editing mistake and thus a loss of new data, or perhaps to a corrupted file to do copying it many times over. I think opening on a different computer shouldn't be a problem, because Cryptainer (which works on Windows) doesn't raise any fuss about doing this.

Due to some reasons (too wordy for me to explain right now), truecrypt (and other programs) cannot see the network drives mounted thru gnome networking.

Instead, use the traditional mount command from command line.  To find out how to use mount, read the manual pages:
```
man mount
```

---

