---
title: "RSYNC question regarding the --delete and --exclude  switches."
date: 2008-09-21
forum: Server Platforms
---

### Post by Luke has no name on 2008-09-21
Let's say I have /home/luke/from and /home/luke/to directories. 

from:
Music/
Videos/
Videos/blah.avi
hello.txt

to:
Music/
Videos/

I want to rsync the from/ and to/ directories using --delete on all files and folders in from/ EXCEPT the Videos/ folder. In other words, the to/ dir has files from/ doesn't, and I want to keep them.

Can I do 

rsync -avze ssh --delete /home/luke/to/ /home/luke/from/ --exclude /home/luke/to/Videos/

?? I don't know the --exclude tag too well.

---

### Post by baeksu on 2008-09-21
The --exclude flag will exclude that path from sync altogether. So with your command 'rsync -avze ssh --delete /home/luke/to/ /home/luke/from/ --exclude /home/luke/to/Videos/', you would sync (with --delete) Music folder plus files in the root folder (hello.txt in your example). Everything in Videos folder on both ends would remain untouched.

If that's not what you want, it's better you run rsync two times. First with --delete while excluding Videos, second just Videos but without --delete. Something like this should do it:
```
rsync -avze ssh --delete /home/luke/to/ /home/luke/from/ --exclude /home/luke/to/Videos/
rsync -avze ssh /home/luke/to/Videos /home/luke/from/Videos
```

---

### Post by Luke has no name on 2008-09-21
Sounds like you answered my question right. Thanks.

---

