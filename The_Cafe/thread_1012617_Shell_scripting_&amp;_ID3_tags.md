---
title: "Shell scripting &amp; ID3 tags"
date: 2008-12-16
forum: The Cafe
---

### Post by blazemore on 2008-12-16
I know next to nothing about shell scripting.

Is it possible to feed a script a folder, and have it go through (including subdirectories), renaming every file it finds according to its ID3 tags:

```
/home/user/Music/%Artist/%Album/%Title
```

While keeping the extension the same

---

### Post by kpkeerthi on 2008-12-16
Why not [easytag]("http://easytag.sourceforge.net/"), [audio tag tool]("http://pwp.netcabo.pt/paol/tagtool/") and exfalso ? The tools can rename files/folders based on ID3 tags.

Thunar (bulk rename) can also do this.

---

### Post by Trail on 2008-12-16
Also amarok can do it (both 1.4 and 2.0 i think).

---

### Post by saulgoode on 2008-12-16
Here is a one-liner BASH command using GNU's AWK processor and the [id3v2]("http://sourceforge.net/projects/id3v2/") tag editor. I don't think id3v2 works with OGG tags (there are other command line tools which support both) but this was more to provide a proof-of-concept for writing your own script -- which should probably have some error checking :) and handle spaces in the source path better (I'm converting them to underscores). 

> FILE=/some/dir/some.mp3 ; BASE=$(basename $FILE) ; EXT=${BASE##*.} ; TGTDIR=$(id3v2 -R $FILE | awk 'BEGIN { FS=": "; OFS=""; } /^TP1/ { $1=""; gsub(" ","_"); artist=$0; } /^TAL/ { $1=""; gsub(" ","_"); album=$0; } END { print artist "/" album "/" }') ; mkdir -p $TGTDIR ; TGTBASE=$(id3v2 -R $FILE | awk 'BEGIN { FS=": "; OFS=""; }  /^TT2/ { $1=""; gsub(" ","_"); title=$0;} END { print title }') ; mv $FILE ${TGTDIR}${TGTBASE}.$EXT

---

### Post by tbroderick on 2008-12-16
> **Trail said:**
> Also amarok can do it (both 1.4 and 2.0 i think).

+1
Amarok 1.4 does this very well.

---

