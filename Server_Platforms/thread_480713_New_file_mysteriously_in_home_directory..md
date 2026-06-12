---
title: "New file mysteriously in home directory."
date: 2007-06-21
forum: Server Platforms
---

### Post by Gen2ly on 2007-06-21
Hello all.  Just wanted you all to know of a possible security issue.  I was just using terminal app and noticed an invisible (at least in nautilus) file.  This really surprised me as I have no idea how it got there.  The file doesn't appear to be of any harm.  It's zero bytes, but it's appearance concerned me.  If this is better placed in another forum could you let me know please.  I have no idea what may have cause this.  Is it best to file a report somewhere?

---

### Post by jimbob on 2007-06-21
Have no idea what it is or where it came from but if its empty it can't do you much harm.

I would delete it and see if it comes back.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Mr. C. on 2007-06-21
Did you visit the site MegaNova.com or try to download something from that site, via torrent or other ?

MrC

---

### Post by Gen2ly on 2007-06-21
> **Mr. C. said:**
> Did you visit the site MegaNova.com or try to download something from that site, via torrent or other ?

MrC

No, thats the really strange thing about it.  I never even knew it existed at all.

---

### Post by Mr. C. on 2007-06-21
It is most likely some form of state file; how it got we won't know for sure.  I'd suspect some app you ran, dropped the file in your home directory.  I personally would want to track down what program dropped that file, and would start backtracking my steps to understand the nature of the file.  Start by looking at the files creation date, and recalling what you did at that time.

Dot files are not "invisible" - they are merely not presented by default as they are typically used as state or preferences files.  One typically doesn't want to see these with each ls command (and in apps like Nautilus).

MrC

---

### Post by AlexThomson_NZ on 2007-06-22
The reason it does not show up in nautilus is because it has a ~ suffix, which is often used for backup files.  Default behaviour is to hide them

---

### Post by Mr. C. on 2007-06-22
Ah, that's pretty funny.  The ~ char in the picture was so small on my monitor, I thought it was a dot !

Oops,
MrC

---

### Post by kerry_s on 2007-06-22
my guess is it's a backup file for one of those games you have.

---

