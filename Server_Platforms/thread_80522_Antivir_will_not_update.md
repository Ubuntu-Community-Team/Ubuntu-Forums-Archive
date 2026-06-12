---
title: "Antivir will not update"
date: 2005-10-22
forum: Server Platforms
---

### Post by fannymites on 2005-10-22
Does anyone have any experience of Antivir on ubuntu?
I've installed Antivir and although I set it to auto update, I keep being told that "antivir.vdf" is more than 14 days old.
I tried doing a manual update and after about 20 minutes of a blinking cursor, I get this - ```
00.00.00.00 <=> 06.32.00.60 [vdf database (part 0), on-disk]
00.00.00.00 <=> 06.32.08.00 [vdf database (part 1), on-disk]
00.00.00.00 <=> 06.32.10.00 [vdf database (part 2), on-disk]
00.00.00.00 <=> 06.32.10.03 [vdf database (part 3), on-disk]
06.32.00.56 <=> 06.32.00.56 [scan engine, running]
02.01.04.20 <=> 02.01.04.20 [main program, running]
antivir0.vdf   0% |                          |    0 KB    0.00 KB/s  --:-- ETA

```
And that's it, it never actually does anything.
It's the same whether run as regular user or with sudo.  Both root and regular user are added to the Antivir group.
Can anyone give me any idea what is going wrong?

Just in case this has anything to do with it, when I try to open the Antivir gui as regular user, it gets as far as "initiating network" then hangs forever.
When run with sudo it opens fine.

[Edit]  Nevermind.  After another half an hour it finally started updating.  I've also read on Wilders Security forums that there are problems with Antivir servers being very slow.  Still having the problem running the gui as normal user though.

---

