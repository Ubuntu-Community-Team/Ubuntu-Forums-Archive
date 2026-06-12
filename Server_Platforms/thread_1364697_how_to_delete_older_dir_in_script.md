---
title: "how to delete older dir in script"
date: 2009-12-26
forum: Server Platforms
---

### Post by toshko3 on 2009-12-26
This is the script I use:
[I]#!/bin/bash
ls -tad /media/backup/* | tail -1 | head -1 > mim.txt
rm -R 'cat /root/scripts/backup/mim.txt'[/I]


The output of cat /root/scripts/backup/mim.txt is:
*/media/backup/1*
Which is correct.
But when I execute the script, the second line is outputting:
*rm: cannot remove `cat /root/scripts/backup/mim.txt': No such file or directory*
Could anyone tell me, where I'm wrong???
:(

---

### Post by sisco311 on 2009-12-26
```
man bash | less --pattern\="Command Substitution"
```

it's:
```
rm -R $(cat /root/scripts/backup/mim.txt)
```
or

```
rm -R `cat /root/scripts/backup/mim.txt`
```

---

### Post by toshko3 on 2009-12-26
Thanks!!!!!!!!!!
I was trying to do this over a day long!
May be sometimes man is better than google :oops:

---

