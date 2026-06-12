---
title: "Script question (burn all of certain extension to CD)"
date: 2008-11-11
forum: Server Platforms
---

### Post by TheGameAh on 2008-11-11
Hey guys.

Should be simple, I think, but the syntax evades me.

Have a 150 gigabyte Samba share.

I want to move all files out of the samba share with a .jpg extension.  Then I'll burn those files to a  CD/DVD.

The burning part isn't a problem.  But how do I traverse through a directory structure, find .jpgs, and move them out?

---

### Post by sprouty on 2008-11-11
Hi,

where "/where/the/share/i" change to sambe directory
"find /where/the/share/is -name *.jpg" >filelist.txt
then is you type

for d in `less filelist.txt`
do
mv $d /jpg/
done

then all you files should be in the jpg directory. if you want to keep them you may want to change mv to cp.

Hope this helps!

---

### Post by TheGameAh on 2008-11-11
Thank you much.

This seemed to work okay on file/directories without spaces.

But how do you account for the spaces?

---

### Post by victorbrca on 2008-11-11
You need to use " for files with spaces:

```
for i in $(find . -name *.jpg) ; do
   mv "$i" "[location]"
done
```

Or do it all in one shot:
```
find . -name '*.jpg' -exec mv {} [location] \;
```
Note: not a sure about spaces on the second. Try it out on a test folder first.


Vic.

---

### Post by TheGameAh on 2008-11-12
Actually this didn't seem to do the trick either (putting quotes around the variable).

---

### Post by victorbrca on 2008-11-12
How about the second option? I just did that two days ago on a spare HD I have.

---

