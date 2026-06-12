---
title: "Broke my dual boot with Windows by installing Pop!_OS over Manjaro, boot-repair"
date: 2020-02-18
forum: Ubuntu/Debian BASED
---

### Post by bogzzzzz on 2020-02-18
[https://paste.ubuntu.com/p/NdNqTTpqjq/](https://paste.ubuntu.com/p/NdNqTTpqjq/)

Above is the pastebin created by boot-repair with recommended settings.

Any ideas on how to fix it? When I boot up I get a GRUB CLI, and I have to type exit to get to the default boot menu. I can boot into both Windows and Pop!_OS from there.

---

### Post by oldfred on 2020-02-18
Moved to Other OS sub-forum since POP issue.

```
Boot0000* Windows Boot Manager	HD([COLOR=#ff0000]2[/COLOR],GPT,448ada60-3d2d-4fe7-ad32-4acf8b8adf74,0x109000,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot0001* ubuntu	HD([COLOR=#ff0000]5[/COLOR],GPT,2de9a473-d786-43b0-ac0a-dde555a5bc82,0x355e1000,0x1fffff)/File(EFIubuntushimx64.efi)
Boot0002* Manjaro	HD([COLOR=#ff0000]2[/COLOR],GPT,448ada60-3d2d-4fe7-ad32-4acf8b8adf74,0x109000,0x32000)/File(EFIManjarogrubx64.efi)
Boot0003* Pop!_OS 19.10	HD([COLOR=#ff0000]5[/COLOR],GPT,2de9a473-d786-43b0-ac0a-dde555a5bc82,0x355e1000,0x1fffff)/File(EFIsystemdsystemd-bootx64.efi)
```

You can only have one ESP - efi system partition per drive. You are showing 2. Some systems may boot from a second FAT32. Often vendors set up a second FAT32 for vendor specific repair or reset files.

You also show in line 1102 grub creating a .new file.
That means you have some typo in your grub scripts or grub configuration file.
I had that once with my 40_custom and a missing unmatched }, error was on last line so took a bit to find where error really was somewhere in middle of file.

---

