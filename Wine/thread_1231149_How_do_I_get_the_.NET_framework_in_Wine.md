---
title: "How do I get the .NET framework in Wine?"
date: 2009-08-04
forum: Wine
---

### Post by Tux118 on 2009-08-04
[SIZE=5][B]How do I get the .NET framework into wine?

[/B][SIZE=2]Will somebody please answer this question?[/SIZE]
[/SIZE]

---

### Post by wojox on 2009-08-04
I don't think you can. May need Mono.
[http://appdb.winehq.org/viewbugs.php?bug_id=13995](http://appdb.winehq.org/viewbugs.php?bug_id=13995)

---

### Post by YokoZar on 2009-08-04
winetricks is what you want: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) -- just install .net 2.0 with it.  Or Mono 2.2, which is supposed to be equivalent

---

### Post by Tux118 on 2009-08-04
> **wojox said:**
> I don't think you can. May need Mono.
[http://appdb.winehq.org/viewbugs.php?bug_id=13995](http://appdb.winehq.org/viewbugs.php?bug_id=13995)

Thanks, this worked like a charm.

> **YokoZar said:**
> winetricks is what you want: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) -- just install .net 2.0 with it.  Or Mono 2.2, which is supposed to be equivalent

I'm sure this would have also worked too.

Thanks a lot guys! :)

---

### Post by YokoZar on 2009-08-04
Be aware that I have encountered at least one app that worked with .net 2.0 but not mono 2.2 -- though this may have been a Wine bug rather than a Mono bug.

---

