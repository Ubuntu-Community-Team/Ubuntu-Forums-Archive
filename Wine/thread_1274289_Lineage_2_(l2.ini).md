---
title: "Lineage 2 (l2.ini)"
date: 2009-09-24
forum: Wine
---

### Post by Raiju on 2009-09-24
I am having trouble editing the l2.ini file so i can disable the directx settings
```
1. Get l2encdec to decrypt the l2.ini
   [http://dstuff.l2wh.com/](http://dstuff.l2wh.com/)
2. Decrypt the l2.ini file:
   l2encdec.exe -s L2.ini myL2.ini
```
When i use the command this comes back 
```

xxx@xxxxx-desktop:~/Desktop/l2encdec_2.9.3$ wine l2encdec.exe -s L2.ini myL2.ini

fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored

Input file: "L2.ini"
Output file (given or generated): "myL2.ini"

Header: "Lineage2Ver413"
Action chosen: decode
Outer stream size: 3456
RSA pair #0 chosen (meaningful for 41x only).

RSA dec call.
Packs: 27
At 0/27....
RSA dec call completed.
Stream error detected during decompression.
There was an error during inner processing.

```

not sure what the problem is.

Could anyone who did this, upload their l2.ini somewhere?

---

