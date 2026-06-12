---
title: "What is fsck can't repair a filesystem"
date: 2007-04-02
forum: Server Platforms
---

### Post by endfx on 2007-04-02
When my server  boots up there is an unclean filesystem.
fsck fails.

Is there anything I can do when fsck can't repair the filesystem?

---

### Post by H3g3m0n on 2007-04-02
You need to get into the system and run fsck manually.

From memory you can just give it your root password after fsck dies, or boot from the cd and use the terminal.

```
fsck -vvy -C - /dev/hda1
```

should fix it, replace hda1 with your filesystem.

If you also want to check for badblocks add c after the y, it will take longer though.

The v's are for verbose so you know whats actually happening, y assumes yes to all questions (normally this is fine, and its pointless to check questions if you don't know what there about anyway, and theres generally on alternative choice :p ) -C is used to display a nice progress bar, the - is the destination file of the bar in this case - is special for stdout.

---

