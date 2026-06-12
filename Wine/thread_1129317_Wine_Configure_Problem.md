---
title: "Wine Configure Problem"
date: 2009-04-18
forum: Wine
---

### Post by Lex-Man on 2009-04-18
I've been stupid and set the default wine text way too large and then made the window area tiny.

What file can I edit to manually change these back to something a tad more sensible.

Thanks

Lex-Man

---

### Post by NightMKoder on 2009-04-18
Please don't post duplicate threads.

I'm assuming you set your DPI too high in winecfg, so open a terminal and do
```

wineserver -k
sed -ibak 's@"LogPixels"=.*@"LogPixels"=dword:00000060@g' ~/.wine/system.reg

```

Which should set your fonts back to normal (96 DPI).

---

### Post by Lex-Man on 2009-04-18
Thanks, for that it helped but I still need to change the Wine Desktop size cause it is tiny.

---

### Post by NightMKoder on 2009-04-18
```

wine explorer /desktop=ref,800x600 winecfg

```

Will let you open winecfg in a decent-sized desktop.

---

### Post by Lex-Man on 2009-04-18
Sweet thanks very much.

---

