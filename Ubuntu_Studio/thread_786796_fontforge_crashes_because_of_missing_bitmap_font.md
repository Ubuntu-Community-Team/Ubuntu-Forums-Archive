---
title: "fontforge crashes because of missing bitmap font"
date: 2008-05-08
forum: Ubuntu Studio
---

### Post by Kakurady on 2008-05-08
Fontforge terminates abruptly when trying to display an error window in Chinese.
It also does so when I'm trying to let it display glyph images instead of character names.
```
nekoyasha@Nekokoneko:~/apps/fontforge/bin$ ./fontforge
Copyright (c) 2000-2008 by George Williams.
 Executable based on sources from 00:29 GMT 29-Apr-2008.
 Library based on sources from 20:49 GMT 30-Apr-2008.
Error attempting to load font:
  -wenquanyi-wenquanyi zenhei-medium-r-normal--16-0-0-0-p-0-gb2312.1980-0
The X Server clained the font existed, but when I asked for it,
I got this error instead:

X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  45.0 (X_OpenFont)
  Serial number of failed request:  31485
  Failed resource ID:  480013f
&#24573;&#30053;
nekoyasha@Nekokoneko:~/apps/fontforge/bin$ 
```

---

